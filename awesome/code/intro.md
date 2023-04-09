# 编程类

编程逻辑是 ChatGPT 对比过去传统 AI 算法及预训练模型表现最优异和突出的场景。人们通常对 AI 的印象都是：科学家和程序员一起通过大量神乎其神的数学算法和程序代码，实现一套逻辑功能。而 ChatGPT "推翻"了这个印象，转而变成：程序员负责聊天提需求，AI 来写代码实现逻辑。

事实当然还没有乐观到不再需要程序员的地步，但ChatGPT确实可以一定程度上解放程序员的双手。后续章节，我们将通过一些编程中的场景，展示 ChatGPT 的能力。

同时拥有 GitHub 和 OpenAI 的微软公司，毫无疑问正是 AI 辅助编程领域的急先锋。微软副 CTO，Sam Schillace 根据自己的使用经验，总结了 9 条将 ChatGPT 用于软件编程领域的原则。这 9 条原则，既包括一些 ChatGPT 用于编程的优点和最佳实践，也包括 ChatGPT 作为编程助手还有什么缺点。这几条原则在英文中颇有韵律感和哲学意味，因此我同时保留其英文原文和中文翻译，方便大家理解：

1. Don’t write code if the model can do it; the model will get better, but the code won’t.(不要编写可以由模型完成的代码；模型会变得更好，但是代码不会)
2. Code is for syntax and process; models are for semantics and intent.(代码用于语法和流程；模型用于语义和意图)
3. Text is the universal wire protocol.(文本是通用的线协议)
4. Trade leverage for precision; use interaction to mitigate.(为了精确性而牺牲杠杆；利用交互来缓解)
5. The system will be as brittle as its most brittle part.(系统的脆弱性取决于其中最脆弱的部分)
6. Uncertainty is an exception throw.(不确定性是一种异常情况)
7. Hard for you is hard for the model.(对于你来说困难的事情，对于模型来说也是困难的)
8. Ask Smart to Get Smart.(好好提问，获取智慧)
9. Beware "pareidolia of consciousness"; the model can be used against itself.(谨防“意识的错觉”；模型可以被用来反过来使用)

其中，第 4 和第 6 条，可以指导我们如何更好的使用 ChatGPT 来获取更好的代码。比如，在使用 ChatGPT 辅助编程时，我们可以通过设置 `temperature` 为0，通过各种解析器做语法校验，把报错直接反馈给 ChatGPT 进行修改调整等手段，让 ChatGPT 生成更好的、更精确的结果。

而第 2、第 7 和第 8 条也在提示我们，不要忘记，ChatGPT 是来辅助编程的，但到底要做一个什么样的软件，决策人，还是我们自己。

最有趣的则是第 1 和第 3 条，过去我们需要熟悉各种技术框架、中间件的 API 和协议，写大量的对接代码，现在这部分恰恰很合适交给 ChatGPT 生成，我们只需要通过文本提问的方式要求对接就够了。

说了这么多，下面就让我们开始进入具体的编程场景示例吧。

