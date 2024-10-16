---
title: Ketch
nav_title: Ketch
description: "この参考記事では、ブレイズとケッチの統合について取り上げている。Ketchは、簡素化されたプライバシー・オペレーションと、完全でダイナミックなデータ・コントロール、そしてインテリジェンスを提供する。"
alias: /partners/ketch
page_type: partner
search_tag: Ketch
---

# Ketch

> [ケッチは](https://www.ketch.com)、企業がデータの責任ある管理者となることを可能にする。Ketchは、簡素化されたプライバシー・オペレーションと、完全でダイナミックなデータ・コントロールとインテリジェンスを提供する。 

BrazeとKetchの統合により、Ketchプリファレンスセンター内で顧客のコミュニケーションプリファレンスをコントロールし、これらの変更を自動的にBrazeに反映させることができる。 

{% alert note %}
購読グループの作成に関するガイダンスをお探しですか？<a href='/docs/user_guide/message_building_by_channel/sms/sms_subscription_group//'>SMS購読グループと</a> <a href='/docs/user_guide/message_building_by_channel/email/managing_user_subscriptions/'>Eメール購読</a>グループの記事をチェックする。
{% endalert %}

## 前提条件

| 要件 | 説明 |
|---|---|
| ケッチアカウント | この統合を有効にするには、管理者権限を持つ[Ketch](https://www.ketch.com)アカウントが必要である。 |
| BrazeのAPIキー | `users.track` 、`subscription.status.get` 、`subscription.status.set` 、`users.delete` 、`users.alias.new` 、`users.export.ids` 、`email.unsubscribe` 、`email.blacklist` のパーミッションを持つBraze REST APIキー。<br><br> これは、Brazeのダッシュボード**（Developer Console**>**REST API Key**>**Create New API Key**）で作成できる。 |
{: .reset-td-br-1 .reset-td-br-2}

## 統合

### ステップ1:Brazeの接続をセットアップする

1. [ケッチ・インスタンスで](https://app.ketch.com)、**データ・**システムに移動し、**ブレイズを**選択する。次に、**New Connectionを**クリックする。
2. Braze接続に識別可能な名前を付け、APIベースの処理でこの接続を参照するために使用する。その接続にはコードも作成される。このコードは、すべての接続で一意でなければならない。
3. ユーザーのIDマッピングを確認する。デフォルトでは、Ketchはユーザーの電子メールアドレス、またはBrazeの`external_id` 。
4. Braze APIキーを追加し、APIエンドポイントを指定する。この[APIエンドポイントは](https://www.braze.com/docs/api/basics/#endpoints)、あなたの組織が使用しているBrazeインスタンスに基づいていることに注意すること。

### ステップ2:購読設定を行う

1. **ポリシー・センター＞サブスクリプションに**進む。**Policy Center（ポリシーセンター）**」に「Subscriptions（購読）」タブが表示されない場合は、マーケティング・プリファレンス・センターにアクセスできることを確認し、製品のこの部分にアクセスするための正しいアカウント権限を持っていることを確認する。
2. **新しい購読を作成**] をクリックして、新しいトピックを作成する。各サブスクリプションには名前とコードがある。
3. 購読トピックを送信するチャンネルを追加する。各チャンネルは、ユーザーのマーケティング・プレファレンス・センターに表示される。また、ケッチ・プリファレンス・センターに特定のオプトインやオプトアウトのシグナルをどのようにオーケストレーションさせたいかの詳細を追加することもできる。
4. オプトインおよびオプトアウト信号の編成に使用するBraze接続を選択する。
5. Ketchユーザー設定を送信したい購読グループのBraze`subscription_group_id` を入力する。

![Brazeサブスクリプション・グループID。][1]

{% alert note %}
ユーザーのオプトインとオプトアウトのシグナルを収集し、組織化するためには、IDが適切に設定されていなければならない。Ketchは、この統合のために、ユーザー・プレファレンス・シグナルをオーケストレーションする識別子として電子メールを設定することを推奨している。
{% endalert %}


### ステップ3:アイデンティティを設定する

ユーザーがマーケティング・プリファレンス・センターを見ることができるのは、Ketchがそのユーザーのマーケティング・プリファレンス・アイデンティティを確認できたときだけである。もしKetchがユーザーのIDを適切に捕捉できない場合、Ketchはユーザーのプリファレンスを管理できないので、マーケティング・プリファレンス・ページはそのユーザーに表示されない。

1. マーケティング・プリファレンス・アイデンティティを構成するには、Ketch の**「Settings」**ページに移動し、「**Identity space**」をクリックする。新しい ID スペースを作成するか、既存の ID スペースを編集して、その ID スペースをマ ーケティング優先 ID として割り当てる必要がある。敷地内に配置されたケッチ・タグが、そのIDスペースを適切に捉えていることを確認する。
2. **エクスペリエンス・サーバー**]、\[**プロパティ**] の順に選択し、目的のプロパティを編集する。そのプロパティのデータレイヤーで、カスタム・アイデンティティ・スペースを有効にする。次に、このサイトでマーケティング嗜好のアイデンティティをどのように取得するかを設定する。
3. アイデンティティ・スペースを設定したら、Ketchタグが配置されたウェブサイト上でプリファレンス・センターを開き、プリファレンス・センターが表示されるかどうかをテストする。


[1]: {% image_buster /assets/img/ketch/ketch1.png %}