# emoji

书写文章时，巧妙的使用一些小图标，可以给文章增加不少的灵动感，读者也会感觉更加轻松。恰当的图标也能增进读者对内容的理解。ChatGPT 目前不能直接联网，但可以使用 emoji 表情文字来达到类似的效果。我们在不少 GitHub 的项目介绍和个人介绍页面上，都可以看到在列表、标题上使用了 emoji 文字。

我们来尝试让 ChatGPT 自己选择合适的 emoji 表情，配属在文章标题上。ChatGPT 支持直接展示 markdown 格式内容。因此，我们可以把二者结合起来使用。

> 写一段关于 ChatGPT 的文章，采用 markdown 格式区分标题和正文。标题部分开头用 emoji

![](/images/awesome/emoji.png)

具体看生成内容的细节，可以感觉到 ChatGPT 确实按照内容做了一定的 emoji 选择。比如开篇用鼓掌，大脑和机器人表示 ChatGPT 属于人工智能领域，未来展望用火箭也是一种常见的意象。

如果想要把这篇内容复制出去使用，那就要使用 markdown 的源格式，不能使用渲染后的效果了。我们可以接着说：

> 把上面内容提供 markdown 源代码格式

![](/images/awesome/markdown.png)

ChatGPT 就会在代码框内，展示源代码格式内容，方便我们直接复制使用。我们可以看到其中标题、列表、加粗格式，都转换成了 markdown 中的 `#`,`-`,`**` 等标记符。

如果我们喜欢这种布局效果，但是不想使用 emoji，而想使用其他专门设计的图标，比如开源社区著名的 font awesome 图标库。也可以让 ChatGPT 直接做转化：

> 将上述内容的 emoji 换成 font-awesome icon，采用 HTML 标签格式

![](/images/awesome/emoji-font.png)

我们把这部分 HTML 代码复制成一个 test.html文件，然后浏览器打开看看效果：

![](/images/awesome/emoji-font-html.png)

虽然和直接使用 emoji 的效果不一样，但确实也能直接使用。

