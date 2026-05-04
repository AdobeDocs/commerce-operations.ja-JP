---
title: ACSD-47004:VAT IDのない請求先住所にVATが適用されない
description: ACSD-47004 パッチを適用して、VAT IDのない請求先住所にVATが適用されないAdobe Commerceの問題を修正します。
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
exl-id: 72a64937-1c04-4fc2-bc61-fd2056e24419
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# ACSD-47004:VAT IDのない請求先住所にVATが適用されない

ACSD-47004 パッチは、VAT IDのない請求先住所にVATが適用されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24がインストールされている場合に利用できます。 パッチ IDはACSD-47004です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

VATは、VAT IDのない請求先住所には適用されません。

<u>複製する手順</u>:

1. [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]**&#x200B;を開き、**[!UICONTROL Enable Automatic Assignment to Customer Group]**&#x200B;を&#x200B;*[!UICONTROL Yes]*&#x200B;に設定します。
1. VAT ID検証用に異なるグループを設定します。 例：

   ![VAT ID検証設定インターフェイスに、税金検証の設定オプションが表示されている](/help/assets/tools/vat-id-validations.png)

1. 新規顧客の登録。
1. VATなしで新しいデフォルトアドレスを追加します。 例：

   ```text
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. お客様のグループが[!UICONTROL General]のままであることを確認します。
1. このアドレスを編集し、有効なVAT番号を追加します。

   ```text
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. お客様のグループが[!UICONTROL Retailer]に変更されていることを確認してください。
1. アドレスを編集し、VAT番号を削除します。

   ```text
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>期待される結果</u>:

顧客グループは、自動的にデフォルトの[!UICONTROL General] グループに変更されます。

<u>実際の結果</u>:

顧客グループは、自動的にデフォルトの[!UICONTROL General] グループに変更されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
