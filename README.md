# SuperCLUE-open
中文通用大模型开放域多轮测评基准 | An Multi-turn Open Domain Benchmark for Foundation Models  in Chinese

## SuperCLUE榜单

SuperCLUE-open：开放域多轮交互；SuperCLUE-opt：三大能力，客观题；SuperCLUE-lyb：开放域众包匿名对战

|      model      | SuperCLUE-open  | SuperCLUE-opt  | SuperCLUE-lyb  |   许可证   |
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
|  baichuan-7B（预训练模型）    |      3.11      |     48.18     |            -      | 开源，商用申请|

SuperCLUE是一个综合性基准，包括三个子基准：开放域多轮交互<a href='https://github.com/CLUEbenchmark/SuperCLUE-open'>SuperCLUE-open</a>，
客观题形式的三大能力<a href='https://github.com/CLUEbenchmark/SuperCLUE'>SuperCLUE-opt</a>（基础能力、中文特性和专业能力），
众包匿名对战形式的<a href='https://www.SuperCLUEAi.com'>琅琊榜</a>


## 使用SuperCLUE-open来评估中文大模型

### 动机
当前已经有一些评价中文大模型的基准，如C-Eval, MMCU，但是这些基准可能不太擅长评估大模型的人类偏好。
传统的基准通常以封闭式问题形式进行测试，要求模型输出简要的结论（如多项选择），但是他们不能很好的反映大模型的典型使用场景（如生成、创作和提供想法）。
当前也刚刚出现一些基准，如加州伯克利的MT-bench, 斯坦福大学的Alpaca-Eval，可以用于评估开放域问题，但是这些基准都是英文。
中文的代表性闭源和开源模型总体上无法进行有效评估。

为了缓解这个问题，我们发布了SuperCLUE-open与SuperCLUE琅琊榜。

SuperCLUE-open：是一个有挑战的多轮对话测试集，用于评估中文大模型对话式和遵循指令的能力。

SuperCLUE-lyb: SuperCLUE琅琊榜是一个众包匿名对战平台，用户问自己感兴趣的问题，并且投票他们喜欢的答案。


### 什么是SuperCLUE-open
这里做一些介绍

## SuperCLUE-open与人类的评估的一致性

### 如何对中文大模型进行评分
这里写评分过程和问题，一致性

## 结果与分析
#### 有效区分行的中文大模型

#### 多轮对话能力

#### 大型语言模型法官的可解释性
这里加一个示例（是否是新的？）

## 如何在SuperCLUE-Auto上评估新的模型
链接或办法

## 下一步

## 相关工作

## 链接



