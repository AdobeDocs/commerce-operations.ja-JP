---
title: セッションストレージの場所
description: Adobe Commerceのセッションストレージの場所とファイル管理について説明します。 ストレージロジックと設定オプションの詳細。
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
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
source-wordcount: '279'
ht-degree: 0%
---
# セッションストレージの場所

このトピックでは、セッションファイルの保存場所を特定する方法について説明します。 システムは、次のロジックを使用してセッションファイルを保存します。

- memcachedを設定した場合、セッションはRAMに保存されます。[ セッションストレージにmemcachedを使用](memcached.md)を参照してください。
- Redisを設定した場合、セッションはRedis サーバーに保存されます。[ セッションストレージにRedisを使用](../cache/redis-session.md)を参照してください。
- デフォルトのファイルベースのセッションストレージを使用している場合は、次の場所にセッションを次の順序で保存します。

  1. [`env.php`](#example-in-envphp)で定義されたディレクトリ
  1. [`php.ini`](#example-in-phpini)で定義されたディレクトリ
  1. `<magento_root>/var/session` ディレクトリ

## `env.php`の例

`<magento_root>/app/etc/env.php`のサンプルスニペットは次のとおりです。

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

前の例では、`/var/www/session`にセッションファイルを保存しています

## `php.ini`の例

`root`権限を持つユーザーとして`php.ini` ファイルを開き、`session.save_path`の値を検索します。 これは、セッションの保存場所を特定します。

## セッションサイズの管理

_ユーザーガイド_&#x200B;の[ セッション管理](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management)を参照してください。

## ガベージコレクション設定

期限切れのセッションをクリーンアップするために、システムは`gc_probability / gc_divisor` ディレクティブによって計算された確率に従って、`gc` （_ガベージコレクション_）ハンドラーをランダムに呼び出します。 例えば、これらのディレクティブをそれぞれ`1/100`に設定した場合、それは`1%`の確率を意味します（_ガベージコレクションの呼び出しを100 リクエストごとに1回行う確率_）。

ガベージコレクションハンドラーは、`gc_maxlifetime` ディレクティブを使用します。このディレクティブの秒数を使用すると、セッションが&#x200B;_ガベージ_&#x200B;と見なされ、クリーンアップされる可能性があります。

一部のオペレーティングシステム （Debian/Ubuntu）では、デフォルトの`session.gc_probability` ディレクティブは`0`であるため、ガベージコレクションハンドラーの実行が妨げられます。

`<magento_root>/app/etc/env.php` ファイルの`php.ini` ファイルから`session.gc_` ディレクティブを上書きできます。

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

設定は、マーチャントのweb サイトのトラフィックと特定のニーズによって異なります。
