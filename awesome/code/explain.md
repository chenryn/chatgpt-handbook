# 代码解释

新手程序员在入门之初，最好的学习路径就是直接阅读其他人的代码，从中学会别人是怎么写的，为什么这么写。过去，这个学习过程可能需要广泛阅读官方文档，在 GitHub issue 上提问，上 Stack Overflow 网站查询，见缝插针找同部门的老同事帮忙……现在，我们可以试试让 ChatGPT 来当这个老师，由 ChatGPT 解释代码。

比如我们在 GitHub 首页右侧的开源项目趋势榜上找到今日热度最高的项目来学习，叫 Auto-GPT(由于 ChatGPT 的火热，目前趋势榜单上几乎都是 ChatGPT 相关内容)。在主要源代码目录 `scripts/` 里，看到一个叫 `llm_utils.py` 的 Python 文件。一般来说以 "util" 命名的文件里放的都死相当独立一些的抽象功能，可以方便快速阅读。我们就让 ChatGPT 来解释这个文件吧：

> 请解释下面这段 python 代码：
> import openai
> from config import Config
> cfg = Config()
> 
> openai.api_key = cfg.openai_api_key
> 
> # Overly simple abstraction until we create something better
> def create_chat_completion(messages, model=None, temperature=None, max_tokens=None)->str:
>     response = openai.ChatCompletion.create(
>         model=model,
>         messages=messages,
>         temperature=temperature,
>         max_tokens=max_tokens
>     )
> 
>     return response.choices[0].message["content"]

![](/images/awesome/explain-1.png)

ChatGPT很贴心的把文件分成了三段，分别解释了第一段导入 openai 外部库，第二段导入 config.py 内部实现类并创建对象，并将对象内的属性值传给 openai。第三段对具体函数做解释，分别包括入参和出参的含义、数据类型等等。

如果是我们自己写代码，其实同样可以让 ChatGPT 解读。这样可以看看 ChatGPT 的理解，是否和我们编程时考虑的逻辑保持一致。未来由其他同事来维护这段代码时，不至于产生误解。为了长期留存 ChatGPT 的解读，我们还可以指定 ChatGPT 按照代码注释说明文档的形式来生成：

> 为上述 create_chat_completion 函数生成一个 docstring 格式的注释

![](/images/awesome/explain-2.png)

生成结果非常惊艳。ChatGPT 不光解释了入参出参，还根据上下文提示了 config 配置的依赖前提，并给出了一个具体的函数使用和输出示例。可以说大大提升了代码的可维护性。

