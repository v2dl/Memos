## 笔记四 (XTuner 微调 LLM：1.8B、多模态、Agent)

### XTuner大模型单卡低成本微调实战

**Finetune**:\
LLM的下游应用中, 经常用增量预训练 (学习新的知识, 以知识文本为数据) 和指令跟随 (学习对话模板, 以对话问答为数据) 进行微调.\
LoRA & QLoRA -> Adapter层.

**XTuner**\
以配置文件的形式封装了很多微调场景.\
对于7B参数量的LLM, 微调所需的最小显存仅为8GB.

**微调LLM**\
**Flash Attention**: 将Attention计算并行化;\
**DeepSpeed ZeRO**: ZeRO优化. 通过将训练过程中的参数、梯度和优化器状态切片保存, 能够在多GPU训练时显著节省显存; 使用FP16的权重.\
微调细节见[教程1](https://github.com/InternLM/Tutorial/blob/camp2/xtuner/personal_assistant_document.md)、[教程2 (多模态)](https://github.com/InternLM/Tutorial/blob/camp2/xtuner/llava/xtuner_llava.md)及作业.