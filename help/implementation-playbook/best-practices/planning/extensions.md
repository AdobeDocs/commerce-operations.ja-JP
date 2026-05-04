---
title: 拡張機能のベストプラクティス
description: サードパーティのAdobe Commerce拡張機能に起因するパフォーマンスの問題を回避する方法について説明します。
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: f9a135fc63574ccbecd3f564a87fc5c4ac03f009
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# 拡張機能のベストプラクティス

Adobe Commerceのサードパーティ製の拡張機能（モジュール）は、ストアフロントのパフォーマンスに悪影響を与えるさまざまな問題を引き起こす可能性があります。 次のベストプラクティスに従うことで、これらの問題を回避できます。

- [ プロセス外の拡張性](https://developer.adobe.com/commerce/extensibility/)を使用して、可能な限りCommerceの統合とカスタマイズを開発し、メンテナンスとアップグレード性を容易にします。
- [Commerce Marketplace](https://commercemarketplace.adobe.com//extensions.html)など、信頼できるソースからサードパーティの拡張機能をダウンロードして購入します。
- すべてのサードパーティ拡張機能を最新バージョンに更新します。
- サードパーティの拡張機能を最新の状態に保つことができない場合は、別の拡張機能の使用を検討してください。
- 新しいバージョンのAdobe Commerceへのアップグレードを計画する場合は、インストールされているサードパーティ製の拡張機能が新しいバージョンと互換性があることを確認し、必要に応じて拡張機能をアップグレードします。

>[!NOTE]
>
> 新しいCommerce リリースとの互換性を維持するには、Adobe Commerce Marketplaceで利用可能なすべての拡張機能が必要です。 [ リリースの互換性](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases)を参照してください。

## 影響を受ける製品とバージョン

[ サポートされているすべてのバージョン ](../../../release/versions.md) /:

- Adobe Commerce on cloud infrastructure
- Adobe Commerce オンプレミス

## 追加情報

- [アップグレード計画のベストプラクティス](../../../upgrade/prepare/best-practices.md)
- Adobe Commerce on cloud インフラストラクチャでサードパーティの拡張機能を使用する
   - [テクノロジーと要件 – 開発とテスト](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-devtest)
   - [Integration and Stagingで完全にテストする理由](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
