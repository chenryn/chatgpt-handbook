= docsGPT

基于企业内部独有的知识库，进行智能的客服问答，毫无疑问是 ChatGPT 出圈以后，所有公司想要融入 ChatGPT 技术时的第一反应。可惜 ChatGPT 实际上是一个基于大语言模型实现的，包括很多其他功能的，完整的聊天产品。并没有直接的接口让用户导入完整的知识库。

此外，openai 提供的 GPT3 接口服务，也必须一直联网使用。对部分传统的 toB 服务产品依然不太友好。有趣的是，业界似乎也都不推荐使用 GPT3 的 fine-tuning 方式，甚至据说 fine-tuning 方式加入新训练数据后反而会导致通用文本的生成能力下降。

docsGPT 开源项目，针对这种情况，采用 GPT3 接口，配合 feiss 向量搜索引擎和 langchain 模型库，快速实现了一个针对技术文档的智能客服。可以作为这类产品的基础原型，供大家参照。

