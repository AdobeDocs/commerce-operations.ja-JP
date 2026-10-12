---
title: クリックジャッキングの悪用を防ぐ
description: 「X-Frame-Options」ヘッダーを使用してページレンダリングを制御し、クリックジャッキングの悪用を防止します。
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
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
source-wordcount: '234'
ht-degree: 0%
---
# クリックジャッキングの悪用を防ぐ

[X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) HTTP リクエストヘッダーをストアフロントへのリクエストに含めることで、[&#x200B; クリックジャッキング &#x200B;](https://owasp.org/www-community/attacks/Clickjacking)の不正利用を防止します。

`X-Frame-Options` ヘッダーを使用すると、ブラウザーが`<frame>`、`<iframe>`、または`<object>`でページをレンダリングできるかどうかを次のように指定できます。

- `DENY`: ページをフレーム内に表示できません。
- `SAMEORIGIN`: （デフォルト） ページは、ページ自体と同じオリジンのフレーム内でのみ表示できます。

>[!WARNING]
>
>Commerceでサポートされているブラウザーではサポートされなくなったため、`ALLOW-FROM <uri>` オプションは廃止されました。 [&#x200B; ブラウザーの互換性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility)を参照してください。

>[!WARNING]
>
>セキュリティ上の理由から、Adobeでは、Commerce ストアフロントをフレーム内で実行しないことを強くお勧めします。

## `X-Frame-Options`を実装

`<project-root>/app/etc/env.php`に`X-Frame-Options`の値を設定します。 デフォルト値は次のように設定されます。

```php
'x-frame-options' => 'SAMEORIGIN',
```

`env.php` ファイルの変更を有効にするには、再デプロイします。

>[!TIP]
>
>`env.php` ファイルを編集する方が、管理者で値を設定するよりも安全です。

## `X-Frame-Options`の設定を確認してください

設定を確認するには、任意のストアフロントページでHTTP ヘッダーを表示します。 これには、web ブラウザーインスペクターの使用など、いくつかの方法があります。

次の例では、HTTP プロトコルを介してCommerce サーバーに接続できる任意のマシンから実行できるcurlを使用しています。

```shell
curl -I -v --location-trusted '<storefront-URL>'
```

ヘッダーで`X-Frame-Options`値を探します。
