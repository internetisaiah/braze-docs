---
nav_title: カスタムイベントの集計値のエクスポート
article_title: カスタムイベントの集計値のエクスポート
page_order: 6
page_type: reference
description: "このリファレンス記事では、カスタムイベントデータの集計値をエクスポートする方法について説明します。"
tool: Reports

---

# カスタムイベントの集計値のエクスポート

> ダッシュボードの \[**カスタムイベント**] レポートページでは、1 つ以上のカスタムイベントの発生数を時系列で確認できます。カスタムイベント数または時刻別カスタムイベント数の詳細統計を表示する場合、セグメント別にデータを表示することもできます。

**カスタムイベントレポート**は \[**分析**] の下にあります。

{% alert note %}
[古いナビゲーション]({{site.baseurl}}/navigation)を使用している場合、**カスタムイベント**レポートは \[**データ**] の下にあります。
{% endalert %}

![カスタムイベント][14]

次の CSV をエクスポートできます。

- 日付別カスタムイベント数
    - (オプション) さまざまなセグメントのカスタムイベント数
- 時刻別カスタムイベント数
    - (オプション) さまざまなセグメントのカスタムイベント数
- MAU あたりのカスタムイベント数
- さまざまなセグメントのカスタムイベント数
- KPI 式あたりのカスタムイベント数
    - (オプション) さまざまなセグメントのカスタムイベント数

{% alert tip %}
CSV および API のエクスポートに関するヘルプについては、「[エクスポートのトラブルシューティング]({{site.baseurl}}/user_guide/data_and_analytics/export_braze_data/export_troubleshooting/)」の記事を参照してください。
{% endalert %}

[14]: {% image_buster /assets/img_archive/Export_events.png %}
