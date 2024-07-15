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

この節では、**ストア**/設定/**設定**/**サービス** の管理でオプションに使用できる変数名と設定パスを示します。

[`magento app:config:dump` コマンドは ](../cli/export-configuration.md) これらの値をソース管理にある共有構成ファイル `app/etc/config.php` に書き込みます。 任意の構成設定を上書きしたり、重要な設定を指定したりするには、[ 環境変数を使用して構成設定を上書き ](override-config-settings.md#environment-variables) を参照してください。 このトピックでは _機密の値とシステム固有の値 [ は_ 表示されません ](config-reference-sens.md)。

## Commerce Web API のパス

これらの設定値は、管理者の **ストア**/設定/**設定**/**サービス**/**Web API** で利用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| デフォルトの応答文字セット | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 匿名ゲスト アクセスを許可する | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth パス

これらの設定値は、管理者の **ストア**/設定/**設定**/**サービス**/**OAuth** で使用できます。

| 名前 | 設定パス | Commerceのみ？ |
|--------------|--------------|--------------|
| 顧客トークンの有効期間（時間） | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理トークンの有効期間（時間） | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クリーンアップ確率 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効期限 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効期限 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth コンシューマー資格情報 HTTP Post maxredirectors | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth コンシューマー資格情報 HTTP Post タイムアウト | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
