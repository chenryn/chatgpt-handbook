=  API 的使用

== api 权限开通

== GPT-3.5 API

openai 公司于 2023 年 3 月 2 日宣布开放 ChatGPT 使用的 GPT-3.5 模型访问 API。其使用方式和 GPT 系列掐模型基本类似，不过 GPT-3.5 接口目前只支持通过 prompt 方式进行 Chat Completion，不支持 fune-tuning。因此，本节将分别介绍两个版本的 API 简明使用示例。

要强调的是，所谓的 ChatGPT 接口，其实只是 ChatGPT 所用的算法模型 "gpt-3.5-turbe" 的接口，ChatGPT 本身还有产品技术层面的前置 instruction/prompt 等设计，所以，个人通过接口使用时，需要自行处理 prompt 、上下文会话聚合摘要等过程——当然，最终效果比不上 openai 公司多年专业 prompt engineering 效果，也是理所当然了。

== GPT-3 API

