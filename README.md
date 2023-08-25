# SuperCLUE-Open
中文通用大模型开放域多轮测评基准 | A Multi-turn Open Domain Benchmark for Foundation Models in Chinese

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/score_10_circle.jpg"  width="60%" height="60%"></img>
<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/socre_10_qianwen.jpg"  width="60%" height="60%"></img>

### 更新

[2023-08-04]  添加通义千问开源模型Qwen-7B-Chat。测评调用代码见<a href='./model_card/Qwen-7B-Chat.md'>Model_Card</a>


## 体系与示例
<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/superclue_category.png"  width="60%" height="60%"></img>

SuperCLUE基础十大能力结构包含四个能力象限，包括语言理解与生成、知识理解与应用、专业能力和环境适应与安全性，进而细化为10项基础能力。

### 能力1：语义理解与抽取

这是一种语言能力，能够理解并解析输入的文字信息的含义。模型需要能够识别短语、句子、段落的含义，同时还要能从更大的文本块中抽取关键信息和主题。

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/open_example_1.png"  width="80%" height="80%"></img>

多轮对话示例




图片

注：本示例中可同时评测多轮对话能力

能力2：闲聊

这是一种语言能力，与用户进行自由形式、非特定目标的对话。模型需要具备生成流畅、自然、符合语言习惯和文化背景的回应。

图片
示例


图片

能力3：上下文对话

这是一种语言能力，需要理解并记住前面的对话信息，以便在回答中保持连贯性。这涉及到理解对话的整体流程和上下文环境，或生成相应的对话。

图片
示例


图片

能力4：生成与创作

这是一种语言能力，能够创造新的文本内容，如文章、文案、短故事、诗歌。这涉及到创造性地运用语言，同时还要考虑到风格、语境和目标读者。

图片
示例


图片

能力5：知识与百科

这是一种知识能力，能够像百科全书一样提供知识信息。这涉及到理解和回答关于广泛主题的问题，以及提供准确、详细和最新的信息。
图片
示例


图片

能力6：代码

这是一种专业能力，能够理解和生成编程代码。这涉及到理解多种编程语言的语法、结构和习惯，以及如何解决编程问题。
图片
多轮对话示例


图片
注：本示例中可同时评测多轮对话能力

能力7：逻辑与推理

这是一种专业能力，能够理解和应用逻辑原则进行推理。这涉及到分析问题、识别问题及推理。

图片
示例
图片

能力8：计算

这是一种专业能力，使其能够执行数学运算，如加法、减法、乘法和除法，甚至更复杂的数学问题。这涉及到理解数学问题的表述，以及如何步骤地解决这些问题。

图片
多轮对话示例


图片
注：本示例中可同时评测多轮对话能力

能力9：角色扮演

这是一种感知能力，使其能够在特定的模拟环境或情景中扮演一个角色。这涉及到理解特定角色的行为、说话风格，以及在特定情境下的适当反应。

图片
示例


图片

能力10：安全

这是一种安全能力，防止生成可能引起困扰或伤害的内容。这涉及到识别和避免可能包含敏感或不适当内容的请求，以及遵守用户的隐私和安全政策。
图片
示例


图片


## SuperCLUE榜单(Open开放域多轮-Opt封闭域-LYB匿名对战)

SuperCLUE-Open：开放域多轮交互；SuperCLUE-Opt：三大能力，客观题；SuperCLUE-LYB：开放域众包匿名对战

<span style="font-size: 0.8em;">

|                                                   Model                                                    |    机构     | Open开放域 | Opt封闭域 | LYB匿名对战 |  许可证   |
|:----------------------------------------------------------------------------------------------------------:|:---------:|:-------:|:------:|:-------:|:------:|
|                                  <a href='https://openai.com/'>GPT-4</a>                                   |  OpenAI   |  94.64  | 78.76  |    -    |  专有服务  |
|                        <a href='https://www.anthropic.com/'>Claude-instant-v1 </a>                         | Authropic |  69.51  | 60.38  |  1215   |  专有服务  |
|                              <a href='https://openai.com/'>gpt-3.5-turbo</a>                               |  OpenAI   |  66.67  | 67.98  |  1202   |  专有服务  |
|                           <a href='https://api.minimax.chat/'>MiniMax-abab5</a>                            |  MiniMax  |  57.94  | 58.19  |  1250   |  专有服务  |
|                         <a href='https://yiyan.baidu.com/welcome'>文心一言(v2.0.4)</a>                         |    百度     |  50.48  | 62.85  |    -    |  专有服务  |
|                             <a href='https://xinghuo.xfyun.cn/'>讯飞星火(v1.5)</a>                             |   科大讯飞    |  48.87  |  59.8  |    -    |  专有服务  |
|                               <a href='https://chatglm.cn'>ChatGLM-130B</a>                                |  清华&智谱AI  |  42.46  | 51.53  |  1180   |  专有服务  |
|                       <a href='https://github.com/THUDM/ChatGLM2-6B'>ChatGLM2-6B</a>                       |  清华&智谱AI  |  36.50  | 48.56  |  1105   | 开源-可商用 |
|             <a href='https://modelscope.cn/models/qwen/Qwen-7B-Chat/summary'>Qwen-7B-Chat</a>              |    阿里云    |  25.75  |   -    |    -    | 开源-可商用 |
|                                 <a href='https://ai.360.cn'>360智脑(4.0)</a>                                 |    360    |  23.93  | 63.53  |    -    |  专有服务  |
|              <a href='https://huggingface.co/IDEA-CCNL/Ziya-LLaMA-13B-v1.1'>IDEA-姜子牙-13B</a>               |  深圳IDEA   |  22.04  | 48.67  |  1069   | 开源-非商用 |
|                          <a href='https://github.com/OpenLMLab/MOSS'>MOSS-16B</a>                          |    复旦     |  21.14  | 38.56  |  1058   | 开源-可商用 |
|                        <a href='https://github.com/LianjiaTech/BELLE'>BELLE-13B</a>                        |    链家     |  15.61  | 50.65  |   967   | 开源-非商用 |
|              <a href='https://huggingface.co/spaces/BlinkDL/RWKV-World-7B'>RWKV-world-7B</a>               |  RWKV基金会  |  24.54  | 24.83  |  1034   | 开源-可商用 |
|                <a href='https://github.com/baichuan-inc/baichuan-7B'>baichuan-7B(预训练模型)</a>                |   百川智能    |  3.11   | 48.18  |   846   | 开源-可商用 |
|          <a href='https://huggingface.co/FreedomIntelligence/phoenix-inst-chat-7b'>phoenix-7B</a>          |  香港中文大学   |    -    | 43.60	 |  1087   | 开源-可商用 |
|                        <a href='https://github.com/lm-sys/FastChat'>Vicuna-13B</a>                         |   UC伯克利   |    -    | 29.15	 |  1001	  | 开源-非商用 |

<a href='https://www.superclueai.com/'>LYB匿名对战数据</a>，更新与2023-07-07
 </span>
SuperCLUE是一个综合性基准，包括三个子基准：开放域多轮交互基准，<a href='https://github.com/CLUEbenchmark/SuperCLUE-open'>SuperCLUE-Open</a>；
客观题形式的三大能力基准，<a href='https://github.com/CLUEbenchmark/SuperCLUE'>SuperCLUE-Opt</a>（基础能力、中文特性和专业能力）；
众包匿名对战形式基准琅琊榜，<a href='https://www.SuperCLUEAi.com'>SuperCLUE-LYB</a>

### SuperCLUE开放域多轮基准与封闭域基准相关性

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/superclue_open_vs_opt.png"  width="70%" height="70%"></img>

从相关性分析中可以看到，SuperCLUE-open与SuperCLUE-opt具有较高的一致性（Pearson/Spearman相关性系数0.78--0.82）


### SuperCLUE-Open开放域多轮测评基准

| 排名 |       Model       | Score | Win | Loss | Tie |   Win_rate(%)   |   Loss_rate(%)    |
|:--:|:-----------------:|:-----:|:---:|:----:|:---:|:---------------:|:-----------------:|
| 🏅 |       gpt-4       | 94.64 | 264 |  24  | 160 |      58.93      |       5.36        |
| 🥈 | Claude-instant-v1 | 69.51 | 127 | 161  | 240 |      24.05      |       30.49       |
| 🥉 |   gpt-3.5-turbo   | 66.67 | 176 | 176  | 176 |      33.33      |       33.33       |
| 4  |   MiniMax-abab5   | 57.94 | 82  | 212  | 210 |      16.27      |       42.06       |
| 5  |   文心一言(v2.0.4)    | 50.48 | 70  | 257  | 192 |      13.49      |       49.52       |
| 6  |    讯飞星火(v1.5)     | 48.87 | 81  | 249  | 157 |      16.63      |       51.13       |
| 7  |   ChatGLM-130B    | 42.46 | 56  | 290  | 158 |      11.11      |       57.54       |
| 8  |    ChatGLM2-6B    | 36.50 | 80  | 381  | 139 |      13.33      |       63.50       |
| 9  |   Qwen-7B-Chat    | 25.75 | 14  |   222   |  63   |      4.68       |       74.25       |
| 10 |    360智脑(4.0)     | 23.93 | 20  | 426  | 114 |      3.57       |       76.07       |
| 11|   IDEA-姜子牙-13B    | 22.04 | 22  | 435  | 101 |      3.94       |       77.96       |
| 12|     MOSS-16B      | 21.14 | 27  | 470  | 99  |      4.53       |       78.86       |
| 13|     BELLE-13B     | 15.61 | 12  | 481  | 77  |      2.11       |       84.39       |
| 14|   RWKV-world-7B   | 12.45 | 11  | 471  | 56  |      2.04       |       87.55       |
| 15|    baichuan-7B    | 3.11  |  3  | 560  | 15  |      0.52       |       96.89       |

注：Score分数(即胜和率)，是模型的胜率加上平局率之和，即(win+tie)/(win+tie+loss)*100。


### SuperCLUE-Open十大能力表

<span style="font-size: 0.8em;">

|        模型         |    胜和率     | <span style="font-size: 0.2em;">语言理解 </span> |    闲聊     |   <span style="font-size: 0.2em;">上下文对话</span>   |    角色扮演    |   <span style="font-size: 0.2em;">知识百科</span>   | <span style="font-size: 0.2em;">生成创作</span> |  代码   | <span style="font-size: 0.2em;">逻辑推理</span> |   计算   | 安全 |
|:-----------------:|:----------:|:--------------------------------------------:|:---------:|:------------------------------------------------:|:----------:|:-----------------------------------------------:|:-------------------------------------------:|:-----:|:-------------------------------------------:|:------:|:----:|
|       GPT-4       |   94.64    |                    80.00                     |   97.30   |                      93.18                       |   100.00   |                      87.76                      |                   100.00                    | 97.92 |                   100.00                    | 100.00 | 95.12 |
| Claude-instant-v1 |   69.51    |                    64.29                     |   92.31   |                      68.52                       |   83.02    |                      51.79                      |                    51.06                    | 54.00 |                    59.57                    | 80.00  | 86.79 |
|   MinMax-abab5    |   57.94    |                    55.36                     |   78.00   |                      59.62                       |   85.42    |                      57.41                      |                    69.23                    | 37.25 |                    34.78                    | 32.20  | 77.55 |
|   文心一言(v2.0.4)    |   50.48    |                    32.76                     |   56.86   |                      47.06                       |   52.73    |                      37.50                      |                    62.50                    | 53.19 |                    70.59                    | 60.34  | 36.54 |
|    讯飞星火(v1.5)     |   48.87    |                    45.61                     |   25.49   |                      60.00                       |   83.67    |                      29.63                      |                    71.79                    | 37.74 |                    39.58                    | 57.14  | 50.00 |
|   ChatGLM-130B    |   42.46    |                    44.64                     |   53.06   |                      50.00                       |   51.92    |                      39.29                      |                    52.50                    | 17.07 |                    37.25                    | 42.37  | 34.00 |
| ChatGLM2-6B-Chat  |   36.50    |                    33.33                     |   38.33   |                      36.67                       |   41.67    |                      20.00                      |                    40.00                    | 21.67 |                    55.00                    | 45.00  | 33.33 |
|   Qwen-7B-Chat    |   25.75    |                    30.00                     | 16.67     |  23.33                                           |  16.67     |              10.00                              |                    20.00                    |   40.00    |      58.62                                  |   36.67     | 6.67 |
| 360智脑(4.0) | 23.93 |                    25.42                     |   16.95   |                      23.64                       |   14.04    |                      10.17                      | 41.67 | 32.08 |                    43.40                    | 30.00 | 7.02 |
| jiangziya-13B-v1.1 | 22.04 |                    13.33                     |   8.47    |                      24.56                       |   16.07    |                      24.14                      | 19.61 | 25.49 |                    28.00                    | 38.98 | 22.81 |
| MOSS-16B | 21.14 |                    26.67                     |   20.00   |                      11.67                       |   27.59    |                      11.86                      | 25.42 | 15.00 |                    35.00                    | 21.67 | 16.67 |
| BELLE-13B | 15.61 |                    25.00                     |   8.47    |                      15.25                       |    6.90    |                      11.67                      | 9.80 | 33.33 |                    32.08                    | 13.56 | 3.33 |
| DLM | 12.54 |                    16.67                     |   0.00    |                      13.79                       |   10.00    |                      6.90                       | 3.57 | 11.11 |                    45.83                    | 20.00 | 3.33 |
| RWKV-world-7B | 12.45 |                    10.64                     |   8.47    |                      12.96                       |    7.27    |                      11.86                      | 10.20 | 25.00 |                    18.00                    | 12.28 | 8.93 |
| baichuan-7B（预训练模型） | 3.11 |                     1.89                     |   0.00    |                       0.00                       |    0.00    |                      1.72                       | 1.69 | 3.33 |                    18.33                    | 3.33 | 0.00 |

 </span>
 
注：胜和率，是模型的胜率加上平局率之和，即(win+tie)/(win+tie+loss)*100；语义理解：语义理解与抽取；
   表格较大，请往后拉

## 使用SuperCLUE-Open来评估中文大模型

### 动机
当前已经有一些评价中文大模型的基准，如C-Eval, MMCU，但是这些基准可能不太擅长评估大模型的人类偏好。
传统的基准通常以封闭式问题形式进行测试，要求模型输出简要的结论（如多项选择），但是他们不能很好的反映大模型的典型使用场景（如生成、创作和提供想法）。
当前也刚刚出现一些基准，如加州伯克利的MT-bench, 斯坦福大学的Alpaca-Eval，可以用于评估开放域问题，但是这些基准都是英文。
中文的代表性专有服务和开源模型总体上无法进行有效评估。

为了缓解这个问题，我们发布了SuperCLUE-Open与SuperCLUE琅琊榜：

SuperCLUE-Open：是一个有挑战的多轮对话测试集，用于评估中文大模型对话式和遵循指令的能力。

SuperCLUE-LYB: SuperCLUE琅琊榜是一个众包匿名对战平台，用户问自己感兴趣的问题，并且投票他们喜欢的答案。

这两个基准设计的首要度量标准是人类的偏好。

### 什么是SuperCLUE-Open
SuperCLUE-Open是一个多轮开放域中文基准，包括600个高质量多轮问题。这里面的问题用于评估中文大模型对话能力和遵循指令的能力。
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
#### SuperCLUE-Open，有区别性的中文大模型基准
我们对14个模型，针对10项能力，进行了全面的评估。我们的基准可以清晰的区分模型在不同能力上的表现。特别是一些国际专有服务gpt-4, gpt-3.5, Claude，
相比中开源模型ChatGM2-6B, MOSS-16B有明显的效果差异。

<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/score_10_circle.jpg"  width="60%" height="60%"></img>


#### 多轮对话能力

#### 大型语言模型评估的可解释性
<img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/superclue_open_example.jpeg"  width="115%" height="115%"></img>


## 如何在SuperCLUE-Open上评估新的模型

1.SuperCLUE榜单大模型评测申请：https://wj.qq.com/s2/12305633/a73d/

（针对已公开发布、有代表性的模型服务或开源模型）

2.机构内部测评需求收集：https://wj.qq.com/s2/12307825/2ae0/

模型详情或需求描述中，请注明：“SuperCLUE-Open”

## 下一步
1. 在报告SuperCLUE-Open与SuperCLUE-Opt一致性基础上，添加SuperCLUE-Open与人类测评的一致性分析
2. 扩充测试集规模
3. 加入更多中文大模型


## 相关工作
1.论文：<a href='https://arxiv.org/abs/2306.05685'>Judging LLM-as-a-judge with MT-Bench and Chatbot Arena</a>

2.文章：<a href='https://lmsys.org/blog/2023-06-22-leaderboard/'>Chatbot Arena Leaderboard Week 8: Introducing MT-Bench and Vicuna-33B</a>

3.项目地址：<a href='https://github.com/tatsu-lab/alpaca_eval'>Alpaca_Eval: A validated automatic evaluator for instruction-following language models</a>

4.排行榜 <a href='https://tatsu-lab.github.io/alpaca_eval/'>AlpacaEval Leaderboard</a>


## 链接

1. <a href='https://github.com/CLUEbenchmark/SuperCLUE'>SuperCLUE-Opt</a>： 中文通用大模型综合性基准(基础能力、中文特性和专业能力）

2. <a href='https://www.superclueai.com'>SuperCLUE琅琊榜</a>：中文通用大模型匿名对战评价基准


## SuperCLUE-Open讨论与交流

<p float="left">   
  <img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/superclue_open_group.jpg"  width="30%" height="30%"></img>
  <img src="https://github.com/CLUEbenchmark/SuperCLUE-Open/blob/main/resources/img/brightmart_s.jpeg"  width="30%" height="30%"></img>
</p> 

## 致谢
本基准的成功运行离不开FastChat项目在源代码方面的大力支持，在此十分感谢Large Model Systems Organization(<a href=''>LMSYS ORG</a>)和<a href='https://github.com/lm-sys/FastChat'>FastChat</a>


## 引用

如果使用本项目的，请引用本项目，包括相关的论文或项目。

    @misc{SuperCLUE,
      author = {Liang Xu, Anqi Li, Lei Zhu, Hang Xue, Changtai Zhu, Kangkang Zhao, Haonan He, Xuanwei Zhang, Qiyue Kang, Zhenzhong Lan},
      title = {SuperCLUE: A Comprehensive Chinese Large Language Model Benchmark},
      year = {2023},
      publisher = {arxiv},
      howpublished = {\url{https://arxiv.org/abs/2307.15020}},
    }
