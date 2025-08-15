---
title: ACSD-56621：会社管理者ユーザーの挨拶ヘッダーに表示されない更新された名前
description: ACSD-56621 パッチを適用すると、会社の管理者ユーザーの更新された名と姓が「挨拶ヘッダー」セクションに反映されないAdobe Commerceの問題が修正されます。
feature: Companies, B2B, User Account
role: Admin, Developer
exl-id: 739c1c8c-e079-4ad7-be97-7c60b0347e12
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-56621：会社管理者ユーザーの挨拶ヘッダーに表示されない更新された名前

ACSD-56621 パッチでは、会社の管理者ユーザーの更新された名と姓が「挨拶ヘッダー」セクションに反映されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46 がインストールされている場合に使用できます。 パッチ ID は ACSD-56621 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

更新された名前は、会社の管理者ユーザーの挨拶ヘッダーには表示されません。

<u> 再現手順 </u>:

1. **[!UICONTROL Admin]** パネルに移動します。
1. **[!UICONTROL Stores]** に移動し、「**[!UICONTROL Configuration]**」を選択します。
1. 「**[!UICONTROL General]**」セクションで、「**[!UICONTROL B2B]**」を選択して、B2B 会社の機能を有効にします。
1. **[!UICONTROL Storefront]** に移動して、新しい会社を登録してください。
1. 会社管理者ユーザーとしてログインします。
1. **[!UICONTROL My Account]**/**[!UICONTROL Company Users]** に移動し、必要に応じて「名」フィールドと「姓」フィールドを変更します。

<u> 期待される結果 </u>:

挨拶ヘッダーセクションのユーザーの姓と名は、すぐに変更されます。

<u> 実際の結果 </u>:

ユーザーの姓と名は、ユーザーがログアウトして再度ログインした場合にのみ変更されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
