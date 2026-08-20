---
title: ACSD-51574：別の画像に置き換えると、フロントエンドで画像が更新されない
description: ACSD-51574 パッチを適用して、別の画像に置き換えた後、フロントエンドで画像が更新されないAdobe Commerceの問題を修正します。
feature: Configuration
role: Admin
exl-id: 199674fc-c3b3-4fee-9061-f0546833c1cd
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-51574：別の画像に置き換えると、フロントエンドで画像が更新されない

ACSD-51574 パッチは、別の画像に置き換えた後にフロントエンドで画像が更新されない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.37がインストールされている場合に利用できます。 パッチ IDはACSD-51574です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

別の画像に置き換えた後、画像はフロントエンドで更新されません。

<u>複製する手順</u>:

1. いくつかの画像を含む商品を作成する。
1. 製品を編集し、既知の名前の画像をアップロードします（例：*image.jpg*）。
1. 製品を保存します。
1. 製品をもう一度編集し、古いバージョンの画像を削除し、同じ名前の新しいバージョンの画像をアップロードします。 **新しいバージョンが明らかに異なることを確認して、問題を確認してください。**
1. 製品を保存します。 管理者とフロントエンドの両方が画像を表示します。
1. 製品をもう一度編集し、同じ新しい画像をもう一度アップロードします（同じ名前を使用）。
1. 商品を保存し、フロントエンドの商品ページを確認します。

<u>期待される結果</u>:

2回目にアップロードされた画像は、名前を変更した画像名とともに、新しい画像になります。

<u>実際の結果</u>:

2回目にアップロードされた画像は、同じ新しい画像ではなく、以前に削除された古いバージョンの画像です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
