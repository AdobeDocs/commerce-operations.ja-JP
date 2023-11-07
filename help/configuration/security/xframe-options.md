---
title: クリックジャックの弱点を防ぐ
description: 「X-Frame-Options」ヘッダーを使用してページのレンダリングを制御することで、クリックジャックの悪用を防ぎます。
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# クリックジャックの弱点を防ぐ

回避 [クリックジャッキング](https://owasp.org/www-community/attacks/Clickjacking) ～を含むことによる悪用 [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) ストアフロントへのリクエストの HTTP リクエストヘッダー。

The `X-Frame-Options` ヘッダーを使用すると、ブラウザーでページを `<frame>`, `<iframe>`または `<object>` 次のように指定します。

- `DENY`：ページをフレームに表示できません。
- `SAMEORIGIN`:（デフォルト）ページは、ページ自体と同じ接触チャネル上のフレームにのみ表示できます。

>[!WARNING]
>
>The `ALLOW-FROM <uri>` コマースがサポートされているブラウザーがサポートしなくなったので、オプションは非推奨になりました。 詳しくは、 [ブラウザーの互換性](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>セキュリティ上の理由から、Adobeでは、コマースストアフロントをフレーム内で実行しないことを強くお勧めします。

## 実装方法 `X-Frame-Options`

次の値を設定： `X-Frame-Options` in `<project-root>/app/etc/env.php`. デフォルト値は次のように設定されます。

```php
'x-frame-options' => 'SAMEORIGIN',
```

の変更を再デプロイ `env.php` ファイルを有効にします。

>[!TIP]
>
>セキュリティの高い方法で `env.php` ファイルの内容が、管理者に値を設定する場合とは異なります。

## 次の設定を確認： `X-Frame-Options`

設定を確認するには、任意のストアフロントページで HTTP ヘッダーを表示します。 これをおこなう方法はいくつかあります。例えば、Web ブラウザーインスペクターを使用する方法もあります。

次の例では、HTTP プロトコルを使用して Commerce サーバーに接続できる任意のマシンから実行できる curl を使用します。

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

を探します。 `X-Frame-Options` の値を含める必要があります。
