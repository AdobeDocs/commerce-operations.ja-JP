---
title: 'ACSD-47004: VAT ID のない請求先住所には VAT が適用されません'
description: VAT ID のない請求先住所に VAT が適用されないAdobe Commerceの問題を修正するには、ACSD-47004 パッチを適用してください。
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
exl-id: 72a64937-1c04-4fc2-bc61-fd2056e24419
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 1%

---

# ACSD-47004: VAT ID のない請求先住所には VAT が適用されません

ACSD-47004 パッチは、VAT ID のない請求先住所に VAT が適用されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 がインストールされている場合に使用できます。 パッチ ID は ACSD-47004 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

VAT ID のない請求先住所には VAT が適用されません。

<u> 再現手順 </u>:

1. [!UICONTROL Commerce Admin]/**[!UICONTROL Store]**/**[!UICONTROL Configuration]**/**[!UICONTROL Customers]**/**[!UICONTROL Customer Configuration]**/**[!UICONTROL Create New Account Options]** を開き、**[!UICONTROL Enable Automatic Assignment to Customer Group]** を *[!UICONTROL Yes]* に設定します。
1. VAT ID 検証用に別のグループを設定します。 例：

   ![VAT-ID-validations](/help/assets/tools/vat-id-validations.png)

1. 新規顧客を登録します。
1. VAT なしで新しい既定の住所を追加します。 例：

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. 顧客のグループが [!UICONTROL General] しいことを確認します。
1. この住所を編集して、有効な VAT 番号を追加してください：

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. 顧客のグループが [!UICONTROL Retailer] に変更されていることを確認します。
1. 住所を編集し、VAT 番号を削除します。

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u> 期待される結果 </u>:

顧客グループは、デフォルトの [!UICONTROL General] グループに自動的に変更されます。

<u> 実際の結果 </u>:

顧客グループは、デフォルトの [!UICONTROL General] グループに自動的には変更されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
