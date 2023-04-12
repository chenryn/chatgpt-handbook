# Wechat-chatgpt

微信可以说是人们最常用的聊天应用了，而随着ChatGPT越来越多的出现在人们的视野中，当我们感受过ChatGPT令人惊艳的智能对话体验以后，自然而然就希望能够在微信中快速接入ChatGPT，方便我们使用最长用的聊天工具和ChatGPT进行对话，而 wechat-chatgpt <https://github.com/fuergaosi233/wechat-chatgpt.git> 这个开源库，就能帮助我们实现这个愿望。

wechat-chatgpt帮助我们基于wechaty和Official API技术在微信中使用ChatGPT，它支持多轮对话和命令设置。部署和配置方面，它提供了Dockerfile文件，可以使用docker进行部署，也可以使用docker compose进行部署。此外，这项技术还支持在Railway和Fly.io上进行部署。不仅仅是ChatGPT，它还支持 Dall·E 和 whisper，并且可以设置prompt。wechat-chatgpt官方推荐使用Docker进行部署。

首先我们准备一台安装了Docker服务的服务器，将wechat-chatgpt的imange下载下来。

```
docker pull holegots/wechat-chatgpt
```
![intro](/images/api/wechat_pull.png)

接下来我们使用下面的命令运行 Docker，这里要注意，需要提供自己的 OpenAI API Key。

```
docker run -d --name wechat-chatgpt \
    -e OPENAI_API_KEY=<我们的 OPENAI API KEY> \
    -e MODEL="gpt-3.5-turbo" \
    -e CHAT_PRIVATE_TRIGGER_KEYWORD="" \
    -v $(pwd)/data:/app/data/wechat-assistant.memory-card.json \
    holegots/wechat-chatgpt:latest
```
运行后，会返回容器的id，我们可以使用这个id查看下容器是否正常运行。

最后我们使用如下命令打开微信的二维码，然后扫码登陆微信。

```
docker logs -f wechat-chatgpt
```
与行命令以后，终端界面中会出现一个二维码，我们使用一个微信扫码登陆，注意在登陆时手机会提示在新设备登陆，我们确定明确风险后，wechat-chatgpt就会处于登陆状态了。可以看到终端中最新的输出提示了我们的登陆状态。

![intro](/images/api/wechat_qr.png)

到此，我们已经使用 wechat-chatgpt 建立起了一个微信和 ChatGPT 的沟通通道，如果我们使用另一个微信号和这个用于登陆的微信号聊天，我们发送的信息会被刚才启动的服务接收到，然后转发给ChatGPT，等ChatGPT回答以后，这个服务再把回答作为回复发送回刚才的聊天。例如我们发送：请介绍一些自己，就会有如下对话。

![intro](/images/api/wechat_co.png)

而在刚才的服务端，我们也能看到同样的对话内容，并且能清晰的看到问题发送给了 ChatGPT 。

![intro](/images/api/wechat_chat.png)

是不是很有趣，这样我们就能在微信中使用 ChatGPT 的神奇功能啦！

