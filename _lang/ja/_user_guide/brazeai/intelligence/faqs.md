---
nav_title: FAQ
article_title: インテリジェンスFAQ
page_order: 191
description: "この記事では、インテリジェント・チャンネル、インテリジェント・セレクション、インテリジェント・タイミングに関するよくある質問に対する回答を提供します。"
---

# よくある質問

> この記事では、Intelligence Suite に関するよくある質問にお答えします。

## インテリジェントセレクション

### インテリジェントセレクションと組み合わせた場合、24 時間が経過しないと再適格性が利用できないのはなぜですか?

インテリジェントセレクションキャンペーンは、コントロールバリアントの整合性に影響を与えるため、ウィンドウが短すぎると再適格性を得ることはできません。24 時間のギャップを作成することで、アルゴリズムが統計的に有効なデータセットを使用できるようになります。

通常、再適格性のあるキャンペーンでは、ユーザーは以前に受け取ったのと同じバリアントに再エントリします。インテリジェントセレクションを使用すると、バリアントの分布がこの機能の最適な割り当てアスペクトによってシフトするため、ユーザが同じキャンペーンバリアントを受け取ることが保証されません。インテリジェントセレクションがバリアントのパフォーマンスを再確認する前にユーザーの再エントリが許可された場合、再エントリしたユーザーが原因でデータに歪みが生じる可能性があります。

たとえば、キャンペーンが次のバリアントを使用しているとします。

- バリアントA:20%
- バリアントB:20%
- コントロール: 60%

次に、第2ラウンドのバリアント分布は次のようになります。

- バリアントA:15%
- バリアントB:25%
- コントロール: 60%

### キャンペーンの初期段階で、等しいセンドを示すインテリジェントセレクションバリアントがあるのはなぜですか?

インテリジェントセレクションは、キャンペーンコンバージョンの現在のステータスに基づいて、送信するバリアントを割り当てます。これは、送信がバリアント間で均等に送られる、トレーニング周期を 1 度経た後の最終的なバリアント割り当てのみを決定します。キャンペーンの初期段階でインテリジェントセレクションが均等に送信されないようにするには、従来のA/B テストに固定バリアントを使用します。

### インテリジェント・セレクションは、明確な勝者を選ばずに最適化を停止するか?

インテリジェントセレクションは、実験を継続してもコンバージョン率の改善は現在の 1% を超えることはないという信頼度が 95% に達すると、最適化を停止します。

### キャンバスまたはキャンペーンでインテリジェントセレクションを有効にできないのはなぜですか(グレー表示)?

インテリジェント選択は、次の場合には使用できません。

- キャンペーンまたはキャンバスに変換イベントを追加していない
- 単一送信キャンペーンを作成している
- 24 時間未満のウィンドウで再適格性が有効になっている
- キャンバスが 1 つのバリアントで構成されており、追加のバリアントやコントロールグループは追加されない
- キャンバスは、1 つのコントロールグループで構成され、バリアントは追加されません

## インテリジェントタイミング

### インテリジェント・タイミングは、ユーザがいつ変換される可能性が最も高いか、またはユーザが開いたりクリックしたりする可能性が最も高い場合にのみ予測しますか?

インテリジェントタイミングは、ユーザがいつ開いたりクリックしたりするかを予測します。

### 最も人気のあるアプリの時間はどのように決められていますか?

最も人気の高いアプリの時間は、ワークスペースのセッション開始時刻の平均 (現地時刻) によって決まります。このメトリクスは、キャンペーンの時間をプレビューするときにダッシュボードに表示されます(赤色で表示)。

### マシンのインテリジェントタイミングアカウントが開きますか?

はい、マシン開封数はインテリジェントタイミングでフィルタリングされるため、出力には影響しません。

### インテリジェントタイミングを可能な限り確実に機能させるにはどうすればよいですか?

Intelligent Timing は、メッセージを受信した時点で、各ユーザのメッセージエンゲージメントの個々の履歴を使用します。Intelligent Timing を使用する前に、一日の異なる時間帯にユーザーメッセージを送信していることを確認してください。こうすることで、それぞれのユーザーにとっていつが最良の時期かを「サンプリング」することができます。さまざまな時間帯のサンプリングが不十分だと、インテリジェントタイミングはユーザーにとって最適でない送信時刻を選択してしまう可能性があります。 

### すべてのタイムゾーンのすべてのユーザーにインテリジェント・タイミング・キャンペーンを成功裏に配信するには、どの程度前もって開始すればよいですか?

ろう付けは、サモア時間の午前0時(世界初のタイムゾーンの1つ)に最適な時間を計算します。1 日は約 48 時間に及びます。例えば、最適な時刻が午前 12 時 1 分で、オーストラリアに住んでいる人にとって、すでに最適な時刻が過ぎているので、送信するには「遅すぎる」ことになります。こうした理由から、アプリを利用する世界中のすべての人に確実に配信されるようにするには、48 時間前にはスケジュールする必要があります。

### インテリジェント・タイミング・キャンペーンが送信をほとんど表示しないのはなぜですか?

Braze は、良好な推定を行うためにデータポイント数のベースラインデータを必要とします。十分なセッションデータがなかったり、ターゲットとなるユーザーのメールクリック数や開封数がほとんどない場合 (例えば新規ユーザーの場合など)、インテリジェントタイミングは、その曜日のワークスペースの最も人気の高い時間帯をデフォルトとして使用することがあります。ワークスペースに関する十分な情報がない場合は、デフォルトの午後 5 時にフォールバックします。特定の[フォールバック時間]({{site.baseurl}}/user_guide/brazeai/intelligence/intelligent_timing/#fallback-options)を設定することもできます。

### インテリジェント・タイミング・キャンペーンがスケジュールされた日付を過ぎて送信するのはなぜですか?

インテリジェントタイミングキャンペーンでは、A/B テストを活用しているため、スケジュールされた日付を過ぎて送信される場合があります。A/Bテストを使用するキャンペーンは、A/Bテストが終了した後、自動的にWinning Variantを送信することができ、キャンペーン送信の期間が長くなります。デフォルトでは、インテリジェントタイミングキャンペーンは、翌日の残りのユーザーに勝者バリアントを送信するようにスケジュールされますが、この送信日は変更することができます。

インテリジェント・タイミング・キャンペーンがある場合は、A/Bテストが終了するまでさらに時間を置いて、Winning Variantが1つではなく2日間送信するようにスケジュールすることをお勧めします。 

### ブレーズは、セグメントおよびオーディエンスフィルタの適格性基準をいつチェックしますか?

キャンペーンが起動されると、Braze は次の2 つのチェックを実行します。

1. 最初のタイムゾーンが識別されたらすぐに、ユーザーのキュー処理を開始し、
2. スケジュールされた時刻にユーザーがまだキャンペーンを受け取る資格があるかどうかを確認します。

他のキャンペーンの送信をフィルタリングするキャンペーンを登録する場合は、注意が必要です。たとえば、同じ日に2 つのキャンペーンを異なる時間に送信し、ユーザが最初のキャンペーンを受信した場合に2 番目のキャンペーンしか受信できないフィルタを追加した場合、ユーザは2 番目のキャンペーンを受信しません。これは、キャンペーンが最初に作成され、セグメントが形成されたときに、誰も適格ではなかったためです。

### インテリジェントタイミングキャンペーンでサイレント時間を使用できますか?

キャンペーンまたはキャンバスにインテリジェントタイミングと静かな時間の両方を使用することは、逆効果であるためお勧めしません。サイレント時間はユーザーの行動に関するトップダウンの仮定に基づいているのに対し、インテリジェントタイミングはユーザーのアクティビティに基づいています。

### インテリジェントタイミングとレートリミットを使用できますか?

Braze では、メッセージがいつ配信されるかが保証されないため、インテリジェントタイミングとレート制限の使用はお勧めしません。

### IP ウォーミング中にインテリジェントタイミングを使用できますか?

Braze では、ユーザーが最初に IP ウォーミングを行うときにインテリジェントタイミングを使用することはお勧めしていません。その動作によっては、1 日の容量達成が困難になる場合があるためです。これは、インテリジェントタイミングがキャンペーンセグメントを 2 回評価することが原因です。キャンペーンが最初に作成されたときに 1 回評価した後、ユーザーに送信する前に 2 回目を行い、ユーザーがまだそのセグメントにいるべきかを確認します。 

これにより、セグメントがシフトおよび変更される可能性があり、2回目の評価で一部のユーザーがセグメントから外れてしまうことがよくあります。これらのユーザーは置き換えられないため、最大ユーザー数にどれだけ近づけるかに影響します。
