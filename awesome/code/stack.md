= stackoverflow

ChatGPT 公开服务以来，程序员们无疑是最早深入体验和"测试"的一批人。出色的效果也引发了一系列知识产权上的争议。著名的 stackoverflow 网站，就宣布禁止用户使用 ChatGPT 生成的内容来回答问题，一经发现，哪怕回答是正确的，也要封号——而不仅仅是删除这个回答。

事实上，对于通用开发框架或中间件的报错，ChatGPT 的回答准确度可能并不像 Stack Overflow 说的那么低。作为一线 7 * 24 小时 oncall 的入门级 IT 人员，使用 ChatGPT 来辅助判断故障，不失为有效之举。

<https://github.com/shobrook/stackexplain> 项目，就是一个简化工具。项目逻辑非常简单，判断运行程序是什么语言，然后 prompt 中预先提示 ChatGPT，结果交由 ChatGPT 解释。对应的 prompt 如下：


我们完全可以在 ChatGPT 的聊天界面上，复制这段 prompt 进行使用：

