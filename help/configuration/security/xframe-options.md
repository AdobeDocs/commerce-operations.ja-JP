---
title: X-Frame-Options ヘッダー
description: X-Frame-Options を使用して、ページのレンダリングを制御します。
source-git-commit: db696b8ca501d128db655c5ebb161c654c6378a7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# X-Frame-Options ヘッダー

を防ぐには [クリックジャッキング](https://owasp.org/www-community/attacks/Clickjacking) を使用する場合、 [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) ストアフロントへのリクエストの HTTP リクエストヘッダー。

この `X-Frame-Options` ヘッダーを使用すると、ブラウザーでページを `<frame>`, `<iframe>`または `<object>` 次のように指定します。

- `DENY`:ページはフレームに表示できません。
- `SAMEORIGIN`:（デフォルト）ページは、ページ自体と同じオリジンのフレームにのみ表示できます。

>[!WARNING]
>
>この `ALLOW-FROM <uri>` コマースがサポートされているブラウザーがサポートしなくなったので、オプションは非推奨になりました。 詳しくは、 [ブラウザーの互換性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>セキュリティ上の理由から、Adobeでは、コマースストアフロントをフレーム内で実行しないことを強くお勧めします。

## 実装方法 `X-Frame-Options`

次の値を設定： `X-Frame-Options` in `<project-root>/app/etc/env.php`. デフォルト値は次のように設定されます。

```php
'x-frame-options' => 'SAMEORIGIN',
```

変更を `env.php` ファイルを有効にします。

>[!TIP]
>
>セキュリティの高い `env.php` ファイルの内容が、管理者に値を設定する場合とは異なります。

## 次の設定を確認： `X-Frame-Options`

設定を確認するには、任意のストアフロントページで HTTP ヘッダーを表示します。 これをおこなう方法はいくつかあります。例えば、Web ブラウザーインスペクターを使用する方法もあります。

次の例では、HTTP プロトコルを使用して Commerce サーバーに接続できる任意のマシンから実行できる curl を使用します。

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

を探します。 `X-Frame-Options` の値を含める必要があります。
