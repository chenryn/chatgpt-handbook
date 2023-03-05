= badcase

谈 ChatGPT 的不成功用例，我们其实可以先放大到更广阔的 AIGC 领域。当前所有 AI 都是在人类现有知识和数据基础上进行训练的。因此，它们在某种程度上，也都有类似的局限性。

依然是 Stephen Wolfram 的话：

 And indeed, much like for humans, if you tell it something bizarre and unexpected that completely doesn’t fit into the framework it knows, it doesn’t seem like it’ll successfully be able to “integrate” this. It can “integrate” it only if it’s basically riding in a fairly simple way on top of the framework it already has.

所以当 AI 用于创作时，需要足够合理的假设和引导。打个比方，古代人类设想了各种非人、半人的神仙妖怪，比如半人马族，至今都有大量的讨论：人马族奔跑的风阻怎么样？人马族的内脏怎么分布？诸类等等。这还是人和马勉强都算动物。现在如果让 AI 来创造一个半人车族，AI 画的出来么？显然不能，AI 只能理解为车里的司机或者车外的模特……

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

