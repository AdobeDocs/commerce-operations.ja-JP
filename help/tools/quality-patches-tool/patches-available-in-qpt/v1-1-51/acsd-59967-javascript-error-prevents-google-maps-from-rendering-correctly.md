---
title: ACSD-59967:JavaScript エラーにより  [!DNL Google Maps]  が正しくレンダリングされない
description: ACSD-59967 パッチを適用して、JavaScript エラーによって正しくレンダリングできないAdobe Commerceの問題  [!DNL Google Maps]  修正してください。
feature: Admin Workspace, Page Builder, CMS
role: Admin, Developer
exl-id: 2982857a-7adb-4163-be18-4d2caf0d645c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-59967:JavaScript エラーにより、[!DNL Google Maps] が正しくレンダリングされない

ACSD-59967 パッチでは、JavaScript エラーによって [!DNL Google Maps] が正しくレンダリングされない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 がインストールされている場合に使用できます。 パッチ ID は ACSD-59967 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

JavaScript エラーにより、[!DNL Google Maps] が正しくレンダリングされません。

<u> 再現手順 </u>:

1. 有効な [!DNL Google Maps] キーを生成します。
1. [!DNL Google Maps]/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]** の下で、**[!UICONTROL Content Management]** API キーを設定します。
1. [!DNL Google API Key] をフィールドに追加 **[!UICONTROL Google Maps API Key]** て、設定を保存します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Content]**/**[!UICONTROL Pages]**/**[!UICONTROL Create New Page]** に移動します。
1. **[!UICONTROL Row]** 要素と **[!UICONTROL Maps]** 要素を追加します。

<u> 期待される結果 </u>:

コンソールにJavaScript エラーは存在せず、マップは *ストアフロント* および *管理* で適切にレンダリングされます。

<u> 実際の結果 </u>:

JavaScript エラーがコンソールに表示され、マップが正しくレンダリングされません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
