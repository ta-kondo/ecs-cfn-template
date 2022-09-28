# ecs-cfn-template

ECSを起動するCloudformationテンプレートのRepository template

# Features

AWSアカウント内に一撃で

  - VPC
  - Subnet (Private, Public)
  - ECS
    - Cluster
    - Service
    - Task
  - LoadBalancer

を建てる。

起動するTaskはNginx。

# Requirement

起動条件特になし

AWSアカウントでCloudformationが実行できること(各リソースを作成する権限)

# Usage

1. `./cloudformation` フォルダを任意のS3バケットへアップロード

1. AWS管理コンソールの `Cloudformation` で新規スタックを作成

    1. 新規作成

        - [スタックの作製]
          - 新しいリソースを使用 (標準)

    1. アップロードしたファイルを起動テンプレートとして指定

        - [テンプレートの準備完了]
        - [テンプレートの指定]
          - S3バケットへアップロードしたファイルのうち、`cloudformation/stacks/Nginx/purpose/develop.yml`のオブジェクトURLをテンプレートに指定

            ex) 「https:// < Your S3 BucketName > .s3.ap-northeast-1.amazonaws.com/cloudformation/stacks/Nginx/purpose/develop.yml」

    1. 必要事項を入力し、スタックを実行

        - スタックの名前

            任意の名前

        - パラメータ

          - BucketName

            任意のS3バケット

          - CidrBlock

            172.31.x.0/24 ... x: 0 〜 255

          - Environment

            dev

          - SystemName

            任意の名前

          - TurnOnECS

            On／Off ... Off: ECS Service を立ち上げない

# Note

雛形のRepository（Repository template）。

利用側でTask、Serviceを任意に変更。

# Author

* ta-kondo
* E-mail @gmail.com

# License

ecs-cfn-template is under [MIT license](https://en.wikipedia.org/wiki/MIT_License).

# Change log

  - 2022.09.28
    - 新規作成
