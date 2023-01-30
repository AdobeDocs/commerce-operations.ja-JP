---
title: Redis サービス設定のベストプラクティス
description: Adobe Commerce 2.3.5 用の拡張 Redis キャッシュ実装を使用して、キャッシュのパフォーマンスを向上させる方法について説明します。
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 12de523cc7ea1486c894d54efe6944d92d87ded0
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Redis サービス設定のベストプラクティス

- Adobe Commerce 2.3.3 以降をクラウドインフラストラクチャにデプロイする場合は、Redis バージョン 5.0 にアップグレードします。
- Adobe Commerceバージョン 2.3.5 以降では、拡張 Redis キャッシュ実装を使用します。 この実装には、Adobe Commerceからの各リクエストで実行される Redis クエリの数を最小限に抑えるための、次の最適化が含まれています。
   - Redis とAdobe Commerceの間のネットワークデータ転送のサイズを減らす
   - CPU サイクルの消費を減らすため、アダプタの読み込みが必要な項目を自動的に決定する機能を改善
   - Redis 書き込み操作の競合状態を軽減

## 影響を受ける製品およびバージョン

Adobe Commerce on cloud infrastructure （バージョン 2.3.3 以降）
Adobe Commerce（すべてのデプロイメント方法）、バージョン 2.3.5 以降

## クラウドデプロイメント用の Redis バージョンを更新

Adobe Commerce 2.3.3 以降を使用したクラウドインフラストラクチャ上でのAdobe Commerceデプロイメントの場合は、Redis サービスを Redis バージョン 5.0 にアップグレードします。手順については、クラウドインフラストラクチャに関するAdobe Commerceのドキュメントの次のトピックを参照してください。

- [Redis サービスの設定](https://devdocs.magento.com/cloud/project/services-redis.html)
- [サービスのバージョンを変更](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## 拡張 Redis キャッシュ実装の設定

Adobe Commerce 2.3.5 以降の場合は、拡張された Redis キャッシュ実装を使用するように設定を更新します。 `\Magento\Framework\Cache\Backend\Redis`.

### クラウドデプロイメントの設定

を使用 `ece-tools` 2002.1.1 以降では、 `REDIS_BACKEND` 環境設定ファイルの deployment 変数 `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

詳しくは、 [変数をデプロイ > `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) ( クラウドインフラストラクチャ上のAdobe Commerceに関するドキュメント ) を参照してください。

>[!NOTE]
>
> を使用して、コマンドラインからローカルクラウド環境にインストールされている ece-tools のバージョンを確認します。 `composer show magento/ece-tools` コマンドを使用します。 必要に応じて、 [ece-tools バージョンを更新](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

>[!WARNING]
>
>実行 _not_ クラウドインフラストラクチャプロジェクトの Redis スレーブ接続を [スケールアーキテクチャ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). これにより、Redis 接続エラーが発生します。 詳しくは、 [レディスの構成指導](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) 内 _クラウドインフラストラクチャ上のコマース_ ガイド。


### オンプレミスデプロイメント用の設定

Adobe Commerceのオンプレミスデプロイメントの場合は、 `bin/magento:setup` コマンド 手順については、 [デフォルトのキャッシュに Redis を使用](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## 追加情報

- [Adobe Commerceリリース v2.3.5 — パフォーマンスの向上](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Redis ページキャッシュ](../../../configuration/cache/redis-pg-cache.md)


