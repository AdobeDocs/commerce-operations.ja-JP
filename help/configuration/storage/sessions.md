---
title: セッションストレージの場所
description: セッションファイルの保存場所について説明します。
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# セッションストレージの場所

このトピックでは、セッションファイルが格納されている場所を特定する方法について説明します。 システムでは、次のロジックを使用してセッションファイルを保存します。

- memcached を設定した場合、セッションは RAM に格納されます。を参照してください [セッションストレージに memcached を使用](memcached.md).
- Redis を設定した場合、セッションは Redis サーバーに保存されます。を参照してください [セッションストレージに Redis を使用](../cache/redis-session.md).
- デフォルトのファイルベースのセッションストレージを使用している場合は、以下の場所に、表示されている順序でセッションが保存されます。

   1. で定義されたディレクトリ [`env.php`](#example-in-envphp)
   1. で定義されたディレクトリ [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## の例 `env.php`

からのサンプルスニペット `<magento_root>/app/etc/env.php` 次のようになります。

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

上記の例では、セッションファイルをに格納します。 `/var/www/session`

## の例 `php.ini`

を使用した As a ユーザー `root` 権限、を開く `php.ini` ファイルで、の値を検索します。 `session.save_path`. これは、セッションが格納される場所を識別します。

## セッションサイズの管理

を参照してください。 [セッション管理](https://docs.magento.com/user-guide/stores/security-session-management.html) が含まれる _ユーザーガイド_.

## ガベージコレクション設定

期限切れのセッションをクリーンアップするには、システムによって次が呼び出されます `gc` （_ガベージコレクション_）により計算される確率に従ってランダムにハンドラーを作成します。 `gc_probability / gc_divisor` ディレクティブ。 例えば、これらのディレクティブをに設定した場合 `1/100` それぞれ、次の確率を意味します `1%` （_100 件のリクエストにつきガベージコレクションが 1 回呼び出される確率_）に設定します。

ガベージコレクションハンドラーは、 `gc_maxlifetime` ディレクティブ – セッションが次のように表示されるまでの秒数 _ガベージ_ 場合によってはクリーンアップされます。

一部のオペレーティングシステム（Debian/Ubuntu）では、デフォルト `session.gc_probability` ディレクティブは `0`ガベージコレクションハンドラーを実行できないようにします。

を上書きできます `session.gc_` からのディレクティブ `php.ini` 内のファイル `<magento_root>/app/etc/env.php` ファイル：

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

設定は、マーチャントの web サイトのトラフィックや特定のニーズに応じて異なります。
