---
nav_title: インテリジェントセレクション
article_title: インテリジェントセレクション
page_order: 1
description: "この記事では、インテリジェントセレクションについて説明します。インテリジェントセレクションは、定期的なキャンペーンまたはキャンバスのパフォーマンスを1 日に2 回分析し、各メッセージバリアントを受信するユーザの割合を自動的に調整する機能です。"
search_rank: 10
---

# インテリジェントセレクション {#intelligent-selection}

> インテリジェントセレクションは、定期的なキャンペーンまたはキャンバスのパフォーマンスを1 日に2 回分析し、各メッセージバリアントを受信するユーザの割合を自動的に調整する機能です。 

パフォーマンスが他のユーザーよりも優れていると思われるバリアントは、より多くのユーザーに送信され、パフォーマンスの低いバリアントは、より少ないユーザーをターゲットにします。各調整は、\[統計的アルゴリズム][227]を使用して行われ、ランダムな確率だけでなく実際のパフォーマンスの違いを調整していることを確認します。

![インテリジェント選択を有効にしたキャンペーンのA/B テストセクション。][3]

インテリジェントセレクションは以下のことを行います。
- パフォーマンスデータを繰り返し確認し、キャンペーンのトラフィックを段階的に勝者バリアントにシフトさせる。
- 統計的な信頼性を犠牲にすることなく、より多くのユーザーがベストパフォーマンスのバリアントを受け取っていることを確認します。
- [従来の AB テスト][1]よりも迅速にパフォーマンスの低いバリアントを除外し、パフォーマンスの高いバリアントを特定する。
- より頻繁にテストを行い、ユーザーに最高のメッセージが表示されることを確信してください。 

インテリジェントセレクションは、複数回送信するようにスケジュールされたキャンペーンに最適です。キャンペーンの調整を開始するには、最初の結果が必要です。したがって、一度だけ送信するキャンペーンはメリットがありません。これらのキャンペーンでは、[A/B test][1] の方が効果的です。

## インテリジェントセレクションをキャンペーンに追加するにはどうすればよいですか?

### キャンペーンインテリジェントセレクション
インテリジェントセレクションは、Braze キャンペーンコンポーザーの**Target Audiences** ステップの任意のマルチセンドキャンペーンに追加できます。一度だけ送信するキャンペーンは、この機能を利用できません。

### キャンバスインテリジェント選択
キャンバスにバリアントを追加する際、バリアントのパーセンテージのうち 1 つをクリックします。すると、バリアント分布を編集してインテリジェントセレクションをオンにすることができます。

![それぞれが 50% のバリアント分布に設定された 2 つのバリアントがあり、インテリジェントセレクションを有効化できるキャンバス。][2]

キャンバスに変換イベントをまだ追加していない場合、またはキャンペーンがソロバリアントで構成されている場合、インテリジェント選択は使用できません。

{% alert note %}
インテリジェントセレクションは、コントロールバリアントの整合性に影響するため、24 時間未満の再適格性チェックが有効なキャンペーンでは使用できません。詳細については、[インテリジェンス FAQ]({{site.baseurl}}/user_guide/brazeai/intelligence/faqs/#why-is-re-eligibility-in-less-than-24-hours-not-available-when-combined-with-intelligent-selection) を参照してください。
{% endalert %}

## いつまで実行されますか?

キャンペーンおよびキャンバスの場合、インテリジェントセレクションは、"true"バリアントの換算レートに関する十分なエビデンスを収集するまで実行されます。「十分」かどうかは、「後悔」と呼ばれる特別な指標によって決定されます。インテリジェントセレクションは、どのバリアントが最良かを特定するのに十分なデータがあれば、自らオフになるという点で、信頼度に似ていると考えることができます。 

ほとんどの場合、インテリジェントセレクションはいずれかのバリアントを勝者バリアントとして選択します。このバリアントは、今後送信されるオーディエンスの100% に送られます。

{% alert note %}
インテリジェント・セレクションは、1つの明確な勝者を選ばずに最適化を停止することが可能です。インテリジェント・セレクションは、実験を継続しても現在の割合の1%を超える変換率は向上しないという95%の信頼度がある場合、最適化を停止します。
{% endalert %}

[1]: {{site.baseurl}}/user_guide/intelligence/multivariate_testing/
[2]: {% image_buster /assets/img/intelligent_selection.png %}
[3]: {% image_buster /assets/img/intelligent_selection1.png %}
\[227]: https://en.wikipedia.org/wiki/Multi-armed_bandit

