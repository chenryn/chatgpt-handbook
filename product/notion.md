= notion

notion 是一款流行的笔记应用。不过功能实际远超笔记，官方自己定义是：“将笔记、知识库和任务管理无缝整合的协作平台”。其独特的 `block` 概念，极大的扩展了笔记文档的作用，一个 `block` 可以是个数据库、多媒体、超链接、公式等等。利用数据库 block，可以实现敏捷看板、日历、画廊等诸多高级功能。

notion 在 2022 年发布 notion AI 功能，可以在一至多个 `block` 上启动 AI 助手，帮助用户完成拼写修正，格式调整、内容扩缩、文本续写等 NLP 任务。和类似的 lex 等竞品相比，notion AI 能生成的内容更长更完整。免费账号试用 20 次后，可以通过信用卡方式购买 $10 月卡继续使用。

有趣的是，notion 官方拒绝公开自己的 AI 能力来源，同时在官网上也没有提过一次 GPT 字眼。但外界普遍认为 notion AI 是基于 GPT3 的接口进行微调实现的。

这个差异，也可以用来较好的区分 ChatGPT 和传统搜索引擎的差异。

因为外界传言甚多，所以当你询问 ChatGPT 时，它会给出比较模糊的回答：

![](/images/product/notion-ai-gpt.png)

而传统搜索引擎，用户可以通过 `site:notion.so "GPT"` 语法，指定查询 notion 官网内容，必须包含 GPT 字符，然后直接得到空结果：

![](/images/product/notion-ai-no-gpt.png)

浏览器地址栏输入 `https://www.notion.so` 访问 notion 官网。正常注册或登录账户后，就能看到 notion 文档编辑空间。notion 总体界面布局清晰简单，左侧是笔记列表，右侧是编辑器。编辑器中每行为一个 `block`，可以在行首点击呼出菜单栏，进行删除、复制、格式转换、颜色修改等操作。国内的飞书、语雀、我来笔记也都采用了类似设计。

![](/images/product/notion-page.png)

我们看到，notion 目前菜单栏顶部，多了一个选项，叫"Ask AI"。点击选项后，进入 AI 辅助文本生成状态。在当前 block 下方多出一个 prompt 输入框，输入 prompt 并回车，notion AI 将根据 prompt 自动生成一段文本。

![](/images/product/notion-ai-menu.png)

如果自己已经写了一部分文本，则可以通过 Ask AI 菜单栏的其他选项进行修改。包括：优化语法、修正拼写、扩写、缩写、按风格改写等。修改完成后，notion AI 会临时展示生成结果，我们如果满意，可以点击下方的"Replace selection"，将生成的内容替换掉原来的内容；或者点击"Insert below"，将生成的内容插入原来的内容下方；或者点击"Continue Writing"，让 notion AI 继续生成后续内容。

![](/images/product/notion-make-longer.png)

除了最重要的创作以外，notion AI 还可以做多语言翻译、文章概要总结等功能。如果主要工作内容是自然语言处理类任务，notion AI 一定程度上可以视为 ChatGPT 的优秀替代品，并更有针对性的设计了良好的人机交互方式，值得尝试。

