---
title: ベースディレクトリパスのカスタマイズ
description: MAGE_DIRS 変数を使用して、絶対パスの配列を設定します。
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# ベースディレクトリのパス

この `MAGE_DIRS` 環境変数を使用すると、Commerce アプリケーションが様々なファイルへの絶対パスを構築したり、URL を生成したりするために使用する、カスタムのベースディレクトリパスとベース URL のフラグメントを指定できます。

## MAGE_DIRS を設定

キーが定数である連想配列を [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] および値は、それぞれディレクトリの絶対パスまたはその URL パスです。

次を設定できます `MAGE_DIRS` 次のいずれかの方法を使用します。

- [ブートストラップパラメーターの値を設定](../bootstrap/set-parameters.md)
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

上記の例では、のパスを設定します `[cache]` および `[media]` ディレクトリ `/mnt/nfs/cache` および `/mnt/nfs/media`、それぞれ。

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
