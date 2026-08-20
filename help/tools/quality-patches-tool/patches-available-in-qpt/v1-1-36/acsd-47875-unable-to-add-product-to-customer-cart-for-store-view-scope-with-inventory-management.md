---
title: ACSD-47875：在庫管理機能で、ストアビューの範囲をカートに商品を追加できない
description: 在庫管理機能を使用して、特定のストアビュー範囲の管理者から商品をカスタマーカートに追加できないAdobe Commerceの問題を修正するには、ACSD-47875 パッチを適用します。
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: 10862e09-d561-4ed5-ab6f-cf002fae6850
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# ACSD-47875：在庫管理機能で、ストアビューの範囲をカートに商品を追加できない

ACSD-47875 パッチは、在庫管理機能を使用して特定のストアビュースコープの管理者から顧客カートに商品を追加できない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.36がインストールされている場合に利用できます。 パッチ IDはACSD-47875です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーは、MSIがインストールされた特定のストアビュースコープの管理者機能&#x200B;**[!UICONTROL Manage Shopping Cart]**&#x200B;を使用して、製品を顧客カートに追加できません。

<u>前提条件</u>:

[!DNL Adobe Commerce Inventory Management (MSI)]個のモジュールがインストールされ、有効になっています。

<u>複製する手順</u>:

1. web サイト、ストア、ストアビューを作成する。
1. *Default*&#x200B;以外のソースを追加します。
1. 新しい在庫を作成し、新しいweb サイトと新しいソースに割り当てます。
1. 新しいweb サイトの新規顧客を作成します。
1. 新しいweb サイトにのみ製品を割り当てる。デフォルトのweb サイトから割り当てを解除する。

   * 新しいソースを割り当て、新しいソースには数量&#x200B;*0*&#x200B;を、デフォルトのソースには&#x200B;*0*&#x200B;を設定します。

1. 管理画面の&#x200B;**[!UICONTROL Customer Edit]** ページに移動します。 **[!UICONTROL Manage Shopping Cart]**&#x200B;をクリックします。
1. ストアビューの範囲を新しいストアビューに変更します。
1. 「**[!UICONTROL Products]**」セクションに移動し、製品を検索します。
1. 製品を選択し、**[!UICONTROL Add selections to my cart]**&#x200B;をクリックします。

<u>期待される結果</u>:

商品がカートに追加されます。

<u>実際の結果</u>:

* 次のエラーがスローされます：*追加しようとしている製品は利用できません。*
* 商品がショッピングカートに追加されない。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
