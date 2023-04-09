# 语言翻译

多语种翻译是 NLP 领域的经典话题，也是过去很多 AI 研究的热门领域。一般来说，我们认为主流语种的互译一定程度上属于传统 AI 已经能较好完成的任务。比如谷歌翻译所采用的的神经机器翻译(NMT, Neural Machine Translation)技术就一度让世人惊喜不已，直呼翻译已经可以被取代了。那么在翻译领域，ChatGPT 的表现如何呢？

我们选择一种中文领域比较特殊的存在作为测试——绕口令。相信这段绕口令是所有中国人耳熟能详的文本。

> 分别翻译如下一段绕口令为英文、日文、法文、葡萄牙文。
> 打南边来了个喇嘛，手里提拉着五斤鳎目。
> 打北边来了个哑巴，腰里别着个喇叭。

![](/images/awesome/translate.png)

作为对应，我们看看翻译为英文的部分，中国的有道词典、美国的谷歌翻译和德国的 DeepL 的结果。DeepL 是前段时间名噪一时的新产品，号称机器学习效果足以对标谷歌翻译。这三者的翻译一般来说结果比较稳定，不像 ChatGPT 可能生成会有差异，所以我们直接复制结果上来。

有道词典的翻译结果为：

> To the south came a lama, carrying five pounds of sole in his hand.
> There's a dumb guy up north with a trumpet in his waist.

谷歌翻译的翻译结果为：

> A lama came from the south, holding a five-jin sole in his hand.
> From the north, let me be a dumb, with a horn in his waist.

DeepL 的翻译结果为：

> A lama came from the south, carrying five pounds of sole in his hand.
> To the north came a dumb man with a trumpet in his waist.

对比来看，除谷歌翻译那个莫名其妙的"let me be a dumb"外，大家表意都基本正确，就是 holding 和 hand 有些重复累赘。不过如果考虑绕口令属于一种带韵律的文本，ChatGPT 生成的结果，韵律感形式非常明显，确实更胜一筹。

