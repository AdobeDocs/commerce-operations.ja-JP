---
title: キャッシュの設定
description: キャッシュと、Adobe CommerceおよびMagento Open Sourceアプリケーションのキャッシュメカニズムの設定方法について説明します。
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# キャッシュの設定

[!DNL Commerce] では、デフォルトのファイルシステムキャッシュの代替オプションを設定できます。 このガイドでは、これらの代替策の一部を説明します。すなわち

- 次の設定を行います [キャッシュ](https://glossary.magento.com/cache) メカニズム [!DNL Commerce] 設定：

   - [データベース](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [レディス](config-redis.md)
   - ファイルシステム（デフォルト）:デフォルトのファイルシステムキャッシュを使用する場合は、設定は必要ありません。

- 設定 [ワニス](config-varnish.md) 変更せずに [!DNL Commerce] 設定。

## キャッシュの用語

[!DNL Commerce] では、次のキャッシュ用語が使用されます。

- **フロントエンド** — キャッシュストレージのインターフェイスまたはゲートウェイと似ており、 [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **キャッシュタイプ** — 次のいずれかのタイプを指定できます： [!DNL Commerce] または、 [独自の](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **バックエンド** — 詳細を指定します。 [キャッシュストレージ](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html)，実装元 [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **2 レベルのバックエンド**—2 つのバックエンドにキャッシュレコードを格納します。速い方が速く、遅い方が速い。

   >[!INFO]
   >
   >2 レベルのバックエンドキャッシュ設定は、このガイドの範囲外です。

## 設定オプション

- 提供されたの変更 `default` キャッシュフロントエンド —

   次の項目のみを変更します。 `<magento_root>/app/etc/di.xml` ファイル、Commerce アプリケーションのグローバル [依存注入](https://glossary.magento.com/dependency-injection) 設定。

- 独自のカスタムキャッシュフロントエンドの設定 —

   次の項目のみを変更します。 `<magento_root>/app/etc/env.php` ファイルを編集する必要があります。 `di.xml` ファイル。

>[!TIP]
>
>ワニスは、 [!DNL Commerce] 設定。 詳しくは、 [Vanish の設定と使用](config-varnish.md).
