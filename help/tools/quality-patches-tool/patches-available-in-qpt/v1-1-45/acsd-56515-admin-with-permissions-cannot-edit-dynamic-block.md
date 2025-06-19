---
title: ACSD-56515:Web サイトレベルの権限を持つ管理者が [!UICONTROL Dynamic Block] を編集できない
description: ACSD-56515 パッチを適用すると、web サイトレベルの権限を持つ管理者が [!UICONTROL Dynamic Block] を追加または編集できないAdobe Commerceの問題を修正できます。
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: dd3e61a4-aba4-4f86-b4fe-88ca4276ace5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-56515:Web サイトレベルの権限を持つ管理者が [!UICONTROL Dynamic Block] を編集できない

ACSD-56515 パッチでは、web サイトレベルの権限を持つ管理者が [!UICONTROL Dynamic Block] ールを追加または編集できない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 がインストールされている場合に使用できます。 パッチ ID は ACSD-56515 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Web サイトレベルの権限を持つ管理者は、[!UICONTROL Dynamic Block] ールを追加または編集できません。

<u> 再現手順 </u>:

1. store と storereview を使用してセカンダリ web サイトを作成します。
1. **[!UICONTROL System]**/**[!UICONTROL Permissions]**/**[!UICONTROL User Roles]** に移動し、セカンダリ web サイト範囲に制限されたユーザーの役割を、使用可能なすべてのリソースで作成します。
1. 管理者ユーザーを、上記で作成した役割で作成します。
1. 制限付きの管理者ユーザーでログインし、[!UICONTROL Dynamic Block] を作成します。

<u> 期待される結果 </u>:

Web サイトに対する制限を持つ管理者ユーザーは、[!UICONTROL Dynamic Block] を作成できます。

<u> 実際の結果 </u>:

次のエラーが表示されます：*この項目を表示するには、さらに権限が必要です*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
