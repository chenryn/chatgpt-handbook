# 不成功示例：避坑指南

ChatGPT 作为一种人工智能文本生成技术，有可能产生虚假、错误或无意义的对话内容。在 ChatGPT 成为新一代人工智能代表性产品的今天，人类可能会产生一种科技崇拜，认定 ChatGPT 输出的权威性，最后造成负面影响。类似的现象，在二十年前互联网诞生之时，搜索引擎技术就曾经经历过。至今，我们依然经常看到医患关系的新闻，患者经常以"百度上说我这种情况是 XXX"为由，质疑医生的判断。如果对 ChatGPT 没有正确的认知，不了解 ChatGPT 的错误内容风险，类似的"ChatGPT 说我这个病怎么治"，很可能会出现在现实中，比搜索引擎更加可怕。

和 ChatGPT Checker 能初步检查文本内容是否由 AI 生成不同，ChatGPT 生成文本的"正确性"，目前尚无专门的检验或鉴别算法。因此，我们只能通过一些大的原则，提前判断 ChatGPT 的适用场景，避免在这些场景中，过于依赖 ChatGPT。

比如下面是一个很好的示例，ChatGPT 根据"林黛玉"的人物性格，"倒拔垂杨柳"的可能性，编造一个完整的故事，有理有据有始有终。生成完毕以后，ChatGPT 甚至因为其中关键字"自杀"的负面情绪，触发了红色风险警告！但本次问答最根本的问题是：《红楼梦》中根本不存在林黛玉倒拔垂杨柳这么件事情。这个内容是不可信的。

![](/images/badcase/diff.png)

谈 ChatGPT 的不成功用例，我们其实可以先放大到更广阔的 AIGC 领域。当前所有 AI 都是在人类现有知识和数据基础上进行训练的。因此，它们在某种程度上，也都有类似的局限性。

依然是 Stephen Wolfram 的话：

 And indeed, much like for humans, if you tell it something bizarre and unexpected that completely doesn’t fit into the framework it knows, it doesn’t seem like it’ll successfully be able to “integrate” this. It can “integrate” it only if it’s basically riding in a fairly simple way on top of the framework it already has.

所以当 AI 用于创作时，需要足够合理的假设和引导。打个比方，古代人类设想了各种非人、半人的神仙妖怪，比如半人马族，至今都有大量的讨论：人马族奔跑的风阻怎么样？人马族的内脏怎么分布？诸类等等。这还是人和马勉强都算动物。现在如果让 AI 来创造一个半人车族，AI 画的出来么？显然不能，AI 只能理解为车里的司机或者车外的模特。

事实上，由于法律或者训练集限制的原因，实际动手操作一下就会发现，目前最流行的画图 AI，stable-diffusion 和 dalle2，如果仅使用文生图方式的 prompt，压根连人马族都画不出来。我多次测试，绝大多数输出都是普通的马或人骑马，偶尔能出来一次人身马脸、人屁股上铺个马鞍……

具体到 ChatGPT 方面，同样在大语言模型领域卓有建树的 cohere 公司创始人 Yunyu Lin，曾经著文讲解他认为最合适大语言模型的三类场景：

 1. There is no one correct answer (creative applications, summarization)
 2. There is some tolerance for error (routing, tagging, searching, and other tasks where perfection isn’t required)
 3. The answer can be easily verified (math, writing code for specific tasks, or human-in-the-loop use cases).

ChatGPT 的可用场景，显然是列举不完的。但从这几个特点，我们可以反向提取出 ChatGPT 不合适的场景特点：

1. 有明确且唯一可行的标准定义
2. 即使稍微犯错也会造成较大影响，故而不可接受
3. 错误不是很容易发现或证实，至少相对当前使用者的知识水平来说很难

一旦某个场景，会同时满足以上 3 个条件，那显然就不太适合使用 ChatGPT。

