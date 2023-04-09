# 如何识别来自 ChatGPT 的文本输出

既然 ChatGPT 生成的内容需要和人类生成的内容有明确的区分，那如果我们拿到一个几经转手的、缺失标记的内容片段，有没有办法来判断他的作者，到底属于 ChatGPT，还是属于人类呢？

openai 公司，为此主动推出了内容检测工具：<https://platform.openai.com/ai-text-classifier>

注意：该内容检测工具只能检测超过 1000 个字符的长文本。对于英文来说，这可能也就是一两百个单词，但对于中文来说，就是扎扎实实五百个汉字了。

该工具对输入的文本，会给出：very unlikely, unlikely, unclear if it is, possibly, likely AI-generated 五种分类判断。AI 生成的概率依次变高。

我们使用当前最流行的 AI 写作工具 notion AI，来写一篇 ChatGPT 相关的 ICL 和 CoT 的介绍。这两个概念，在之前章节中已经提过。让我们看看 notion AI 的输出：

![](images/law/notion.png)

虽然外界一直传言 notion AI 的背后使用的就是 openai 公司的 GPT3 接口，不过 notion 公司官方其实一直拒绝证明回答，官网上也完全没有提及 GPT 技术字样。用 notion 生成的文本做检测，正好也是一个验证。

让我们打开 openai 的内容检测工具，将 notion 生成的内容复制粘贴进 Text 文本框，然后点击 Submit：

![](images/law/gpt-checker.png)

没问题，成功分类为：AI 创作内容。

但如果仅仅将一段自己编写的材料，通过 notion AI 仅仅进行 fix spelling & grammar 优化，那就很难区分了：

![](images/law/notion.png)

这次，openai 的内容检测工具就认为内容确实是人类完成的了：

![](images/law/gpt-checker-2.png)

事实上，openai 公司自身发布检查工具时，表示该工具的召回率只有 26%。AI 文本的检测，依然还是一个未解决的问题。斯坦福大学也在 2023 年发布了一个 DetectGPT 工具，通过人类文本和 AI 修改后的差异概率，来训练检查模型。但对未开源模型只提供 API 形式的 ChatGPT 并没有太好效果。

所以，我们既要对 ChatGPT 输出的内容保有一定的警觉性，不要过于信任，也应该持有一定的信任，在自己的主见之上，合理的运用 AI 技术，取得更好效果。

