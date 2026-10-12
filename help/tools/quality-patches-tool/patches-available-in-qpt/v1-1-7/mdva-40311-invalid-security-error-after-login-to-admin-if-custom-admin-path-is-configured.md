---
title: MDVA-40311：カスタム管理者パスが設定されている場合、管理者にログインした後に「無効なセキュリティまたはフォームキー」エラーが発生する
description: MDVA-40311 パッチは、管理者ユーザーがエラーメッセージを受け取る問題を修正します：*無効なセキュリティまたはフォームキー。 カスタム管理者パスが設定され、秘密鍵が有効になっている場合は、管理者にログインした後、ページ*を更新してください。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.7がインストールされている場合に利用できます。 パッチ IDはMDVA-40311です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Admin Workspace, Compliance, Security
role: Admin
exl-id: dce4914b-e32e-4af0-be24-e55680191fa3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%
---
# MDVA-40311：カスタム管理者パスが設定されている場合、管理者にログインした後に「無効なセキュリティまたはフォームキー」エラーが発生する

MDVA-40311 パッチは、管理者ユーザーに次のエラーメッセージが表示される問題を修正します。*セキュリティまたはフォームキーが無効です。 カスタム管理者パスが設定され、秘密鍵が有効になっている場合は、管理者にログインした後、ページ*&#x200B;を更新してください。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.7がインストールされている場合に使用できます。 パッチ IDはMDVA-40311です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーに次のエラーメッセージが表示されます：*セキュリティまたはフォームキーが無効です。 カスタム管理者パスが設定され、秘密鍵が有効になっている場合は、管理者にログインした後、ページ*&#x200B;を更新してください。

<u>複製する手順</u>:

* 有効なユーザー名とパスワードを使用して、Admin ユーザーとしてログインします。

<u>期待される結果</u>:

ユーザーはエラーメッセージなしでログインできます。

<u>実際の結果</u>:

*セキュリティ キーまたはフォーム キーが無効です。 ページを更新してください* エラーメッセージが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
