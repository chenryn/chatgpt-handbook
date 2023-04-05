# stable diffusion

## 直接生成

按照惯用的扮演思路，我们可以让 ChatGPT 扮演一个艺术家，协助我们生成绘图 prompt。考虑到 ChatGPT 和 DallE 同为 openai 公司产品，且 stable-diffusion 开源模型出现较晚，ChatGPT 训练数据中没有 stable-diffusion 相关内容，我们的扮演角色只能是 DallE。

 Pretend you are an advanced AI, optimized for dialogue and for generating helpful Dall-E 2 prompts. Please give me a numbered list of five prompts that I could provide Dall-E 2 that would result in an accurate representation of how you, Assistant, would look if you had a physical body.

然后以"冬天奔跑的小女孩"为题，要求生成 prompt：

![](/images/awesome/sd-1.png)

将 ChatGPT 提供的内容复制粘贴到 stable-diffusion 上得到效果如下：

![](/images/awesome/sd-ret.jpeg)

稍微有点 stable-diffusion 知识的用户都知道，AI 画图的 prompt 中，除了核心要素，还需要加一些风格描述，但是直接使用自己心仪的艺术家或者公众人物名字，又有侵权的危险。因此，我们可以让 ChatGPT 帮我们转写艺术家的风格或者公众人物的特征。比如，我们借鉴新垣结衣的长相时，可以让 ChatGPT 帮我们提取她长相的核心元素：

![](/images/awesome/sd-help-2.png)

现在，我们复制这段ChatGPT 回答中的纯描述部分，合并到原始 prompt 里，得到这么一段：

 illustration of a young japanese girl running through a wintery landscape. She has a heart-shaped face with soft, delicate features.  Her eyes are large and almond-shaped, with long eyelashes and a slight upward slant at the outer corners.  Her eyebrows are thin and arched, giving her a slightly quizzical expression.  Her nose is small and straight, and her lips are full and pouty.  She has a clear, porcelain complexion and a gentle smile that lights up her entire face.  Her hair is long and typically styled in loose waves or a simple, elegant updo.  Overall, she has a classic beauty that is both timeless and modern.

因为 stable-diffusion prompt 的关键字不一定非得是自然语言顺序，所以我们可以要求 ChatGPT 做一定的简化"please using short sentences and keywords"：

![](/images/awesome/sd-help-1.png)

得到的效果如下：

![](/images/awesome/sd-ret-2.jpeg)

## 思维链生成

绘图 AI 的 prompt 相对 ChatGPT 的 prompt 来说，还是有些不够自然语言。prompt 中标点符号的不同，句子次序的先后，甚至括号的数量，都对结果有明显的影响。因此，直接通过文本生成得到的 prompt 语句，最终画图效果可能未必如愿。

我们可以通过思维链方式，引导 ChatGPT 学会 prompt 中的规则，输出更好的结果。

第一步，给出一个包含各种复杂格式的 prompt 示例。为了让我们的示例一开始就有个较高的起点，可以选择上 <https://prompthero.com/stable-diffusion-prompts> 官网，选择 stable-diffusion 标签后，按照 Hot、Top 排序，找到一些效果较好的效果图，点击查看对应的 prompt，复制过来待用。作为示例，我们选择 3 月 3 日当天，首屏出现的若干图片的 prompt。先拿一张图片的 prompt 作为示例，让 ChatGPT 自行理解：

![](/images/awesome/sd-cot-1.png)

甚至可以像给小学生上课一样，让 ChatGPT 自己复述一下理解：

![](/images/awesome/sd-cot-2.png)

第二步，调整 ChatGPT 的理解，指出正确的规则。stable-diffusion 的 prompt 有些特殊用法，比如括号、加减号、冒号等。我们需要单独给 ChatGPT 强调一下：

![](/images/awesome/sd-cot-3.png)

第三步，给出多个包含各种复杂格式的 prompt 示例，加强理解。把挑好待用的另几个 prompt 这时候都可以贴过来，然后让 ChatGPT 照着随意仿写：

![](/images/awesome/sd-cot-4.png)

第四步，仿写完毕，可以正式出题，检验 ChatGPT 的学习结果了。让他依然以冬天奔跑的小女孩为题，生成一份 prompt 吧：

![](/images/awesome/sd-cot-5.png)

放到 stable-diffusion-webui，或者 blue willow 频道等地方，实际运行，挑出自己满意的效果：

![](/images/awesome/nlp-sd-ret.jpeg)

