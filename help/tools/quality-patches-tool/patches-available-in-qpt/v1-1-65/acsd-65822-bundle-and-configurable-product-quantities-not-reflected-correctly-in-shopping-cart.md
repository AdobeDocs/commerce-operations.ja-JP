---
title: ACSD-65822：バンドルおよび設定可能な製品数量がショッピングカートに正しく反映されない
description: ACSD-65822 パッチを適用して、バンドル製品を追加する際に、管理パネルのカスタマーショッピングカートのセクションに数量が0として表示されるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
exl-id: 6740b5a6-8710-458c-abe4-03d2a8a694c5
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-65822: バンドルおよび設定可能な製品数量が[!UICONTROL Shopping Cart]に正しく反映されない

ACSD-65822 パッチは、*[!UICONTROL Customer's Activities]*&#x200B;の&#x200B;**[!UICONTROL Shopping Cart]** セクションにバンドルと設定可能な製品数量が正しく表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65がインストールされている場合に利用できます。 パッチ IDはACSD-65822です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バンドルと設定可能な製品数量が、*[!UICONTROL Customer's Activities]*&#x200B;の&#x200B;**[!UICONTROL Shopping Cart]** セクションに正しく表示されません。

<u>複製する手順</u>:

1. ストアフロントでユーザーを作成する。
2. 管理パネルで&#x200B;**[!UICONTROL Bundle product]**&#x200B;を作成します。
3. ストアフロントで、ログインユーザーとして、指定した数量のバンドル商品をショッピングカートに追加します。
4. *管理者* パネルで、**[!UICONTROL Customers]**&#x200B;に移動し、手順1で作成した顧客の&#x200B;**[!UICONTROL Edit]**&#x200B;をクリックします。
5. **[!UICONTROL Create Order]**&#x200B;をクリックします。
6. 左側の&#x200B;*[!UICONTROL Customer's Activities]*&#x200B;の下にある「**[!UICONTROL Shopping Cart]**」セクションを確認します。 選択した数量と一緒にバンドル製品が表示されます。

<u>期待される結果</u>:

バンドルアイテムの数量は、ストアフロントに表示されている数量と一致する必要があります。

<u>実際の結果</u>:

バンドル品目数量は0として表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
