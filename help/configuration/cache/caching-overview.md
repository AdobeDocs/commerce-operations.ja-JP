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

[!DNL Commerce] を使用すると、デフォルトのファイルシステムキャッシュに代わる設定を行うことができます。 このガイドでは、その代替手段の一部、つまり

- で次のキャッシュメカニズムを設定します。 [!DNL Commerce] 設定：

   - [データベース](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - ファイルシステム（デフォルト）: デフォルトのファイルシステムキャッシュを使用するための設定は必要ありません。

- の設定 [ワニス](config-varnish.md) を変更せずに [!DNL Commerce] 設定。

## キャッシュの用語

[!DNL Commerce] では、次のキャッシュ用語を使用します。

- **フロントエンド** – キャッシュ・ストレージに対するインタフェースまたはゲートウェイに似ており、次によって実装される [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **キャッシュタイプ** – には、次のいずれかのタイプを指定できます。 [!DNL Commerce] または、次のことができます [独自に作成](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **バックエンド** – 詳細を指定する [キャッシュストレージ](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)、実装者 [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **2 レベルバックエンド**- キャッシュレコードを、高速なバックエンドと低速なバックエンドの 2 つのバックエンドに格納します。

  >[!INFO]
  >
  >2 レベルのバックエンドキャッシュの設定については、このガイドの範囲外です。

## 設定オプション

- 指定されたを変更する `default` キャッシュフロントエンド – 

  以下のみを変更します `<magento_root>/app/etc/di.xml` ファイル。Commerce アプリケーションのグローバルな依存関係挿入の設定です。

- 独自のカスタムキャッシュフロントエンドの設定 – 

  以下のみを変更します `<magento_root>/app/etc/env.php` ファイルします。これは、内の同等の設定を `di.xml` ファイル。

>[!TIP]
>
>ワニスは変更を必要としません [!DNL Commerce] 設定。 参照： [ワニスの設定と使用](config-varnish.md).
