---
title: ACSD-47704：バンドルされた商品は、在庫のある商品の価格のみを示します
description: ACSD-47704 パッチを適用して、バンドルされた商品が在庫商品の価格のみを表示するAdobe Commerceの問題を修正します。
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
exl-id: 7f05ceed-869c-4d1a-91fd-0122dc98e65e
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 2%

---

# ACSD-47704：バンドルされた商品は、在庫のある商品の価格のみを示します

ACSD-47704 パッチは、顧客グループ間で顧客セグメントの価格が誤ってキャッシュされる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28がインストールされている場合に利用できます。 パッチ IDはACSD-47704です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

動的価格設定が有効になっているバンドル商品の価格は、在庫商品のみが含まれているため、誤っています。

<u>複製する手順</u>:

1. Commerce Admin パネルに移動します。
1. **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**&#x200B;に移動します。
1. **[UICONROL Dynamic Price]**&#x200B;を&#x200B;**[!UICONTROL Yes]**&#x200B;に設定します。
1. バンドルアイテム：
   * **[!UICONTROL Ship bundle items]**&#x200B;を&#x200B;**[!UICONTROL Together]**&#x200B;に設定
   * **[!UICONTROL Add Option]**&#x200B;を選択
     * **[!UICONTROL Title]** = o1
     * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
     * 「必須をマーク」チェックボックス
     * 在庫のあるシンプルな商品を追加します。例えば、Joust Duffle Bag SKU 24-MB01などです。 製品を追加する前に、その価格をメモしてください – $34
   * デフォルト数量：1
   * **[!UICONTROL Add Option]**&#x200B;を選択
     * **[!UICONTROL Option Title]** = o2
     * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
     * 「必須をマーク」チェックボックス
     * 前の手順で追加した製品とは異なり、在庫のあるシンプルな製品を追加します。例えば、Strive Shoulder Pack 24-MB04。 製品を追加する前に、その価格をメモしてください – $32
     * デフォルト数量：1
1. 製品を保存。
1. ストアフロントに移動し、前の手順で作成した製品を見つけます。 価格を下げる – $66
(66 = 32 + 34).
現在、バンドル製品の価格はそのオプションの価格の合計に等しいです。
1. Commerce Admin パネルに移動します。 **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**&#x200B;に移動します。
1. 以前にバンドル製品にオプションとして割り当てられたシンプルな製品の1つを見つけます。
SKU 24-MB01、価格は$34です。
1. 数量を0に変更します。
1. 製品を保存します。
1. ストアフロントに移動し、前の手順で作成したバンドル製品を見つけます。 価格を下げてください – $32。 以前は66 ドルの価格でしたが、SKU 24-MB01からは34 ドル、SKU 24-MB04からは32 ドルの合計でした。 商品24-MB01が在庫切れとなったところで、バンドル価格は32 ドルに設定されています。 それは他の製品の価格です、それは在庫オプションです。

<u>期待される結果</u>:

動的価格設定が有効になっているバンドル商品の価格は、オプションの在庫や在庫切れにかかわらず、一貫して計算されます。

<u>実際の結果</u>:

動的価格設定が有効になっているバンドル製品の価格が誤って計算される。 これは、在庫のあるオプションのみを考慮し、いずれかのオプションが在庫切れの場合、実際のオプションよりも表示額が低くなります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
