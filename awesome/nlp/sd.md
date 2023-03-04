= stable-diffusion

== 直接生成

按照惯用的扮演思路，我们可以让 ChatGPT 扮演一个艺术家和 stable-diffusion 爱好者，生成一份绘图 prompt。以冬天奔跑的小女孩为题：


然后我们提交到 stable-diffusion 上得到效果如下：

![]()

稍微有点 stable-diffusion 知识的用户都知道，AI 画图的 prompt 中，除了核心要素，还需要加一些风格描述，而且关键字不一定非得是自然语言顺序，所以我们可以要求 ChatGPT 做一定的简化：

![]()

得到的效果如下：

![]()

== 思维链生成

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

