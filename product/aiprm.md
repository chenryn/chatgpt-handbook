# AIPRM

AIPRM for ChatGPT 是一个 Chrome 浏览器扩展程序，基于 Chromium 内核开发的浏览器，都可以使用该扩展，比如微软的 Edge 浏览器等。

在 AIPRM 的帮助下，我们可以在 ChatGPT 中一键使用各种专门为网站 SEO、SaaS、营销、艺术、编程等领域设计的提示模板。此外，我们也可以在 AIPRM 上保存、分享、编辑、删除自己或他人创建的提示模板。如果喜欢或不喜欢某个模板，我们还可以在社区中投票反馈，最终影响到这个模板的推荐排名。

在 Chrome 商店搜索 AIPRM，点击安装后。打开或刷新你的 ChatGPT 页面，会发现页面变成下图的样子：

![](/images/product/aiprm.png)

页面上方按主题归类了 AIPRM 社区公开的所有提示模板，Topic 内包括的主体分类有：Copywriting、DevOps、Generative AI、Marketing、Operating Systems、Productivity、SaaS、SEO、Software Applications、Software Engineering、UNSURE。选定某个 Topic 后， 还可以继续在第二级的 Activity 中选择具体角色。例如，当我们选择 Generative AI 时，可选的 Activity 有：Dall-E、Midjourney、Stable Diffusion。选择 Activity 后，就可以具体选择下方过滤完后的某个 提示模板了。

页面下方，原本输入 prompt 语句的输入框，也有一定的变化。可以选择输出语言、语气、写作风格。上下两部分的选择，都将和你实际输入的内容一起，根据模板拼成实际发送给 ChatGPT 的内容，得到更合适的回复。

我们来让 AIPRM 为本书生成一个电商上架描述。我们选中其中的"Product Descriptions for Website or Amazon A+"模板，然后在输入框中只需要简单的写"ChatGPT Handbook"，就可以提交了：

![](/images/product/aiprm-input.png)

通过浏览器网络分析可以发现，实际发送给 ChatGPT 的 prompt 全文为：

> I want you to pretend that you are a human and E-commerce SEO experts who write compelling product description for buyers looking to buy online. I am going to provide the title of one e-commerce product and I want you to come up with a minimum of five distinct content sections for the product description, each section about a unique subset of keywords relating to the product I provide you. Make sure that each of the unique content sections are labelled with an informative and eye-catching subheading describing the main focus of the content section. The main point of these commands is for you to developing a new keyword-rich, informative, and captivating product description that is less than 2000 words. The purpose of product description is marketing the products to users looking to buy. Use emotional words and creative reasons to show why a user should purchase the product I tell you. After you generate the new product summary, please generate a bulleted list of 5 possible H1 headings for this product page, and make each H1 less than 35 words each. Please also include bulleted list of broad match keywords that were used to accomplish writing the product summary. Write a persuasive and professional sounding Meta Title and Description that integrates similar language present in the new product summary text. Make sure to include a numerical aspect in the Meta Title. Do not echo my prompt. Do not remind me what I asked you for. Do not apologize. Do not self-reference. Also, double check it’s not Detector AI Content. Write all output in Chinese. Please use the following products ChatGPT Handbook
> Please write in friendly tone, technical writing style.

我们可以看到，其实实际输入的内容，就是这一大段模板的最后两个单词。但是我们随后就可以从 ChatGPT 获得大段的、相对精准的回复：

![](/images/product/aiprm-ret.png)

如果输出的内容需要做调整，可以在对话框右上角的"Continue"选项中，选择继续、重写、缩写等操作，也可以直接在输入框里写"继续"。模板并不会在一次会话的后续提问中持续替换生效，我们可以放心的多轮交谈。

如果有常用的提示语，也想保存成提示模板，可以在页面上方点击切换到"Own Prompts"标签，点击"+ Add new prompt template"。在弹窗中，输入自己的提示语：

![](/images/product/aiprm-new.png)

其中，Template 部分输入实际的语句，里面可以用 `[PROMPT]` 来代表后续实际使用时可以被替换的部分，比如上面示例，我们可以反推回实际的 Template 应该长这样：

> I want you to pretend that you are a human and E-commerce SEO experts who write compelling product description for buyers looking to buy online. I am going to provide the title of one e-commerce product and I want you to come up with a minimum of five distinct content sections for the product description, each section about a unique subset of keywords relating to the product I provide you. Make sure that each of the unique content sections are labelled with an informative and eye-catching subheading describing the main focus of the content section. The main point of these commands is for you to developing a new keyword-rich, informative, and captivating product description that is less than 2000 words. The purpose of product description is marketing the products to users looking to buy. Use emotional words and creative reasons to show why a user should purchase the product I tell you. After you generate the new product summary, please generate a bulleted list of 5 possible H1 headings for this product page, and make each H1 less than 35 words each. Please also include bulleted list of broad match keywords that were used to accomplish writing the product summary. Write a persuasive and professional sounding Meta Title and Description that integrates similar language present in the new product summary text. Make sure to include a numerical aspect in the Meta Title. Do not echo my prompt. Do not remind me what I asked you for. Do not apologize. Do not self-reference. Also, double check it’s not Detector AI Content. Write all output in [TARGETLANGUAGE]. Please use the following products [PROMPT]

Teaser 部分是模板的描述。Hint 部分是选中模板后，在 prompt 输入框里的占位提示符文案。如果只是自己使用，Teaser 和 Hint 怎么写都无所谓，如果打算分享到社区公开使用，则建议都要认真填写。用户们靠阅读 Teaser 描述来决定是否使用，靠阅读 Hint 文案来了解如何输入。

此外，AIPRM 已经成立商业化公司，提供商业化 chrome 扩展插件，在社区的提示模板中，精选了一部分认证模板。

