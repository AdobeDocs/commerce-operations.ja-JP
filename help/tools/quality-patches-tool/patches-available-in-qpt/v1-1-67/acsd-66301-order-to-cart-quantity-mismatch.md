---
title: ACSD-66301:Commerce管理で注文から買い物かごに商品を移動すると、数量が一致しない
description: ACSD-66301 パッチを適用すると、管理パネルから注文を作成する際に、顧客の買い物かごの商品が注文に追加された後で削除されないAdobe Commerceの問題を修正できます。
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 61e0e491-b2dc-4ae0-807e-2ae80d17f9c2
source-git-commit: 1e56c38713344b117ca3882861ced35e602b3239
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-66301:Commerce管理者で注文から買い物かごに商品を戻すと、数量が一致しない

ACSD-66301 パッチでは、製品を注文から管理画面の買い物かごに戻すと、数量が一致しない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 がインストールされている場合に使用できます。 パッチ ID は ACSD-66301 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p10、2.4.7-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p9 - 2.4.6-p11、2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Commerce管理で注文から買い物かごに商品を戻すと、数量が一致しません。

<u> 再現手順 </u>:

1. ストアフロントを通じてユーザーを作成します。
2. 買い物かごに数量= *5* の商品を追加します。
3. 管理パネルに移動し、製品が追加されたユーザーアカウントを開きます。
4. 「**[!UICONTROL Create Order]**」をクリックします。
5. 左側のパネルでは、追加された製品や数量を含む、顧客のアクティビティを表示できます。
6. 製品を注文に追加します。
7. メイン注文セクションの数量= *4* を更新します。
8. ボタン **[!UICONTROL Update Items and Quantities]** クリックします。
9. 選択した品目を注文から顧客の買い物かごに移動します。

<u> 期待される結果 </u>:

商品が買い物かごに追加され、新しい数量= *4* が設定されました。

<u> 実際の結果 </u>:

商品が買い物かごに追加されました（旧数量= *5*）。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
