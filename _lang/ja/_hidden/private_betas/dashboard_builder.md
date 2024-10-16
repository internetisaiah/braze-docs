---
nav_title: ダッシュボードビルダー
article_title: ダッシュボードビルダー
permalink: "/dashboard_builder/"
description: "このレファレンス記事では、ダッシュボードビルダーを使用して、クエリビルダーで作成されたレポートを使用してダッシュボードとビジュアライゼーションを作成する方法について説明します。"
page_type: reference
hidden: true
---

# ダッシュボードビルダー

> ダッシュボードビルダーを使用して、クエリビルダーで作成されたレポートを使用してダッシュボードとビジュアライゼーションを作成します。Query Builderの組み込みSQLクエリテンプレートの使用を開始するか、独自のカスタムSQLクエリを作成して、さらに多くのインサイトをアンロックすることができます。

Braze では、ラストタッチアトリビューションを使用した収益の解析など、頻繁にユースケースするためのダッシュボード テンプレートs が事前に構築されています。テンプレート ダッシュボードをエディットする機能はまだ使用できません。

{% alert note %}
ダッシュボードビルダーは現在早期アクセス段階です。この早期アクセスへ参加することに興味がある場合は、カスタマーサクセスマネージャーにお問い合わせください。
{% endalert %}

## ダッシュボード テンプレートの実行

1. **Analytics**> **Dashboard Builder**に移動します。ホームページには、ワークスペース内に存在するすべてのダッシュボードが一覧表示され、Braze作成されたテンプレートs が一番上に表示されます。これらは、タイトルでは「(Braze)」で表されます。
2. 関心のあるダッシュボードを選択します。
3. **ダッシュボード**を実行を選択して、そのテンプレートを使用してダッシュボードを生成します。

### 利用可能なダッシュボード テンプレート

#### 売上 - 前回のタッチのアトリビューション

**Revenue - Last Touch Attribution** テンプレートでは、キャンペーンs、キャンバス、およびチャネルs 全体の収益を確認できます。すべての収益データは、アトリビューション期間中に最後にタッチされたメッセージに関連付けられます。

タッチには、`Email Click`、`Content Card Click`、`In-App Message Click`、`SMS Delivery`、`WhatsApp Read`、`Webhook Send` などがあります。

| 指標 | 定義 |
| --- | --- |
| ラストタッチ収益合計 | 選択された日付範囲およびアトリビューション期間内にラストタッチイベントがあるすべてのキャンペーンおよびキャンバスの収益イベントの合計。 |
| 購入コンバージョンの合計 | 対象となるラストタッチイベントを含む、すべてのキャンペーンおよびキャンバスの収益イベントの数。 |
| コンバージョンまでの平均日数 | 対象のラストタッチイベントを含むすべてのキャンペーンおよびキャンバス購入イベント間の平均時間。 |
| 受信者あたりの収益 | 対象収益イベントの収益合計を、日付範囲内にメッセージを受信した一意のユーザー数で割った値。 |
| 一意の購入者 | 対象収益イベントがある一意のユーザーの数。 |
| 国別売上高 | 国別にグループ化された、ラストタッチイベントを含むすべてのキャンペーンおよびキャンバスの収益イベントの合計。 |
| キャンペーン別売上高 | キャンペーン別にグループ化された、すべてのキャンペーンおよびキャンバスの収益イベントと、該当するラストタッチイベントの合計。 |
| キャンペーンバリアント別売上高 | キャンペーン バリアント別にグループ化された、すべてのキャンペーンおよびキャンバスの収益イベントと、該当するラストタッチイベントの合計。 |
| キャンバス別売上高 | キャンバス別にグループ化された、すべてのキャンペーンおよびキャンバスの収益イベントの合計と、該当するラストタッチイベントの合計。 |
| キャンバスバリアント別売上高 | 対象のラストタッチイベントを含むすべてのキャンペーンおよびキャンバス収益イベントの合計 (キャンバスバリアント別にグループ化)。 |
| 製品あたりの購入数 | 製品別にグループ化されたすべての購入数。 |
| チャネル別売上収益 | チャネル別にグループ化された、すべてのキャンペーンおよびキャンバスの収益イベントと、該当するラストタッチイベントの合計。 | 
| 収益の時系列 | 対象のラストタッチイベントを含むすべてのキャンペーンおよびキャンバス収益イベントの合計 (UTC 日付別にグループ化)。 |
{: .reset-td-br-1 .reset-td-br-2}

#### デバイスと通信事業者

| 指標 | 定義 |
| --- | --- |
| デバイスの通信事業者 | 選択した日付範囲にプッシュ通知を開封したユーザの数 (デバイスの通信事業者別にグループ化)。 |
| デバイスモデル | デバイスモデル別にグループ化された、プッシュ通知を開封した選択された日付範囲内のユーザーs の数。 |
| デバイスオペレーティングシステム | プッシュ通知を開封した選択された日付範囲のユーザーの数(機器オペレーティングシステム別にグループ化)。 |
| デバイス画面サイズ | 選択した日付範囲内にプッシュ通知を開封したユーザーの数 (デバイス画面の解像度 (サイズ) 別にグループ化)。 |
{: .reset-td-br-1 .reset-td-br-2}

## カスタマイズしたダッシュボードの作成

1. **ダッシュボード**を作成するか、既存のダッシュボードと**編集**を選択します。\[**\+ タイルを追加**] を選択します。
2. \[**既存のクエリの選択**] を選択し、クエリビルダーで実行したクエリを選択します。
3. タイルでのクエリー結果の表示方法を編集するには、鉛筆アイコンを選択してタイトルとグラフの種類を変更します。<br><br>![タイトルとチャートの種類を変更するオプションを含むタイルエディタビュー。][2]{: style="max-width:60%;"}<br><br>
    - **Column**、**Bar**、または**Line**のチャートタイプを選択した場合:
        - X 軸で使用するフィールドをクエリーから選択します。
        - 関心のない列を選択解除します。<br><br>![グラフの種類を含むドロップダウン。][1]{: style="max-width:40%;"}

{: start="4"}        
4\.変更を保存してください。タイルを削除する場合は、ごみ箱アイコンを選択します。削除したタイルは元に戻せず、再作成する必要があります。
5. 右下隅をドラッグしてタイルのサイズを調整し、右上隅のハンドルをドラッグしてダッシュボード上のタイルの位置を調整します。<br><br>![タイルがハンドルでドラッグされています。][3]<br><br>
6. ダッシュボードが完了するまで、タイルを追加します。
7. \[**ダッシュボードを表示**] を選択し、\[**ダッシュボードを実行**] を選択します。ダッシュボードがレポートの生成を完了するまでに数分かかる場合があります。

## フィードバックを共有する

カスタマーサクセスマネージャーに連絡するか、受け取ったイネーブルメントメールに返信して、お気軽にフィードバックをお寄せください。

[1]: {% image_buster /assets/img/chart_type.png %}
[2]: {% image_buster /assets/img/sample_tile.png %}
[3]: {% image_buster /assets/img/drag_tile.png %}
