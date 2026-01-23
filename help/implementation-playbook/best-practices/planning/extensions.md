---
title: 拡張機能のベストプラクティス
description: サードパーティのAdobe Commerce拡張機能によって発生するパフォーマンスの問題を回避する方法について説明します。
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# 拡張機能のベストプラクティス

Adobe Commerce サードパーティの拡張機能（モジュール）は、ストアフロントのパフォーマンスに悪影響を与える可能性のある様々な問題を引き起こす可能性があります。 次のベストプラクティスに従うことで、これらの問題を回避できます。

- 可能な限り [&#x200B; プロセス外の拡張機能 &#x200B;](https://developer.adobe.com/commerce/extensibility/) を使用してCommerceの統合とカスタマイズを開発し、メンテナンスとアップグレード性を容易にします。
- [Commerce Marketplace](https://commercemarketplace.adobe.com//extensions.html) などの信頼できる発行元からサードパーティの拡張機能をダウンロードして購入します。
- サードパーティの拡張機能をすべて最新バージョンに更新します。
- サードパーティの拡張機能を最新の状態に保つことができない場合は、別の拡張機能の使用を検討します。
- 新しいバージョンのAdobe Commerceへのアップグレードを計画している場合は、インストールされているサードパーティ製の拡張機能が新しいバージョンと互換性があることを確認し、必要に応じて拡張機能をアップグレードします。

>[!NOTE]
>
> Commerce Marketplace で利用可能なすべての拡張機能は、新しいAdobe Commerce リリースとの互換性を維持するために必要です。 [&#x200B; リリースの互換性 &#x200B;](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/) を参照してください。

## 影響を受ける製品とバージョン

[&#x200B; サポートされているすべてのバージョン &#x200B;](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## 追加情報

- [アップグレード計画のベストプラクティス](../../../upgrade/prepare/best-practices.md)
- クラウドインフラストラクチャー上のAdobe Commerceでのサードパーティ拡張機能の使用
   - [&#x200B; 技術と要件 – 開発とテスト &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-devtest)
   - [&#x200B; 統合とステージングで完全にテストする理由 &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-cloud-service/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
