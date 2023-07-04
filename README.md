# SuperCLUE-open
中文通用大模型开放域多轮测评基准 | An Multi-turn Open Domain Benchmark for Foundation Models  in Chinese

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/score_10_circle.jpg"  width="70%" height="70%"></img>

## SuperCLUE榜单

SuperCLUE-Open：开放域多轮交互；SuperCLUE-Opt：三大能力，客观题；SuperCLUE-LYB：开放域众包匿名对战

|      Model      | SuperCLUE-Open  | SuperCLUE-Opt  | SuperCLUE-LYB  |   许可证   |
|:---------------:|:--------------:|:-------------:|:------------:|:---------:|
|     gpt-4       |     94.64      |     78.76     |          -      |  专有服务  |
| Claude-instant-v1 |    69.51     |     60.38     |          1215     |  专有服务  |
| gpt-3.5-turbo   |     66.67      |     67.98     |          1171     |  专有服务  |
|  MiniMax-abab5  |     57.94      |     58.19     |           1188     |  专有服务  |
| 文心一言(v2.0.4)  |     50.48      |     62.85     |             -      |  专有服务  |
| 讯飞星火(v1.5)    |     48.87      |     59.8      |            -      |  专有服务  |
|  ChatGLM-130B   |     42.46      |     51.53     |          1163     |  专有服务  |
|  ChatGLM2-6B    |     36.50      |     48.56     |           -      | 开源，商用申请|
|  360智脑(4.0)    |     23.93      |     63.53     |           -      |  专有服务  |
| IDEA-姜子牙-13B  |     22.04      |     48.67     |           1010     | 开源，非商用|
|    MOSS-16B     |     21.14      |     38.56     |           1049     | 开源，商用申请|
|  BELLE-13B     |     15.61      |     50.65     |           958     | 开源，非商用|
|  RWKV-world-7B  |     24.54      |     24.83     |           811     | 开源，可商用|
| phoenix-7B  |     -  | 43.60	| 1100  | 开源，可商用|
|  Vicuna-13B  |     -  |  29.15	| 994	 |  开源，非商用|
|  baichuan-7B（预训练模型）    |      3.11      |     48.18     |            -      | 开源，商用申请|

SuperCLUE是一个综合性基准，包括三个子基准：开放域多轮交互基准，<a href='https://github.com/CLUEbenchmark/SuperCLUE-open'>SuperCLUE-Open</a>；
客观题形式的三大能力基准，<a href='https://github.com/CLUEbenchmark/SuperCLUE'>SuperCLUE-Opt</a>（基础能力、中文特性和专业能力）；
众包匿名对战形式基准琅琊榜，<a href='https://www.SuperCLUEAi.com'>SuperCLUE-LYB</a>

### SuperCLUE开放域多轮基准与封闭域基准相关性

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/superclue_open_vs_opt.png"  width="65%" height="65%"></img>

从相关性分析中可以看到，SuperCLUE-open与SuperCLUE-opt具有较高的一致性（Pearson/Spearman相关性系数0.78--0.82）


### SuperCLUE-open开放域多轮测评基准

| 排名 |         Model         | Score  | Win | Loss | Tie | Win_rate(%) | Loss_rate(%) |
|:---:|:---------------------:|:------:|:---:|:----:|:---:|:-----------:|:------------:|
| 🏅 |        gpt-4     | 94.64  | 264 |  24  | 160 |    58.93    |     5.36     |
| 🥈  | Claude-instant-v1  | 69.51  | 127 | 161  | 240 |    24.05    |     30.49    |
|🥉 |   gpt-3.5-turbo    | 66.67  | 176 | 176  | 176 |    33.33    |     33.33    |
| 4 |    MiniMax-abab5   | 57.94  |  82 | 212  | 210 |    16.27    |     42.06    |
| 5 |  文心一言(v2.0.4)   | 50.48  |  70 | 257  | 192 |    13.49    |     49.52    |
| 6|   讯飞星火(v1.5)   | 48.87  |  81 | 249  | 157 |    16.63    |     51.13    |
| 7|   ChatGLM-130B     | 42.46  |  56 | 290  | 158 |    11.11    |     57.54    |
| 8|    ChatGLM2-6B    | 36.50  |  80 | 381  | 139 |    13.33    |     63.50    |
| 9 |    360智脑(4.0)     | 23.93  |  20 | 426  | 114 |     3.57    |     76.07    |
| 10| IDEA-姜子牙-13B     | 22.04  |  22 | 435  | 101 |     3.94    |     77.96    |
| 11|      MOSS-16B      | 21.14  |  27 | 470  |  99 |     4.53    |     78.86    |
| 12|     BELLE-13B      | 15.61  |  12 | 481  |  77 |     2.11    |     84.39    |
| 13|   RWKV-world-7B    | 12.45  |  11 | 471  |  56 |     2.04    |     87.55    |
| 14|    baichuan-7B     |  3.11  |   3 | 560  |  15 |     0.52    |     96.89    |

注：Score分数(即胜和率)，是模型的胜率加上平局率之和，即(win+tie)/(win+tie+loss)*100。

以下是根据给定的Excel表格内容生成的Markdown表格（内容句子显示）：

### SuperCLUE-Open十大能力表

| 模型 | 胜和率 | 语义理解 | 闲聊 | 上下文对话 | 角色扮演 | 知识与百科 | 生成与创作 | 代码 | 逻辑与推理 | 计算 | 安全 |
|:----:|:-----:|:-------:|:----:|:--------:|:------:|:--------:|:--------:|:----:|:--------:|:----:|:----:|
| GPT-4 | 94.64 | 80.00 | 97.30 | 93.18 | 100.00 | 87.76 | 100.00 | 97.92 | 100.00 | 100.00 | 95.12 |
| Claude-instant-v1 | 69.51 | 64.29 | 92.31 | 68.52 | 83.02 | 51.79 | 51.06 | 54.00 | 59.57 | 80.00 | 86.79 |
| MinMax-abab5 | 57.94 | 55.36 | 78.00 | 59.62 | 85.42 | 57.41 | 69.23 | 37.25 | 34.78 | 32.20 | 77.55 |
| 文心一言(v2.0.4) | 50.48 | 32.76 | 56.86 | 47.06 | 52.73 | 37.50 | 62.50 | 53.19 | 70.59 | 60.34 | 36.54 |
| 讯飞星火(v1.5) | 48.87 | 45.61 | 25.49 | 60.00 | 83.67 | 29.63 | 71.79 | 37.74 | 39.58 | 57.14 | 50.00 |
| ChatGLM-130B | 42.46 | 44.64 | 53.06 | 50.00 | 51.92 | 39.29 | 52.50 | 17.07 | 37.25 | 42.37 | 34.00 |
| ChatGLM2-6B | 36.50 | 33.33 | 38.33 | 36.67 | 41.67 | 20.00 | 40.00 | 21.67 | 55.00 | 45.00 | 33.33 |
| 360智脑(4.0) | 23.93 | 25.42 | 16.95 | 23.64 | 14.04 | 10.17 | 41.67 | 32.08 | 43.40 | 30.00 | 7.02 |
| jiangziya-13B-v1.1 | 22.04 | 13.33 | 8.47 | 24.56 | 16.07 | 24.14 | 19.61 | 25.49 | 28.00 | 38.98 | 22.81 |
| MOSS-16B | 21.14 | 26.67 | 20.00 | 11.67 | 27.59 | 11.86 | 25.42 | 15.00 | 35.00 | 21.67 | 16.67 |
| BELLE-13B | 15.61 | 25.00 | 8.47 | 15.25 | 6.90 | 11.67 | 9.80 | 33.33 | 32.08 | 13.56 | 3.33 |
| DLM | 12.54 | 16.67 | 0.00 | 13.79 | 10.00 | 6.90 | 3.57 | 11.11 | 45.83 | 20.00 | 3.33 |
| RWKV-world-7B | 12.45 | 10.64 | 8.47 | 12.96 | 7.27 | 11.86 | 10.20 | 25.00 | 18.00 | 12.28 | 8.93 |
| baichuan-7B（预训练模型） | 3.11 | 1.89 | 0.00 | 0.00 | 0.00 | 1.72 | 1.69 | 3.33 | 18.33 | 3.33 | 0.00 |


注：胜和率，是模型的胜率加上平局率之和，即(win+tie)/(win+tie+loss)*100。

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

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/superclue_open_examples.jpeg"  width="70%" height="70%"></img>

### 如何对中文大模型进行评估
针对中文大模型的人类偏好能力，可以通过人工进行评估，但是它一般时间周期比较长、并且成本高。国际上已经开始有一些自动化模型评估的方式。

比如加州伯克利的MT-bench, 斯坦福大学的Alpaca-Eval进行了比较系统的自动化评估。这里面存在对比模型时模型位置、生成答案的长度、模型对数学推理的评估能力有限的问题。
借鉴上面两个工作的经验，我们也进行了针对性的处理，减少这些方面的问题。正如这两个工作提到的，GPT-4的评估可以实现和人类评估高达80-90%的一致性，这充分的说明了自动化评估的潜力。

我们的评估，通过使用超级模型作为评判官，使用一个待评估模型与一个基准模型进行对比，需要让模型选出哪个模型更好。答案可以是，A模型好，B模型好，或平局。
评估的标准，是要求超级模型作为一个公证的评估者，评估模型的质量。回答的质量包括回答有针对性、准确和全面。

## 结果与分析
#### SuperCLUE-open，有区别性的中文大模型基准
我们对14个模型，针对10项能力，进行了全面的评估。我们的基准可以清晰的区分模型在不同能力上的表现。特别是一些国际专有服务gpt-4, gpt-3.5, Claude，
相比中开源模型ChatGM2-6B, MOSS-16B有明显的效果差异。

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/score_10_circle.jpg"  width="70%" height="70%"></img>


#### 多轮对话能力

#### 大型语言模型评估的可解释性
<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/superclue_open_example.jpeg"  width="115%" height="115%"></img>


## 如何在SuperCLUE-Auto上评估新的模型

1.SuperCLUE榜单大模型评测申请：https://wj.qq.com/s2/12305633/a73d/

（针对已公开发布、有代表性的模型服务或开源模型）

2.机构内部测评需求收集：https://wj.qq.com/s2/12307825/2ae0/


## 下一步
1. 添加SuperCLUE-open与人类测评的一致性分析
2. 扩充测试集规模
3. 加入更多中文大模型


## 相关工作
1.论文：<a href='https://arxiv.org/abs/2306.05685'>Judging LLM-as-a-judge with MT-Bench and Chatbot Arena</a>

2.文章：<a href='https://lmsys.org/blog/2023-06-22-leaderboard/'>Chatbot Arena Leaderboard Week 8: Introducing MT-Bench and Vicuna-33B</a>

3.项目地址：<a href='https://github.com/tatsu-lab/alpaca_eval'>Alpaca_Eval: A validated automatic evaluator for instruction-following language models. High-quality, cheap, and fast.</a>

4.排行榜 <a href='https://tatsu-lab.github.io/alpaca_eval/'>AlpacaEval Leaderboard</a>

## 致谢
本基准的成功运行离不开FastChat项目在源代码方面的大力支持，在此十分感谢Large Model Systems Organization(<a href=''>LMSYS ORG</a>)和<a href='https://github.com/lm-sys/FastChat'>FastChat</a>



## 链接

1. <a href='https://github.com/CLUEbenchmark/SuperCLUE'>SuperCLUE-Opt</a>： 中文通用大模型综合性基准(基础能力、中文特性和专业能力）

2. <a href='www.superclueai.com'>SuperCLUE琅琊榜</a>：中文通用大模型匿名对战评价基准


