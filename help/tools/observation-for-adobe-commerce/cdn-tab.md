---
title: 「[!UICONTROL CDN]」タブ
description: '[!UICONTROL CDN] の「 [!DNL Observation for Adobe Commerce]」タブについて説明します。'
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e753528a1d74eda0a1393e2cc455f33f529db739
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# 「[!UICONTROL CDN]」タブ

このタブには、[!DNL content delivery network (CDN)] に焦点を当てた情報があります。 Adobe Commerce Cloud の場合、これは [!DNL Fastly] サービスです。

## [!UICONTROL HIT rate]

![ ヒット率 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

**[!UICONTROL HIT rate]** フレームには、直前の [!UICONTROL HITS] ラーにつながったキャッシュ可能なリクエストの数が表示されます。 これは、キャッシュが成功したことを示します。 右側の矢印は、1 週間前の同じ時刻を上下に表す割合を示します。

## [!UICONTROL HIT Processing]

![ ヒットの処理 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

この **[!UICONTROL HIT processing]** ボックスには、1 週間に [!UICONTROL HITS] ストが発生したキャッシュ可能なリクエストの数が表示されます。

## [!UICONTROL MISS rate]

![ ミスレート ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

この **[!UICONTROL MISS rate]** ボックスには、最後の 1 分間にキャッシュ可能なリクエストが失敗した回数が表示されます。 ミスとは、リクエストがキャッシュされておらず、コンテンツを提供するためにリクエストをオリジンサーバーに渡す必要がある場合です。 右側の値は、1 週間前の 1 分あたりの分数と増減の比較です。

## [!UICONTROL MISS time]

![ ミスタイム ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![ ヒット率 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![ エラーの割合 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

**[!UICONTROL Error Percentage]** のボックスには、リクエストのエラー率の値と、1 週間前の同じ時刻と比較した相対的な増減が表示されます。

## [!UICONTROL Total Requests]

![ 合計要求数 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![ エラー率 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![ 選択した期間の Fastly キャッシュの平均応答（秒） ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

このフレームは、キャッシュ可能なリクエストの期間を秒単位で表示します。つまり、`cache_response` が [!UICONTROL MISS] の場合は、選択した時間にキャッシュされた応答が欠落している平均が表示されます。

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![POP がファセットした、選択された期間の Fastly キャッシュ平均応答（秒） ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

*POP* とは、このコンテキストでは、キャッシュストレージのプールとして機能するように設定された POP （Point of Presence）を指します。 [ プレゼンスポイント ](https://developer.fastly.com/learning/concepts/pop/) を参照してください。

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![1 週間前と比較した、選択した期間の合計帯域幅（すべての POP） （% の増加/減少） ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![ リクエスト – 選択した時間枠を 1 週間前と比較した結果 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

このフレームは、上部の [!UICONTROL Total Requests] の概要ボックスに似ていますが、前の週のリクエスト数を表示します。 これらは、キャッシュ可能なリクエスト（`is_cacheable` が true の場合）だけでなく、すべてのリクエストです。

## [!UICONTROL Response Count]

![ 応答数 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![POP による帯域幅 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![ 上位 5 件の URL （5xx または 3xx ステータスコード） ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

**[!UICONTROL Top 5 URLs]** ビューには、5xx または 3xx のエラー応答が発生している上位 5 つの URL が表示されます。 スペースの制約により、URL の上にマウスポインターを置いて、その URL に関連付けられた特定のエラーコードを表示する必要があります。 （上の図の赤いボックスの例）。

## [!UICONTROL Top 25 URLs (200 status)]

![ 上位 25 件の URL （200 ステータス） ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

**[!UICONTROL Top 25 URLs]** のフレームには、選択した期間にカウント別に 200 ステータスを返した URL が表示されます。

## [!UICONTROL Duration by Response Status]

![ 期間（応答ステータス別） ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

**[!UICONTROL Duration by Response Status]** グラフには、選択した期間のエラー応答がカウント別に表示されます。このカウントは、エラーステータスコードで切り替えられます。

## [!UICONTROL Duration by Response Status, top 25 urls]

![ 期間（応答ステータス別、上位 25 件の URL） ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

**[!UICONTROL Duration by Response Status, top 25 URLs]** のグラフには、応答期間別の上位 25 個の URL が秒単位で表示されます。 パス全体を表示するには、URL の上にマウスを置く必要がある場合があります。 また、1 つの URL 以外をすべて削除するには、その URL をクリックします。 その後、他の URL を個別にクリックして、追加し直すことができます。 個々の URL を削除する場合は、キーを押したまま各 URL をクリックすると、グラフから削除できます。

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![ 期間（応答ステータス別）、上位 25 件（200 以外） ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

**[!UICONTROL Duration by Response Status, top 25 non-200 status]** グラフは最後のグラフと似ていますが、フォーカスが 200 以外のステータスコードまたはエラーステータスコードにある点が異なります。 エラーコードと URL が表示されます。 パス全体を表示するには、URL の上にマウスを置く必要がある場合があります。 また、1 つの URL 以外をすべて削除するには、その URL をクリックします。 その後、他の URL を個別にクリックして、追加し直すことができます。 個々の URL を削除する場合は、キーを押したまま各 URL をクリックすると、グラフから削除できます。

## [!UICONTROL Error Count by POP timeline]

![POP タイムライン別のエラー数 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

**[!UICONTROL Error Count by POP timeline]** グラフには、選択した期間タイムラインに沿ったエラーステータスの数が、エラーコードでファセットされて表示されます。

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![ 応答ステータス、上位 25 件のクライアント IP、非 200 ステータス別の期間 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

**[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** のグラフは、ステータスエラーコードが存在した場合に、選択した時間枠での平均期間別に IP アドレスを表示します。

## [!UICONTROL IP Frequency]

![IP 周波数 ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

**[!UICONTROL IP Frequency]** フレームは、[!DNL Fastly] ログから各 IP の（「MISS」および「PASS」）ステータスをカウントします。 これらのステータスを持つ web リクエストは、接触チャネルサーバーに到達し、サーバーに負荷を追加します。 これは、頻度の上位 20 件のアドレスを表示します。 このフレームは、Web サイトに対する IP 攻撃や高負荷のソースを検出するために使用できます。 このグラフは「概要」タブにも表示され、このタブに表示される [!DNL Fastly] ログ情報の詳細と簡単に比較できるように、ここに配置されています。
