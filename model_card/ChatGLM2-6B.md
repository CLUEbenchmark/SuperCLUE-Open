# ChatGLM2-6B
| 🤗[Huagging Face](https://huggingface.co/THUDM/chatglm2-6b) | [GitHub](https://github.com/THUDM/ChatGLM2-6B) | [chatglm.cn](https://chatglm.cn/) | [WeChat](https://github.com/THUDM/ChatGLM2-6B/blob/main/resources/WECHAT.md) |

SuperCLUE-Open 采用以下代码进行测评：

```
import torch
from fastapi import FastAPI, Request
from transformers import AutoTokenizer, AutoModel
import uvicorn, json, datetime


# DEVICE = "cuda"
# DEVICE_ID = "2"
# CUDA_DEVICE = f"{DEVICE}:{DEVICE_ID}" if DEVICE_ID else DEVICE

device='cuda'
def torch_gc():
    if torch.cuda.is_available():
        with torch.cuda.device(device):
            torch.cuda.empty_cache()
            torch.cuda.ipc_collect()


app = FastAPI()

@app.post("/api/api_server_01")
async def create_item(request: Request):
    global model, tokenizer
    json_post_raw = await request.json()
    json_post = json.dumps(json_post_raw)
    json_post_list = json.loads(json_post)
    prompt = json_post_list.get('prompt')
    history = json_post_list.get('history')
    max_length = json_post_list.get('max_length')
    top_p = json_post_list.get('top_p')
    temperature = json_post_list.get('temperature')
    response, history = model.chat(tokenizer,
                                   prompt,
                                   history=history,
                                   max_length=max_length if max_length else 2048,
                                   top_p=top_p if top_p else 0.7,
                                   temperature=temperature if temperature else 0.95)
    now = datetime.datetime.now()
    time = now.strftime("%Y-%m-%d %H:%M:%S")
    answer = {
        "response": response,
        "history": history,
        "status": 200,
        "time": time
    }
    log = "[" + time + "] " + '", prompt:"' + prompt + '", response:"' + repr(response) + '"'
    print(log)
    torch_gc()
    return answer


if __name__ == '__main__':
    tokenizer = AutoTokenizer.from_pretrained("../pretrained/ChatGLM2-6B/chatglm2-6b", trust_remote_code=True)
    model = AutoModel.from_pretrained("../pretrained/ChatGLM2-6B/chatglm2-6b", trust_remote_code=True).cuda()
    # 多显卡支持，使用下面三行代替上面两行，将num_gpus改为你实际的显卡数量
    # model_path = "THUDM/chatglm2-6b"
    # tokenizer = AutoTokenizer.from_pretrained(model_path, trust_remote_code=True)
    # model = load_model_on_gpus(model_path, num_gpus=2)
    model.eval()
    uvicorn.run(app, host='0.0.0.0', port=9101, workers=1)
'''
conda activate chatglm-6b
CUDA_VISIBLE_DEVICES=1 nohup python -u chatglm2-6b_api.py > chatglm2-6b.log 2>&1 &
'''
```

以上代码修改自：https://github.com/THUDM/ChatGLM2-6B/blob/main/api.py