# bingchat

## new bing

微软作为 openai 公司背后的大股东，多年投入一朝开花结果，当然要把 ChatGPT 技术融入到自己的核心产品中，提升整体生产力。微软的第一个措施，就是在必应搜索引擎 bing.com 中，嵌入 ChatGPT。

ChatGPT 一次训练花费甚巨，所以模型一直保留在 2021 年的数据训练结果上。但搜索引擎需要一直爬取最新的网页，提供最新的新闻、博客、文章和知识，所以，微软设计了一套传统 NLP 技术和 ChatGPT 技术融合协作的新一代搜索产品，并称为 New Bing。

New Bing 目前还处于公测阶段，必须排队申请试用。在浏览器地址栏中输入 <https://www.bing.com/new> 访问官网点击申请加入 waitlist，系统将提示您使用微软账号登录。曾经有微软账号的请尽量试用老账号登录而不是随手点击重新注册一个，这样有助于提升申请试用的排队优先级。过去的 MSN 账户、hotmail 邮箱、Windows 正版电脑等，都属于微软账号体系，可以使用。

![](/images/collaboration/bing-waitlist.png)

申请获批后，再访问 bing.com 时，输入搜索问题，我们就会发现搜索页面和过去有所不同。比如我们搜索"人工智能可以做什么"，必应会识别到"人工智能"是个专属名词，在页面右侧直接返回"人工智能"的知识图谱内容：

![](/images/collaboration/bing-before.png)

而我们搜索"日志分析可以做什么"，必应找不到对应的知识图谱内容，就会在搜索结果的顶部，普通的网页结果和相关搜素提示之外，还新增 ChatGPT 问答区域。其中 ChatGPT 给出了自然语言式的回答，并列出自己主要参考的资料：

![](/images/collaboration/bing-after.png)

如果网页结果不太满意，想通过 ChatGPT 做进一步交流，可以点击 ChatGPT 区域的 message 对话框开始输入问题，也可以点击顶部菜单栏的 "chat" 或鼠标/触控板滚动下拉，进入全屏 Chat 状态，开始具体聊天过程：

![](/images/collaboration/bing-fullscreen.png)

### new bing 原理解读

从 new bing 的 chat 页面上，我们可以看到必应团队如何把不同技术融合在一起，设计成新一代搜索产品。整个流程总结如下：

1. 分词并提取搜索关键字——传统 NLP 技术实现。在上图示例中，我们明确看到必应尝试搜索"日志分析"关键字。
2. 查询获取若干相关性最高的网页——传统搜索引擎技术实现
3. 将网页内容，通过预设的 prompt 模板处理，提交给 ChatGPT 作为上下文——New Bing 的创新性设计
4. 将你的原始问题提交给 ChatGPT——ChatGPT 的核心
5. 给出回答和引用题注——New Bing 的创新性设计，在上图示例中，我们看到有些句子的末尾，会夹杂着上标 `1` 的引用计数。点击可以直接打开来源网页。
6. 根据内容生成若干可选问题，以及是否满意的反馈——一个回答完成，会利用 ChatGPT 的文本生成能力，主动提出几个候选问题。同时附加一个满意不满意的选项，辅助人工反馈的收集，继续提升 ChatGPT 算法效果。

这种流程，在学术上，被称为知识整合提示(knowledge integration prompts)，即把新内容和模型内已有旧知识进行整合输入。

既然第 2 步可以获取网页内容，用户也就可以在问答过程中，直接提供额外的 URL 地址，New Bing 识别到 URL 以后，也同样会获取该 URL 的网页内容，提交到 ChatGPT。指定内容，又比搜索引擎自行搜索，要更精准。比如上例中，列出的产品都不太满意，我们可以直接提供自己已知的产品官网，要求进行对比：

![](/images/collaboration/bing-url.png)

在每一步对话中，都可以重复这个过程，某种程度还可以加强 ReAct(Reason Action) 提示框架的效果。即上一次回答中如果给出了还不够明确的结果时，我们可以重复这些结果关键词，让 New Bing 再次 Action(针对性搜索)，得到更精确结论。

注意：New Bing 控制一次会话最多只能进行 8 次提问，甚至在第 5 次时，前面的小绿点就开始变黄做警示。你可以点击 message 框左侧的扫帚图标，重新开始会话问答。

### new bing 语气偏好设置

刚开始一个新的会话问答时，New Bing 会提示你设置本地会话的语气偏好，可以从平衡改为更有创意的，或是更严谨的。

假设我们设置为更有创意(creative)的偏好，New Bing 就会在你提问范围之外，做更多的响应。比如我们重复上一次的问答过程，看到 creative 下 New Bing 新增了一段内容，而且这段内容没有一处引用题注，是纯 ChatGPT 编写：

![](/images/collaboration/bing-creative.png)

相反，设置为更严谨(precise)的偏好，New Bing 就会尽量简洁的回答问题，绝不做多余的扩展。以至于我们重复上一次的问答过程时，看到 precise 下 New Bing 给出的工具推荐到第二个就停下，无法直接应对我们的第三个问题，要重新搜索一次 Elastic Stack 关键字才能继续：

![](/images/collaboration/bing-precise.png)

### new bing 引用题注的风险

New Bing 引用题注的方式，一方面方便了我们快速查看最新和最直接的来源材料原始内容，一方面也让我们更加确信 ChatGPT 生成回答的准确性。但请注意：后者可能是一种错误信号！

![](/images/collaboration/bing-error.png)

如上图所示，New Bing 会在明显错误被用户明确指出的情况下，回答说自己是根据另一个引用出处总结的，如果两个出处有冲突，请你自行判断。事实上，无论引用出处 1 的龙榆生纪念网站，还是出处 2 的百度百科，实际内容都是正确的，没有 ChatGPT 这种错误用法。

因此，引用题注只是搜索引擎产品层的设计，并不影响 ChatGPT 文本生成算法的实质。请一定牢记这点。

New Bing 在公测过程中已经发挥了一定作用，微软还在逐步将 ChatGPT 技术加入更多的微软产品中，例如 Edge、Skype、Windows 11 操作系统的桌面任务条等等。相信 New Bing 功能的可用范围也会逐步扩大，最终全面可用。

### new bing 引入不良搜索结果的风险

New Bing 通过即时查询获取搜索结果，并通过预设 prompt 传递给 ChatGPT 的方式，在有些情况下，可能反而误导 ChatGPT 自身的判断。对一些 ChatGPT 根据零散知识可以正常推断的结论，因为搜索引擎没有答案，New Bing 也无法正常回复。

比如我们想了解在 Linux 命令行中 `wc -m` 指令统计中文文本的字符数量，和 Word 软件中字数统计的字符数量有什么差别。问 ChatGPT 时，可以得到非常明确的回答：

![](/images/collaboration/chatgpt-wc.png)

但询问 New Bing 时，因为搜索引擎搜不到结果，反而导致 New Bing 也无法回答了：

![](/images/collaboration/bing-wc.png)

## edge dev

微软除了在 bing.com 搜索网站上引入 ChatGPT 以外，在自家另一款明星产品，Edge 浏览器中，也尝试引入 ChatGPT。目前仅限 Edge Dev 开发测试版本可用。

搜索 Edge Dev，或直接在浏览器地址栏中输入 <https://www.microsoftedgeinsider.com/en-us/download/dev>，打开 Edge Dev 官网，页面首屏正中间的位置就可以点击下载安装包。页面会根据您的电脑配置自动推荐对应操作系统的下载，比如 macOS、Linux(.deb)、Linux(.rpm)、Windows 10/11、Windows 8/8.1、Windows 7、iOS、Android 等。

下载并安装完成后，打开 Edge Dev，右上角会比普通 Edge 版本多一个 ChatGPT 图标，点击打开，网页右侧抽屉拉出，登录你的微软账号，就是 ChatGPT 对话区域了。如果你的 New Bing 试用申请还没通过，则依然无法使用。如果你还没申请使用，也可以在此时直接点击申请：

![](/images/collaboration/bing-waitlist.png)

New Bing 功能登录可用后，可以看到该区域有三个不同选择：

![](/images/collaboration/edge-dev.png)

* 聊天：支持设定响应的语气，包括精确、平衡和有创造力。为了控制使用，Edge Dev 也限定一次会话最多提 6 个问题。达到限制后，点击对话输入框左侧的扫帚图标，开启新一轮会话。
* 撰写：一个简易的文本编辑器，输入标题，就能根据 edge 预设的语气、格式、长度，生成你想要撰写的内容。
    * 语气：专业、休闲、热情、信息、古怪
    * 格式：段落、电子邮件、博客文章、创意
    * 长度：短、中度、长
* 见解：相当于藏在抽屉中的 bing.com 热门搜索。可以根据新闻热点开始聊天。

我们这里还是说说聊天功能的特殊设计。Edge Dev 里的 ChatGPT 和网页服务不同，它默认自己拿当前打开的标签页网页内容作为聊天背景材料。因此，你可以免去复制粘贴的手工操作、免去字数超标的担心，直接基于当前页面开聊。

加上 Edge 浏览器一直以来对主流文档格式都有超强的阅读支持，用来读文章，简直犀利无比。

普通文章我们已经见得多了，这次尝试解读一下更专业的学术论文。下面以 2023 年最新发表的一篇智能运维论文 LogPPT 为例，实际上其他论文也完全一样。

我们都知道，写论文、读论文其实一般是有套路的，内容大体都分为：内容摘要、场景问题、创新点、具体方法、评估结果、总结展望。

考虑到 ChatGPT 的输出字数有限，让他一口气全部解读完不太合适。所以，就按这个步骤来问吧：

1. Don't search the Internet, summarize this article according to what method, what technology is used, and what effect is achieved in this paper?
2. Don't search the Internet, what are the advantages of their solution compared with the previous ones, and what problems did they solve that the previous methods could not solve?
3. Don't search the Internet, please describe the main procedure of the method in detail in combination with the content of the Method section. Please use latex to display the key variables.
4. Don't search the Internet, combined with the Experiments section, please summarize what task and performance the method achieves? Please list specific values according to this section.
5. Don't search the Internet, please combine the Conclusion section to summarize what problems still exist in this method?

刚好五个问题，不超标。

注意每次提问前都要加上"Don't search the Internet"，否则 edge 会和 new bing 一样，同时尝试将提问关键词在互联网进行搜索，把搜索结果也作为背景知识传给 ChatGPT。在只想阅读论文时，我们没必要掺入互联网内容。当然，另一些时候，可能论文中引用的知识描述不详细，可能引用一些外部知识又有助于理解，大家可以按情况自行决定。

![](/images/collaboration/edge-dev-chat.png)

如上图所示，ChatGPT 也会明确告知你，这段内容仅来自本页："The response is from the web page context"。否则，ChatGPT 开头会说："The response is from both the web page context and the web search results"。

上面这段特殊"咒语"，目前 edge dev 只识别英文，甚至连大小写都要保持一致。因此，即使你想用中文交流，也要先加上这句英文：

![](/images/collaboration/edge-dev-chat-chinese.png)

从上图我们可以看到，甚至连返回通知的数据来源告示，其实也是 edge dev 额外加的，并不是真正的 ChatGPT 响应结果。

