---
title: PHP 設定
description: 以下の手順に従って、必要な PHP 拡張をインストールし、Adobe CommerceとMagento Open Sourceのオンプレミスインストールに必要な PHP 設定を構成します。
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: aacc4332cecec0cb9b0f5c23d60b7abd1c63feea
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---


# PHP 設定

このトピックでは、必要な PHP オプションを設定する方法について説明します。

>[!NOTE]
>
>最新バージョンのAdobe CommerceとMagento Open Sourceには、PHP 8.1 以上が必要です。詳しくは、 [システム要件](../system-requirements.md) PHP のすべてのサポート対象バージョンを対象としています。

## PHP がインストールされていることを確認します

PHP は、ほとんどの Linux ディストリビューションにデフォルトでインストールされます。 このトピックでは、PHP が既にインストールされていることを前提としています。 PHP がインストールされているかどうかを確認するには、コマンドラインに次のように入力します。

```bash
php -v
```

PHP がインストールされている場合、次のようなメッセージが表示されます。

```terminal
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

PHP がインストールされていない（またはアップグレードが必要な）場合は、Linux ディストリビューションの指示に従ってインストールします。

## インストールされている拡張機能の検証

Adobe CommerceとMagento Open Sourceには、特定の PHP 拡張が必要です。 次のリストは、Commerce の各エディションに必要な拡張を指定します。 リストは、各エディションの最新バージョンを実行しているデプロイメントから自動生成されます。

{{$include /help/_includes/templated/php-extensions.md}}

インストールされている拡張機能を検証するには：

1. インストールされているモジュールの一覧を表示します。

   ```bash
   php -m
   ```

1. 必要な拡張機能がすべてインストールされていることを確認します。
1. PHP のインストールに使用したのと同じワークフローを使用して、見つからないモジュールを追加します。

## PHP 設定を確認する

>[!WARNING]
>
>PHP 7.4.20 を使用している場合は、 `pcre.jit=0` の `php.ini` ファイル。 これは PHP を回避します。 [バグ](https://bugs.php.net/bug.php?id=81101) CSS の読み込みを妨げる

- PHP のシステムタイムゾーンを設定します。設定しないと、インストール中に次のようなエラーが表示され、cron のような時間関連の操作が動作しない場合があります。

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- PHP のメモリ制限を設定します。

  Adobeでは、次のことをお勧めします。

   - コードのコンパイルまたは静的アセットのデプロイ `1G`
   - デバッグ， `2G`
   - テスト、 `~3-4G`

- PHP の値を増やします。 `realpath_cache_size` および `realpath_cache_ttl` 推奨設定に変更するには：

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  これらの設定を使用すると、PHP プロセスは、ページの読み込み時にファイルを検索する代わりに、ファイルへのパスをキャッシュできます。 詳しくは、 [パフォーマンスの調整](https://www.php.net/manual/en/ini.core.php) PHP ドキュメント内。

- 有効にする [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments):Adobe CommerceおよびMagento Open Source2.1 以降で必要です。

  Adobeでは、 [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) パフォーマンス上の理由から OPcache は多くの PHP ディストリビューションで有効になっています。

  Adobe CommerceおよびMagento Open Source2.1 以降では、コード生成に PHP コードコメントを使用します。

>[!NOTE]
>
>インストールとアップグレードの際の問題を回避するため、Adobeでは、PHP のコマンドライン設定と PHP Web サーバーのプラグイン設定の両方に同じ PHP 設定を適用することを強くお勧めします。 詳しくは、次の節を参照してください。

## PHP 設定ファイルを検索する

このセクションでは、必要な設定を更新するために必要な設定ファイルを見つける方法について説明します。

### 検索文字列 `php.ini` 設定ファイル

Web サーバー設定を検索するには、 [`phpinfo.php` ファイル](optional-software.md#create-phpinfophp) を探し、 `Loaded Configuration File` 次のように指定します。

![PHP 情報ページ](../../assets/installation/config_phpini-webserver.png)

PHP のコマンドライン設定を検索するには、次のように入力します。

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>1 つしかない場合 `php.ini` ファイルを変更します。 2 人いる場合 `php.ini` ファイル、変更 *両方* ファイル。 そうしないと、予期しないパフォーマンスを引き起こす可能性があります。

### OPcache 構成設定を検索

PHP OPcache 設定は、通常、 `php.ini` または `opcache.ini`. 場所は、オペレーティングシステムと PHP のバージョンによって異なる場合があります。 OPcache 設定ファイルには、 `opcache` セクションや設定 `opcache.enable`.

次のガイドラインに従って検索します。

- Apache Web サーバー：

  Apache を使用する Ubuntu の場合、OPcache の設定は、通常、 `php.ini` ファイル。

  Apache または nginx を使用する CentOS の場合、OPcache 設定は通常、 `/etc/php.d/opcache.ini`

  見つからない場合は、次のコマンドを使用して見つけます。

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- PHP-FPM を使用した nginx Web サーバ： `/etc/php/8.1/fpm/php.ini`

複数の `opcache.ini`、すべてのを変更します。

## PHP オプションを設定する方法

PHP オプションを設定するには：

1. を開きます。 `php.ini` をクリックします。
1. 使用可能な [タイムゾーン設定](https://www.php.net/manual/en/timezones.php)
1. 次の設定を探し、必要に応じてコメントを解除します。

   ```conf
   date.timezone =
   ```

1. 手順 2 で見つけたタイムゾーン設定を追加します。

1. の値を変更 `memory_limit` を、この節の最初に推奨される値の 1 つに追加します。

   以下に例を挙げます。

   ```conf
   memory_limit=2G
   ```

1. を追加または更新します。 `realpath_cache` 次の値に一致する設定：

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

1. もう 1 つを開く `php.ini` （異なる場合）と同じ変更を加えます。

## OPcache オプションを設定

次の手順で `opcache.ini` options:

1. OPcache 設定ファイルをテキストエディターで開きます。

   - `opcache.ini` (CentOS)
   - `php.ini` （ウブントゥ）
   - `/etc/php/8.1/fpm/php.ini` (nginx Web サーバー（CentOS または Ubuntu）)

1. 場所 `opcache.save_comments` 必要に応じて、コメントを解除します。
1. その値がに設定されていることを確認します。 `1`.
1. 変更を保存し、テキストエディターを終了します。
1. Web サーバーを再起動します。

   - Apache、Ubuntu: `service apache2 restart`
   - Apache、CentOS: `service httpd restart`
   - nginx、Ubuntu、CentOS: `service nginx restart`

## トラブルシューティング

PHP の問題のトラブルシューティングに関するヘルプについては、次のAdobe Commerceサポート記事を参照してください。

- [ブラウザーでAdobe Commerceにアクセスする際に PHP バージョンエラーが発生する、または 404 エラーが発生する](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP 設定エラー](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP の mcrypt 拡張機能が正しくインストールされていません](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP バージョンの対応チェックの問題](https://support.magento.com/hc/en-us/articles/360033546411)
- [一般的な PHP の致命的なエラーと解決策](https://support.magento.com/hc/en-us/articles/360030568432)
