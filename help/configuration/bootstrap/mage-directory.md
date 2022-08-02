---
title: 基本ディレクトリパスのカスタマイズ
description: MAGE_DIRS 変数を使用して、絶対パスの配列を設定します。
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# 基本ディレクトリパス

この `MAGE_DIRS` 環境変数を使用して、コマースアプリケーションが様々なファイルへの絶対パスを構築したり、URL を生成したりするために使用する、ベースディレクトリのカスタムパスとベース URL のフラグメントを指定できます。

## MAGE_DIRS を設定

キーが定数である連想配列を指定します。 [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] との値は、それぞれディレクトリの絶対パスまたはディレクトリの URL パスです。

次の設定が可能です。 `MAGE_DIRS` 次のいずれかの方法で、

- [ブートストラップパラメータの値を設定する](../bootstrap/set-parameters.md)
- 次のようなカスタムエントリポイントスクリプトを使用します。

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\App\Bootstrap;
   use Magento\Framework\App\Filesystem\DirectoryList;
   use Magento\Framework\App\Http;
   
   require __DIR__ . '/app/bootstrap.php';
   $params = $_SERVER;
   $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
        DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
        DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
        DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
        DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
        DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
   ];
   $bootstrap = Bootstrap::create(BP, $params);
   /** @var Http $app */
   $app = $bootstrap->createApplication(Http::class);
   $bootstrap->run($app);
   ```

前述の例では、 `[cache]` および `[media]` ディレクトリ `/mnt/nfs/cache` および `/mnt/nfs/media`、それぞれ。

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
