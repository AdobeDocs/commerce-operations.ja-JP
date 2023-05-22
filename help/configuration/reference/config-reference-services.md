---
title: サービス設定パスの参照
description: サービス設定値の一覧を参照してください。
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# サービス設定パスの参照

この節では、以下の管理で使用できる変数名と設定パスを示します。 **ストア** /設定/ **設定** > **サービス**.

この [`magento app:config:dump` command](../cli/export-configuration.md) は、これらの値を共有設定ファイルに書き込みます。 `app/etc/config.php`（ソース管理下に置く必要があります） オプションで設定を上書きしたり、機密設定を設定したりするには、 [環境変数を使用して設定を上書きする](override-config-settings.md#environment-variables). このトピックでは、 _not_ リスト [機密性の高いシステム固有の値](config-reference-sens.md).

## Commerce Web API パス

これらの設定値は、 **ストア** /設定/ **設定** > **サービス** > **Web API**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| デフォルトの応答文字セット | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 匿名ゲストによるアクセスを許可 | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth パス

これらの設定値は、 **ストア** /設定/ **設定** > **サービス** > **OAuth**.

| 名前 | 設定パス | コマースのみ？ |
|--------------|--------------|--------------|
| 顧客トークンの有効期間（時間） | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理トークンの有効期間（時間） | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クリーンアップの確率 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効期限 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効期限 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth 消費者資格情報 HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth 消費者資格情報 HTTP Post タイムアウト | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
