---
title: ACSD-47497：ストア/設定/サービス [!UICONTROL OAuth] の ACL がありません
description: 特定の役割に権限が設定されており、設定セクションへのアクセスを定義できない場合は、ACSD-47497 パッチを適用して、Adobe Commerceの問題を修正してください。
feature: Configuration, Identity Management, Services
role: Admin
exl-id: 4dbbd7df-f34b-4db8-a207-3de40fb39c6f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-47497：ストア/設定/サービス [!UICONTROL OAuth] の ACL がありません

ACSD-47497 パッチを使用すると、Adobe Commerce Admin の **[!UICONTROL Configuration]** セクションに「**[!UICONTROL Services]**」タブが表示されない問題を解決できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23 がインストールされている場合に使用できます。 パッチ ID は ACSD-47497 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

特定の役割に対して権限が設定されている場合、**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Services]**/**[!UICONTROL OAuth]** へのアクセスを定義することはできません。

<u> 再現手順 </u>:

1. Adobe Commerce Admin にログインします。 **[!UICONTROL System]**/**[!UICONTROL Permissions]**/**[!UICONTROL User Roles]** に移動します。
1. 管理者の役割で「**[!UICONTROL Role Resources]**」を選択し、「**[!UICONTROL Roles Resources]**」の下の「**[!UICONTROL Resource Access]**」を「_カスタム_」に設定して、すべてのチェックボックスをオンにします。 「**[!UICONTROL Save Role]**」を選択します。
1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Services]** を選択します。 **[!UICONTROL OAuth]** 設定セクションは使用できません。

<u> 期待される結果 </u>:

**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Services]**/**[!UICONTROL OAuth]** に、設定セクションが表示されます。

<u> 実際の結果 </u>:

**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Services]**/**[!UICONTROL OAuth]** に、設定セクションがありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：開発者向けドキュメントの [ アップグレードとパッチ/パッチの適用 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
