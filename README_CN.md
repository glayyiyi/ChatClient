<div align="center">
<img src="./public/logo.png" alt="icon" width="96" height="96" />

<h1 align="center">OneAIChat</h1>

本项目由 https://github.com/Yidadaa/ChatGPT-Next-Web/ 分支而来，做简化后单纯支持AWS Bedrock

很快会提供发布的测试程序，打开程序以后在“配置”界面配置AWS Region, AK/SK 就可以开始使用。

</div>

## 重要的注意事项:
```
本项目是个样例项目，单纯用于展示如何构建一个连接Bedrock大语言模型的客户端。

本项目并不是为生产环境准备的，请不要直接在生产环境使用。
```


## 安装使用：

根据你的电脑情况下载对应的链接:

Windows用户解压下载的zip文件后点击msi文件进行安装。

Mac用户解压下载的zip文件后直接打开 OneAIChat.app 使用。
项目中附加的Mac app文件由开源社区贡献者签名，仅为了方便测试，签名者保留一切和该签名有关的权利，被签名的文件也不在本项目开源协议覆盖范围中。

Download links:

Windows:
https://github.com/aws-samples/OneAIChat/releases/download/v1.11.8/OneAIChat_windows.zip


Mac M 系列:
https://github.com/aws-samples/OneAIChat/releases/download/v1.11.8/OneAIChat_m_series.zip


Mac x86 系列:
https://github.com/aws-samples/OneAIChat/releases/download/v1.11.8/OneAIChat_x86_mac.zip






打开程序以后在“配置”界面配置AWS Region, AK/SK 就可以开始使用。

#### 开发者

目前项目还在快速开发阶段，所以建议使用开发者模式:

1. 使用git克隆当前项目: `git clone https://github.com/aws-samples/OneAIChat.git`
2. 安装yarn
3. 进入项目文件夹
4. 运行 `yarn install`安装依赖包
5. 运行 `yarn app:dev`命令启动应用，或者:   运行 `yarn dev` 启动浏览器模式，通过localhost:3000访问
6. （可选），如果你想构建自己的单独应用，可以运行 `yarn app:build`执行打包命令，然后去找一下打包出来的程序，都是开发者了，相信你可以找到。

#### IAM 权限

要开始使用 OneAIChat,您必须创建一个 IAM 用户并生成 Access Key/Secret Key。您有两个选择:

* 选项 1:使用托管策略(快速设置)
  - 转到身份和访问管理(IAM) -> 用户 -> 创建用户
  - 设置权限 -> 选择"直接附加策略"
  - 选择 `AmazonBedrockFullAccess`
  - 单击下一步 -> 创建用户

* 选项 2:设置最小权限
  - 在使用 IAM 策略设置权限时,只授予执行任务所需的权限, 这称为最小权限。以下是 OneAIChat 最小 IAM 权限的示例:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "LeastPrivilege4OneAIChat",
      "Effect": "Allow",
      "Action": [
        "bedrock:InvokeModel",
        "bedrock:InvokeModelWithResponseStream"
      ],
      "Resource": "arn:aws:bedrock:*::foundation-model/*"
    }
  ]
}
### `GOOGLE_URL` (optional)

Google Gemini Pro Api Url.

### `ANTHROPIC_API_KEY` (optional)

anthropic claude Api Key.

### `ANTHROPIC_API_VERSION` (optional)

anthropic claude Api version.

### `ANTHROPIC_URL` (optional)

anthropic claude Api Url.

### `HIDE_USER_API_KEY` （可选）

如果你不想让用户自行填入 API Key，将此环境变量设置为 1 即可。

### `DISABLE_GPT4` （可选）

如果你不想让用户使用 GPT-4，将此环境变量设置为 1 即可。

### `ENABLE_BALANCE_QUERY` （可选）

如果你想启用余额查询功能，将此环境变量设置为 1 即可。

### `DISABLE_FAST_LINK` （可选）

如果你想禁用从链接解析预制设置，将此环境变量设置为 1 即可。

### `WHITE_WEBDEV_ENDPOINTS` (可选)

如果你想增加允许访问的webdav服务地址，可以使用该选项，格式要求：
- 每一个地址必须是一个完整的 endpoint
> `https://xxxx/xxx`
- 多个地址以`,`相连

### `CUSTOM_MODELS` （可选）

> 示例：`+qwen-7b-chat,+glm-6b,-gpt-3.5-turbo,gpt-4-1106-preview=gpt-4-turbo` 表示增加 `qwen-7b-chat` 和 `glm-6b` 到模型列表，而从列表中删除 `gpt-3.5-turbo`，并将 `gpt-4-1106-preview` 模型名字展示为 `gpt-4-turbo`。
> 如果你想先禁用所有模型，再启用指定模型，可以使用 `-all,+gpt-3.5-turbo`，则表示仅启用 `gpt-3.5-turbo`

用来控制模型列表，使用 `+` 增加一个模型，使用 `-` 来隐藏一个模型，使用 `模型名=展示名` 来自定义模型的展示名，用英文逗号隔开。

### `DEFAULT_INPUT_TEMPLATE` （可选）
自定义默认的 template，用于初始化『设置』中的『用户输入预处理』配置项

## 开发

点击下方按钮，开始二次开发：

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/Yidadaa/ChatGPT-Next-Web)

在开始写代码之前，需要在项目根目录新建一个 `.env.local` 文件，里面填入环境变量：

```
OPENAI_API_KEY=<your api key here>

# 中国大陆用户，可以使用本项目自带的代理进行开发，你也可以自由选择其他代理地址
BASE_URL=https://b.nextweb.fun/api/proxy
```

有关 Amazon Bedrock 基于身份的策略的更多详细信息,请访问[链接](https://docs.aws.amazon.com/bedrock/latest/userguide/security_iam_id-based-policy-examples.html)。


## 开源协议

[MIT](https://opensource.org/license/mit/)
