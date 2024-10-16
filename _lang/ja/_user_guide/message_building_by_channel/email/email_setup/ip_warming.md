---
nav_title: IP ウォームアップ
article_title: IP ウォームアップ
page_order: 1
page_type: reference
description: "この参照記事では、IPの温暖化とベストプラクティスに関するトピックについて説明します。"
channel: email

---

# IP温暖化

> IP ウォームアップは、専用IP アドレスからメッセージングを受信するためにメール 受信トレイプロバイダを使用する方法です。メール プロバイダー(メールサービスプロバイダー (ESP)) とBraze の標準的な手法を使用して送信することは、メッセージが常に高率で送信先 受信トレイに到達していることを確認する上で非常に大切なメールです。

IP ウォーミングは、インターネットサービスプロバイダ(Iサービスプロバイダー) との良好な評価を確立するために設計されています。新しいIP アドレスを使用してメールを送信するたびに、Iサービスプロバイダー はプログラムでそれらのメールを監視して、スパムがユーザーs に送信されていないことを確認します。

## IPを温める時間がなければどうしますか?

**IPウォーミングが必要です。**IPアプリを適切に暖めず、メールのパターンが疑わしい場合は、メールの配信スピードが大幅に遅くなったり遅くなったりします。また、ドメインまたはIP がIサービスプロバイダー によってブロックされる場合もあります。そのため、メールはユーザーの受信トレイのスパムフォルダーに直接接続される可能性があります。そのため、IP を適切に温めることが重要です。

Iサービスプロバイダーは、ユーザーsを保護できるように、スパムの氷結が発生したときにメールの送達を抑制する。たとえば、100,000 ユーザー に送信すると、Iサービスプロバイダー は最初の1 時間で5000 のユーザー s にのみメールを配信できます。次に、Iサービスプロバイダーは、開封率s、クリック率s、配信停止s、スパム レポートsなどのエンゲージメントの測定値を監視する。そのため、かなりの数のスパム レポートが発生した場合、ユーザーの受信トレイに送信するのではなく、その送信の残りの部分をスパムフォルダーに送信することを選択する可能性があります。 

エンゲージメントが中程度の場合、より確実にメールがスパムかどうかを判断するために、より多くのエンゲージメント情報を収集するためにメールを調整し続けることがあります。メールのエンゲージメントメトリクスが非常に大きい場合は、このメールを完全に調整しなくなる可能性があります。そのデータを使用してメールレピュテーションを作成し、最終的にメールsが自動的にスパムにフィルターされるかどうかを決定します。

ドメインまたはIP がIサービスプロバイダー によってブロックされている場合、メッセージログは<サービスプロバイダー an id="1">Message Activity Log</サービスプロバイダー an> に、これらのIサービスプロバイダー をアプリし、これらのリストを解除するためにどのWeb サイトにアクセスするかについての情報が記録されます。

## 温暖化スケジュール

この温暖化スケジュールに厳密に従うことを強く推奨し、配信可能性をサポートします。また、一貫したスケーリングにより配信メトリクスが向上するため、日数をスキップしないことも重要です。

日 | 送信するメールの数
----|--------------------------|
1 | 50
2 | 100
3 | 500
4 | 1,000
5 | 5,000
6 | 10,000
7 | 20,000
8 | 40,000
9 | 70,000
10 | 100,000
11 | 150,000
12 | 250,000
13 | 400,000
14 | 600,000
15 | 1,000,000
16 | 2,000,000
17 | 4,000,000
18+ | 1日2回~希望量

送付ピークまでのウォーミングアップをお勧めします。つまり、通常、1日に200万メールを送信するが、季節期間に700万を送信する予定の場合、その"peak"送信は、ウォームアップする必要があるものです。

ウォーミングが完了し、希望の1日の体積に達したら、その体積を毎日維持するようにします。ある程度の変動が予想されますが、望ましいボリュームに到達すると、週に1回大量送出を行うだけで、配信メトリクスと送信者の評判に悪影響を与える可能性があります。 

{% alert important %}
ほとんどのIサービスプロバイダー は、レピュテーションデータのみを30 日間保存します。メッセージを送信せずに1ヶ月経過した場合は、IPウォーミングプロセスを繰り返す必要があります。
{% endalert %}

## ウォーミング時の送信制限方法

内蔵のユーザー制限機能は、IP アドレスのウォームアップに役立ちます。キャンペーンの作成中に必要なメッセージング Segments を選択した後、[Target ユーザーs]({{site.baseurl}}/user_guide/message_building_by_channel/email/html_editor/creating_an_email_campaign/#step-4-build-the-remainder-of-your-campaign-or-canvas) ステップで、**詳細オプション** ドロップダウンを選択してユーザーs を制限します。ウォーミングスケジュールが続くと、この制限を徐々に引き上げて、送信するメールの量を増やすことができます。

![][18]

## サブドメインセグメンテーション

多くのIサービスプロバイダーおよびメールアクセスプロバイダは、IPアドレスレピュテーションによってのみフィルターされなくなりました。これらのフィルターリングテクノロジーは、ドメインベースのレピュテーションにも対応しています。つまり、フィルターは、送信者のドメインに関連付けられているすべてのデータを調べ、IP アドレスをシングルアウトするだけではありません。このため、メール IP のウォームアップに加えて、マーケティング、トランスアクション al、および企業メール用に別々のドメインまたはサブドメインを持つことをお勧めします。 

{% alert important %}
サブドメインセグメンテーションは、大量の送信者にとってはとくに大切である。これらの送信者は、自分の口座を設定し、この慣行を遵守していることを確認する際に、Braze担当者と連携する必要があります。
{% endalert %}

企業メールが最上位ドメイン経由で送信され、マーケティングメールとトランスメールが別のドメインまたはサブドメイン経由で送信されるように、ドメインをSegmentすることをお勧めします。

## ベストプラクティス

IP温暖化ではない結果は、IP温暖化のベストプラクティスに従えば避けることができます。

### 少量のメールを送信することから始める

毎日送る金額を少しずつ増やしていきます。急激で大量のメール キャンペーンは、Iサービスプロバイダーによる最も懐疑的なものと見なされている。そのため、まず少量のメールを送信し、最終的に送信する予定のメールの量に合わせて段階的にスケールする必要があります。ボリュームに関係なく、IP を安全にウォーミングアップすることをお勧めします。[IPウォーミングスケジュール](#ip-warming-schedule)参照。

### 導入コンテンツを持つ

最初のコンテンツが非常に魅力的であることを確認し、ユーザーがクリックし、開封し、メールと関わる可能性を最大限に高めます。IPを温める際には、無差別の爆風よりも、必ず、十分にターゲットを絞ったメールを選好する。

### 一貫した送信ケイデンスを設定する

IPウォーミングが完了したら、送信ケイデンスを作成し、1日または数日間にわたってメールを分散させるようにします。一貫性のあるスケジュールをできるだけ多く作成することで、IP クールダウンを防ぐことができます。これは、送信ボリュームが数日間以上停止したり大幅に低下したりした場合に発生する可能性があります。 

一度に大量の爆風を送るのではなく、より長い時間枠に送信を広げるには、私たちの[IP温暖化スケジュール](#ip-warming-schedules)を参照してください。

### メール一覧を消去する

メール一覧が清潔で、古い、または検証されていないメールがないことを確認します。\[CASL-とCAN-サービスプロバイダーAM-compliant][40] の両方がアイデア l であることを確認します。

### 送信者の評価を監視する

IP ウォーミングプロセスを実行する場合は、IP ウォーミングプロセスを実行する際に送信者のレピュテーションを注意深く監視してください。これらの特定のメトリクスは、以下を監視するために重要です。
- **バウンスレート:**3～5%を超えるキャンペーンがバウンドする場合は、\[清潔に保つ]の指針に従って、一覧の清浄度を評価する必要があります。EメールリストHygiene][43]の記事の重要性。さらに、\[sunset policy][46] を実装して、メール が接続されていないアドレスまたは休止状態 メール アドレスを停止することを検討する必要があります。
- **スパムレポート:**いずれかのキャンペーンが0.08%を超える割合でスパムとしてレポートされている場合は、送信している内容を再評価し、関心のあるオーディエンスを対象としていることを確認し、メールsがアプリ適切な言葉で関心をそそるようにしてください。
- **オープンレート:**オープンレートは、受信トレイの配置に役立ちます。一意の開封率が25% を超える場合は、受信トレイが高くなる可能性があります。これは、送信者の評価が高いことを示しています。

{% alert tip %}
Braze は、[インテリジェントタイミング]({{site.baseurl}}/user_guide/sage_ai/intelligence/intelligent_timing/) を使用してIP をウォームアップしないことをお勧めします。IP ウォーミングキャンペーンs は最初に送信するキャンペーンの一部であるため、Braze では、最適な送信時刻を計算するのに十分な情報がユーザーs にありません。この例では、インテリジェントタイミングを持つすべてのメッセージがフォールバックの時刻にデフォルトされ、同時に送信されます。
{% endalert %}

{% alert tip %}
ドメインとIP がまだ肯定的な評価を確立していないため、IP ウォームアップ中にメールがスパム フォルダーに送信されるのは通常です。メールがスパムフォルダーに保存されている場合、メール管理者はBraze送信ドメインとIP を会社の許可リストに追加する必要があります。
{% endalert %}

[18]: {% image_buster /assets/img_archive/email_ip_warming_sends_limit_new.png %}
[40]: {{site.baseurl}}/user_guide/onboarding_with_braze/spam_regulations/
[43]: https://www.braze.com/blog/email-list-hygiene/
[44]: https://senderscore.org/
[45]: http://www.senderbase.org/
[46]: {{site.baseurl}}/user_guide/message_building_by_channel/email/best_practices/sunset_policies/
