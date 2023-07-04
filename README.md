# SuperCLUE-open
中文通用大模型开放域多轮测评基准 | An Multi-turn Open Domain Benchmark for Foundation Models  in Chinese

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/score_10_circle.jpg"  width="70%" height="70%"></img>

## SuperCLUE榜单

SuperCLUE-Open：开放域多轮交互；SuperCLUE-Opt：三大能力，客观题；SuperCLUE-LYB：开放域众包匿名对战

|      Model      | SuperCLUE-Open  | SuperCLUE-Opt  | SuperCLUE-LYB  |   许可证   |
|:---------------:|:--------------:|:-------------:|:------------:|:---------:|
|     gpt-4       |     94.64      |     78.76     |          -      |  专有服务  |
| gpt-3.5-turbo   |     66.67      |     67.98     |          1171     |  专有服务  |
| Claude-instant-v1 |    69.51     |     60.38     |          1215     |  专有服务  |
|  MiniMax-abab5  |     57.94      |     58.19     |           1188     |  专有服务  |
| 文心一言(v2.0.4)  |     50.48      |     62.85     |             -      |  专有服务  |
| 讯飞星火(v1.5)    |     48.87      |     59.8      |            -      |  专有服务  |
|  ChatGLM-130B   |     42.46      |     51.53     |          1163     |  专有服务  |
|  ChatGLM2-6B    |     36.50      |     48.56     |           -      | 开源，商用申请|
|  360智脑(4.0)    |     23.93      |     63.53     |           -      |  专有服务  |
| IDEA-姜子牙-13B  |     22.04      |     48.67     |           1010     | 开源，非商用|
|    MOSS-16B     |     21.14      |     38.56     |           1049     | 开源，商用申请|
|   BELLE-13B     |     15.61      |     50.65     |           958     | 开源，非商用|
|  RWKV-world-7B  |     24.54      |     24.83     |           811     | 开源，可商用|
| phoenix-7B  |     -  | 43.60	| 1100  | 开源，可商用|
| Vicuna-13B  |     -  |  29.15	| 994	 |  开源，非商用|
|  baichuan-7B（预训练模型）    |      3.11      |     48.18     |            -      | 开源，商用申请|

SuperCLUE是一个综合性基准，包括三个子基准：开放域多轮交互基准，<a href='https://github.com/CLUEbenchmark/SuperCLUE-open'>SuperCLUE-Open</a>；
客观题形式的三大能力基准，<a href='https://github.com/CLUEbenchmark/SuperCLUE'>SuperCLUE-Opt</a>（基础能力、中文特性和专业能力）；
众包匿名对战形式基准琅琊榜，<a href='https://www.SuperCLUEAi.com'>SuperCLUE-LYB</a>


以下是根据给定的Excel表格内容生成的Markdown表格（内容居中显示）：

### SuperCLUE-open模型排行榜

|         Model         | Score  | Win | Loss | Tie | Win_rate(%) | Loss_rate(%) |
|:---------------------:|:------:|:---:|:----:|:---:|:-----------:|:------------:|
|        gpt-4     | 94.64  | 264 |  24  | 160 |    58.93    |     5.36     |
|   gpt-3.5-turbo    | 66.67  | 176 | 176  | 176 |    33.33    |     33.33    |
| Claude-instant-v1  | 69.51  | 127 | 161  | 240 |    24.05    |     30.49    |
|    MiniMax-abab5   | 57.94  |  82 | 212  | 210 |    16.27    |     42.06    |
|  文心一言(v2.0.4)   | 50.48  |  70 | 257  | 192 |    13.49    |     49.52    |
|   讯飞星火(v1.5)   | 48.87  |  81 | 249  | 157 |    16.63    |     51.13    |
|   ChatGLM-130B     | 42.46  |  56 | 290  | 158 |    11.11    |     57.54    |
|    ChatGLM2-6B    | 36.50  |  80 | 381  | 139 |    13.33    |     63.50    |
|    360智脑(4.0)     | 23.93  |  20 | 426  | 114 |     3.57    |     76.07    |
| IDEA-姜子牙-13B     | 22.04  |  22 | 435  | 101 |     3.94    |     77.96    |
|      MOSS-16B      | 21.14  |  27 | 470  |  99 |     4.53    |     78.86    |
|     BELLE-13B      | 15.61  |  12 | 481  |  77 |     2.11    |     84.39    |
|   RWKV-world-7B    | 12.45  |  11 | 471  |  56 |     2.04    |     87.55    |
|    baichuan-7B     |  3.11  |   3 | 560  |  15 |     0.52    |     96.89    |

注：Score分数，是模型的胜率加上平局率之和，即(win+tie)/(win+tie+loss)。

## 使用SuperCLUE-open来评估中文大模型

### 动机
当前已经有一些评价中文大模型的基准，如C-Eval, MMCU，但是这些基准可能不太擅长评估大模型的人类偏好。
传统的基准通常以封闭式问题形式进行测试，要求模型输出简要的结论（如多项选择），但是他们不能很好的反映大模型的典型使用场景（如生成、创作和提供想法）。
当前也刚刚出现一些基准，如加州伯克利的MT-bench, 斯坦福大学的Alpaca-Eval，可以用于评估开放域问题，但是这些基准都是英文。
中文的代表性专有服务和开源模型总体上无法进行有效评估。

为了缓解这个问题，我们发布了SuperCLUE-open与SuperCLUE琅琊榜：

SuperCLUE-open：是一个有挑战的多轮对话测试集，用于评估中文大模型对话式和遵循指令的能力。

SuperCLUE-lyb: SuperCLUE琅琊榜是一个众包匿名对战平台，用户问自己感兴趣的问题，并且投票他们喜欢的答案。

这两个基准设计的首要度量标准是人类的偏好。

### 什么是SuperCLUE-open
SuperCLUE-open是一个多轮开放域中文基准，包括600个高质量多轮问题。这里面的问题用于评估中文大模型对话能力和遵循指令的能力。
里面包括一些常用的使用场景和一些挑战性的指令用于区分不同的模型。它考察模型的十大能力，
包括：语义理解与抽取，闲聊，上下文对话，角色扮演，知识与百科，生成与创作，代码，逻辑与推理，计算，代码和安全。每个子能力六十道题目，每个题目包括两轮问题。

### 如何对中文大模型进行评分
这里写评分过程和问题，一致性

## 结果与分析
#### 有效区分行的中文大模型

#### 多轮对话能力

#### 大型语言模型法官的可解释性
<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/superclue_open_example.jpeg"  width="70%" height="70%"></img>


## 如何在SuperCLUE-Auto上评估新的模型
链接或办法

## 下一步

## 相关工作

## 链接



