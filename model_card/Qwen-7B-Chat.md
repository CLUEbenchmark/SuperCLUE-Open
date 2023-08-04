# Qwen-7B-Chat
| 🤗[Huagging Face](https://huggingface.co/Qwen/Qwen-7B-Chat) | 🤖 [ModelScope](https://modelscope.cn/models/qwen/Qwen-7B-Chat/summary) | [GitHub](https://github.com/QwenLM/Qwen-7B) | [Demo](https://modelscope.cn/studios/qwen/Qwen-7B-Chat-Demo/summary) | [Report](https://github.com/QwenLM/Qwen-7B/blob/main/tech_memo.md) |

SuperCLUE-Open 采用以下代码进行测评：

```
import os 
os.environ['TRANSFORMERS_CACHE'] = './weight'
from fastapi import FastAPI, Request
import uvicorn
import torch
from transformers import AutoModelForCausalLM, AutoTokenizer
from transformers.generation import GenerationConfig

app = FastAPI()

@app.post('/api/api_server_03')
async def chat_completion(request: Request):
    data = await request.json()
    prompt = data['prompt']
    print(prompt)
    history = data['history']
    if len(history) == 0:
        print('First time to chat...')
        history = None
    response, history = model.chat(tokenizer, prompt, history=history)
    return {'response': response, 'history': history}


if __name__ == '__main__':
    tokenizer = AutoTokenizer.from_pretrained("Qwen/Qwen-7B-Chat", trust_remote_code=True)
    ## 打开bf16精度，A100、H100、RTX3060、RTX3070等显卡建议启用以节省显存
    # model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen-7B-Chat", device_map="auto", trust_remote_code=True, bf16=True).eval()
    ## 打开fp16精度，V100、P100、T4等显卡建议启用以节省显存
    # model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen-7B-Chat", device_map="auto", trust_remote_code=True, fp16=True).eval()
    # 默认使用fp32精度
    model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen-7B-Chat", device_map="auto", trust_remote_code=True).eval()
    model.generation_config = GenerationConfig.from_pretrained("Qwen/Qwen-7B-Chat", trust_remote_code=True) # 可指定不同的生成长度、top_p等相关超参
    print(f'temperature: {model.generation_config.temperature}')
    print(f'max_new_tokens: {model.generation_config.max_new_tokens}')
    # temperature: 1.0
    # max_new_tokens: 512
    uvicorn.run(app, host='0.0.0.0', port=9103)

'''
执行命令：
conda activate llama
CUDA_VISIBLE_DEVICES=0 nohup python -u api_qwen_7b_chat.py > qwen.log 2>&1 &
'''
```

以上代码修改自：https://github.com/QwenLM/Qwen-7B#-transformers