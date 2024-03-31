## 笔记二
### [轻松玩转书生·浦语大模型趣味 Demo](https://www.bilibili.com/video/BV1AH4y1H78d)

**Demo实战**
1. 实战部署InterLM2-Chat-1.8B
2. 实战部署八戒-Chat-1.8B (10% A100)
3. 实战进阶运行Lagent智能体Demo (30% A100)
4. 实战进阶灵笔InternLM-XComposer2 (50% A100)

**书生·浦语大模型SIG**
- 角色扮演兴趣小组
- RAG兴趣小组
- 多模态学习小组
- Agent学习小组
- Deploy并行与量化兴趣小组
- 模型评测兴趣小组
- 兴趣小组圆桌会议
  
Chatty-Horo (基于《狼与香辛料》小说文本、对话等语料)  
Roleplay-With-XiYou (基于《西游记》原文、白话文、ChatGPT生成数据)  
Chat-嬛嬛 (基于《甄嬛传》剧本)

教程地址:
https://github.com/InternLM/Tutorial/blob/camp2/helloworld/hello_world.md

Notes:  
**InterLM2-Chat-1.8B**  
创建约20 mins之后显示可以进入开发机  
`studio-conda -o internlm-base -t demo` (约12 mins)  
`conda activate demo`  
根据下载速度推测带宽约为500Mbps, InterLM2-Chat-1.8B约占显存5G  
Prompt:  
请创作一则短小精悍，具有获奖潜质的300字故事  
使用`exit`离开

**Bajie-Chat-1.8B**  
`ssh -CNg -L 6006:127.0.0.1:6006 root@ssh.intern-ai.org.cn -p [port_num]`
bUQomoXzlbOXmCTS
`pip install huggingface_hub`  
`from huggingface_hub import hf_hub_download`
`hf_hub_download(repo_id="internlm/internlm2-chat-7b", filename="config.json")`