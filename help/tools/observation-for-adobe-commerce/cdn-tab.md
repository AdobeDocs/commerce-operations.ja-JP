---
title: この [!UICONTROL CDN] タブ
description: について説明します [!UICONTROL CDN] タブ / [!DNL Observation for Adobe Commerce].
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e753528a1d74eda0a1393e2cc455f33f529db739
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# この [!UICONTROL CDN] タブ

このタブには、に焦点を当てた情報があります [!DNL content delivery network (CDN)]. Adobe Commerce Cloudの場合は、です [!DNL Fastly] サービス。

## [!UICONTROL HIT rate]

![ヒット率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

この **[!UICONTROL HIT rate]** フレームは、結果として発生したキャッシュ可能なリクエストの数を示します。 [!UICONTROL HITS] 土壇場で。 これは、キャッシュが成功したことを示します。 右側の矢印は、1 週間前の同じ時刻を上下に表す割合を示します。

## [!UICONTROL HIT Processing]

![ヒット処理](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

この **[!UICONTROL HIT processing]** ボックスは、結果として生じたキャッシュ可能なリクエストの数を表示します [!UICONTROL HITS] 平日の間。

## [!UICONTROL MISS rate]

![ミス率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

この **[!UICONTROL MISS rate]** ボックスには、最後の 1 分間にキャッシュ可能なリクエストが失敗した回数が表示されます。 ミスとは、リクエストがキャッシュされておらず、コンテンツを提供するためにリクエストをオリジンサーバーに渡す必要がある場合です。 右側の値は、1 週間前の 1 分あたりの分数と増減の比較です。

## [!UICONTROL MISS time]

![ミスタイム](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![ヒット率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![エラー率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

この **[!UICONTROL Error Percentage]** ボックスには、リクエストのエラー率の値と、1 週間前の同じ時刻と比較した相対的な増減が表示されます。

## [!UICONTROL Total Requests]

![合計リクエスト数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![エラー率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![Fastly が、選択した期間の平均応答を秒単位でキャッシュします](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

このフレームには、キャッシュ可能なリクエストの期間が秒単位で表示されます。つまり、 `cache_response` が [!UICONTROL MISS]：選択した時間にキャッシュされた応答が欠落している平均数を表示します。

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Fastly キャッシュ POP でファセットされた、選択した期間の平均応答（秒）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

*POP* このコンテキストでは、キャッシュストレージのプールとして機能するように設定された POP （Point of Presence）を指します。 参照： [プレゼンスのポイント](https://developer.fastly.com/learning/concepts/pop/).

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![1 週間前と比較した、選択した期間の合計帯域幅（すべての POP） （% の増加/減少）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![リクエスト – 選択した時間枠以降を 1 週間前と比較](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

このフレームは、のサマリーボックスに似ています [!UICONTROL Total Requests] 上部には、前の週のリクエストがカウントされて表示されます。 これらは、キャッシュ可能なリクエストだけでなく、すべてのリクエストです（条件： `is_cacheable` が true の場合）。

## [!UICONTROL Response Count]

![応答数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![POP による帯域幅](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![上位 5 件の URL （5xx または 3xx ステータスコード）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

この **[!UICONTROL Top 5 URLs]** 表示には、5xx または 3xx のエラー応答が発生している上位 5 つの URL が表示されます。 スペースの制約により、URL の上にマウスポインターを置いて、その URL に関連付けられた特定のエラーコードを表示する必要があります。 （上の図の赤いボックスの例）。

## [!UICONTROL Top 25 URLs (200 status)]

![上位 25 件の URL （200 ステータス）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

この **[!UICONTROL Top 25 URLs]** フレームは、選択した期間内にカウント別に 200 ステータスを返した URL を表示します。

## [!UICONTROL Duration by Response Status]

![期間（応答ステータス別）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

この **[!UICONTROL Duration by Response Status]** グラフには、選択した期間のエラー応答がカウント別に表示され、エラーステータスコードでファセットされます。

## [!UICONTROL Duration by Response Status, top 25 urls]

![期間（応答ステータス別、上位 25 件の URL）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

この **[!UICONTROL Duration by Response Status, top 25 URLs]** グラフには、応答期間別の上位 25 個の URL が秒単位で表示されます。 パス全体を表示するには、URL の上にマウスを置く必要がある場合があります。 また、1 つの URL 以外をすべて削除するには、その URL をクリックします。 その後、他の URL を個別にクリックして、追加し直すことができます。 個々の URL を削除する場合は、キーを押したまま各 URL をクリックすると、グラフから削除できます。

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![期間（応答ステータス別）、上位 25 の非 200 ステータス](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

この **[!UICONTROL Duration by Response Status, top 25 non-200 status]** グラフは最後のグラフと似ていますが、フォーカスが 200 以外のステータスコードまたはエラーステータスコードにある点が異なります。 エラーコードと URL が表示されます。 パス全体を表示するには、URL の上にマウスを置く必要がある場合があります。 また、1 つの URL 以外をすべて削除するには、その URL をクリックします。 その後、他の URL を個別にクリックして、追加し直すことができます。 個々の URL を削除する場合は、キーを押したまま各 URL をクリックすると、グラフから削除できます。

## [!UICONTROL Error Count by POP timeline]

![POP タイムライン別のエラー数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

この **[!UICONTROL Error Count by POP timeline]** グラフには、選択した期間のタイムラインに沿ったエラーステータスの数が、エラーコードでファセットされて表示されます。

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![応答ステータス、上位 25 クライアント IP、非 200 ステータス別の期間](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

この **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** グラフには、ステータスエラーコードが存在した場合に、選択した時間枠での平均期間別に IP アドレスが表示されます。

## [!UICONTROL IP Frequency]

![IP 頻度](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

この **[!UICONTROL IP Frequency]** フレームは、から各 IP の（「ミス」および「パス」）ステータスをカウントします。 [!DNL Fastly] ログ。 これらのステータスを持つ web リクエストは、接触チャネルサーバーに到達し、サーバーに負荷を追加します。 これは、頻度の上位 20 件のアドレスを表示します。 このフレームは、Web サイトに対する IP 攻撃や高負荷のソースを検出するために使用できます。 このグラフは「概要」タブにも表示され、の詳細と簡単に比較できるように、ここに配置されています。 [!DNL Fastly] このタブに表示されるログ情報。
