---
nav_title: "メッセージングインタラクションデータ"
article_title: "メッセージングインタラクションデータ"
permalink: "/messaging_interaction_data/"
hidden: true
---

# メッセージングインタラクションデータの可用性について

> この記事では、キャンペーンとキャンバスのインターアクション情報とその利用可能性について説明します。

### メッセージングインタラクションデータとは

メッセージングインターアクションデータとは、ユーザーが受信したキャンペーンまたはキャンバスとのやり取り方法を指します(たとえば、ユーザー 開封がキャンペーン Aまたはユーザーがバリアント Aを受信した場合)。リターゲティングに使用します。

{% alert important %}
2024年初頭から、ここで説明する手順に従ってメッセージングインタラクションデータを利用できるようになります。
{% endalert %}

### メッセージングインタラクションデータはいつ利用できますか。

インタラクションデータはいつでも利用可能です。アクティブなキャンペーンやキャンバスの場合、インタラクションデータは常にリアルタイムで利用できます。 

停止したキャンペーンとキャンバスの場合、アクティブなキャンペーンまたはキャンバスによるリターゲティングフィルターで使用されない限り、インタラクションデータは3か月後に期限切れになります。期限切れのインタラクションデータは長期ストレージに移動され、次に説明するプロセスを使用して復元しない限り使用できません。

期限切れのインタラクションデータは削除されず、いつでも復元できます。

#### インタラクションデータを使用する機能

次の機能はメッセージングインタラクションデータを使用します。

- 特定のキャンペーンやキャンバスでリターゲティングを行うリターゲティングフィルター
    - キャンペーンでクリックしたエイリアス
    - キャンバスステップでクリックしたエイリアス
    - クリックされた/開封されたキャンペーン
    - クリックされた/開封されたステップ
    - キャンペーンからコンバージョン済み
    - キャンバスからコンバージョン済み
    - 入力したキャンバスバリエーション
    - キャンペーンのコントロールグループ内
    - キャンバスのコントロールグループ内
    - 特定のキャンペーンから最後に受信したメッセージ
    - 特定のキャンバスステップから最後に受信したメッセージ
    - キャンペーンバリアントを受信
    - キャンペーンから受信したメッセージ
    - キャンバスステップからメッセージを受信
- 特定のタグのキャンペーンまたはキャンバスでリターゲティングを行うリターゲティングフィルター
    - キャンペーンまたはキャンバスからタグ付きで受信したメッセージ
    - クリック/開いたキャンペーンまたはタグ付きキャンバス
    - キャンペーンまたはCanvas With Tagから最後に受信したメッセージ
- ユーザープロファイルの \[**受信したキャンペーン**] リストおよび \[**キャンバスメッセージの受信**] リスト
- `/users/export` エンドポイント
- **ユーザデータ** キャンペーン およびキャンバスサマリページでのCSV エクスポート

これらの機能の結果には、期限切れのインタラクションデータは含まれません。これらの機能の結果に期限切れのインタラクションデータを含めるには、キャンペーンまたはキャンバスを期限切れのデータで復元します。

#### インタラクションデータを使用しない機能

次の機能はメッセージングインタラクションデータを使用**しません**。つまり、これらの機能はメッセージングインタラクションデータが期限切れになっても影響を受けません。

- キャンペーンとキャンバスの設定
- キャンペーンとキャンバスの分析
- 分析レポート (レポートビルダ、クエリビルダ、およびエンゲージメントレポートなど)
- Currents
- Snowflakeデータシェア
- セグメントエクステンション
- データポイント
- 次のリターゲティング フィルター:
    - キャンペーンステップまたはキャンバスステップでクリックしたエイリアス
    - フィーチャーフラグ
    - ハードバウンス
    - スパムとしてマークされた
    - キャンペーンステップまたはキャンバスステップからメッセージを受信していない
    - 不正な電話番号
    - メッセージへの最終エンゲージ
    - 任意のコントロールグループに最後に登録された
    - 最後のアプリ内メッセージインプレッション
    - メッセージの最終受信
    - 最後に受信したメール 
    - 最後に受信したプッシュ
    - 最後に受信した SMS
    - 最後に受信した Webhook
    - 最後に受信した WhatsApp
    - 最後に送信された特定の SMS インバウンドキーワードカテゴリ
    - 最後に閲覧したニュースフィード
    - ニュースフィードの閲覧数

### メッセージングインタラクションデータを復元するには？

インタラクションデータを復元するには、次のステップに従います。

1. 期限切れのキャンペーンまたはキャンバスに移動します。
2. キャンペーン またはキャンバスランディングページの上部で、バナーの**Restore inter アクション data** をクリックします。

![][1]

キャンペーンを選択し、\[インタラクションデータの復元] ボタンをクリックして、キャンペーンページから複数のキャンペーンのインタラクションデータを復元することもできます。

インタラクションデータの復元にかかる時間はさまざまですが、ほとんどの場合、このプロセスは5～15分です。復元が完了するとメールが届きます。

#### タグによる復元

また、指定したタグを使用して、期限切れのキャンペーンまたはキャンバスのアクション間データを復元することもできます。

1. **Campaigns**または**Canvas**ページに移動し、関連するタグで検索します。
2. キャンペーンまたはキャンバスを選択します。
3. **Restore inter アクション data**を選択して、これらのキャンペーンまたはキャンバスのデータを復元します。

さらに3 か月間何も操作しないと、これらのキャンペーンs またはキャンバスは期限切れになります。

#### タグによるリターゲット

タグによってリターゲティングするリターゲティングフィルターを使用するキャンペーンは、期限切れの対象から除外されません。タグによってリターゲティングするリターゲティングフィルターには、次のものがあります。

- キャンペーンまたはキャンバスからタグ付きで受信したメッセージ
- クリック/開いたキャンペーンまたはタグ付きキャンバス
- キャンペーンまたはCanvas With Tagから最後に受信したメッセージ

### メッセージングのインターアクション情報は、これまでいつ利用可能だった?

以前は、キャンペーンまたはキャンバスが次の場合、メッセージインタラクションデータは削除されていました。
- 25 カレンダー月以内にメッセージが送信されなかった場合、および
- 有効なキャンペーン、キャンバス、またはコンテンツカードのリターゲティングには使用されませんでした。

キャンペーンs と、以前に削除されたメッセージングインターアクションデータを含むキャンバスは、キャンペーンs、キャンバス、およびSegments のリターゲティング フィルターs では使用できません。

[1]: {% image_buster /assets/img/restore_interaction_data.png %}
