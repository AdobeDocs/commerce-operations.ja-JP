---
title: セッションストレージの場所
description: セッションファイルの保存場所について説明します。
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# セッションストレージの場所

このトピックでは、セッションファイルが格納されている場所を特定する方法について説明します。 システムでは、次のロジックを使用してセッションファイルを保存します。

- memcached を設定した場合、セッションは RAM に保存されます。[ セッションストレージに memcached を使用 ](memcached.md) を参照してください。
- Redis を設定した場合、セッションは Redis サーバに保存されます。[ セッションストレージに Redis を使用する ](../cache/redis-session.md) を参照してください。
- デフォルトのファイルベースのセッションストレージを使用している場合は、以下の場所に、表示されている順序でセッションが保存されます。

   1. [`env.php`](#example-in-envphp) で定義されたディレクトリ
   1. [`php.ini`](#example-in-phpini) で定義されたディレクトリ
   1. `<magento_root>/var/session` ディレクトリ

## `env.php` の例

`<magento_root>/app/etc/env.php` のサンプルスニペットを次に示します。

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

上記の例では、セッションファイルを `/var/www/session` に保存します

## `php.ini` の例

`root` 権限を持つユーザーとして、`php.ini` ファイルを開き、`session.save_path` の値を検索します。 これは、セッションが格納される場所を識別します。

## セッションサイズの管理

[ ユーザーガイド ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management) の _セッション管理_ を参照してください。

## ガベージコレクション設定

期限切れのセッションをクリーンアップするために、システムは `gc_probability / gc_divisor` ディレクティブによって計算される確率に従ってランダムに `gc` （_ガベージコレクション_）ハンドラーを呼び出します。 例えば、これらのディレクティブをそれぞれ `1/100` に設定した場合、`1%` の確率（_100 件のリクエストごとに 1 回のガベージコレクションの呼び出しの確率_）を意味します。

ガベージコレクションハンドラーでは、`gc_maxlifetime` ディレクティブを使用します。このディレクティブは、セッションが _ガベージ_ と見なされてクリーンアップされる秒数を示します。

一部のオペレーティングシステム（Debian/Ubuntu）では、デフォルトの `session.gc_probability` ディレクティブが `0` なので、ガベージコレクションハンドラーを実行できません。

`<magento_root>/app/etc/env.php` ファイルの `php.ini` ファイルから `session.gc_` ディレクティブを上書きできます。

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

設定は、マーチャントの web サイトのトラフィックや特定のニーズに応じて異なります。
