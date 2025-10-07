---
title: キャッシュの設定
description: Adobe Commerce アプリケーションのキャッシュメカニズムと設定オプションについて説明します。 デフォルトのファイルシステムキャッシュに代わる方法について説明します。
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# キャッシュの設定

[!DNL Commerce] を使用すると、デフォルトのファイルシステムのキャッシュに代わるキャッシュを設定できます。 このガイドでは、その代替手段の一部、つまり

- [!DNL Commerce] 設定で、次のキャッシュメカニズムを設定します。

   - [&#x200B; データベース &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - ファイルシステム（デフォルト）: デフォルトのファイルシステムキャッシュを使用するための設定は必要ありません。

- [&#x200B; 設定を変更せずに &#x200B;](config-varnish.md) ワニス [!DNL Commerce] を設定します。

## キャッシュの用語

[!DNL Commerce] では、次のキャッシュ用語を使用します。

- **フロントエンド** - [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend) によって実装される、キャッシュストレージへのインターフェイスまたはゲートウェイに似ています。
- **キャッシュタイプ** - [!DNL Commerce] に用意されているタイプの 1 つにすることも、[&#x200B; 独自のタイプを作成 &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/) することもできます。
- **バックエンド** - [&#x200B; キャッシュストレージ &#x200B;](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) に関する詳細を指定します。[Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend) によって実装されます
- **2 レベルバックエンド** - キャッシュレコードを 2 つのバックエンドに保存します。高速なバックエンドと低速なバックエンドがあります。

  >[!INFO]
  >
  >2 レベルのバックエンドキャッシュの設定については、このガイドの範囲外です。

## 設定オプション

- 提供された `default` キャッシュフロントエンドの変更 – 

  `<magento_root>/app/etc/di.xml` ファイル（Commerce アプリケーションのグローバルな依存関係のインジェクション設定）のみを変更できます。

- 独自のカスタムキャッシュフロントエンドの設定 – 

  `<magento_root>/app/etc/env.php` ファイル内の同等の設定を上書きするので、`di.xml` ファイルのみを変更します。

>[!TIP]
>
>ワニスは [!DNL Commerce] の構成を変更する必要はありません。 [&#x200B; ワニスの設定と使用 &#x200B;](config-varnish.md) を参照してください。
