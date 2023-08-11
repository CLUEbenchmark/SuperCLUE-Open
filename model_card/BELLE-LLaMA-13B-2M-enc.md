# BELLE-LLaMA-13B-2M-enc
| 🤗[Huagging Face](https://huggingface.co/BelleGroup/BELLE-LLaMA-13B-2M-enc) | [GitHub](https://github.com/LianjiaTech/BELLE) |

SuperCLUE-Open 采用以下代码进行测评：

```
import os
os.environ['CUDA_VISIBLE_DEVICES']='2'
import torch
from transformers import LlamaForCausalLM, LlamaTokenizer
from flask import Flask, request, jsonify
import time
import threading
m_lock = threading.Lock()

ckpt = '../pretrained/BELLE-LLaMA-13B-2M-enc'
device = torch.device('cuda')
tokenizer = LlamaTokenizer.from_pretrained(ckpt)
print('loading model')
model = LlamaForCausalLM.from_pretrained(ckpt).half().to(device)
print('loading finished')

app = Flask(__name__)
app.config['JSON_AS_ASCII'] = False
@app.route('/api/belle', methods=['POST'])
def api():
    with m_lock:
        t0=time.time()
        data = request.get_json()
        message=data['message']
        prompt=''
        for line in message:
            if line['role']=='user':
                prompt+=f"Human: {line['content']} \n\nAssistant: "
            elif line['role']=='assistant':        
                prompt+=line['content']+'\n'

        input_ids = tokenizer(prompt, return_tensors="pt").input_ids.to(device)
        generate_ids = model.generate(input_ids, max_new_tokens=1024, do_sample = True, top_k = 30, top_p = 0.85, temperature = 0.5, repetition_penalty=1., eos_token_id=2, bos_token_id=1, pad_token_id=0)
        output = tokenizer.batch_decode(generate_ids, skip_special_tokens=True, clean_up_tokenization_spaces=False)[0]
        response = output[len(prompt):]
        print(response)

        item={
                'prompt':str(prompt),
                'answer':str(response),
                't':time.time()-t0
            }

        return jsonify({'result': response})


if __name__ == '__main__':
    app.run(host='0.0.0.0', port=9004)
'''
conda activate belle
nohup python -u belle-13b_api.py > belle.log 2>&1 &
'''
```