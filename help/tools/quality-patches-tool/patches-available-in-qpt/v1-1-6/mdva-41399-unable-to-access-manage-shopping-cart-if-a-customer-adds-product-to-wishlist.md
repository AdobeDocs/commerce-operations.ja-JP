---
title: MDVA-41399：お客様がウィッシュリストに商品を追加した場合、ショッピングカートの管理にアクセスできない
description: MDVA-41399 パッチは、お客様がウィッシュリストに商品を追加した場合に、管理者ユーザーがショッピングカートの管理ページにアクセスできない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.6がインストールされている場合に利用できます。 パッチ IDはMDVA-41399です。 この問題はAdobe Commerce 2.4.2で修正されています。
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-41399：お客様がウィッシュリストに商品を追加した場合、ショッピングカートの管理にアクセスできない

MDVA-41399 パッチは、お客様がウィッシュリストに商品を追加した場合に、管理者ユーザーがショッピングカートの管理ページにアクセスできない問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.6がインストールされている場合に使用できます。 パッチ IDはMDVA-41399です。 この問題はAdobe Commerce 2.4.2で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

お客様がウィッシュリストに商品を追加した場合、管理者ユーザーはショッピングカートの管理ページにアクセスできません。

<u>前提条件</u>:

1. 2つ以上の商品を作成する。
1. 顧客の構築：
1. 開発者モードを有効にします。

<u>複製する手順</u>:

1. Storefrontに移動し、前提条件から顧客としてログインします。
1. 商品をウィッシュリストに追加します。
1. 管理パネルに移動し、作成した顧客編集ページに移動し、**ショッピングカートの管理** ボタンをクリックします。

<u>期待される結果</u>:

管理者ユーザーはショッピングカートを管理できます。

<u>実際の結果</u>:

管理者ユーザーにエラーメッセージが表示されます：*エラーが発生しました。 詳細については、エラーログを参照してください。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
