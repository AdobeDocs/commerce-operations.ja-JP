---
title: ACSD-51819：単一の見積もりIDで複数の注文を配置する
description: ACSD-51819 パッチを適用して、同じ見積もりIDを通じて複数の注文を配置できるAdobe Commerceの問題を修正します。
feature: Orders, Checkout
role: Admin, Developer
exl-id: dbca8790-d947-4104-bba9-b29abcfc0344
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-51819：単一の見積もりIDで複数の注文を配置する

ACSD-51819 パッチでは、同じ見積もりIDを通じて複数の注文を配置できる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41がインストールされている場合に利用できます。 パッチ IDはACSD-51819です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p2、2.4.5-p5、2.4.6、2.4.6-p4、2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4 - 2.4.4-p11、2.4.5-p3 - 2.4.5-p10、2.4.6 - 2.4.6-p8、2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

同じ見積もりIDで複数の注文を配置できます。

<u>複製する手順</u>:

1. ユーザーとしてログインします。
1. カートに商品を追加して、チェックアウトに進みます。
1. 任意の支払い方法を選択しますが、**[!UICONTROL Place Order]** ボタンをクリックしないでください。
1. 別のブラウザーで同じアカウントにログインします。
1. **[!UICONTROL Place Order]** ボタンをクリックせずに、同じ項目でチェックアウトに進みます。
1. 両方のシステムで&#x200B;**[!UICONTROL Place Order]** ボタンを同時にクリックします。
1. 両方のブラウザーに配置された注文を検証します。

<u>期待される結果</u>:

ひとつのブラウザーから最初に注文された注文のみが正常に処理されます。

<u>実際の結果</u>:

両方のブラウザーで注文が行われました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
