# 连续提问和重新生成的作用


和 ChatGPT 聊天，也是有套路的。我们把给 ChatGPT 输入的问题文本，叫 Prompt，提示词。实际上，传统搜索引擎也有比较相类似的功能。

在 Prompt Learning 提示学习之后，又总结出一种更好的聊天套路，叫 In-Context Learning 上下文学习。采用教学生做题的方案，先主动提供几个例题，然后出题让算法作答。

再之后，又有更新的聊天套路，叫 Chain of Thought 思维链。不光是给学生例题，还把解题步骤给他写出来，这样他学习成绩就更好了——按照研究人员的说法：只有当模型参数大于 100B 的时候，思维链的威力才能发挥出来。可以说是大语言模型的专属套路了。

说回ChatGPT，它使用的是基于```Transformer``` 的自回归语言模型，这种模型采用了自注意力机制（Self-Attention Mechanism），它可以让机器理解和捕捉对话的上下文，进而实现上下文连续对话，ChatGPT还采用了```LSTM```长短期记忆模型，让ChatGPT准确地捕捉对话的上下文，从而实现更好的上下文连续对话能力。就好像让ChatGPT在对话的海洋中不断地吸收成长，它对于对话的处理也就随之越来越棒！

## 连续提问

对于ChatGPT来说，突出的就是一个```chat```--聊天，聊天就是有问有答，是双方的对话。当我们围绕着一个话题进行讨论或者交流的时候，ChatGPT会记住前面已经发生过的对话内容，并会结合之前的内容生成新的问题的答案，在我们看来这就好像在和ChatGPT聊天一样。

![intro](/images/webpage/chat_continu.png)

## 重新生成

当我们对于某个答案不满意，可以点击对话输入框上方的 Regenerate response 按钮，这个时候ChatGPT会为最后一个问题生成一版新的回答。注意，这里我用了“一版”来描述这个新的回答，这是因为之前的回答也作为一个版本保留了下来，我们可以点击答案左侧的 ```当前版本/总版本数``` 的前后箭头来切换答案的版本。例如，对于女朋友生日小惊喜这个问题，我们希望ChatGPT再给出一个版本的答案，于是我们点击了 Regenerate response 按钮，大家一起看看哪个版本更有趣呢？

新版本
![intro](/images/webpage/chat_regen2.png)

第一个版本
![intro](/images/webpage/chat_regen1.png)

为什么ChatGPT能给出不同版本的回答呢？因为ChatGPT是一个基于神经网络的语言模型，其生成的回答是基于其在训练数据中学习到的语言规则、语义知识和上下文信息等因素。因此，对于同一个问题，ChatGPT可以根据不同的上下文和语境生成不同的回答。

此外，ChatGPT模型中的权重参数是通过随机初始化开始训练的，而训练过程中也会受到随机性的影响。这意味着即使相同的问题和上下文被输入到模型中，由于随机性的影响，它们也可能被映射到不同的隐藏状态，进而导致生成不同的回答。

最后，ChatGPT还具有一些可以控制生成回答风格和特定输出的参数和超参数，如temperature、max_tokens、top-p采样等，这些参数也会影响生成的回答。因此，即使输入相同的问题和上下文，不同的参数设置也可能导致生成不同的回答。

