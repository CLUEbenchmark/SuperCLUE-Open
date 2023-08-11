# Baichuan-7B
| 🤗[Huagging Face](https://huggingface.co/baichuan-inc/Baichuan-7B) | 🤖[ModelScope](https://modelscope.cn/organization/baichuan-inc) | [GitHub](https://github.com/baichuan-inc/baichuan-7B) |

SuperCLUE-Open 采用以下代码进行测评：

```
from transformers import AutoModelForCausalLM, AutoTokenizer
from fastapi import FastAPI, Request
import uvicorn, json
import torch

app = FastAPI()

@app.post("/")
async def create_item(request: Request):
    global model, tokenizer
    json_post_raw = await request.json()
    json_post = json.dumps(json_post_raw)
    json_post_list = json.loads(json_post)
    prompt = json_post_list.get('prompt')
    print('来自用户的输入', prompt)

    inputs = tokenizer(prompt, return_tensors='pt')
    inputs = inputs.to('cuda:0')
    pred = model.generate(**inputs, max_new_tokens=64, repetition_penalty=1.1)
    return tokenizer.decode(pred.cpu()[0], skip_special_tokens=True)


if __name__ == '__main__':
    torch.cuda.set_device(0)
    tokenizer = AutoTokenizer.from_pretrained("../baichuan-7B", trust_remote_code=True)
    model = AutoModelForCausalLM.from_pretrained("../baichuan-7B", device_map="auto", trust_remote_code=True)
    model.eval()
    uvicorn.run(app, host='0.0.0.0', port=8222, workers=1)
'''
CUDA_VISIBLE_DEVICES=0 nohup python -u api.py > baichuan-7b.log 2>&1 & 
'''
```

以上代码修改自：https://github.com/baichuan-inc/baichuan-7B#%E6%8E%A8%E7%90%86%E6%96%B9%E6%B3%95