---
title: PHP 設定
description: 以下の手順に従って、必要な PHP 拡張をインストールし、Adobe CommerceとMagento Open Sourceのオンプレミスインストールに必要な PHP 設定を構成します。
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---


# PHP 設定

このトピックでは、必要な PHP オプションを設定する方法について説明します。

>[!NOTE]
>
>詳しくは、 [システム要件](../system-requirements.md) を参照してください。

## PHP がインストールされていることを確認します

Linux のほとんどのフレーバーは、デフォルトで PHP をインストールしています。 このトピックでは、PHP が既にインストールされていることを前提としています。 PHP が既にインストールされているかどうかを確認するには、コマンドラインで次のように入力します。

```bash
php -v
```

PHP がインストールされている場合、次のようなメッセージが表示されます。

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe CommerceとMagento Open Source2.4 は PHP 7.3 と互換性がありますが、PHP 7.4 とのテストを行い、使用することをお勧めします。

PHP がインストールされていない場合、またはバージョンのアップグレードが必要な場合は、Linux 固有のフレーバに対する指示に従ってインストールします。
CentOS では、 [追加の手順が必要になる場合があります](https://wiki.centos.org/HowTos/php7).

## インストールされている拡張機能の検証

Adobe CommerceとMagento Open Sourceには、一連の拡張機能をインストールする必要があります。

{{$include /help/_includes/templated/php-extensions.md}}

インストールされている拡張機能を検証するには：

1. インストールされているモジュールの一覧を表示します。

   ```bash
   php -m
   ```

1. 必要な拡張機能がすべてインストールされていることを確認します。
1. PHP のインストールに使用したのと同じワークフローを使用して、見つからないモジュールを追加します。 例えば、 `yum` PHP をインストールするには、PHP 7.4 モジュールを次のように追加します。

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## PHP 設定を確認する

>[!WARNING]
>
>PHP 7.4.20 を使用している場合は、 `pcre.jit=0` の `php.ini` ファイル。 これは PHP を回避します [バグ](https://bugs.php.net/bug.php?id=81101) CSS の読み込みを妨げる

- PHP のシステムタイムゾーンを設定する。そうしないと、インストール中に次のようなエラーが表示され、cron などの時間関連の操作が機能しない場合があります。

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- PHP のメモリ制限を設定します。

   アドビの詳細な推奨事項は次のとおりです。

   - コードのコンパイルまたは静的アセットのデプロイ `1G`
   - デバッグ， `2G`
   - テスト、 `~3-4G`

- PHP の値を増やします `realpath_cache_size` および `realpath_cache_ttl` 推奨設定に変更するには：

   ```conf
   realpath_cache_size=10M
   realpath_cache_ttl=7200
   ```

   これらの設定を使用すると、PHP プロセスは、ページが読み込まれるたびにファイルを検索するのではなく、ファイルへのパスをキャッシュできます。 詳しくは、 [パフォーマンスの調整](https://www.php.net/manual/en/ini.core.php) PHP ドキュメント内。

- 有効にする [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments):Adobe CommerceおよびMagento Open Source2.1 以降で必要です。

   次を有効にすることをお勧めします： [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) パフォーマンス上の理由から OPcache は多くの PHP ディストリビューションで有効になっています。

   Adobe CommerceおよびMagento Open Source2.1 以降では、コード生成に PHP コードコメントを使用します。

>[!NOTE]
>
>インストールとアップグレードの際の問題を回避するため、PHP のコマンドライン設定と PHP の Web サーバプラグイン設定の両方に同じ PHP 設定を適用することを強くお勧めします。 詳しくは、次の節を参照してください。

## PHP 設定ファイルを検索する

このセクションでは、必要な設定を更新するために必要な設定ファイルを見つける方法について説明します。

### 検索 `php.ini` 設定ファイル

Web サーバー設定を検索するには、 [`phpinfo.php` ファイル](optional-software.md#create-phpinfophp) を探し、 `Loaded Configuration File` 次のように指定します。

![PHP 情報ページ](../../assets/installation/config_phpini-webserver.png)

PHP のコマンドライン設定を検索するには、

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>1 つしかない場合 `php.ini` ファイルを編集し、そのファイルに変更を加えます。 2 人いる場合 `php.ini` ファイルを編集する場合は、 *すべて* ファイル。 そうしないと、予期しないパフォーマンスを引き起こす可能性があります。

### OPcache 構成設定を検索

PHP OPcache 設定は、通常、 `php.ini` または `opcache.ini`. 場所は、オペレーティングシステムと PHP のバージョンによって異なる場合があります。 OPcache 設定ファイルには、 `opcache` セクションや設定 `opcache.enable`.

次のガイドラインに従って検索します。

- Apache Web サーバー：

   Apache を使用する Ubuntu の場合、OPcache の設定は通常、 `php.ini` ファイル。

   Apache または nginx を使用する CentOS の場合、OPcache 設定は通常、 `/etc/php.d/opcache.ini`

   見つからない場合は、次のコマンドを使用して見つけます。

   ```bash
   sudo find / -name 'opcache.ini'
   ```

- PHP-FPM を使用した nginx web サーバ： `/etc/php/7.2/fpm/php.ini`

複数の `opcache.ini`、すべてのを変更します。

## PHP オプションの設定方法

PHP オプションを設定するには：

1. を開きます。 `php.ini` をクリックします。
1. 使用可能な [タイムゾーン設定](https://www.php.net/manual/en/timezones.php)
1. 次の設定を探し、必要に応じてコメントを解除します。

   ```conf
   date.timezone =
   ```

1. 手順 2 で見つけたタイムゾーン設定を追加します。

1. の値を変更 `memory_limit` を、この節の最初に推奨される値の 1 つに追加します。

   例：

   ```conf
   memory_limit=2G
   ```

1. を追加または更新 `realpath_cache` 次の値に一致する設定：

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

1. もう一方を開く `php.ini` （異なる場合）と同じ変更を加えます。

## OPcache オプションを設定

設定するには `opcache.ini` options:

1. OPcache 設定ファイルをテキストエディターで開きます。

   - `opcache.ini` (CentOS)
   - `php.ini` （ウブントゥ）
   - `/etc/php/7.2/fpm/php.ini` (nginx Web サーバー（CentOS または Ubuntu）)

1. 場所 `opcache.save_comments` 必要に応じて、コメントを解除します。
1. その値がに設定されていることを確認します。 `1`.
1. 変更を保存し、テキストエディターを終了します。
1. Web サーバーを再起動します。

   - Apache、Ubuntu: `service apache2 restart`
   - Apache、CentOS: `service httpd restart`
   - nginx、Ubuntu、CentOS: `service nginx restart`

## トラブルシューティング

PHP の問題のトラブルシューティングに関するヘルプについては、次のAdobe Commerceサポート記事を参照してください。

- [ブラウザでAdobe Commerceにアクセスする際に、PHP バージョンエラーまたは 404 エラーが発生する](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [PHP 設定エラー](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP の mcrypt 拡張機能が正しくインストールされていません](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [PHP バージョンの対応チェックの問題](https://support.magento.com/hc/en-us/articles/360033546411)
- [一般的な PHP の致命的なエラーと解決策](https://support.magento.com/hc/en-us/articles/360030568432)
