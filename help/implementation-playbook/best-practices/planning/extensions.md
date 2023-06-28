---
title: 拡張機能のベストプラクティス
description: サードパーティのAdobe Commerce拡張機能によって生じるパフォーマンスの問題を回避する方法について説明します。
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# 拡張機能のベストプラクティス

Adobe Commerceサードパーティの拡張機能（モジュール）は、ストアフロントのパフォーマンスに悪影響を与える可能性のある様々な問題の原因となる可能性があります。 次のベストプラクティスに従うことで、これらの問題を回避できます。

- サードパーティの拡張機能を、信頼できるソース ( [Commerce Marketplace](https://marketplace.magento.com/extensions.html).
- すべてのサードパーティの拡張機能を最新バージョンに更新します。
- サードパーティの拡張機能を更新したままにできない場合は、異なる拡張機能を使用することを検討してください。
- 新しいバージョンのAdobe Commerceへのアップグレードを計画する場合は、インストールされているサードパーティの拡張機能が新しいバージョンと互換性があることを確認し、必要に応じて拡張機能をアップグレードします。

>[!NOTE]
>
> 新しい Commerce リリースとの互換性を維持するには、Adobe Commerce Marketplace で使用可能なすべての拡張機能が必要です。 詳しくは、 [リリースの互換性](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/).

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 追加情報

- [アップグレード計画のベストプラクティス](../../../upgrade/prepare/best-practices.md)
- クラウドインフラストラクチャ上でのAdobe Commerceとのサードパーティの拡張機能の使用
   - [テクノロジーと要件 — 開発とテスト](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-devtest)
   - [統合とステージングで完全にテストをおこなうのはなぜですか？](https://devdocs.magento.com/cloud/live/live.html#whytest)
