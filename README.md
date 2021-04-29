# cfn_ec2
複数の EC2 インスタンスを作成する CloudFormation テンプレートです。

![image](https://user-images.githubusercontent.com/83407414/116553300-f0e70e80-a934-11eb-925b-b1b8b82ecce4.png)

テンプレートデプロイ時、以下の設定を入力します。

- AvailabilityZone: コンピュートノードをデプロイするアベイラビリティゾーン
- AMI: コンピュートノードで使用する AMI ID
- KeyPair: 全てのインスタンスで利用するキーペア名
- ComputeInstanceNumber: コンピュートノードの数
- InstanceType: コンピュートノードのインスタンスタイプ (例: c5n.18xlarge)
- EBSVolumeSize: コンピュートノードのディスクサイズ
- EC2ImageID: 踏み台サーバの AMI ID (デフォルトで最新の Amazon Linux 2 の AMI ID が入力されています)

補足

- 踏み台サーバのセキュリティグループにおけるアクセス元が "0.0.0.0" で設定されているため、必要に応じてアクセス元を絞ってください。
- CloudFormation スタックを削除することで、EC2 含めて全てのリソースが削除されます。
- コンピュートノードは Cluster Placement Group 内に作成されます。
- インスタンス不足により起動に失敗した場合、アベイラビリティゾーンを変えて再度実行してください。
