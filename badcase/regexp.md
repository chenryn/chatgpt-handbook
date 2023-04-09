# regex 生成

正则表达式可谓是一门让广大程序员们又爱又恨的技术。它易学难精，而且可维护性又差，别说交接给其他同事，同一个人写的正则表达式，三个月后回头再看，也可能完全不知所云。

因此，让 ChatGPT 来写正则表达式，成为很多程序员在接触 ChatGPT 时自然而然想到的场景。

ChatGPT 的训练数据中专门考虑了编程场景数据，所以确实对正则表达式有一定的理解能力。我们可以尝试让 ChatGPT 来解释一些年久失修的正则表达式：

![](/images/badcase/regexp-explain.png)

如上图所示，甚至可以让 ChatGPT 一本正经提出一些改进方案。在一定程度上，可以启发不太精通正则表达式的初级程序员。

但如果进一步希望 ChatGPT 可以从原始数据中直接编写出正则表达式，就会碰到很多麻烦。

首先，ChatGPT 更擅长全自动化的语义分析或实体识别，很难接受仅提取指定内容的约束。

![](/images/badcase/regexp-auto.png)

如上图所示，当我们直接要求 ChatGPT 生成正则，它看似给出了结果，但多出来很多我们并没有提及的命名捕获。这些多余的内容，反而需要我们再次明确提出去除哪些命名捕获字段才行。

仔细看的话，还可以发现我们最开始的 prompt 里其实已经要求了"Do not capture any other word"。所以再试试调整 prompt，加强一下捕获方面的描述，看看能不能让 ChatGPT 领会到我们期望的意思：

![](/images/badcase/regexp-without.png)

领会到意思以后，输出的结果质量就大幅下降，这个结果可以一眼看出错误非常严重，完全不正确—— "\S" 不可能匹配 url 和 HTTP 之间的空格。

由于 prompt 和 ChatGPT 模型的不确定性，我们多次调换 prompt 的语句次序和写法(就像下面列举的这样)，都没能获得更好的结果。

* "you can write a PCRE regex pattern to only capture them without any other word."
* "you can write a PCRE regex pattern to only capture them."
* "Do not capture but only match the other words in the pattern"

此外更重要的是，ChatGPT 生成的正则表达式，有时候肉眼难以定位问题，进行修正。我们回到本节之前全自动化识别生成的正则表达式，似乎一眼看过去应该是正确的：

 ^(?<ip>\d{1,3}.\d{1,3}.\d{1,3}.\d{1,3})\s-\s-\s[(?<datetime>[^]]+)]\s"(?<method>GET|POST|PUT|DELETE)\s(?<url>[^"\s]+)\sHTTP/\d.\d"\s(?<status>\d{3})\s(?<bytes>\d+)\s"[^"]+"\s"[^"]+"\s"[^"]+"\s(?<response_time>[\d.]+)\s(?<connection_time>[\d.]+)$

但事实上，当我们通过正则表达式的在线调试网站，进行实际测试时，会发现这个表达式其实并不正确：

![](/images/badcase/regexp-error.png)

知道这个正则表达式不对，但是错误具体在哪里，就很难判断了。如果靠肉眼判断，只能一点一点，从后往前删内容，慢慢调试，即使有上图展示的调试工具的帮忙，发现有两个隐藏问题，也不能直接调整正确：

1. `) Unmatched parenthesis`：调试工具说的错误是")"未闭合，但其实是datetime 前后 2 处"["和 1 处"]"没有转义；
2. `/ An unescaped delimiter must be escaped; in most languages with a backslash (\)`：此处调试工具说的错误可以直接修改。

正确可用的正则表达式应该是下面这样。对比 ChatGPT 的输出，可以说相似度极高，问题极难发现，但完全不可用：

 ^(?<ip>\d{1,3}.\d{1,3}.\d{1,3}.\d{1,3})\s-\s-\s\[(?<datetime>[^\]]+)\]\s"(?<method>GET|POST|PUT|DELETE)\s(?<url>[^"\s]+)\sHTTP\/\d.\d"\s(?<status>\d{3})\s(?<bytes>\d+)\s"[^"]+"\s"[^"]+"\s"[^"]+"\s(?<response_time>[\d.]+)\s(?<connection_time>[\d.]+)$

因此，正则表达式作为一种复杂的，难以调试的技术，无法符合 Cohere 提出的三原则中方便定位错误的要求，也不适合采用 ChatGPT 技术进行生成。

