

## Installation:

Download the latest version following the links:

For Windows user, unzip the zip file and then double click the msi file to install.

For Mac user, unzip the zip file and then open the BRClient.app directly.





After the client was launched, click the gear icon to config your AWS region and credentials. Then you are ready to go.

#### For Developer:


As the project is still in rapid itelating, we would like to suggest developers to build it their own version following the following steps:

1. git clone current project: `git clone https://github.com/DamonDeng/BRClient.git`
2. install yarn on your desktop
3. go to the project folder
4. run `yarn install` to install all the dependences of the project
5. run `yarn app:dev` to start a desktop app in developer mode.    or:   run `yarn dev` to start a local server and then access the app with browser.
6. Optional, if you want to run it as an app, run `yarn app:build` to build it, and the find the target file (we believe you can, :-)

#### IAM Permissions

To get started with BRClient, you must create an IAM user and generate Access Key/Secret Key. You have two options:

* Option 1: Use the Managed Policy (Quick Setup)
  - Go to Identity and Access Management (IAM) -> Users -> Create User
  - Set permissions -> Select "Attach policies directly"
  - Choose `AmazonBedrockFullAccess`
  - Click Next -> Create User

* Option 2: Set Least-Privilege Permissions
  - When setting permissions with IAM policies, grant only the permissions required to perform a task. This is known as least-privilege permissions. Here's an example of least-privilege IAM Permissions for BRClient:
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

For more details about Amazon Bedrock identity-based policy, please visit [Link](https://docs.aws.amazon.com/bedrock/latest/userguide/security_iam_id-based-policy-examples.html)

## Donation
If you like this project, buy original author yidadaa a Coffee
[Buy Original Author a Coffee](https://www.buymeacoffee.com/yidadaa)

## LICENSE

[MIT](https://opensource.org/license/mit/)
