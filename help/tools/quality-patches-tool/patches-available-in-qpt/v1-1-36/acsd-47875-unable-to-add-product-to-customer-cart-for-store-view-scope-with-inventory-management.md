---
title: ACSD-47875：在庫管理を使用したストア表示範囲の買い物かごに製品を追加できない
description: ACSD-47875 パッチを適用すると、在庫管理の特定のストア表示範囲で、管理者から商品を買い物かごに追加できないAdobe Commerceの問題を修正できます。
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: 10862e09-d561-4ed5-ab6f-cf002fae6850
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ACSD-47875：在庫管理を使用したストア表示範囲の買い物かごに製品を追加できない

ACSD-47875 パッチを使用すると、在庫管理の特定のストア表示範囲に対して管理者から製品を顧客の買い物かごに追加できない問題を修正できます。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.36 がインストールされている場合に使用できます。 パッチ ID は ACSD-47875 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理者ユーザーは、MSI がインストールされている特定のストア表示範囲に対して、管理者の **[!UICONTROL Manage Shopping Cart]** 機能を使用して製品を顧客の買い物かごに追加できません。

<u> 前提条件 </u>:

[!DNL Adobe Commerce Inventory Management (MSI)] モジュールがインストールされ、有効になっています。

<u> 再現手順 </u>:

1. Web サイト、ストア、ストアビューを作成します。
1. *デフォルト* 以外の追加ソースを作成します。
1. 新しい在庫を作成し、新しい web サイトと新しいソースに割り当てます。
1. 新しい web サイトの新しい顧客を作成します。
1. 新しい web サイトにのみ製品を割り当て、デフォルトの web サイトから割り当てを解除します。

   * 新しいソースを割り当て、新しいソースには数量 *0 より上*、デフォルトソースには *0* を設定します。

1. 管理者の **[!UICONTROL Customer Edit]** ページに移動します。 「**[!UICONTROL Manage Shopping Cart]**」をクリックします。
1. ストア表示の範囲を新しいストア表示に変更します。
1. 「**[!UICONTROL Products]**」セクションに移動し、製品を検索します。
1. 製品を選択し、「**[!UICONTROL Add selections to my cart]**」をクリックします。

<u> 期待される結果 </u>:

商品が買い物かごに追加されます。

<u> 実際の結果 </u>:

* 次のエラーが発生します。*追加しようとしている製品は使用できません。*
* 商品は買い物かごに追加されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
