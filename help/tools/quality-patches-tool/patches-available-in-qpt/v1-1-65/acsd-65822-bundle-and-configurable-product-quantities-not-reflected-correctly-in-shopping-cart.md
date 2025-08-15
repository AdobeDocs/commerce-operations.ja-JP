---
title: ACSD-65822：バンドルおよび設定可能な製品数量が買い物かごに正しく反映されない
description: ACSD-65822 パッチを適用すると、バンドル製品を追加する際に、管理パネルのカスタマーの買い物かごセクションに数量が 0 と表示されるAdobe Commerceの問題が修正されます。
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
source-git-commit: 7e9598e3ac0558706ef98ca81c19d27c37f7e860
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-65822：バンドルおよび設定可能な製品数量が [!UICONTROL Shopping Cart] に正しく反映されない

ACSD-65822 パッチでは、バンドルと設定可能な製品数が **[!UICONTROL Shopping Cart]** の *[!UICONTROL Customer's Activities]* セクションに正しく表示されない問題を修正しています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 がインストールされている場合に使用できます。 パッチ ID は ACSD-65822 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドルおよび設定可能な製品数が、**[!UICONTROL Shopping Cart]** の *[!UICONTROL Customer's Activities]* セクションに正しく表示されません。

<u> 再現手順 </u>:

1. ストアフロントでユーザーを作成します。
2. 管理パネルで **[!UICONTROL Bundle product]** を作成します。
3. ストアフロントで、ログインユーザーとして、指定した数量のバンドル製品を買い物かごに追加します。
4. *管理者* パネルの **[!UICONTROL Customers]** に移動し、手順 1 で作成した顧客の **[!UICONTROL Edit]** をクリックします。
5. 「**[!UICONTROL Create Order]**」をクリックします。
6. 左側の「*[!UICONTROL Customer's Activities]*」の下で、「**[!UICONTROL Shopping Cart]**」セクションを確認します。 バンドル製品と選択した数量が表示されます。

<u> 期待される結果 </u>:

バンドル品目の数量は、ストアフロントに表示される数量と一致する必要があります。

<u> 実際の結果 </u>:

バンドル品目の数量は 0 と表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
