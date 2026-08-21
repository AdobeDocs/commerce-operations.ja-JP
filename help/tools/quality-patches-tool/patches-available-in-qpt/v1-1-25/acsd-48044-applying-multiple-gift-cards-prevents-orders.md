---
title: ACSD-48044：複数のギフトカードを適用すると、注文が行われなくなります
description: ACSD-48044 パッチを適用して、複数配送の1つの注文に複数のギフトカードを適用すると、注文が行われなくなるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# ACSD-48044：複数のギフトカードを適用すると、注文が行われなくなります

ACSD-48044 パッチでは、複数配送を伴う1つの注文に複数のギフトカードを適用すると、注文が行われない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-48044です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数配送の1つの注文に複数のギフトカードを適用すると、注文が行われなくなります。

<u>複製する手順</u>:

1. クリーンなバージョンのAdobe Commerceをインストールします。
1. 価格が100 ドルのシンプルな商品と、価格が10 ドルのシンプルな商品を作成します。
1. [!UICONTROL Admin panel]にログインして、2枚のギフトカードを作成します。

   * 02KB8M0H0GRD = $50
   * 00GXM6SUGBLW = 25 ドル

1. 2つのアドレスを持つ顧客を作成します。
1. 商品を2つカートに追加します。

   * まず$10の商品を追加し、次に$100の商品を追加します。 100 ドルの商品が最初に追加された場合、問題を再現することはできません。

1. ショッピングカートに移動し、作成した2枚のギフトカードを追加します。
1. 買い物かごページの&#x200B;**[!UICONTROL Ship to Multiple Addresses]**&#x200B;をクリックします。
1. 各商品に別の住所を割り当てます。
1. **[!UICONTROL Shipping information]** ページに移動します。
1. **[!UICONTROL Billing information]** ページに移動します。
1. 問題を確認できる&#x200B;**[!UICONTROL Review Your Order]** ページに移動します。
1. 注文してみます。

<u>期待される結果</u>:

* ギフトカードは合計金額に正しく適用されます。
* 注文が行われます。

<u>実際の結果</u>:

ギフトカードの金額にエラー&#x200B;*が混在しています。「ギフトカードコードを修正してください。」* ご注文の際。

* 最初の製品：

  * ギフトカードの削除（00GXM6SUGBLW） - $15.00
  * ギフトカードの削除（02KB8M0H0GRD） - $0.00

* 2つ目の製品：

  * ギフトカードの削除（00GXM6SUGBLW） - $25.00
  * ギフトカードの削除（02KB8M0H0GRD） - $35.00

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
