= bingchat

== new bing

== edge dev

微软除了在 bing.com 搜索网站上引入 ChatGPT 以外，在自家另一款明星产品，Edge 浏览器中，也尝试引入 ChatGPT。目前仅限 edge dev 开发测试版本可用。



安装完成后，打开 Edge Dev，右上角会比普通 Edge 版本多一个 ChatGPT 图标，点击打开，网页右侧抽屉拉出，就是 ChatGPT 对话区域了。可以看到还有三个不同选择：

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

 Don't search the Internet, summarize this article according to what method, what technology is used, and what effect is achieved in this paper?

 Don't search the Internet, what are the advantages of their solution compared with the previous ones, and what problems did they solve that the previous methods could not solve?

 Don't search the Internet, please describe the main procedure of the method in detail in combination with the content of the Method section. Please use latex to display the key variables.

 Don't search the Internet, combined with the Experiments section, please summarize what task and performance the method achieves? Please list specific values according to this section.

 Don't search the Internet, please combine the Conclusion section to summarize what problems still exist in this method?

刚好五个问题，不超标。

注意每次提问要加上"Donot search the Internet"，否则 edge 会和 new bing 一样，同时尝试将提问关键词在互联网进行搜索，把搜索结果也作为背景知识传给 ChatGPT。在只想阅读论文时，我们没必要掺入互联网内容。当然，另一些时候，可能论文中引用的知识描述不详细，可能引用一些外部知识又有助于理解，大家可以按情况自行决定。

![](/images/collaboration/edge-dev-chat.png)

如上图所示，ChatGPT 也会明确告知你，这段内容仅来自本页："The response is from the web page context"。否则，ChatGPT 开头会说："The response is from both the web page context and the web search results"。

上面这段特殊"咒语"，目前 edge dev 只识别英文。因此，即使你想用中文交流，也要先加上这句英文：

![](/images/collaboration/edge-dev-chat-chinese.png)

从上图我们可以看到，甚至连返回通知的数据来源告示，其实也是 edge dev 额外加的，并不是真正的 ChatGPT 响应结果。

