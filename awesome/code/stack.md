# stackoverflow 解释

ChatGPT 公开服务以来，程序员们无疑是最早深入体验和"测试"的一批人。出色的效果也引发了一系列知识产权上的争议。著名的 stackoverflow 网站，就宣布禁止用户使用 ChatGPT 生成的内容来回答问题，一经发现，哪怕回答是正确的，也要封号——而不仅仅是删除这个回答。

事实上，对于通用开发框架或中间件的报错，ChatGPT 的回答准确度可能并不像 Stack Overflow 说的那么低。作为一线 7 * 24 小时 oncall 的入门级 IT 人员，使用 ChatGPT 来辅助判断故障，不失为有效之举。

<https://github.com/shobrook/stackexplain> 项目，就是一个简化工具。项目逻辑非常简单，判断运行程序是什么语言，然后 prompt 中预先提示 ChatGPT，结果交由 ChatGPT 解释。对应的 prompt 如下：

>请简明扼要的解释 {language} 程序的错误信息:
>
>{error_message}
>

其中{language}是程序语言，{error_message}是报错信息。我们完全可以在 ChatGPT 的聊天界面上，使用这段 prompt 要求他帮助我们解释错误原因并给出解决方案，如下图所示：

![](/images/awesome/code-language-stackexplain1.png)

可以看到ChatGPT对这个错误给出了准确的解释，甚至给出了解决方案，但是因为这个ChatGPT并没有产生错误的源码，所以无法给出具体的代码示例，我们可以把出错的源代码片段也告知ChatGPT，让他结合刚才的错我帮我们修改成正确的代码，如下图所示：

![](/images/awesome/code-language-stackexplain2.png)

修改后的代码经过测试是可以运行的，也得到了我们想要的结果，如果我们利用好这个工具，可以在解决代码问题的时候节省大量的时间，提高工作效率。

在基础设施层排障场景，目前有越来越多的小工具在基于 ChatGPT 构建，比如实现 bpftrace 编写的 GPTtrace、实现kubenertes 状态解读的 k8sgpt 等等。

