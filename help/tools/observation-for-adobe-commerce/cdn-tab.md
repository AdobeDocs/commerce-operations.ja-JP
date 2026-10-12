---
title: 「[!UICONTROL CDN]」タブ
description: '[!DNL Observation for Adobe Commerce]の「[!UICONTROL CDN]」タブについて説明します。'
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%
---
# 「[!UICONTROL CDN]」タブ

このタブには、[!DNL content delivery network (CDN)]に焦点を当てた情報があります。 Adobe Commerce Cloudの場合、これは[!DNL Fastly] サービスです。

## [!UICONTROL HIT rate]

![&#x200B; ヒット率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

**[!UICONTROL HIT rate]** フレームには、最後の1分間に[!UICONTROL HITS]に至ったキャッシュ可能なリクエストの数が表示されます。 これは、キャッシュが成功したことを示します。 右側の矢印は、1週間前の同じ時間に上下の割合を示します。

## [!UICONTROL HIT Processing]

![&#x200B; ヒット処理](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

この&#x200B;**[!UICONTROL HIT processing]** ボックスには、1週間に[!UICONTROL HITS]が発生したキャッシュ可能なリクエストの数が表示されます。

## [!UICONTROL MISS rate]

![失敗率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

この&#x200B;**[!UICONTROL MISS rate]** ボックスには、最後の1分間にキャッシュ可能な要求が失敗した回数が表示されます。 失敗とは、リクエストがキャッシュされないときに、コンテンツを提供するためにリクエストをオリジンサーバーに渡す必要がある場合です。 右の値は、1週間前の1分あたりの分数の増減の比較です。

## [!UICONTROL MISS time]

![時間を逃す](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![&#x200B; ヒット率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![&#x200B; エラー率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

**[!UICONTROL Error Percentage]** ボックスには、リクエストのERROR パーセンテージの値が表示され、1週間前の同じ時間と比較した相対的な増減が表示されます。

## [!UICONTROL Total Requests]

![&#x200B; リクエストの合計数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![&#x200B; エラー率](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![選択した期間のFastly キャッシュの平均応答時間（秒） &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

このフレームは、キャッシュ可能なリクエストの期間を秒単位で示します。つまり、`cache_response`が[!UICONTROL MISS]の場合、選択した時間のキャッシュされた応答が欠落した場合の平均が表示されます。

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![選択した期間のFastly キャッシュの平均応答時間（POPによってファセットされる秒単位） &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

このコンテキストの&#x200B;*POP*&#x200B;は、キャッシュ ストレージのプールとして機能するように構成されたPOP （Point of Presence）を指します。 [&#x200B; プレゼンスのポイント &#x200B;](https://developer.fastly.com/learning/concepts/pop/)を参照してください。

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

選択した時間枠内の![合計帯域幅（すべてのPOP）、1週間前と比較（%増加/減少） &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![&#x200B; リクエスト – 選択した時間枠から1週間前と比較](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

このフレームは、上部の[!UICONTROL Total Requests]の概要ボックスと似ていますが、前週のリクエスト数が表示されます。 これらは、キャッシュ可能なリクエストだけでなく、すべてのリクエストです（`is_cacheable`がtrueの場合）。

## [!UICONTROL Response Count]

![回答数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![POPによる帯域幅](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![上位5つのURL （5xxまたは3xx ステータスコード） &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

**[!UICONTROL Top 5 URLs]** ビューには、5xxまたは3xx エラー応答が発生しているURLの上位5件が表示されます。 スペース制約のため、URLにマウスポインターを置いて、そのURLに関連付けられている特定のエラーコードを確認する必要があります。 （上の図の赤いボックスの例）。

## [!UICONTROL Top 25 URLs (200 status)]

![上位25個のURL （200 ステータス） &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

**[!UICONTROL Top 25 URLs]** フレームには、選択した期間にカウント別に200 ステータスを返したURLが表示されます。

## [!UICONTROL Duration by Response Status]

![応答状態による期間](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

**[!UICONTROL Duration by Response Status]** グラフには、選択した期間のエラー応答がカウント別に表示されます。エラーステータスコードがファセットになっています。

## [!UICONTROL Duration by Response Status, top 25 urls]

![応答状態による期間、上位25個のURL](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

**[!UICONTROL Duration by Response Status, top 25 URLs]** グラフには、応答時間を秒単位で示す上位25個のURLが表示されます。 パス全体を表示するには、URLにマウスを合わせる必要がある場合があります。 また、1つのURLを除くすべてを削除するには、そのURLをクリックします。 その後、他のURLを個別にクリックして戻すことができます。 個々のURLを削除する場合は、キーを押しながら各URLをクリックして、グラフから削除できます。

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![応答状況別の期間、200件以外の上位25件](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

**[!UICONTROL Duration by Response Status, top 25 non-200 status]** グラフは、200以外のステータスコードまたはエラーステータスコードに焦点を当てていることを除けば、最後のグラフと似ています。 エラーコードとURLが表示されます。 パス全体を表示するには、URLにマウスを合わせる必要がある場合があります。 また、1つのURLを除くすべてを削除するには、そのURLをクリックします。 その後、他のURLを個別にクリックして戻すことができます。 個々のURLを削除する場合は、キーを押しながら各URLをクリックして、グラフから削除できます。

## [!UICONTROL Error Count by POP timeline]

POP タイムライン別![&#x200B; エラー数](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

**[!UICONTROL Error Count by POP timeline]** グラフには、選択した時間枠タイムラインに沿ったエラーステータスのカウントが、エラーコードによってファセットされて表示されます。

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![応答状態、上位25 クライアント IP、非200 ステータス &#x200B;](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)による期間

**[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** グラフには、選択した時間枠でステータスエラーコードが発生した場合の平均期間によるIP アドレスが表示されます。

## [!UICONTROL IP Frequency]

![IP頻度](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

**[!UICONTROL IP Frequency]** フレームは、[!DNL Fastly] ログから各IPの（&#39;MISS&#39;および&#39;PASS&#39;） ステータスをカウントします。 これらのステータスを持つweb リクエストは、オリジンサーバーに到達し、サーバーにロードを追加します。 上位20個のアドレスが頻度で表示されます。 このフレームは、web サイト上のIP攻撃や負荷の高いソースを検出するために使用できます。 このグラフは概要タブにも表示され、このタブに表示される[!DNL Fastly] ログ情報の詳細を簡単に比較するためにここに配置されます。
