---
title: PHP 設定
description: 次の手順に従って、必要な PHP 拡張機能をインストールし、Adobe Commerceのオンプレミス版インストールに必要な PHP 設定を行います。
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# PHP 設定

このトピックでは、必要な PHP オプションを設定する方法について説明します。

>[!NOTE]
>
>最新バージョンのAdobe Commerceを使用するには、最低でも PHP 8.1 が必要です。参照： [必要システム構成](../system-requirements.md) （サポートされている PHP の全バージョン）

クラウド設定のガイダンスについては、を参照してください [PHP 設定](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) が含まれる _クラウドインフラストラクチャー上の Commerce_ ガイド。

## PHP プロセスコントロール

{{php-process-control}}

## PHP がインストールされていることを確認します

PHP はほとんどの Linux ディストリビューションにデフォルトでインストールされます。 このトピックは、PHP がすでにインストールされていることを前提としています。 PHP がインストールされているかどうかを確認するには、コマンドラインに以下を入力します。

```bash
php -v
```

PHP がインストールされている場合は、次のようなメッセージが表示されます。

```terminal
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

PHP がインストールされていない（またはアップグレードが必要な）場合は、Linux ディストリビューションの指示に従ってインストールしてください。

## インストールされている拡張機能の検証

Adobe Commerceには特定の PHP 拡張モジュールが必要です。 次のリストに、Commerceの各エディションで必要な拡張機能を示します。 リストは、各エディションの最新バージョンを実行しているデプロイメントから自動生成されます。

{{$include /help/_includes/templated/php-extensions.md}}

インストールされている拡張機能を確認するには：

1. インストールされているモジュールのリスト。

   ```bash
   php -m
   ```

1. 必要な拡張機能がすべてインストールされていることを確認します。
1. PHP のインストールに使用するのと同じワークフローを使用して、不足しているモジュールを追加します。

## PHP の設定を確認する

>[!WARNING]
>
>PHP 7.4.20 を使用している場合、次のように設定します。 `pcre.jit=0` が含まれる `php.ini` ファイル。 これは PHP に関連します [バグ](https://bugs.php.net/bug.php?id=81101) これにより、CSS が読み込まれなくなります。

- PHP のシステムタイムゾーンを設定します。設定しないと、インストール中に次のようなエラーが表示され、cron のような時間関連の操作が機能しない場合があります。

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- PHP のメモリ制限を設定します。

  Adobeでは、次のことをお勧めします。

   - コードのコンパイルまたは静的アセットのデプロイ `1G`
   - デバッグ、 `2G`
   - テスト、 `~3-4G`

- PHP の値を増やす `realpath_cache_size` および `realpath_cache_ttl` 推奨設定：

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  これらの設定により、PHP プロセスはページの読み込み時にパスを検索する代わりにファイルへのパスをキャッシュすることができます。 参照： [パフォーマンスチューニング](https://www.php.net/manual/en/ini.core.php) PHP のドキュメントに書かれています。

- Enable （有効） [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments)（Adobe Commerce 2.1 以降で必要）

  Adobeでは、 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) パフォーマンス上の理由から。 OPcache は多くの PHP ディストリビューションで有効になっています。

  Adobe Commerce 2.1 以降では、コードの生成に PHP コードコメントを使用します。

>[!NOTE]
>
>インストールおよびアップグレード時の問題を回避するために、Adobeでは、PHP コマンドライン設定と PHP Web Server プラグイン設定の両方に同じ PHP 設定を適用することを強くお勧めします。 詳しくは、次の節を参照してください。

## PHP 設定ファイルの検索

この節では、必要な設定を更新するために必要な設定ファイルを見つける方法について説明します。

### 検索 `php.ini` 設定ファイル

Web サーバー設定を見つけるには、 [`phpinfo.php` ファイル](optional-software.md#create-phpinfophp) web ブラウザーでを探します。 `Loaded Configuration File` 次のように設定します。

![PHP 情報ページ](../../assets/installation/config_phpini-webserver.png)

PHP コマンドライン設定を探すには、次のように入力します。

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>1 つしかない場合 `php.ini` ファイル、そのファイルを変更します。 次の 2 つの場合： `php.ini` ファイル，変更 *両方* ファイル。 そうしないと、予期しないパフォーマンスが発生する可能性があります。

### OPcache 構成設定の検索

PHP OPcache の設定は、通常、次の場所にあります。 `php.ini` または `opcache.ini`. 場所は、オペレーティングシステムと PHP のバージョンによって異なる場合があります。 OPcache 構成ファイルには、次のファイルが含まれる場合があります `opcache` 次のようなセクションまたは設定 `opcache.enable`.

検索には、次のガイドラインを使用します。

- Apache web サーバー：

  Apache を使用する Ubuntu の場合、OPcache 設定は通常、にあります。 `php.ini` ファイル。

  Apache または nginx を使用する CentOS の場合、OPcache 設定は通常、にあります。 `/etc/php.d/opcache.ini`

  存在しない場合は、次のコマンドを使用して検索します。

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- nginx web サーバと PHP-FPM: `/etc/php/8.1/fpm/php.ini`

2 つ以上の場合 `opcache.ini`を選択し、それらをすべて変更します。

## PHP オプションの設定方法

PHP オプションを設定するには、次の手順に従います。

1. を開く `php.ini` テキストエディター。
1. でサーバーのタイムゾーンを見つけます [タイムゾーン設定](https://www.php.net/manual/en/timezones.php)
1. 次の設定を探し、必要に応じてコメントを解除します。

   ```conf
   date.timezone =
   ```

1. 手順 2 で確認したタイムゾーン設定を追加します。

1. の値を変更します `memory_limit` を、この節の最初に推奨する値の 1 つに設定します。

   以下に例を挙げます。

   ```conf
   memory_limit=2G
   ```

1. を追加または更新 `realpath_cache` 次の値に一致するように設定します。

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. 変更を保存し、テキストエディターを終了します。

1. もう 1 つを開きます `php.ini` （異なる場合）同じ変更を加えます。

## OPcache オプションの設定

を設定 `opcache.ini` オプション：

1. テキストエディターで OPcache 設定ファイルを開きます。

   - `opcache.ini` （CentOS）
   - `php.ini` （Ubuntu）
   - `/etc/php/8.1/fpm/php.ini` （nginx web サーバ（CentOS または Ubuntu））

1. を見つける `opcache.save_comments` 必要に応じてコメント解除します。
1. その値がに設定されていることを確認します。 `1`.
1. 変更を保存し、テキストエディターを終了します。
1. Web サーバーを再起動します。

   - Apache、Ubuntu: `service apache2 restart`
   - Apache、CentOS: `service httpd restart`
   - nginx、Ubuntu、CentOS: `service nginx restart`

## トラブルシューティング

PHP の問題のトラブルシューティングについては、以下のAdobe Commerce サポートの記事を参照してください。

- [ブラウザーでAdobe Commerceにアクセスすると、PHP バージョンエラーまたは 404 エラーが発生する](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP 設定エラー](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP mcrypt 拡張モジュールが正しくインストールされていません](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP バージョン準備チェックの問題](https://support.magento.com/hc/en-us/articles/360033546411)
- [一般的な PHP の致命的なエラーと解決策](https://support.magento.com/hc/en-us/articles/360030568432)
