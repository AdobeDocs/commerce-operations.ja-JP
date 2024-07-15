---
title: キャッシュの設定
description: キャッシュの概要と、Adobe Commerce アプリケーションのキャッシュメカニズムを設定する方法について説明します。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# キャッシュの設定

[!DNL Commerce] を使用すると、デフォルトのファイルシステムのキャッシュに代わるキャッシュを設定できます。 このガイドでは、その代替手段の一部、つまり

- [!DNL Commerce] 設定で、次のキャッシュメカニズムを設定します。

   - [ データベース ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - ファイルシステム（デフォルト）: デフォルトのファイルシステムキャッシュを使用するための設定は必要ありません。

- [!DNL Commerce] 設定を変更せずに [ ワニス ](config-varnish.md) を設定します。

## キャッシュの用語

[!DNL Commerce] では、次のキャッシュ用語を使用します。

- **フロントエンド** - [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend) によって実装される、キャッシュストレージへのインターフェイスまたはゲートウェイに似ています。
- **キャッシュタイプ** - [!DNL Commerce] に用意されているタイプの 1 つにすることも、[ 独自のタイプを作成 ](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/) することもできます。
- **バックエンド** - [ キャッシュストレージ ](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) に関する詳細を指定します。[Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend) によって実装されます
- **2 レベルバックエンド** - キャッシュレコードを 2 つのバックエンドに保存します。高速なバックエンドと低速なバックエンドがあります。

  >[!INFO]
  >
  >2 レベルのバックエンドキャッシュの設定については、このガイドの範囲外です。

## 設定オプション

- 提供された `default` キャッシュフロントエンドの変更 – 

  `<magento_root>/app/etc/di.xml` ファイル（Commerce アプリケーションのグローバルな依存関係のインジェクション設定）のみを変更できます。

- 独自のカスタムキャッシュフロントエンドの設定 – 

  `di.xml` ファイル内の同等の設定を上書きするので、`<magento_root>/app/etc/env.php` ファイルのみを変更します。

>[!TIP]
>
>ワニスは [!DNL Commerce] の構成を変更する必要はありません。 [ ワニスの設定と使用 ](config-varnish.md) を参照してください。
