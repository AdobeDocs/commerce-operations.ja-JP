---
title: ACSD-65164：単一チェックボックスのカスタムオプションが選択された状態で、設定可能な製品の並べ替え時にエラーメッセージが表示される
description: 設定可能な商品を 1 つのチェックボックスを選択したカスタムオプションで並べ替えると、「選択された商品の一部は現在利用できません」というエラーメッセージが表示されるAdobe Commerceの問題を修正するために、ACSD-65164 パッチを適用してください。
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-65164：単一チェックボックスのカスタムオプションが選択された状態で、設定可能な製品の並べ替え時にエラーメッセージが表示される

ACSD-65164 パッチでは、単一のチェックボックスのカスタムオプションを選択して設定可能な製品の順序を変更すると、エラーメッセージ *選択した項目オプションの一部は現在使用できません* が発生する問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 がインストールされている場合に使用できます。 パッチ ID は ACSD-65164 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

設定可能な製品を、選択した 1 つのチェックボックスカスタムオプションで並べ替えると、次のエラーメッセージが返されます。*選択した項目の一部のオプションは、現在利用できません*。

### レプリケートする手順：

1. 管理パネルで、**[!UICONTROL Catalog]**/**[!UICONTROL Products]**/**[!UICONTROL Add Product]**/**[!UICONTROL Simple Product]** に移動します。
1. 「**[!UICONTROL Customizable Options]**」の下に、「*チェックボックス*」オプションを追加します。
   * チェックボックスオプションを「*必須*」に設定します。
   * 2 つのオプション値を追加します。
1. ストアフロントに移動し、登録済みの顧客としてログインします。
1. 1 つのチェックボックスオプションを選択した状態で、商品を買い物かごに追加します。
1. **[!UICONTROL Cart]**/**[!UICONTROL Proceed to Checkout]**/**[!UICONTROL Place an Order]** に移動します。
1. **[!UICONTROL My Account]**/**[!UICONTROL Orders]**/**[!UICONTROL Reorder]** に移動して、同じ製品を追加します。

**期待される結果：**

商品が正常に買い物かごに追加されます。

**実績：**

次のエラーメッセージが表示されます。

*SKU が&quot;24-MB01&quot;の製品を買い物かごに追加できませんでした：選択した項目の一部のオプションは、現在利用できません。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
