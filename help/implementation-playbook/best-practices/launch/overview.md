---
title: 導入フェーズ
description: Adobe Commerce プロジェクトのローンチ段階での実装のベストプラクティスについて説明します。
exl-id: 2e85346c-2063-49c9-9b8d-1b5fdd3f1cef
feature: Best Practices
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
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
source-wordcount: '181'
ht-degree: 1%
---
# ローンチフェーズ

ローンチフェーズには、次のアクティビティが含まれます。

- ローンチ前後の最終的なチェックリストのレビュー
- 実稼動環境への展開
- セキュリティ設定
- サービス検証
- パフォーマンス監視

次の節では、ローンチ段階のベストプラクティス情報を示します。

## セキュリティ設定

| ベストプラクティス | 説明 |
|------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Adobe セキュリティ通知サービス ](https://www.adobe.com/subscription/adbeSecurityNotifications.html) | Adobeのセキュリティ通知を購読します。 |
| [Commerce サイトとインフラストラクチャの保護](security-best-practices.md) | Commerceを導入する際のセキュリティ体制を強化し、Commerceストアフロント、管理者、インフラストラクチャ、データを不正アクセスやサイバー攻撃から保護します。 |
| [Google reCAPTCHA](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html) | 登録ユーザーが開始した管理者アクセスと様々なストアフロントアクション用にGoogle reCAPTCHAを設定します。 |
| [Web web クローラーの設定](robots-txt.md) | Adobe Commerce サイトに関する手順をweb web クローラーに渡します。 |
| [ セキュリティ設定の確認](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/launch/checklist) | Adobe Commerce on cloud infrastructure サイトを立ち上げる前に、チェックリスト項目を確認します。 |

## パフォーマンス監視

| ベストプラクティス | 説明 |
|------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| [を使用 [!DNL Site-Wide Analysis Tool]](../../../tools/site-wide-analysis-tool/intro.md#integrations-with-other-adobe-commerce-support-tools) | Adobe Commerceサイトに関する重要なインサイトを一元的に確認できます。 |
