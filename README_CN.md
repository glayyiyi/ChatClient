<div align="center">
<img src="./public/logo.png" alt="预览"/>

<h1 align="center">BRClient</h1>

本项目由 https://github.com/Yidadaa/ChatGPT-Next-Web/ 分支而来，做简化后单纯支持AWS Bedrock

很快会提供发布的测试程序，打开程序以后在“配置”界面配置AWS Region, AK/SK 就可以开始使用。

</div>

## 安装使用：

根据你的电脑情况下载对应的链接:

Windows用户解压下载的zip文件后点击msi文件进行安装。

Mac用户解压下载的zip文件后直接打开 BRClient.app 使用

Download links:

Windows:
https://github.com/DamonDeng/BRClient/releases/download/v1.11.8/brclient_windows.zip


Mac M 系列:
https://github.com/DamonDeng/BRClient/releases/download/v1.11.8/brclient_m_series.zip


Mac x86 系列:
https://github.com/DamonDeng/BRClient/releases/download/v1.11.8/brclient_x86_mac.zip






打开程序以后在“配置”界面配置AWS Region, AK/SK 就可以开始使用。

#### 开发者

目前项目还在快速开发阶段，所以建议使用开发者模式:

1. 使用git克隆当前项目: `git clone https://github.com/DamonDeng/BRClient.git`
2. 安装yarn
3. 进入项目文件夹
4. 运行 `yarn install`安装依赖包
5. 运行 `yarn app:dev`命令启动应用，或者:   运行 `yarn dev` 启动浏览器模式，通过localhost:3000访问
6. （可选），如果你想构建自己的单独应用，可以运行 `yarn app:build`执行打包命令，然后去找一下打包出来的程序，都是开发者了，相信你可以找到。

#### IAM 权限

要开始使用 BRClient,您必须创建一个 IAM 用户并生成 Access Key/Secret Key。您有两个选择:

* 选项 1:使用托管策略(快速设置)
  - 转到身份和访问管理(IAM) -> 用户 -> 创建用户
  - 设置权限 -> 选择"直接附加策略"
  - 选择 `AmazonBedrockFullAccess`
  - 单击下一步 -> 创建用户

* 选项 2:设置最小权限
  - 在使用 IAM 策略设置权限时,只授予执行任务所需的权限, 这称为最小权限。以下是 BRClient 最小 IAM 权限的示例:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "LeastPrivilege4BRClient",
      "Effect": "Allow",
      "Action": [
        "bedrock:InvokeModel",
        "bedrock:InvokeModelWithResponseStream"
      ],
      "Resource": "arn:aws:bedrock:*::foundation-model/*"
    }
  ]
}
```

有关 Amazon Bedrock 基于身份的策略的更多详细信息,请访问[链接](https://docs.aws.amazon.com/bedrock/latest/userguide/security_iam_id-based-policy-examples.html)。

## 支持一下
如果你喜欢这个项目，大概率是因为你喜欢这个界面，那给项目的原作者yidadaa买杯咖啡吧

[给原作者买杯咖啡，记得要大杯](https://www.buymeacoffee.com/yidadaa)



## 开源协议

[MIT](https://opensource.org/license/mit/)
