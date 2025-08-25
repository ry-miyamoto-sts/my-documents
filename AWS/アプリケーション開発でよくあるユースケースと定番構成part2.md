# アプリケーション開発でよくあるユースケースと定番構成 part2

(まだAIに下書きしてもらっただけの状態。加筆修正予定)


<details>
<summary>⏰ 定期バッチ・重い処理を実行したい</summary>

- **AWS Batch + ECS/Fargate**
  - 大規模・長時間バッチ処理の定番。リソース自動調整、並列処理対応
  - 1時間程度の重い処理に最適、キューイング機能あり
- **Amazon ECS Scheduled Tasks**
  - ECSタスクの定期実行。cron的な使い方
  - コンテナベースで環境の再現性が高い
- **Lambda + EventBridge**
  - 15分以内の軽量バッチ処理。完全サーバーレス
  - 簡単なデータ変換・通知処理向け
- **Step Functions + Lambda/ECS**
  - 複雑なワークフロー制御が必要なバッチ処理
  - エラーハンドリング・リトライ機能が充実

**使い分け**: AWS Batch（重い・大規模処理）、ECS Scheduled（定期的なコンテナ実行）、Lambda（軽量・短時間）、Step Functions（複雑フロー）

</details>

<details>
<summary>💾 アプリのデータを保存したい</summary>

- **Amazon RDS（MySQL/PostgreSQL）**
  - 一般的なWebアプリケーション、ACIDトランザクション必要
  - 既存のSQL知識活用可能、複雑なクエリ対応
- **Amazon DynamoDB**
  - 大量アクセス・高速レスポンス重視、サーバーレスと相性◎
  - NoSQL、シンプルなデータ構造向け
- **Amazon Aurora**
  - 高性能・高可用性が必要な本格運用
  - MySQL/PostgreSQL互換、自動バックアップ・レプリケーション

**使い分け**: RDS（一般的なWebアプリ・複雑クエリ）、DynamoDB（大量アクセス・シンプル構造）、Aurora（高性能・ミッションクリティカル）

</details>

<details>
<summary>🏃‍♂️ アプリの処理を高速化したい</summary>

- **Amazon ElastiCache（Redis）**
  - セッション管理、アプリケーションキャッシュ
  - 複雑なデータ構造、Pub/Sub機能も利用可能
- **Amazon ElastiCache（Memcached）**
  - シンプルなキー・バリューキャッシュ
  - 軽量、マルチスレッド対応
- **CloudFront**
  - 静的コンテンツ・API レスポンスのキャッシュ配信
  - エッジロケーションでの高速化

**使い分け**: Redis（セッション・複雑データ）、Memcached（シンプルキャッシュ）、CloudFront（コンテンツ配信）

</details>

<details>
<summary>🔐 ユーザーログイン機能を作りたい</summary>

- **Amazon Cognito User Pools**
  - ユーザー登録・ログイン・パスワードリセット
  - ソーシャルログイン（Google/Facebook等）対応
- **Amazon Cognito Identity Pools**
  - 一時的なAWS認証情報の発行
  - ゲストアクセスや外部IDプロバイダー連携
- **AWS IAM**
  - AWSリソース間の権限制御
  - アプリケーション内のロールベースアクセス制御

**使い分け**: User Pools（アプリユーザー管理）、Identity Pools（AWS リソースアクセス）、IAM（システム権限管理）

</details>

<details>
<summary>🔑 機密情報・設定値を安全に管理したい</summary>

- **AWS Secrets Manager**
  - データベース接続情報、APIキーの自動ローテーション
  - 高セキュリティ、自動暗号化、アクセス監査
- **AWS Systems Manager Parameter Store**
  - アプリケーション設定値の一元管理
  - 無料枠あり（標準パラメータ10,000個まで無料）、階層構造対応
- **AWS Certificate Manager (ACM)**
  - SSL/TLS証明書の自動取得・更新
  - CloudFront、ALBとの自動連携

**使い分け**: Secrets Manager（機密情報・自動ローテーション）、Parameter Store（設定値・コスト重視）、ACM（SSL証明書）

</details>

<details>
<summary>📬 ユーザーに通知・メールを送りたい</summary>

- **Amazon SNS**
  - プッシュ通知（iOS/Android）、SMS送信
  - リアルタイム通知、複数宛先への一括配信
- **Amazon SES**
  - トランザクションメール（パスワードリセット等）
  - 大量メール配信、配信状況の詳細追跡
- **Amazon Pinpoint**
  - マーケティングメール、ユーザーセグメント配信
  - A/Bテスト、キャンペーン管理機能

**使い分け**: SNS（即時通知・SMS）、SES（システムメール・大量配信）、Pinpoint（マーケティング用途）

</details>

<details>
<summary>🔄 非同期処理・ジョブキューを実装したい</summary>

- **Amazon SQS**
  - 基本的なメッセージキュー、重要な処理の確実な実行
  - Dead Letter Queue、可視性タイムアウト機能
- **Amazon SNS + SQS**
  - ファンアウトパターン、複数サービスへの同時処理
  - 疎結合なマイクロサービス連携
- **AWS Step Functions**
  - 複雑なワークフロー、条件分岐・並列処理
  - エラーハンドリング、可視化機能が充実

**使い分け**: SQS（シンプルキュー）、SNS+SQS（ファンアウト）、Step Functions（複雑ワークフロー）

</details>

<details>
<summary>📊 アプリの動作状況を監視したい</summary>

- **Amazon CloudWatch Logs**
  - アプリケーションログの収集・検索
  - ログベースアラート、メトリクス抽出
- **Amazon CloudWatch Metrics + Alarms**
  - CPU・メモリ・レスポンス時間の監視
  - 閾値アラート、Auto Scaling連携
- **AWS X-Ray**
  - API・DB呼び出しのパフォーマンス分析
  - ボトルネック特定、分散トレーシング
- **AWS CloudTrail**
  - API呼び出しの監査ログ
  - セキュリティ分析、コンプライアンス対応

**使い分け**: CloudWatch Logs（アプリログ）、CloudWatch Metrics（リソース監視）、X-Ray（パフォーマンス分析）、CloudTrail（セキュリティ監査）

</details>

<details>
<summary>🚀 アプリを自動デプロイしたい</summary>

- **AWS CodePipeline + CodeBuild + CodeDeploy**
  - AWS純正CI/CDパイプライン、GitHub連携
  - ブルーグリーンデプロイ、カナリアリリース対応
- **GitHub Actions + AWS CLI**
  - GitHub中心の開発フロー
  - 豊富なアクション、コミュニティサポート
- **Amazon ECR**
  - Dockerイメージの管理・バージョニング
  - ECS/Fargateとの自動連携

**使い分け**: CodePipeline（AWS完結型）、GitHub Actions（GitHub中心）、ECR（コンテナ管理）

</details>
