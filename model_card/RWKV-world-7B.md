# RWKV-world-7B
| 🤗[Huagging Face](https://huggingface.co/spaces/BlinkDL/RWKV-World-7B) | [GitHub](https://github.com/BlinkDL/ChatRWKV) |

SuperCLUE-Open 采用以下代码进行测评：

```
import os, re
from fastapi import FastAPI, Request
import uvicorn
import json

os.environ['RWKV_JIT_ON'] = '1' #### set these before import RWKV
os.environ["RWKV_CUDA_ON"] = '0' #### set to '1' to compile CUDA kernel (10x faster) - requires c++ compiler & cuda libraries

from rwkv.model import RWKV #### pip install rwkv --upgrade
from rwkv.utils import PIPELINE, PIPELINE_ARGS

MODEL_FILE = '../pretrained/RWKV-World-7B/RWKV-4-World-CHNtuned-7B-v1-20230626-ctx4096'
# from huggingface_hub import hf_hub_download 
# model_path = hf_hub_download(repo_id="BlinkDL/rwkv-4-world", filename=f"RWKV-4-World-7B-v1-20230626-ctx4096.pth") 
# model = RWKV(model=model_path, strategy='cuda fp16') 
model = RWKV(model=MODEL_FILE, strategy='cuda fp16')
pipeline = PIPELINE(model, "rwkv_vocab_v20230424") #### vocab for rwkv-4-world models


def my_qa_generator(ctx):
    out_tokens = []
    out_len = 0
    out_str = ''
    occurrence = {}
    state = None
    for i in range(2048):
        if i == 0:
            out, state = pipeline.model.forward(pipeline.encode(ctx), state)
        else:
            out, state = pipeline.model.forward([token], state)

        for n in occurrence: out[n] -= (0.4 + occurrence[n] * 0.4) #### higher repetition penalty because of lower top_p here
        
        token = pipeline.sample_logits(out, temperature=1.0, top_p=0.2) #### sample the next token

        if token == 0: break #### exit at token [0] = <|endoftext|>
        
        out_tokens += [token]

        for n in occurrence: occurrence[n] *= 0.996 #### decay repetition penalty
        occurrence[token] = 1 + (occurrence[token] if token in occurrence else 0)
        
        tmp = pipeline.decode(out_tokens[out_len:])
        if ('\ufffd' not in tmp) and (not tmp.endswith('\n')): #### print() only when out_str is valid utf-8 and not end with \n
            out_str += tmp
            print(tmp, end = '', flush = True)
            out_len = i + 1    
        elif '\n\n' in tmp: #### exit at '\n\n'
            tmp = tmp.rstrip()
            out_str += tmp
            print(tmp, end = '', flush = True)
            break
    return out_str.strip()

app = FastAPI()

@app.post("/api/rwkv")
async def create_item(request: Request):
    json_post_raw = await request.json()
    json_post = json.dumps(json_post_raw)
    json_post_list = json.loads(json_post)
    prompt = json_post_list.get('prompt')
    history = json_post_list.get('history', [])
    
    chat_rounds = []
    for user_prompt, bot_reply in history:
        chat_rounds.append('User: ' + re.sub(r'\n{2,}', '\n', user_prompt).strip().replace('\r\n','\n'))
        chat_rounds.append('Assistant: ' + bot_reply)
    
    chat_rounds.append('User: ' + re.sub(r'\n{2,}', '\n', prompt).strip().replace('\r\n','\n'))
    chat_rounds.append('Assistant:')

    print('\n\n'.join(chat_rounds), end = '')
    result = my_qa_generator('\n\n'.join(chat_rounds))

    return {'result': result}


if __name__ == "__main__":
    uvicorn.run(app, host='0.0.0.0', port=9003, workers=1)
'''
conda activate rwkv
CUDA_VISIBLE_DEVICES=1 nohup python -u api_demo_world.py > world-7b.log 2>&1 &
'''
```

以上代码修改自：https://github.com/BlinkDL/ChatRWKV/blob/main/API_DEMO_WORLD.py