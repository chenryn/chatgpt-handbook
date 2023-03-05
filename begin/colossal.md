= opensource

在 ChatGPT 以外，谷歌、脸书等互联网巨头，也都发不过去千亿级参数的大语言模型，但在交谈问答方面表现相对 ChatGPT 来说都显得一般。根据科学人员推测，很重要的一部分原因是缺失了RLHF(Reinforcement Learning with Human Feedback，人类反馈强化学习)和PPO(Proximal Policy Optimization，近线策略优化)部分。因此，开源社区开始尝试在当前开源的千亿级参数大语言模型基础上，添加 RLHF 技术，尽力复现 ChatGPT 效果。

目前已知有两个开源项目在进行中：

* colossal <https://github.com/hpcaitech/ColossalAI/tree/main/applications/ChatGPT>
* chatllama <https://github.com/nebuly-ai/nebullvm/tree/main/apps/accelerate/chatllama>
