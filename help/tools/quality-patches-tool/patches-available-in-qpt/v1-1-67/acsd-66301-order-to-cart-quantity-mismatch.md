---
title: ACSD-66301:Commerce Adminで注文から買い物かごに商品を移動すると、数量が一致しない
description: ACSD-66301 パッチを適用して、管理パネルから注文を作成する際に、注文に追加された後に顧客のカート内の商品が削除されないAdobe Commerceの問題を修正します。
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 61e0e491-b2dc-4ae0-807e-2ae80d17f9c2
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-66301:Commerce Adminで注文から買い物かごに商品を戻すと、数量が一致しない

ACSD-66301 パッチでは、管理画面で注文から買い物かごに商品を移動すると、数量が一致しない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67がインストールされている場合に利用できます。 パッチ IDはACSD-66301です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p10、2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.6-p9 - 2.4.6-p11、2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Commerce管理画面で注文から買い物かごに商品を戻すと、数量が一致しません。

<u>複製する手順</u>:

1. ストアフロントでユーザーを作成する。
2. 数量= *5*&#x200B;のショッピングカートに商品を追加します。
3. 管理パネルに移動し、製品が追加されたユーザーアカウントを開きます。
4. **[!UICONTROL Create Order]**&#x200B;をクリックします。
5. 左側のパネルでは、追加された製品と数量を含む、顧客のアクティビティを表示できます。
6. 商品を注文に追加します。
7. メイン注文セクションの数量= *4*&#x200B;を更新します。
8. 「**[!UICONTROL Update Items and Quantities]**」ボタンをクリックします。
9. 選択した商品を注文から顧客のショッピングカートに戻します。

<u>期待される結果</u>:

新しい数量= *4*&#x200B;の商品がショッピングカートに追加されました。

<u>実際の結果</u>:

古い数量= *5*&#x200B;の製品がショッピングカートに追加されました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
