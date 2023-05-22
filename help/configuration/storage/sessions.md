---
title: セッションストレージの場所
description: セッションファイルの保存場所を説明します。
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# セッションストレージの場所

このトピックでは、セッションファイルが保存されている場所を特定する方法について説明します。 システムは、次のロジックを使用してセッションファイルを保存します。

- memcached を設定した場合、セッションは RAM に保存されます。参照 [セッションストレージに memcached を使用](memcached.md).
- Redis を設定した場合、セッションは Redis サーバーに保存されます。参照 [セッションストレージに Redis を使用](../cache/redis-session.md).
- デフォルトのファイルベースのセッションストレージを使用している場合、セッションは次の順序で次の場所に保存されます。

   1. で定義されたディレクトリ [`env.php`](#example-in-envphp)
   1. で定義されたディレクトリ [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## の例 `env.php`

サンプルスニペット `<magento_root>/app/etc/env.php` 以下に示します。

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

前述の例では、セッションファイルを `/var/www/session`

## の例 `php.ini`

を使用して `root` 権限、開く `php.ini` ファイルを開き、 `session.save_path`. セッションが保存される場所を識別します。

## セッションサイズを管理

詳しくは、 [セッション管理](https://docs.magento.com/user-guide/stores/security-session-management.html) 内 _ユーザーガイド_.

## ガベージコレクションの設定

期限切れセッションをクリーンアップするには、 `gc` (_ごみ収集_) ハンドラーは、 `gc_probability / gc_divisor` ディレクティブ。 例えば、次のディレクティブをに設定した場合、 `1/100` それぞれが、次の確率を意味する `1%` (_100 リクエストごとに 1 回のガベージコレクション呼び出しの確率_) をクリックします。

ガベージコレクションハンドラーは、 `gc_maxlifetime` directive — セッションが次のように認識されるまでの秒数 _ごみ箱_ クリーンアップされた可能性があります。

一部のオペレーティングシステム (Debian/Ubuntu) では、デフォルト `session.gc_probability` 指令は `0`：ガベージコレクションハンドラーの実行を防ぎます。

上書き可能な `session.gc_` 指令 `php.ini` ファイルを `<magento_root>/app/etc/env.php` ファイル：

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

設定は、商人の Web サイトのトラフィックや特定のニーズに応じて異なります。
