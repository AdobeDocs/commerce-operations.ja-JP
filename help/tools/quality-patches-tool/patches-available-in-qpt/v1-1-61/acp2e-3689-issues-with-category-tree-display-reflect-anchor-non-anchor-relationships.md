---
title: ACP2E-3689：カテゴリーツリーの表示がより深いレベルになり、アンカー/アンカー以外の関係を反映する複数の問題
description: ACP2E-3689 パッチを適用して、深さ4以上のネストおよびアンカー/アンカー以外のリレーションにカテゴリーツリーが表示されるAdobe Commerceの問題を修正します。
feature: Categories, Page Content
role: Admin, Developer
exl-id: 8d3c484f-3f8d-4fc1-8b31-e850cb34341c
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACP2E-3689：カテゴリーツリーの表示がより深いレベルになり、アンカー/アンカー以外の関係を反映する複数の問題

>[!NOTE]
>
>このパッチは、バージョン 2.4.7以降の[ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md)に置き換わります。

ACP2E-3689 パッチは、深さ4を超えるネスト化およびアンカー/アンカー以外の関係を反映したカテゴリーツリー表示に関する複数の問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACP2E-3689です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

より深いレベル（4以上）のカテゴリーツリーが正しく表示されず、アンカー/アンカー以外の関係を反映しています。

<u>複製する手順</u>:

1. 4 レベルを超えるネストされたカテゴリを含むカテゴリーツリーを設定します。
1. 管理画面のカテゴリーツリーを展開して、別の場所に表示します。
   1. [!UICONTROL Related Products Rule]を設定し、カテゴリに基づいて条件を設定します。
   1. ウィジェットを作成し、[!UICONTROL Layout Updates]で[!UICONTROL Anchor categories]を選択します。

<u>期待される結果</u>:

カテゴリーツリーのすべてのレベルが適切に表示されます。

<u>実際の結果</u>:

カテゴリツリーの最初のいくつかのレベル（&lt;4）のみが使用可能です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
