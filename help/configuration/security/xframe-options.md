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

防止 [クリックジャッキング](https://owasp.org/www-community/attacks/Clickjacking) を含めることによる悪用 [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) ストアフロントへのリクエストの HTTP リクエストヘッダー。

この `X-Frame-Options` ヘッダーを使用すると、ブラウザーでページをレンダリングできるかどうかを指定できます `<frame>`, `<iframe>`、または `<object>` 次のように設定します。

- `DENY`：ページをフレーム内に表示することはできません。
- `SAMEORIGIN`:（デフォルト）ページは、ページ自体と同じオリジン上のフレーム内にのみ表示できます。

>[!WARNING]
>
>この `ALLOW-FROM <uri>` Commerceでサポートされているブラウザーがサポートしなくなったので、オプションは非推奨（廃止予定）になりました。 参照： [ブラウザーの互換性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>セキュリティ上の理由から、AdobeではCommerce ストアフロントをフレーム内で実行しないことを強くお勧めします。

## 実装方法 `X-Frame-Options`

の値を設定 `X-Frame-Options` 。対象： `<project-root>/app/etc/env.php`. デフォルト値は次のように設定されています。

```php
'x-frame-options' => 'SAMEORIGIN',
```

に変更がある場合は再デプロイ `env.php` ファイルが有効になります。

>[!TIP]
>
>を編集する方がより安全です。 `env.php` ファイルの方が、管理者で値を設定する必要があります。

## の設定を確認します `X-Frame-Options`

設定を検証するには、任意のストアフロントページで HTTP ヘッダーを表示します。 Web ブラウザーインスペクターの使用など、いくつかの方法があります。

次の例では、HTTP プロトコルを使用してCommerce サーバーに接続できる任意のマシンから実行できる curl を使用しています。

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

を探します。 `X-Frame-Options` ヘッダーの値。
