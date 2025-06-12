---
title: MDVA-41399：顧客がウィッシュリストに製品を追加すると、買い物かごの管理にアクセスできない
description: MDVA-41399 パッチは、顧客がウィッシュリストに製品を追加した場合に、管理者ユーザーが買い物かごの管理ページにアクセスできない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.6 がインストールされている場合に利用できます。 パッチ ID は MDVA-41399。 この問題はAdobe Commerce 2.4.2 で修正されました。
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41399：顧客がウィッシュリストに製品を追加すると、買い物かごの管理にアクセスできない

MDVA-41399 パッチは、顧客がウィッシュリストに製品を追加した場合に、管理者ユーザーが買い物かごの管理ページにアクセスできない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.6 がインストールされている場合に使用できます。 パッチ ID は MDVA-41399。 この問題はAdobe Commerce 2.4.2 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

顧客がウィッシュリストに製品を追加すると、管理者ユーザーは買い物かごの管理ページにアクセスできません。

<u> 前提条件 </u>:

1. 2 つ以上の商品を作成します。
1. 顧客を作成します。
1. 開発者モードを有効にします。

<u> 再現手順 </u>:

1. ストアフロントに移動し、前提条件から顧客としてログインします。
1. ウィッシュリストに商品を追加します。
1. 管理パネルに移動し、作成した顧客編集ページに移動して、「**買い物かごを管理**」ボタンをクリックします。

<u> 期待される結果 </u>:

管理者ユーザーは、買い物かごを管理できます。

<u> 実際の結果 </u>:

管理者ユーザーに「*エラーが発生しました。 詳しくは、エラーログを参照してください。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) の節を参照してください。
