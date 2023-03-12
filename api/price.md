# API 开通使用

## OpenAI API 费用

OpenAI API 是商业服务，使用 API 需要支付费用，不过当我们创建OpenAI账户后，会有5美元的免费试用额度（最开始的新用户有18美元的额度，后面降下来了），不过要注意一下，免费额度有时间限制，过期就作废了。我们可以打开`https://platform.openai.com/account/usage`网址查看自己的额度信息。

![intro](../images/api/price_usage.png)

既然API的使用需要付费，我们就需要了解一下它的计费方式。根据官方文档，OpenAI的API是以每1000个token作为一个计费单元，使用不同的模型，每计费单元的单价也不尽相同，就拿2023年3月2号新开放的ChatGPT所使用的gpt-3.5-turbo模型来说，他的价格为`0.002美元/1K tokens`，也比之前便宜了很多。虽然1000个token看起来很多，但实际上通过API发送一段文本就会花去很多token。所以，到底什么是token呢？Token是OpenAI对文本进行自然语言处理进行分词后切分成的最小字符序列。举个例子：`Hello ChatGPT World!`这句话，会被切分成 `Hello`、`Chat`、`G`、`PT`、` World`、`！`这六个token。

![intro](../images/api/price_tokens.png)

如果是中文呢？我们猜猜`你好，科技的未来！`会花费多少个token呢？答案是21个！

![intro](../images/api/price_tokens_cn.png)

通常来讲，英语中的一个 token 大概对应约4字符，这相当于大约3/4个单词，因此整体上来说 100个token大约为75个英文单词。而1个汉字大致就要花费是2~2.5个token。如果我们想查询一串文本到底需要小号多少token，可以使用官方的免费查询计算器 https://platform.openai.com/tokenizer 计算一下，心里就有底了。


## 生成API KEY

想使用OpenAI的API，光有余额是不行的，还要生成一个API KEY。我们在OpenAI的概览页面点击左侧导航的 API Keys —> 再点击Create new secret key，就可以生成一个新的API，这里要注意，*这个API只在生成的时候展示一次*，请务必在关闭对话框之前，将其复制到你其他的地方保管。有了这个API，就可以再任何需要调用ChatGPT API的场景中使用了。

还需要注意的是，出于安全原因，我们不要把这个API Key分享给其他人使用，也不要在浏览器或其他客户端代码中公开它。为了保护账户的安全，OpenAI也可能会自动更改任何已经公开泄露的API密钥。

![intro](../images/api/price_apikey.png)

我们可以简单使用postman试一下通过API KEY调用API是否好用。我们在地址栏中输入 https://api.open.com/v1/completions 然后选择POST，在Authorization中选择Bearer Token同时把Token 设置为刚才获取的 API KEY ，设置header中的 Content-Type 为 application/json，发送的body写成如下形式，表示在100个token的限制内，通过api接口获取北京天气状况。
```
{
  "model": "text-davinci-003",
  "prompt": "今天北京天气如何？",
  "max_tokens": 100,
  "temperature": 0
}
```
发过去稍等片刻后，返回的数据如下：

![intro](../images/api/price_test.png)

我们发现返回的数据中用了100个以内的token描述了北京今日的天气状况。
好了，这就是Open API的大概情况，后面会详细给大家介绍一下各个接口的使用方法。
