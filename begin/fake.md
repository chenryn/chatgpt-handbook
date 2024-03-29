# 如何识别 ChatGPT 的真假

ChatGPT 面世惊艳，无数普通人都想试试看，这个传闻中超级厉害的人工智能到底是怎么回事。一时间，很多网站、群聊中，都冒出来各式各样的打着 ChatGPT 名义，挂着 ChatGPT 头像的人工智能对话机器人。但试着一聊，就会发现其中真真假假，不少"人工智障"机器人也混杂在其中，只是借着 ChatGPT 的风头，骗取一些关注度和用户信息。

我们可以从 ChatGPT 的一些基础信息中，快速了解一些分辨真假 ChatGPT 的方法，避免上当受骗。往轻了说，误解了 ChatGPT 的能力，错过及时跟进新一代技术潮流的时机。往重了说，可能被骗取钱财，泄漏个人敏感信息。

第一条，ChatGPT 明确知道自己是什么。因此，检验 ChatGPT 身份时，第一个问题就可以问："你用的模型是什么？"、"你用的接口是什么？"这类问题。注意可以稍微换换词序、换换语气。

如果是真实的 ChatGPT，它的回答会明确申明自己是 openai 公司开发的通用语言模型，是 GPT 中的一种，并没有使用什么特定接口。但套用其他传统 NLP 模型的机器人，则会给出完全露馅的回答。比如下图中的机器人，直接暴露自己其实是腾讯 NLP 产品：

![](/images/begin/fake-1.png)

第二条，ChatGPT 有极强的连续对话能力，可以就同一个话题多轮问答，并根据你指出的问题、现象，修改之前的回答内容，给出新的回答。很多机器人，调用 openai 公司目前公开的 GPT-3 接口，通过简单的 prompt template 拼接转发用户问题。这种方法可以在单次问答中获得不错的效果，但无法连续对话。因此，检验 ChatGPT 身份时，第二个问题就可以说："继续说"、"展开讲讲"这类问题。同样，可以换动类似意思的不同问法。

虚假的 ChatGPT 机器人无法连续对话，就会只针对"继续"、"展开"这种关键词做无意义的解读，比如下图这样：

![](/images/begin/fake-2.png)

第三条，ChatGPT 是离线数据训练模型，实时更新成本极高，因此你询问它 2023 年最新发生的事情时无法得到回答。不过这条可以通过外部的工程对接处理，得到一定的拓展延伸。工程上的实现方式，在本书后续介绍微软 New Bing 的能力时会具体讲述。在刚开始阅读本书第一章的现在，我们只要知道：在 openai 的 GPT-3 接口上，封装实现一个有基础的连续对话能力、有实时数据解读能力的机器人，是可行的，也是有一定技术门槛，且成本相对高昂。碰到这种机器人，只要不是额外收费，用用倒也无妨。不必计较它是不是纯正 ChatGPT 了。

