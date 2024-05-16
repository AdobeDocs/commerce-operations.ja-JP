---
title: この [!UICONTROL bots] タブ
description: について説明します [!UICONTROL bots] タブ / [!DNL Observation for Adobe Commerce].
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1905'
ht-degree: 0%

---

# この [!UICONTROL bots] タブ

このタブには、かどうかを識別する方法と識別方法に関する情報があります [!DNL bots] サイトの問題を引き起こしている。

## の概要 [!DNL bots]:

* A [!DNL bot] は、自動化されたタスクを繰り返し実行するソフトウェアです。 人工知能と機械学習の進化により、のタスク、方法、インタラクションを最適化 [!DNL bots] が変更されます。 次のものがあります *良好* [!DNL bots] これは、サイトをクロールしてインターネット検索エンジンに追加することで、サイトにメリットを与えます。 その結果、インターネットユーザーは検索エンジンの結果を通じてサイトに誘導されます。 A *良好* [!DNL bot] 通常、上に配置された境界を尊重します [!DNL bot] 基準： `robots.txt` 検索エンジン コンソールのファイルまたは設定。 境界は、サイトまたはサイトの一部へのアクセスを制限できます。
* 悪意のある [!DNL bots] 無視： `robots.txt` ファイルまたは彼らは良いをスプーフィングする可能性があります [!DNL bot] HTTP リクエストデータのリクエストユーザーエージェントフィールドを介して。 悪意のあることをいくつか [!DNL bots] 実行：
   * サイトに負荷を追加して、サイトへの正規のユーザーのアクセスを拒否します。
   * 許可なくコンテンツを削除して再利用します。
   * 偽のアカウントを登録してメールサービスやアドレスを氾濫させるか、他のサイトにリダイレクトさせる（[!DNL SPAM bots]）に設定します。
   * フェイクビューを作成（[!DNL Viewbots]）に設定します。
   * 商品やチケットを購入（[!DNL Focused bots]）に設定します。
* 管理 [!DNL bots]
   * [!DNL Observation for Adobe Commerce] 次のビューがあります [!DNL bot] トラフィック：
      * キャッシュされていない値の合計が表示されます [!DNL bot] という負荷を表示するアクティビティ [!DNL bot] がサイトに追加され、その読み込みが行われているタイミング。
      * 次の項目が表示されます [!DNL bots] でエラーが発生しています。 通常、次の場合： [!DNL bot] 読み込みを追加するとサイトの問題が発生する [!DNL bot] または IP アドレスはエラーの頻度が最も高くなります。
      * それが示すのは [!DNL bot] の名前（リクエストユーザーエージェントフィールドの値）と、以下で管理する IP アドレス。
         * [!DNL Fastly] （レート制限または [!DNL VCLs] ブロックする IP アドレス、範囲、または [!DNL bots] （名前の値）。
         * 良いものを追加 [!DNL bot] の情報 `robots.txt field` サイトアクセス率を制限または制限するため。
         * 管理 [!DNL Bing] または [!DNL Google bots] 検索エンジンコンソールから。

## [!UICONTROL Experimental Potential Malicious Bots frame]

![潜在的な潜在的な悪意のあるボットフレーム](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame-new.jpg)

この **[!UICONTROL Experimental Potential Malicious Bots frame]** フレームは、12 個の個別の複雑なクエリで実行されます。 悪意のある IP リクエストのシグネチャを検出し、結果を集計し、合計して、降順でカウント別に並べ替えます。 クエリには、CVE の悪用やその他の悪意のあるリクエストの多数のデータ署名が含まれています。 悪用がセキュリティ修正/パッチによってブロックされ、サイトに対する脅威ではない場合でも、リクエストは Web サイトで処理する必要があります。 リクエストの量は、短期間にかなり多くなる可能性があります。 このフレームには、IP アドレスからのリクエストの合計ではなく、リクエストに疑わしい意図があることを示すシグナルを持つリクエストが表示されます。

トラフィックが疑わしく、発信元が [!DNL Content Distributed Network] （CDN）有効なリクエストを配信している可能性のあるアドレス。 リクエストが CDN IP アドレスからのものであると判断した場合は、そのサービスの提供者に連絡して、ネットワークを通過する疑わしいトラフィックをブロックするように依頼してください。 アドレスまたはリクエスト URL をブロックする必要がある場合は、を参照してください。 [Adobe Commerceの悪意のあるトラフィックをブロックする [!DNL Fastly] レベル](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html) （Adobe Commerce サポートナレッジベース）。

## [!UICONTROL Rate of HTTP request per second (top 25) during requested time period]

![リクエストされた期間中の 1 秒あたりの HTTP リクエストの割合（上位 25）](../../assets/tools/observation-for-adobe-commerce/rate-of-http-request-per-second.jpg)

この **[!UICONTROL Rate of HTTP request per second (top 25) during requested time period]** フレームには、選択した時間枠における 1 秒あたりの IP アドレスあたりの最大リクエスト数が表示されます。 これらのアドレスが上記の表にも含まれている場合は、CDN アドレスや悪意がないことを確認し、を介してブロックします [!DNL Fastly].

## [!UICONTROL Total Bot traffic by bot name]:

![選択した期間におけるボット名別のボットトラフィックの合計：](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

この **[!UICONTROL Total Bot traffic by bot name during selected time period]** テーブルには、キャッシュされていない要求の集計数が含まれています。この集計数は、 [!UICONTROL request_user_agent] フィールドの文字列はです [!DNL bots] 値で。 このは、名前の場合とない場合があります [!DNL bot] as the [!UICONTROL request_user_agent] フィールド値はスプーフィングできます。 の下の値 [!UICONTROL Count] 列が最も重要です。

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![選択した期間中のボット名/IP アドレス別のボットトラフィックの合計 Fastly レベルでボットトラフィックをブロックする方法、または robots.txt ファイルを使用してボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

この **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** table には、前のテーブルと同じデータが表示されますが、指定したに代わってリクエストを行う IP アドレスが追加されます [!DNL bot]. 悪意あり [!DNL bots] スプーフィングの良さ [!DNL bots]の場合、不正な IP アドレスを識別する web サイトを通じて、または次を通じて、IP アドレスを検証する必要があります *whois* サービスまたは [!DNL DNS lookups]. 例： [!DNL Google] を次の項目を公開 [[!DNL googlebot] IP アドレス](https://developers.google.com/search/apis/ipranges/googlebot.json) および [!DNL Microsoft] の検証ツールがあります [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors]

![グラフ – 選択した期間に HTTP ステータスエラーが発生したボット Fastly レベルでボットトラフィックをブロックする方法、または robots.txt ファイルを使用してボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

この **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** グラフに次のエラーを表示 [!DNL bots] 「ユーザーエージェントをリクエスト」フィールドで自身を宣言する。 これは、エラーが AEM のボリュームによって引き起こされるとは限りません [!DNL bot] またはその他のトラフィック。 エラーは、次のようになります。 [!DNL bot] が存在しない情報を要求しているか、要求に別の問題があります。

サイトの不安定または停止中に IP アドレスでエラーのスパイクが発生した場合は、サイトの問題の疑いがある可能性があります。

## [!UICONTROL Table - IPs that do not identify as bots]

![表 – 選択した期間に HTTP ステータスエラーのあるボットとして識別されない IP Fastly レベルでボットトラフィックをブロックする方法、または robots.txt ファイルを使用してボットを管理する方法Adobe Commerce robots.txt のベストプラクティス ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

この **[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** テーブルには、として自己識別されない 200 以外の HTTP ステータスコードを持つ IP リクエストが表示されます [!DNL bots] 「ユーザーエージェントをリクエスト」フィールドで指定します。 特に、選択した期間にカウントが多い場合、これらの IP アドレスは悪意のある IP アドレスである可能性があります。

200 以外の HTTP ステータスコードの数が少なく、IP アドレスの範囲が似ていない場合、アドレスがサイトの問題に貢献していない可能性があります。

## [!UICONTROL Table – Cache Status 'ERROR']

![テーブル – キャッシュステータス「エラー」詳細テーブル（これらの IP で何が行われているか） Fastly レベルでボットトラフィックをブロックする方法、または robots.txt ファイルを使用してボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

IP アドレスで頻繁にエラーが発生する場合は、何をしているのかを問い合わせます。 この **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** テーブルには、リクエストされた URL と、キャッシュステータスを持つリクエストの HTTP ステータス値が表示されます [!UICONTROL ERROR] の値。 頻度は URL でファセット化されるので、カウントが少ない場合があります。 選択した期間に、IP アドレスが何千ものリクエストを行う可能性があることに注意してください。 これは、期間中の最大 2000 件のリクエストに対する表示です（レコードの表示制限）。

## [!UICONTROL Show 5XX status distribution]

![IP アドレス間の 5XX ステータス分布を表示する（上位 200 アドレス） Fastly レベルでボットトラフィックをブロックする方法、または robots.txt ファイルを使用してボットを管理する方法Adobe Commerce robots.txt のベストプラクティス ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

この **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** フレームは強力です。 選択した期間の 5XX HTTP ステータスコードを持つ IP アドレスが表示されます。 IP アドレスが大量のリクエストを行い、トラフィックを処理できないほどサイトに影響が及ぶ場合、通常、リクエストの頻度が最も高い IP アドレスのエラーは最も高くなります。 5XX の http ステータスコードは、通常、リクエストに応答するのが困難なサイトを示します。

バーが広いほど、その期間中の合計 5xx エラー数のうち、IP アドレスに含まれるエラーの割合が大きくなります。 メモ：複数の http ステータスコード（例：502 および 503 http ステータス）がある場合、1 つの IP アドレスにグラフ内の複数のセグメントが含まれる可能性があります。

標準的な分布は、IP アドレスの幅が等しいバーの右側に示されるか、カウントが非常に少ない幅の広いバーがいくつかあります。

棒グラフのセグメントの上にマウスポインターを置くと、選択した期間における示されたエラーの数が表示されます。

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![選択した期間中の IP キャッシュステータス（MISS、PASS、ERROR）と HTTP ステータス Fastly でボットトラフィックをブロックする方法、または robots.txt ファイルを通じてボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

この **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** フレームには、選択した期間の HTTPS ステータスコード数と、IP ごとのキャッシュされていないリクエストが表示されます。 これは、各 IP アドレスからの比例負荷とボリュームの合計を示します。 リクエスト数が最も多い IP アドレスが表示されます。

## [!UICONTROL Fastly Cache Summary for selected time period]

![選択した期間の Fastly キャッシュサマリ](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

をクリックした場合 [!UICONTROL Error] アイコン下のグラフでは、最後の 2 つのグラフを比較できます。 これは、負荷がサイトの問題の原因となっている場所を示すのに役立ちます。

![Fastly エラーチェック](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![選択した期間にエラーなくボットとして識別されない IP Fastly レベルでボットトラフィックをブロックする方法、または robots.txt ファイルを使用してボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

この **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** フレームは、リクエストユーザーエージェントフィールド、IP アドレス、およびリクエストのステータスコードを示します。リクエストユーザーエージェントフィールドには、 [!DNL bot]. このフレームには、任意の IP アドレスからの高頻度のリクエストが表示される場合がありますが、特にサイトで問題が発生する可能性がある期間は、高頻度のリクエストに注意が払われます。

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![選択した期間の疑わしい非ボットトラフィック](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

この **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** graph は Go-http-client のリクエストユーザーエージェント値を探しますが、他の疑わしいリクエストユーザーエージェント値を調べるために拡張されます。 この要求ユーザーエージェントの値は、サイトがサービスから接続するために使用します。この値は有効である可能性がありますが、悪意のあるユーザーも使用しています [!DNL bots].

## [!UICONTROL Graph - Bot traffic by Bot name]

![グラフ – 選択した期間のボット名によるボットトラフィック）](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

この **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** フレームには、以下によるボットトラフィックの合計と同じデータが表示されます [!DNL Bot] タブの上部にある「選択した期間の名前」テーブル。 でリクエストを確認できるように、タイムライン経由でデータを表示しています。 [!DNL bots] 作成され、その配布が行われています。

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![選択した期間中のトップ 250 のボット名と IP アドレス Fastly レベルでボットトラフィックをブロックする方法、または robots.txt ファイルを使用してボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

この **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** フレームに合計と同じデータが表示される [!DNL Bot] タブ上部の選択した期間テーブル中のボット名/IP アドレス別のトラフィック。 タイムラインを介してデータを表示し、IP アドレスでファセット化しています。 これは、によるリクエストが [!DNL bots] 作成され、どの IP がリクエストを行い、リクエストの配布をおこないます。

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![選択した期間中にブロックされたボット名/ IP アドレス（Fastly 内）。 このグラフには、403 Forbidden HTTP ステータスコードが返されたボットトラフィックと IP が表示されます](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

この **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** フレームは、ブロックされているボット名と IP アドレスを示します。 このグラフは、ですべてのリクエストがブロックされていることを示しています [!DNL Fastly] 先に進む。

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![選択した期間でブロックされた非ボット名/ IP アドレス（Fastly 内）。 このグラフは、403 Forbidden HTTP ステータスコードが返された非ボットトラフィックと IP を表示します ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

この **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** フレームは、を識別しない IP アドレスを示します。 [!DNL bot] ブロックされた [!DNL Fastly].

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![次の表に、IP アドレスごとのユーザーエージェント数、成功、失敗およびブロックされたリクエストの数を示します。](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

悪意のある [!DNL bots] しばしば他の人をスプーフィングする [!DNL bots] の値によって [!UICONTROL Request User Agent] フィールド。 次の表は、そのフィールドの IP アドレスに含まれる一意の値の数を示しています。 値が大きいほど [!UICONTROL Request User Agent] フィールドに入力すると、IP アドレスの疑いが強くなります。

## [!UICONTROL IP with non-200 status errors]

![非 200 ステータスエラーの IP - 403 ステータスなし](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

この **[!UICONTROL IP with non-200 status errors – without 403 status]** フレームは、HTTP ステータスコードが 200 以外の IP アドレスについて、選択した期間の配信を表示します。 1 つの IP アドレスまたは IP アドレスのグループで値が大きい場合は、さらに調査する必要があります。

## [!UICONTROL IP with 403 status codes:]

![403 ステータスコードの IP:](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

この **[!UICONTROL IP with 403 status codes]** フレームに、キャッシュされていないリクエストが表示される（ない） [!UICONTROL cache_status=ERROR] の HTTP ステータスが 403 である。 これは、オリジンサーバーが次の場所からのブロックではなく、403 （未認証）のソースであることを示している場合があります [!DNL Fastly].

## [!UICONTROL Top 5 with non-200 status codes]

![cache_status を示す非 200 ステータスコードを持つ上位 5 件：](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

この **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** テーブルは、を含んだ各ののカウントを IP/ステータスレベルで表示します [!UICONTROL cache_status] の値。

## [!UICONTROL Pageview Latency will show as spikes]

![ページビューの待ち時間は、このグラフにスパイクとして表示されます。](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

この **[!UICONTROL Pageview Latency will show as spikes on this graph:]** フレームは、に沿ったページ読み込み/API 応答待ち時間を示します。 [!DNL bot] トラフィック。
