---
title: クリックジャッキング攻撃の防止
description: 「X-Frame-Options」ヘッダーを使用してページのレンダリングを制御することで、クリックジャッキング攻撃を防ぎます。
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# クリックジャッキング攻撃の防止

ストアフロントへのリクエストに [X-Frame-Options](https://owasp.org/www-community/attacks/Clickjacking) HTTP リクエストヘッダーを含めることで、[ クリックジャッキング ](https://datatracker.ietf.org/doc/html/rfc7034) による悪用を防ぐことができます。

`X-Frame-Options` ヘッダーを使用すると、ブラウザーでページを `<frame>`、`<iframe>` または `<object>` でレンダリングできるかどうかを次のように指定できます。

- `DENY`: ページをフレーム内に表示することはできません。
- `SAMEORIGIN`:（デフォルト）ページは、ページ自体と同じオリジン上のフレームにのみ表示できます。

>[!WARNING]
>
>Commerceでサポートされているブラウザーがサポートしなくなったため、`ALLOW-FROM <uri>` オプションは非推奨（廃止予定）になりました。 [ ブラウザー互換性 ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility) を参照してください。

>[!WARNING]
>
>セキュリティ上の理由から、AdobeではCommerce ストアフロントをフレーム内で実行しないことを強くお勧めします。

## `X-Frame-Options` の実装

`X-Frame-Options` で `<project-root>/app/etc/env.php` の値を設定します。 デフォルト値は次のように設定されています。

```php
'x-frame-options' => 'SAMEORIGIN',
```

再デプロイして、`env.php` ファイルに対する変更を有効にします。

>[!TIP]
>
>管理者で値を設定するよりも、`env.php` ファイルを編集する方が安全です。

## `X-Frame-Options` の設定を確認してください

設定を検証するには、任意のストアフロントページで HTTP ヘッダーを表示します。 Web ブラウザーインスペクターの使用など、いくつかの方法があります。

次の例では、HTTP プロトコルを使用してCommerce サーバーに接続できる任意のマシンから実行できる curl を使用しています。

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

ヘッダーで `X-Frame-Options` 値を探します。
