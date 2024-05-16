---
title: Adobe CommerceとAdobe Experience Manager インフラストラクチャの連携
description: Adobe CommerceとAdobe Experience Manager インフラストラクチャを調整して、許容できるタイムアウトと接続制限を設定します。
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# インフラストラクチャの調整（タイムアウトと接続制限）

AEMとAdobe Commerce、およびロードバランサーなどの周囲のインフラストラクチャには、連携が必要な設定があります。これらは、接続の制限とタイムアウトの設定に関連しています。

これらの制限の不一致は、接続がAEM側でスロットルされる可能性がある一方で、Adobe Commerceはより多くの接続を処理できる可能性があることを意味します。 同様に、タイムアウト設定では、Adobe Commerceがリクエストを処理中の間に、AEM側でタイムアウトエラーが発生する可能性があります。

タイムアウト設定については、読み込み中に 503 タイムアウトエラーが表示されないように、設定を確認し調整する必要があります。 確認が必要なインフラストラクチャとアプリケーションのタイムアウト設定がいくつかあります。

![AEMのタイムアウトと接続制限を説明する番号付き図](../assets/commerce-at-scale/timeout-settings.svg)

## AEM ロードバランサー

インフラストラクチャに 1 つのAWS アプリケーションのロードバランサーと複数の Dispatcher/パブリッシャーがある場合、ロードバランサーの次の設定を考慮する必要があります。

1. パブリッシャーヘルスチェックを確認して、Dispatcher が負荷サージによって不必要に早くサービスを停止するのを防ぐ必要があります。 ロードバランサーヘルスチェックのタイムアウト設定は、パブリッシャーのタイムアウト設定と合わせる必要があります。

   ![AEM ロードバランサーのヘルスチェックを示すスクリーンショット](../assets/commerce-at-scale/health-checks.png)

1. Dispatcher ターゲットグループのスティッキネスを無効にしたり、ラウンドロビンのロードバランシングアルゴリズムを使用したりできます。 これは、AEM固有の機能や、セッションの堅牢性の設定が必要となるAEM ユーザーセッションが使用されていないことを前提としています。 ここでは、ユーザーのログインとセッションの管理は、GraphQLを介したAdobe Commerceでのみ行われることを前提としています。

   ![AEM セッションのスティッキネス属性を示したスクリーンショット](../assets/commerce-at-scale/session-stickiness.png)

1. セッションのスティッキネスを有効にすると、Fastly へのリクエストがキャッシュされない場合があることに注意してください。デフォルトでは、Fastly は Set-Cookies ヘッダーを使用してページをキャッシュしません。 Adobe Commerceは、キャッシュ可能なページ（TTL > 0）でも cookie を設定しますが、デフォルトの Fastly VCL では、Fastly キャッシュを機能させるために、キャッシュ可能なページでこれらの cookie を削除します。 ページがキャッシュされない場合は、使用しているカスタム cookie を確認し、Fastly VCL をアップロードしてサイトを再確認します。

## Dispatcher タイムアウト設定

Dispatcher の「renders」オプションの/timeout で、AEM パブリッシュインスタンスにアクセスするための接続タイムアウトをミリ秒単位で指定します。 これを確認し、タイムアウト設定を処理するために別のロードバランサーが存在する場合は、デフォルト設定の「0」（無限タイムアウト）を使用する必要があります。

インフラストラクチャにロードバランサーがない場合は、代わりに Dispatcher /timeout 設定で、パブリッシャーのGraphQL タイムアウト設定と一致する値を使用して、タイムアウト設定を指定する必要があります。

## 公開者

公開者GraphQLの接続制限とタイムアウト：最初は、Adobe Commerce CIF GraphQL Client Configuration Factory OSGI 設定の最大 HTTP 接続数を、デフォルトの Fastly 最大接続数に設定する必要があります。現在は、200 に設定されています。 AEM ファームに複数のパブリッシャーがある場合でも、制限は、Fastly 設定に一致させて、各パブリッシャーで同じにする必要があります。 これは、関連付けられている Dispatcher がファームから取得されるなど、場合によっては、1 つのパブリッシャーが他のパブリッシャーよりも多くのトラフィックを処理している可能性があるためです。 つまり、すべてのトラフィックは、残りの単一の Dispatcher とパブリッシャーを通じてルーティングされます。この場合、単一のパブリッシャーは、すべての HTTP 接続を必要とする可能性があります。

「デフォルトの HTTP メソッド」は、POSTからGETに設定する必要があります。 GETリクエストのみがAdobe Commerce GraphQLのキャッシュにキャッシュされるので、デフォルトのメソッドは常にGETに設定する必要があります。

http 接続タイムアウトと http ソケットタイムアウトは、Fastly タイムアウトに一致する値に設定する必要があります。

次の画像は、Magento CIF GraphQL Client Configuration Factory を示しています。 ここに示す設定は例にすぎず、ケースバイケースで調整する必要があります。

![Commerce integration framework設定のスクリーンショット](../assets/commerce-at-scale/cif-config.png)

次の画像は、Fastly バックエンド設定を示しています。 ここに示す設定は例にすぎず、ケースバイケースで調整する必要があります。

![Fastly のCommerce管理設定のスクリーンショット](../assets/commerce-at-scale/cif-config-advanced.png)
