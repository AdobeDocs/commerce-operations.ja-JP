---
title: ACSD-56621：会社管理者ユーザーのグリーティングヘッダーに更新された名前が表示されない
description: ACSD-56621 パッチを適用して、更新された会社管理者ユーザーの姓と名が挨拶文ヘッダーのセクションに反映されないAdobe Commerceの問題を修正します。
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 739c1c8c-e079-4ad7-be97-7c60b0347e12
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: 4560f5f5-d00c-5b5d-b61b-369d85ef7a26
    internal-label: User Account
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '423'
ht-degree: 0%
---
# ACSD-56621：会社管理者ユーザーのグリーティングヘッダーに更新された名前が表示されない

ACSD-56621 パッチでは、更新された会社管理者ユーザーの姓と名が挨拶文ヘッダーセクションに反映されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.46がインストールされている場合に利用できます。 パッチ IDはACSD-56621です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

更新された名前は、会社管理者ユーザーのグリーティングヘッダーには表示されません。

<u>複製する手順</u>:

1. **[!UICONTROL Admin]** パネルに移動します。
1. **[!UICONTROL Stores]**&#x200B;に移動し、**[!UICONTROL Configuration]**&#x200B;を選択します。
1. 「**[!UICONTROL General]**」セクションで「**[!UICONTROL B2B]**」を選択して、B2B企業機能を有効にします。
1. **[!UICONTROL Storefront]**&#x200B;に移動し、新しい会社を登録します。
1. 会社管理者ユーザーとしてログインします。
1. **[!UICONTROL My Account]** > **[!UICONTROL Company Users]**&#x200B;に移動し、必要に応じて姓と名のフィールドを変更します。

<u>期待される結果</u>:

挨拶ヘッダーセクション内のユーザーの姓と名が直ちに変更されます。

<u>実際の結果</u>:

ユーザーの姓と名は、ユーザーがログアウトして再度ログインしたときにのみ変更されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
