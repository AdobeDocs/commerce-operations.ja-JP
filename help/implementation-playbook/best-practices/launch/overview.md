---
title: 導入の開始フェーズ
description: Adobe Commerceプロジェクトの立ち上げ段階に関する実装のベストプラクティスについて説明します。
exl-id: 2e85346c-2063-49c9-9b8d-1b5fdd3f1cef
feature: Best Practices
source-git-commit: e1e7ad76b1df8e920ab7f9740fd4be8dc7335954
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 1%

---

# 立ち上げフェーズ

ローンチフェーズには、次のアクティビティが含まれます。

- 運用開始前と運用開始後の最終的なチェックリストレビュー
- 実稼動のデプロイメント
- セキュリティ設定
- サービスの検証
- パフォーマンスの監視

以下の節では、立ち上げフェーズのベストプラクティス情報について説明します。

## セキュリティ設定

| ベストプラクティス | 説明 |
|------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| [Adobeセキュリティ通知サー&#x200B;ビス](https://www.adobe.com/subscription/adbeSecurityNotifications.html) | Adobeのセキュリティ通知を受け取る |
| [セキュリティインシデントの防止と対応](prevent-respond-security-incident.md) | クラウドインフラストラクチャプロジェクトに関するAdobe Commerceのセキュリティ上の問題を回避し、対応します。 |
| [Google reCAPTCHA](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html) | 管理者アクセス用にGoogle reCAPTCHA を設定し、登録ユーザーが開始した様々なストアフロントアクションを設定します。 |
| [Web クローラーの設定](robots-txt.md) | を使用して、Adobe Commerceサイトに関する指示を Web クローラーに渡す `robots.txt` および `sitemap.xml` ファイル。 |
| [セキュリティ設定の検証](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html) | クラウドインフラストラクチャサイトでAdobe Commerceを起動する前に、チェックリストの項目を確認します。 |

## パフォーマンスの監視

| ベストプラクティス | 説明 |
|------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| [以下を使用します。 [!DNL Site-Wide Analysis Tool]](../../../tools/site-wide-analysis-tool/intro.md#integrations-with-other-adobe-commerce-support-tools) | Adobe Commerceサイトに関する重要なインサイトを 1 か所で表示します。 |
