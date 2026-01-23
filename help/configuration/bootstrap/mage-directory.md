---
title: ベースディレクトリパスのカスタマイズ
description: MAGE_DIRS 変数を使用して、絶対パスの配列を設定します。
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# ベースディレクトリのパス

`MAGE_DIRS` 環境変数を使用すると、カスタムベースディレクトリパスと、Commerce アプリケーションで様々なファイルへの絶対パスの構築または URL の生成に使用されるベース URL のフラグメントを指定できます。

## MAGE_DIRS を設定

キーが [\\Magento\\App\\Filesystem\\DirectoryListの定数で、値がディレクトリの絶対パスまたはその URL パスである連想配列を &#x200B;](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php) それぞれ指定します。

`MAGE_DIRS` は、次のいずれかの方法で設定できます。

- [ブートストラップパラメーターの値を設定](../bootstrap/set-parameters.md)
- 次のようなカスタムエントリポイントスクリプトを使用します。

  ```php
  <?php
  /**
   * Copyright [first year code created] Adobe
   * All Rights Reserved.
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

上記の例では、`[cache]` ディレクトリと `[media]` ディレクトリのパスをそれぞれ `/mnt/nfs/cache` と `/mnt/nfs/media` に設定します。

