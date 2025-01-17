# Midjourney_api
非官方Midjourney API

这是自定义的Midjourney API。使用它，您可以通过编写代码生成图像。它可用于Discord API。

!! 不要忘记，Midjourney的条款不允许任何自动化，因此这个项目只是为了研究目的 !!

包含：
- Sender：用于向Midjourney发送提示
- Receiver：在终端中工作，将所有已完成的图像下载到本地文件夹

# 环境依赖
python3.8及以上，pandas、requests库。
终端运行pip命令安装依赖：
```
pip install pandas requests
```

# 安装步骤：
1. 创建Discord帐户并创建您的服务器（说明在此处：https://discord.com/blog/starting-your-first-discord-server）
2. 加入midjourney官方频道[https://discord.gg/midjourney](https://discord.gg/midjourney)
3. 创建Midjourney帐户并邀请Midjourney机器人到您的服务器（说明在此处：https://docs.midjourney.com/docs/invite-the-bot）
4. 确保从您的服务器进行生成操作
5. 在浏览器中登录Discord，打开您的服务器的文本频道，点击右上角的三个点，然后选择更多工具，再选择 "开发者工具"（直接键盘按F12）。
选择 "网络" 选项卡，您将看到页面的所有网络活动。
1. 现在在您的文本频道中输入任何提示进行生成，按Enter键发送提示消息后，您将在网络活动中看到一个名为“interaction”的新行。
点击它并选择"Payload"（负载）选项卡，您将看到 payload_json - 这就是我们需要的请求相关的参数！
复制channelid、authorization(请求头中获取)、application_id、guild_id、session_id、version和id值，稍后我们会用到它们。
1. 克隆这个repo。
2. 打开“sender_params.json”文件并将第5段中的所有值放入其中。还要填写“flags”字段以指定提示的特殊标志。  
ps：如果你想要使用代理访问，请修改配置文件中的`proxy`为`true`，并在下面`http_proxy`和`https_proxy`的配置你的代理地址。  
1. 现在，您已准备好运行文件：
要启动接收器脚本，请打开终端并输入：
`python receiver.py --params sender_params.json --local_path "./download"`
此脚本将向您显示所有的生成进度，并在图像准备就绪时立即下载图像到`--local_path`设置的路径。

要发送生成提示`--prompt`后就是关键词字符串，请在另一个终端中打开并输入：
`python sender.py --params sender_params.json --prompt "your prompt here"`
9. 尽情享受吧 :)

请注意控制并行请求的数量 - 对于正常和最快的工作，它不应该超过3（在基础和标准计划中），在专业计划中为12。

# 项目注释：
这是第一个简单的API版本，现在我正在开发下一个版本，其中包括：
- 本地队列控制器
- 能够与任意数量的Midjourney账户并行工作，以获得更好和可扩展的性能
- 上采样脚本以发送上采样请求
- 还有很多其他功能。


# Contacts:

For proposals and cooperation:

email: normalabnormalai@gmail.com

WeChat ID: george-iam

Discord: georgeb#0907
