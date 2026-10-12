---
title: サービス設定パスのリファレンス
description: Adobe Commerce管理者設定のサービス設定パスと値について説明します。 Web API、OAuth、サービス統合設定オプションについて説明します。
feature: Configuration, Services
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
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
source-wordcount: '171'
ht-degree: 0%
---
# サービス設定パスのリファレンス

このセクションでは、管理者の&#x200B;**ストア**/設定/**構成**/**サービス**&#x200B;のオプションで使用できる変数名と構成パスを示します。

[`magento app:config:dump` コマンド ](../cli/export-configuration.md)は、これらの値をソース コントロールにある共有設定ファイル `app/etc/config.php`に書き込みます。 任意の構成設定を上書きする方法や、機密設定を設定する方法については、[環境変数を使用して構成設定を上書きする](override-config-settings.md#environment-variables)を参照してください。 このトピックでは、_not_&#x200B;に[機密値とシステム固有の値](config-reference-sens.md)が一覧表示されています。

## Commerce Web API パス

これらの設定値は、**Stores**/設定/**Configuration**/**Services**/**Web API**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| デフォルトの応答文字セット | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 匿名ゲスト アクセスを許可 | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## OAuth パス

これらの設定値は、**Stores**/設定/**Configuration**/**Services**/**OAuth**&#x200B;の管理者で使用できます。

| 名前 | 設定パス | Commerceだけ？ |
|--------------|--------------|--------------|
| 顧客トークンの有効期間（時間） | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 管理者トークンの有効期間（時間） | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| クリーンアップの可能性 | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効期限 | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| 有効期限 | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth コンシューマー資格情報HTTP Post マックスリダイレクト | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| OAuth コンシューマー資格情報HTTP投稿タイムアウト | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
