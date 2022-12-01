---
title: 「 [!UICONTROL CDN] タブ"
description: 詳しくは、 [!UICONTROL CDN] タブ [!DNL Observation for Adobe Commerce].
source-git-commit: 424c832ba7580e5d766dea33e3b776eaca7a0d77
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# この [!UICONTROL CDN] タブ

このタブには、 [!DNL content delivery network (CDN)]. Adobe Commerce Cloudの場合、これは [!DNL Fastly] サービス。

## [!UICONTROL HIT rate]

![ヒット率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

この **[!UICONTROL HIT rate]** frame は、 [!UICONTROL HITS] 最後の瞬間に これは、キャッシュが成功したことを示します。 右側の矢印は、1 週間前の同じ時間の上または下の割合を表示します。

## [!UICONTROL HIT Processing]

![ヒットの処理](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

この **[!UICONTROL HIT processing]** ボックスに、 [!UICONTROL HITS] 週の間に

## [!UICONTROL MISS rate]

![ミス率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

この **[!UICONTROL MISS rate]** ボックスには、最後の 1 分間にキャッシュ可能なリクエストのミス数が表示されます。 ミスとは、リクエストがキャッシュされず、コンテンツを提供するためにリクエストを元のサーバーに渡す必要がある場合です。 右側の値は、1 週間前の分ごとの分数に対する増減の比較です。

## [!UICONTROL MISS time]

![ミス時間](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![ヒット率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![エラーの割合](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

この **[!UICONTROL Error Percentage]** ボックスには、リクエストのエラー率の値が表示され、1 週間前の同じ時間に対する相対的な増減が表示されます。

## [!UICONTROL Total Requests]

![合計リクエスト数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![エラー率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![選択した期間に対する Fastly キャッシュの平均応答時間（秒）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

このフレームは、キャッシュ可能なリクエストの期間を秒単位で表示します。つまり、 `cache_response` は [!UICONTROL MISS]の場合は、選択した時間に対する、キャッシュされなかった応答の平均が表示されます。

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![POP で切り子面化された、選択した期間に対する FASTLY キャッシュの平均応答数（秒）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![1 週間前（%増減）と比較した、選択した期間中の合計帯域幅（すべての POP）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![リクエスト — 1 週間前と比較して選択された期間以降](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

このフレームは、 [!UICONTROL Total Requests] が最上位に表示されますが、これには前の週のリクエスト数が表示されます。 これらはすべてのリクエストであり、キャッシュ可能なリクエスト ( `is_cacheable` が true の場合は除く )。

## [!UICONTROL Response Count]

![応答数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![POP 別の帯域幅](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![上位 5 件の URL（5xx または 3xx ステータスコード）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

この **[!UICONTROL Top 5 URLs]** 「 」には、5xx または 3xx エラー応答が発生した上位 5 件の URL が表示されます。 スペース上の制約があるので、URL の上にマウスを移動して、その URL に関連付けられている特定のエラーコードを確認する必要があります。 （上の図の赤いボックスの例）

## [!UICONTROL Top 25 URLs (200 status)]

![上位 25 件の URL （200 ステータス）](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

この **[!UICONTROL Top 25 URLs]** frame は、選択した期間にカウント別に 200 ステータスを返した URL を表示します。

## [!UICONTROL Duration by Response Status]

![応答ステータス別の期間](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

この **[!UICONTROL Duration by Response Status]** グラフには、選択した期間のエラー応答をエラーステータスコードで切り取った数別に表示します。

## [!UICONTROL Duration by Response Status, top 25 urls]

![応答ステータス別の期間、上位 25 個の URL](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

この **[!UICONTROL Duration by Response Status, top 25 URLs]** グラフには、応答時間別の上位 25 件の URL が秒単位で表示されます。 パス全体を表示するには、URL の上にマウスを置く必要が生じる場合があります。 また、1 つ以外の URL をすべて削除するには、その URL をクリックします。 その後、他の URL を個別にクリックして戻すことができます。 個々の URL を削除する場合は、キーを押したまま各 URL をクリックして、グラフから削除します。

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![応答ステータス別の期間、上位 25 件の非 200 件のステータス](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

この **[!UICONTROL Duration by Response Status, top 25 non-200 status]** グラフは最後のグラフに似ていますが、フォーカスが 200 以外のステータスコードまたはエラーステータスコードにある点が異なります。 エラーコードと URL が表示されます。 パス全体を表示するには、URL の上にマウスを置く必要が生じる場合があります。 また、1 つ以外の URL をすべて削除するには、その URL をクリックします。 その後、他の URL を個別にクリックして戻すことができます。 個々の URL を削除する場合は、キーを押したまま各 URL をクリックして、グラフから削除します。

## [!UICONTROL Error Count by POP timeline]

![POP タイムライン別のエラー数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

この **[!UICONTROL Error Count by POP timeline]** グラフには、選択したタイムフレームタイムラインに沿って、エラーコードで切り子にされたエラーステータスの数が表示されます。

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![応答ステータス別の期間、上位 25 件のクライアント IP、非 200 件のステータス](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

この **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** グラフには、選択した期間内でステータスエラーコードが発生した IP アドレスの平均期間が表示されます。

## [!UICONTROL IP Frequency]

![IP 頻度](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

この **[!UICONTROL IP Frequency]** フレームは、各 IP に対するステータス（「MISS」および「PASS」）を [!DNL Fastly] ログ。 これらのステータスの Web リクエストは、元のサーバーに到達し、サーバーに読み込みが追加されます。 頻度の上位 20 件のアドレスが表示されます。 このフレームは、Web サイト上の IP 攻撃や大量の負荷の発生元を検出するために使用できます。 このグラフは「概要」タブにも表示され、詳細を [!DNL Fastly] このタブに表示されるログ情報。
