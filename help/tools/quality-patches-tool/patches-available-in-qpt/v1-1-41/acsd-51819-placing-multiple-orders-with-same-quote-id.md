---
title: ACSD-51819：単一の見積もりIDで複数の注文を配置する
description: ACSD-51819 パッチを適用して、同じ見積もりIDを通じて複数の注文を配置できるAdobe Commerceの問題を修正します。
feature: Orders, Checkout
role: Admin, Developer
exl-id: dbca8790-d947-4104-bba9-b29abcfc0344
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%
---
# ACSD-51819：単一の見積もりIDで複数の注文を配置する

ACSD-51819 パッチでは、同じ見積もりIDを通じて複数の注文を配置できる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.41がインストールされている場合に利用できます。 パッチ IDはACSD-51819です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p2、2.4.5-p5、2.4.6、2.4.6-p4、2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4 - 2.4.4-p11、2.4.5-p3 - 2.4.5-p10、2.4.6 - 2.4.6-p8、2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
