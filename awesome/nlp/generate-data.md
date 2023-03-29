= generate-data

之前章节我们已经演示过ChatGPT 如何根据 prompt 编写文章或续写文章，文本生成的作用不仅仅在语文方面有用，本节我们演示另一种场景，利用 ChatGPT 来生成数据。看似作用差不多，其实这是目前开源社区非常常用的大语言模型研究中的一步，学名叫 self-instruction。简单来说，将一些人工编写好的或者挑选好的极少数训练数据，交给 ChatGPT 进行仿写，可以得到多出两三个数量级的新训练数据。这样有助于大语言模型的微调训练。

我们以北京航空航天大学开源的 LogQA 标注数据集(https://github.com/LogQA-dataset/LogQA/blob/main/data/Spark/qa.json.train)中的前十行训练数据为例，让 ChatGPT 来生成更多数据：

> {"Question": "What stage was the task 28.0 completed in?", "Answer": "29.0", "RawLog": "Finished task 28.0 in stage 29.0 (TID 1348). 2128 bytes result sent to driver"}
> {"Question": "How many kb is broadcast_3 free?", "Answer": "318.5", "RawLog": "Block broadcast_3 stored as values in memory (estimated size 384.0 B, free 318.5 KB)"}
> {"Question": "Is partition rdd_42_18 found?", "Answer": "not", "RawLog": "Partition rdd_42_18 not found, computing it"}
> {"Question": "Is partition rdd_42_15 found?", "Answer": "not", "RawLog": "Partition rdd_42_15 not found, computing it"}
> {"Question": "How many kb is broadcast_24_piece0 free?", "Answer": "393.0", "RawLog": "Block broadcast_24_piece0 stored as bytes in memory (estimated size 5.6 KB, free 393.0 KB)"}
> {"Question": "Is partition rdd_42_4 found?", "Answer": "not", "RawLog": "Partition rdd_42_4 not found, computing it"}
> {"Question": "What is the ID for stage 7.0?", "Answer": "299", "RawLog": "Running task 1.0 in stage 7.0 (TID 299)"}
> {"Question": "What is the ID for stage 12.0?", "Answer": "494", "RawLog": "Running task 1.0 in stage 12.0 (TID 494)"}
> {"Question": "Is partition rdd_11_1 found?", "Answer": "not", "RawLog": "Partition rdd_11_1 not found, computing it"}
> {"Question": "What stage was the task 42.0 completed in?", "Answer": "24.0", "RawLog": "Finished task 42.0 in stage 24.0 (TID 1127). 2364 bytes result sent to driver"}
> 
> 参照上面数据，仿写一批类似数据。

得到的 ChatGPT 生成结果如图：

![](/images/awesome/generate-data.png)

对比原始数据可以发现，ChatGPT 完美的识别除了数据中哪些内容是可以被随机替换的，应该怎么替换，并且保证了在同一行内，相同的的内容，Question、Answer 和 RawLog 中保持一致。

有趣的是：ChatGPT 严格按照示例数据的样式，循环生成。我们给的 prompt 中，分别是 1 个 complate、1 个 kb、2 个 found、1 个 free、1 个 found、2 个 ID、1 个 found、1 个 complete，ChatGPT 生成 30 条也一模一样按照这个顺序循环 3 次。

所以如果要生成更多数据，或者生成均衡数据的，也可以分批分类生成。这里就不重复演示了。如果我们确实希望采用这种方式生成数以万计的训练数据，建议通过 API 方式调用 ChatGPT 服务。本书后续章节会介绍ChatGPT 的接口开通和调用方法，请参阅。

