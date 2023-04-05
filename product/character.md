# character

Character.AI 公司是一家致力于通用人工智能（AGI）的全栈公司，于2021年10月创立，创始团队来自Google Brain和Meta AI，是深度学习、大型语言模型和对话领域的专家。Character.AI搭建了用户创建AI角色并与之聊天的平台及社区，AI角色有官方创建、社区成员UGC两大类，官方创建的AI 角色包括：马斯克、拜登、洛基等等。不过平台以满足个人需求的个性化定制AI为主，比如AI女友/男友。Character.AI 公司没有公布自己背后的 AI 技术来源，不过从 AI 角色的高级配置过程和效果来看，属于典型的 In-Context Learning 技术，应该和 GPT-3 属于同一代产品。我们可以从 character.ai 的使用过程和效果中，体会到 In-Context Learning 的强大，在后续使用、开发 ChatGPT 相关应用时，可以复用这方面的经验。

注册 Character.AI 账号后，在左侧菜单栏点击 create 菜单，选择"Create a Character"，可以开始角色创建。默认的角色创建内容，主要是添加角色的长描述，在影视界，可以类比演员给剧本中角色写的人物小传。

![](/images/product/character-config-simple.png)

完成描述后，AI 角色就已经可用了。不过这时候，聊天的语气、习惯等等，还是不够贴近期望效果。我们再打开高级配置项，输入一些可以强烈反应和代表该角色性格、语气的对话历史。注意其中，要用 `{{user}}` 替换掉提问人名称，`{{char}}`替换掉应答人名称。

![](/images/product/character-config-advanced.png)

除了预先收集，人工清洗和编辑以外也可以通过先和简单版 AI 角色聊天，生成记录再做调整的方式来积累初期训练数据。

我们在编辑器顶部可以看到一些提示。例如整个 context 限定了 3200 字的上限。从示例来说，大概一共可以输入 40+ 个对话示例，作为传给 AI 模型的 context。

在斯坦福大学的 Alpaca 论文中，就是先通过人工编写了 175 个对话示例，然后通过这 175 个实例进行 ChatGPT  prompt 仿写生成了 52k 条训练数据，对 LLAMA 模型进行微调。我们可以想象一下，charactor.ai 背后，可能也采取了类似原理，对用户自定义的 40+ 个对话示例，也做了更多 prompt 仿写，然后进行模型微调，得到一个最终的 AI 角色。

最后创建好的 AI 角色，我们可以进行对话了。下图这个应答的预期、情感偏好，和实际确实更贴近：

![](/images/product/character-ret.png)

