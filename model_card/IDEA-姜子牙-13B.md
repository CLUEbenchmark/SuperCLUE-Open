# IDEA-姜子牙-13B
| 🤗[Huagging Face](https://huggingface.co/IDEA-CCNL/Ziya-LLaMA-13B-v1.1) | [GitHub](https://github.com/IDEA-CCNL/Fengshenbang-LM) | [Homepage](https://fengshenbang-lm.com/) | 

SuperCLUE-Open 采用以下代码进行测评：

```
import os
os.environ['CUDA_VISIBLE_DEVICES'] = '0'
from transformers import AutoTokenizer
from transformers import LlamaForCausalLM
import torch
from flask import Flask, request, jsonify
import jsonlines
import time
import regex as re
app = Flask(__name__)
app.config['JSON_AS_ASCII'] = False
import threading
m_lock = threading.Lock()

device = torch.device("cuda")
model_path='../pretrained/IDEA-CCNL/Ziya-LLaMA-13B-v1.1'
model = LlamaForCausalLM.from_pretrained(model_path).half().cuda()
tokenizer = AutoTokenizer.from_pretrained(model_path)


@app.route('/api/jiangziya', methods=['POST'])
def api_chat():
    with m_lock:
        t0 = time.time()
        data = request.get_json()
        message = data['message']

        prompt = ''
        for line in message:
            if line['role'] == 'user':
                prompt += f"\n<human>:{line['content']}\n<bot>:"
            elif line['role'] == 'assistant':        
                prompt += line['content']
        prompt = prompt.strip()
        prompt = prompt[-512:]
        
        input_ids = tokenizer(prompt, return_tensors="pt").input_ids.to(device)
        generate_ids = model.generate(
                    input_ids,
                    max_new_tokens=512,
                    do_sample = True, 
                    top_p = 0.85, 
                    temperature = 1.0, 
                    repetition_penalty=1., 
                    eos_token_id=2, 
                    bos_token_id=1, 
                    pad_token_id=0)
        response = tokenizer.batch_decode(generate_ids)[0]
        response=response.split('<bot>   : ')[-1]
        response=response.replace('</s>','')
        print(response)

        item={
                'prompt':str(prompt),
                'answer':str(response),
                't':time.time()-t0
            }

        return jsonify({'result': response})


if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5005)

'''
nohup python -u idea_jiangziya.py > jiangziya.log 2>&1 &
'''
```
