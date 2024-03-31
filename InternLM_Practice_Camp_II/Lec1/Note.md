## 笔记一
### Part 1. [书生·浦语大模型全链路开源体系](https://www.bilibili.com/video/BV1Vx421X72D/)
过去: 特定任务专用模型 => 现在: 通用多模态大模型  

**书生·浦语大模型开源历程:**  
230607, InterLM发布  
240117, InterLM2开源 (轻量7B, 中量20B | InterLM2-Base, InterLM2, InterLM2-Chat)  

回归语言建模的本质，开发新一代数据清洗过滤技术:  
多维度数据价值评估、高质量语料驱动的数据富集、有针对性地数据补齐  

**主要亮点:**  
20万tokens上下文；推理、数学、代码能力、创作能力、工具调用能力、内生计算能力提升

数学评测集 ([GSM8K](https://huggingface.co/datasets/gsm8k), [MATH](https://github.com/hendrycks/math))

**从模型到应用典型流程:**
1. 根据业务场景和算力进行模型选型    
2. 可能会进行: (全部 / 部分)参数微调、构建智能体与环境交互  
3. 模型评测、模型部署

**书生·浦语全链条开源开放体系:**
1. 数据 ([书生·万卷](https://opendatalab.com/OpenDataLab/WanJuan1_dot_0))  
书生·万卷1.0、书生·万卷CC
2. 预训练 ([InternEvo](https://github.com/InternLM/InternEvo))  
3. 微调 ([XTuner](https://github.com/InternLM/xtuner))  
增量续训 (垂类领域，数据: 文章、书籍、代码)、有监督微调 (高质量对话、问答数据 | 全量参数、部分参数微调)  
SFT: Supervised Fine-Tuning  
4. 部署 ([LMDeploy](https://github.com/InternLM/lmdeploy))  
5. 评测 ([OpenCompass](https://github.com/open-compass/opencompass))  
CompassRank、CompassKit、CompassHub
6. 应用 ([Lagent AgentLego](https://github.com/InternLM/agentlego/))  
多模态智能体工具箱 (LangChain, Transformers Agents, Lagent)

### Part 2. [InternLM2 Technical Report](https://arxiv.org/pdf/2403.17297.pdf)
InternLM2的训练流程报告  

SFT (Supervised Fine-Tuning, 监督式微调)  

COOL RLHF (Conditional Online Reinforcement Learning from Human Feedback, 基于人类反馈的条件在线强化学习), which adopts
a conditional reward model to reconcile diverse but potentially conflicting preferences and
executes Proximal Policy Optimization (PPO) over multiple rounds to mitigate emerging
reward hacking in each phase. 调和偏好

InternLM2 first employs Group Query Attention (GQA) to enable a smaller memory footprint when inferring long sequences.

1. 预训练: InternEvo  
预训练数据获取处理清洗、超参数选取、4k tokens上下文训练 => 32k tokens上下文
2. 微调对齐: SFT, COOL RLHF  
   GitHub长上下文代码数据
3. 评估 
