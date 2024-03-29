---
title: The [!UICONTROL bots] タブ
description: 詳しくは、 [!UICONTROL bots] タブ [!DNL Observation for Adobe Commerce].
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 0%

---

# The [!UICONTROL bots] タブ

このタブには、どのようにして特定するかを説明する情報が含まれています [!DNL bots] はサイトの問題を引き起こしています。

## 概要 [!DNL bots]:

* A [!DNL bot] は、反復的な自動化タスクを実行するソフトウェアの一部です。 人工知能と機械学習の進化に伴い、 [!DNL bots] 変更中です。 次のものがあります。 *良い* [!DNL bots] これは、サイトをクロールしてインターネット検索エンジンに追加することで利益を得ることができます。 その結果、インターネットユーザーは検索エンジンの結果を通じてサイトに導かれます。 A *良い* [!DNL bot] 通常、に配置された境界を尊重します [!DNL bot] 作成者 `robots.txt` 検索エンジンコンソールのファイルまたは設定。 境界は、サイトまたはサイトのパーツへのアクセスを制限する場合があります。
* 悪意のある [!DNL bots] 無視する `robots.txt` ファイル、または、それらは良い物を偽るかもしれない [!DNL bot] HTTP リクエストデータの request user agent フィールドを使用します。 悪意のあるもの [!DNL bots] 実行：
   * サイトへの正当なユーザーのアクセスを拒否するために、サイトに読み込みを追加します。
   * 許可なくコンテンツを削除して再利用する。
   * 偽アカウントを登録して、大量の電子メールサービスやアドレスを送信したり、他のサイトにリダイレクトしたりします ([!DNL SPAM bots]) をクリックします。
   * 偽のビューを作成 ([!DNL Viewbots]) をクリックします。
   * 製品またはチケットを購入する ([!DNL Focused bots]) をクリックします。
* 管理 [!DNL bots]
   * [!DNL Observation for Adobe Commerce] は、次のビューを持ちます： [!DNL bot] トラフィック：
      * キャッシュされていない合計が表示されます [!DNL bot] 次の項目の負荷を表示するアクティビティ： [!DNL bot] がサイトに追加されていて、その読み込みが発生したとき。
      * これには、 [!DNL bots] エラーを生成しています。 通常、 [!DNL bot] は、サイトの問題を引き起こす負荷を追加しています。 [!DNL bot] または IP アドレスが最も高いエラー頻度を持っています。
      * これで分かる [!DNL bot] 管理する名前（ユーザーエージェントフィールド値のリクエスト）と IP アドレス：
         * [!DNL Fastly] ( レート制限または [!DNL VCLs] IP アドレス、範囲、または [!DNL bots] 名前の値別 )。
         * 良好な追加 [!DNL bot] 情報を `robots.txt field` をクリックして、サイトへのアクセス率を制限または制限します。
         * 管理 [!DNL Bing] または [!DNL Google bots] 検索エンジンコンソールから。

## [!UICONTROL Experimental Potential Malicious Bots frame]

![試行用悪意のあるボットフレーム](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame-new.jpg)

The **[!UICONTROL Experimental Potential Malicious Bots frame]** フレームは、12 個の複雑なクエリを超えて実行されます。 悪意のある IP 要求署名を検出し、その結果を集計し、合計し、降順に並べ替えます。 クエリには、CVE の悪用と他の悪意のある要求の多数のデータ署名が含まれています。 セキュリティの修正やパッチによってブロックされ、サイトに対する脅威でない場合でも、要求は Web サイトで処理する必要があります。 リクエストの量は、短時間でかなり多くなる場合があります。 このフレームには、IP アドレスからの合計リクエスト数は表示されず、リクエストに疑わしい意図があることを示すシグナルを含むリクエスト数が表示されます。

トラフィックが疑わしく、トラフィックが [!DNL Content Distributed Network] (CDN) アドレス。有効なリクエストも配信している可能性があります。 リクエストが CDN IP アドレスからのものであると判断された場合は、そのサービスサプライヤーに連絡して、ネットワークを介した疑わしいトラフィックをブロックしてください。 アドレスまたはリクエスト URL をブロックする必要がある場合は、 [に対するAdobe Commerceの悪意のあるトラフィックをブロックする [!DNL Fastly] レベル](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html) ( Adobe Commerce Support Knowledge Base )。

## [!UICONTROL Rate of HTTP request per second (top 25) during requested time period]

![リクエスト期間中の 1 秒あたりの HTTP リクエストの割合（上位 25 件）](../../assets/tools/observation-for-adobe-commerce/rate-of-http-request-per-second.jpg)

The **[!UICONTROL Rate of HTTP request per second (top 25) during requested time period]** frame は、選択した期間における 1 秒あたりの最大リクエスト数を示します。 これらのアドレスも上記の表にある場合は、CDN アドレスではなく、悪意のあるアドレスであることを確認し、 [!DNL Fastly].

## [!UICONTROL Total Bot traffic by bot name]:

![選択した期間のボット名別の合計ボットトラフィック数：](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

The **[!UICONTROL Total Bot traffic by bot name during selected time period]** テーブルには、キャッシュされていないリクエストの集計数が含まれます。 [!UICONTROL request_user_agent] フィールドに次の文字列が含まれる： [!DNL bots] を値に含めます。 名前の場合とそうでない場合があります [!DNL bot] として [!UICONTROL request_user_agent] フィールド値はスプーフィングできます。 以下の値 [!UICONTROL Count] 列が最も重要です。

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![選択期間中のボット名/IP アドレス別の合計ボットトラフィック Fastly レベルでのボットトラフィックをブロックする方法 robots.txt ファイルでのボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

The **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** テーブルには、前のテーブルと同じデータが表示されますが、IP アドレスが追加され、名前の付いた [!DNL bot]. 悪意のある [!DNL bots] 見せ掛けの良い [!DNL bots]を使用する場合、IP アドレスは、虐待的な IP アドレスを識別する Web サイトまたはを通じて検証する必要があります *whois* サービスまたは [!DNL DNS lookups]. 例： [!DNL Google] を公開 [[!DNL googlebot] IP アドレス](https://developers.google.com/search/apis/ipranges/googlebot.json) および [!DNL Microsoft] ～のための検証ツールを備えている [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors]

![グラフ — 選択した期間中に HTTP ステータスエラーが発生したボット Fastly レベルでのボットトラフィックをブロックする方法 robots.txt ファイルでのボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

The **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** グラフには次のエラーが表示されます： [!DNL bots] は、リクエストユーザーエージェントフィールドで自分自身を宣言します。 これは、必ずしもエラーが、 [!DNL bot] または他のトラフィック。 エラーは、 [!DNL bot] は、存在しない情報やリクエストに別の問題がある情報をリクエストしています。

サイトの不安定性や停止中に IP アドレスにエラーのスパイクが発生した場合、サイトの問題で疑問が生じる可能性があります。

## [!UICONTROL Table - IPs that do not identify as bots]

![表 — 選択した期間に HTTP ステータスエラーでボットとして識別されない IP Fastly レベルでのボットトラフィックのブロック方法または robots.txt ファイルでのボットの管理Adobe Commerce robots.txt のベストプラクティス ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

The **[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** テーブルには、自己識別されない 200 個以外の http ステータスコードを含む IP リクエストが表示されます。 [!DNL bots] 」と入力します。 これらの IP アドレスは、悪意のある IP アドレスである可能性があります。特に、選択した期間に対してカウントが高い場合に使用されます。

200 以外の HTTP ステータスコードのカウントが少なく、IP アドレスの範囲が類似していない場合は、そのアドレスがサイトの問題に影響を与えていない可能性があります。

## [!UICONTROL Table – Cache Status 'ERROR']

![テーブル — キャッシュステータス「ERROR」詳細テーブル（これらの IP は何をしていますか？） Fastly レベルでのボットトラフィックをブロックする方法 robots.txt ファイルを使用したボットを管理するAdobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

IP アドレスが高い頻度でエラーを生成している場合は、何をしているかを確認します。 The **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** この表には、要求された URL と、キャッシュのステータスを持つリクエストの HTTP ステータス値が表示されます [!UICONTROL ERROR] の値です。 頻度は URL でファセットされるので、カウントは少なくなる場合があります。 IP アドレスは、選択された期間中に何千ものリクエストをおこなう可能性があることに注意してください。 これは、期間（レコードの表示制限）内の最大 2,000 件のリクエストに対するビューです。

## [!UICONTROL Show 5XX status distribution]

![IP アドレス間の 5XX ステータスの配分を表示（上位 200 件のアドレス） Fastly レベルでのボットトラフィックをブロックする方法または robots.txt ファイル経由でのボットを管理する方法Adobe Commerce robots.txt のベストプラクティス ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

The **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** フレームは強力です。 選択した期間に 5XX HTTP ステータスコードを持つ IP アドレスが表示されます。 IP アドレスが大量のリクエストを行っていて、サイトがトラフィックを処理できないポイントに影響を受ける場合、通常、リクエストの頻度が最も高い IP アドレスのエラー数は最も多くなります。 5XX http ステータスコードは、通常、要求への応答に苦労しているサイトを示します。

バーが広いほど、その期間の合計 5xx エラー数に IP アドレスのエラーの割合が大きくなります。 注意：複数の http ステータスコード（例：502 および 503 http ステータス）がある場合、1 つの IP アドレスに対してグラフ内の複数のセグメントが存在する可能性があります。

通常の配分は、IP アドレスの幅が等しいバーの右側に示されます。また、幅の広いバーの数が非常に少ないバーも表示されます。

バーセグメントの上にマウスポインターを置くと、選択した期間に示されたエラー数が表示されます。

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![IP キャッシュの状態 (MISS、PASS、ERROR) と http の状態を選択した期間にブロックする方法 Fastly レベルでボットトラフィックをブロックする方法または robots.txt ファイルを通じてボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

この **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** frame は、選択した期間内の IP による HTTPS ステータスコードカウントおよびキャッシュされていないリクエストを表示します。 これは、各 IP アドレスからの比例負荷と合計ボリュームを示します。 IP アドレスが、ほとんどのリクエストで表示されます。

## [!UICONTROL Fastly Cache Summary for selected time period]

![選択した期間の Fastly キャッシュの概要](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

次の項目をクリックした場合、 [!UICONTROL Error] 下のグラフのアイコンで、最後の 2 つのグラフを相互に比較できます。 これは、負荷がサイトの問題に寄与する場所を示すのに役立ちます。

![エラーチェックに失敗しました](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![選択した期間中にエラーのないボットとして識別されない IP Fastly レベルでのボットトラフィックをブロックする方法 robots.txt ファイルでのボットの管理Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

The **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** frame は、リクエストユーザーエージェントフィールド、IP アドレス、およびリクエストユーザーエージェントフィールドが [!DNL bot]. このフレームは、任意の IP アドレスからの高頻度リクエストを表示しますが、高頻度リクエストに注意を払うことができます。特に、サイトで問題が発生する可能性がある期間中です。

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![選択した期間中の疑わしい非ボットトラフィック](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

The **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** グラフは、Go-http-client のリクエストユーザーエージェント値を探しますが、他の疑わしいリクエストユーザーエージェント値を調べるように拡張されます。 この要求ユーザーエージェントの値は、サービスから接続するサイトによって使用され、有効である可能性がありますが、悪意のあるユーザーエージェントによっても使用されます [!DNL bots].

## [!UICONTROL Graph - Bot traffic by Bot name]

![グラフ — 選択した期間のボット名別ボットトラフィック数 )](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

The **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** フレームに、合計ボットトラフィックと同じデータが表示されます ( [!DNL Bot] 「 」タブの上部にある、選択した期間の名前テーブル。 タイムライン経由でデータを表示し、 [!DNL bots] そしてその分布を作っているのだ。

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![上位 250 件のボット名と IP アドレスを選択した期間に Fastly レベルでボットトラフィックをブロックする方法または robots.txt ファイルでボットを管理する方法Adobe Commerce robots.txt のベストプラクティス](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

The **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** フレームが合計と同じデータを表示している [!DNL Bot] 「 」タブの上部にある選択した期間テーブルでのボット名/IP アドレスによるトラフィック。 タイムラインを介してデータを表示し、IP アドレスでファセット化しています。 これは、 [!DNL bots] が作成され、どの IP がリクエストを実行し、リクエストの配布がおこなわれます。

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![ブロックされたボットの名前/IP アドレス (Fastly) が、選択した期間に有効です。 このグラフには、403 Forbidden HTTP Status コードが返されたボットトラフィックと IP が表示されます](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

The **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** frame には、ブロックされているボット名と IP アドレスが表示されます。 このグラフで、すべてのリクエストが [!DNL Fastly] 前に進む。

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![選択した期間中に（Fastly で）非ボット名/ IP アドレスをブロックしました。 このグラフには、403 Forbidden HTTP Status コードが返された非ボットトラフィックと IP が表示されます ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

The **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** frame は、が識別しない IP アドレスを示します [!DNL bot] 通過を妨げられている [!DNL Fastly].

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![次の表は、IP アドレスごとのユーザーエージェントの数、成功したリクエスト数、失敗したリクエスト数、ブロックされたリクエスト数を示しています。](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

悪意のある [!DNL bots] しばしば他人をだます [!DNL bots] の値 [!UICONTROL Request User Agent] フィールドに入力します。 次の表は、その IP アドレスがそのフィールドに持つ一意の値の数を示しています。 値が大きいほど [!UICONTROL Request User Agent] フィールドに設定されている場合、IP アドレスが疑わしくなります。

## [!UICONTROL IP with non-200 status errors]

![非 200 ステータスエラーの IP - 403 ステータスなし](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

The **[!UICONTROL IP with non-200 status errors – without 403 status]** フレームに、200 以外の HTTP ステータスコードを持つ IP アドレスの選択した期間での配分が表示されます。 単一の IP アドレスまたは IP アドレスのグループに高い値が表示される場合は、さらに調査する必要があります。

## [!UICONTROL IP with 403 status codes:]

![ステータスコードが 403 の IP:](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

The **[!UICONTROL IP with 403 status codes]** frame は、キャッシュされていないリクエストを次の条件を満たさないで表示します [!UICONTROL cache_status=ERROR] HTTP ステータスが 403 である。 これは、オリジンサーバーがブロックではなく 403（未認証）のソースであることを示している可能性があります [!DNL Fastly].

## [!UICONTROL Top 5 with non-200 status codes]

![cache_status を示す非 200 のステータスコードの上位 5:](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

The **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** テーブルが IP /ステータスレベルで表示され、 [!UICONTROL cache_status] の値です。

## [!UICONTROL Pageview Latency will show as spikes]

![ページビューの待ち時間は、このグラフにスパイクとして表示されます。](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

The **[!UICONTROL Pageview Latency will show as spikes on this graph:]** frame は、 [!DNL bot] トラフィック。
