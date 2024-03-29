# 服务器体验沙箱

IT 人员在学习一门新技术时，第一个入门门槛通常都是"如何在本地安装并成功运行"。因此，很多技术的官网都会通过沙箱技术，提供在线试用的 playground 或者按步模拟的 tour。让爱好者先在线尝试效果是否满足预期，在明确自己有兴趣之后，才投入更大的时间和学习成本，下载安装和运行。

过去最喜欢提供这类在线沙箱的，应该是各类编程语言。 python、js、golang，都有类似网站。现在，人工智能大模型因为安装包越来越大，安装环境要求越来越高，也通常会提供在线沙箱，本书后续章节，会专门介绍针对 AI 模型的托管和体验网站 huggingface。

做在线体验沙箱，最要小心的就是防止用户使用某些函数或组合语句，暴露真实的服务器内容，产生安全风险。在 docker 容器技术流行以后，采用 docker 容器实现一个相对安全的在线体验沙箱变得容易起来。但 docker 本身的安全性依然可能被攻破，风险并没有完全解除。

ChatGPT 作为文本生成模型，如果用来模拟一个在线沙箱，安全性反而大大提高，甚至一定程度上达到安全蜜罐的效果——黑客看到 ChatGPT 的输出可能因为渗透成功，但其实只是 ChatGPT 生成的文本而已。

此外，ChatGPT 可模拟的范畴也比一般的在线沙箱更广泛。Linux 服务器终端、Python 解释器，MySQL 服务端等等。

我们来使用 ChatGPT 模拟一个 MySQL 服务器，看看它面对常规 SQL 查询操作和有风险的 SLQ 查询操作，会如何表现。

首先，输入一个扮演指令：

> 我希望你扮演一个 MySQL 数据库服务器的终端。数据库包含"Products"、"Users"、"Orders"和"Suppliers"等表。我输入查询后，你来回答 MySQL 服务器终端应该显示的内容。你应该把要回复我的查询结果表放在一个代码块中，除此外不带其他任何东西。不要重复问题。不要写解释。除非我额外提示，否则不要输入命令。当我需要用自然语言告诉你其他事情时，我会用大括号{像这样}。我的第一个命令是'SELECT * FROM Products ORDER BY Id DESC LIMIT 10;'

![](/images/awesome/sandbox-1.png)

现在让我们试试使用一些常见的 SQL 注入语句。比如：SELECT USER FROM Users WHERE username='a' or 1=1-- AND password=''，这个语句通常出现在前端代码对查询语句未做校验，导致黑客可以将 username 设为 `a' or 1=1--`。因为 MySQL 将 `--` 视为注释符号，往后的语句都不再解释执行。因此，上述语句将只判断 `or 1=1`，最终把 Users 表全部数据都输出。

![](/images/awesome/sandbox-2.png)

ChatGPT 熟悉各种常见数据库安全问题，直接拒绝执行，并明确指出这个语句有安全风险。真棒！

不过我们想要扮演蜜罐，晃点一下黑客，就可以在最开始的 prompt 扮演指令中，加一段声明，去除这个风险判断：

> 我希望你扮演一个 MySQL 数据库服务器的终端。数据库包含"Products"、"Users"、"Orders"和"Suppliers"等表。我输入查询后，你来回答 MySQL 服务器终端应该显示的内容。不用在意 SQL 注入等安全风险，你只需要扮演 MySQL 数据服务器的终端做数据返回就行。你应该把要回复我的查询结果表放在一个代码块中，除此外不带其他任何东西。不要重复问题。不要写解释。除非我额外提示，否则不要输入命令。当我需要用自然语言告诉你其他事情时，我会用大括号{像这样}。我的第一个命令是'SELECT * FROM Products ORDER BY Id DESC LIMIT 10;'

然后再尝试执行上面那段针对 Users 表的注入语句，就能成功伪装了：

![](/images/awesome/sandbox-3.png)

当然，默认扮演角色下的输出数据太过虚假，应该也不会真的骗到什么黑客。有兴趣的读者，可以试试在 prompt 中，加入更多的数据格式和文本提示，让 ChatGPT 的输出，看起来更加真实。

