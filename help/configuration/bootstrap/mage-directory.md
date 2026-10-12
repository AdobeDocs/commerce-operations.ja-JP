---
title: ベースディレクトリパスのカスタマイズ
description: MAGE_DIRS変数を使用して、絶対パスの配列を設定します。
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '128'
ht-degree: 0%
---
# ベースディレクトリのパス

`MAGE_DIRS`環境変数を使用すると、カスタムベースディレクトリのパスとベース URLのフラグメントを指定できます。このフラグメントは、Commerce アプリケーションが様々なファイルへの絶対パスを作成したり、URLを生成したりするために使用します。

## MAGE_DIRSを設定

キーが[\\Magento\\App\\Filesystem\\DirectoryList](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php)からの定数で、値がそれぞれディレクトリまたはそのURL パスの絶対パスである連想配列を指定します。

次のいずれかの方法で`MAGE_DIRS`を設定できます。

- [ブートストラップパラメーターの値を設定する](../bootstrap/set-parameters.md)
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

前述の例では、`[cache]`および`[media]`個のディレクトリのパスをそれぞれ`/mnt/nfs/cache`および`/mnt/nfs/media`に設定しています。

