---
title: サービス設定パスのリファレンス
description: サービス設定値のリストを参照してください。
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# サービス設定パスのリファレンス

この節では、の管理画面でオプションに使用できる変数名と設定パスを示します。 **ストア** > 設定 > **設定** > **サービス**.

この [`magento app:config:dump` コマンド](../cli/export-configuration.md) これらの値を共有構成ファイルに書き込みます。 `app/etc/config.php`（ソース管理にする必要があります）。 必要に応じて設定を上書きしたり、重要な設定を指定するには、を参照してください。 [環境変数を使用して設定を上書きする](override-config-settings.md#environment-variables). このトピックでは、 _ではない_ list [機密性の高いシステム固有の値](config-reference-sens.md).

## Commerce Web API のパス

これらの設定値は、の管理者で使用できます。 **ストア** > 設定 > **設定** > **サービス** > **Web API**.

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| デフォルトの応答文字セット | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 匿名ゲスト アクセスを許可する | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth パス

これらの設定値は、の管理者で使用できます。 **ストア** > 設定 > **設定** > **サービス** > **OAuth**.

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 顧客トークンの有効期間（時間） | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理トークンの有効期間（時間） | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クリーンアップ確率 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効期限 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効期限 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth コンシューマー資格情報 HTTP ポスト maxredirectors | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth コンシューマー資格情報 HTTP POST タイムアウト | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
