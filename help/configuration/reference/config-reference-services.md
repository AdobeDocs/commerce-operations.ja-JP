---
title: サービス設定パスのリファレンス
description: Adobe Commerce Admin Settings のサービス設定パスと値について説明します。 Web API、OAuth、サービス統合設定のオプションについて説明します。
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# サービス設定パスのリファレンス

この節では、**ストア**/設定/**設定**/**サービス** の管理でオプションに使用できる変数名と設定パスを示します。

[`magento app:config:dump` コマンドは &#x200B;](../cli/export-configuration.md) これらの値をソース管理にある共有構成ファイル `app/etc/config.php` に書き込みます。 任意の構成設定を上書きしたり、重要な設定を指定したりするには、[&#x200B; 環境変数を使用して構成設定を上書き &#x200B;](override-config-settings.md#environment-variables) を参照してください。 このトピックでは _機密の値とシステム固有の値_ は [&#x200B; 表示されません &#x200B;](config-reference-sens.md)。

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
| OAuth コンシューマー資格情報 HTTP ポスト maxredirectors | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth コンシューマー資格情報 HTTP POST タイムアウト | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
