---
title: ACSD-56616：単純な在庫不足の間にバンドルされた製品のストアフロント表示
description: 関連するすべてのシンプルな商品の在庫がなくなると、バンドルされた商品がストアフロントに予期せず表示されるAdobe Commerceの問題を修正するには、ACSD-56616 パッチを適用します。
feature: Products
role: Admin, Developer
exl-id: 8b225d9d-1898-4c4d-81be-7b92cbf7d06f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-56616：在庫が不足しているときに、同梱商品のストアフロント表示が表示される。

ACSD-56616 パッチは、関連するすべてのシンプルな製品が在庫切れになった場合に、バンドルされた製品がストアフロントに予期せず表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45がインストールされている場合に利用できます。 パッチ IDはACSD-56616です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

単純な在庫不足の間に、バンドルされた商品の誤ったストアフロント表示が発生する。

<u>複製する手順</u>:

1. 新しいweb サイト/ストア/ストアフロントを作成する。
1. 新しいソースを作成します。
1. 新しいストックを作成し、新しく作成したweb サイトに割り当てます。
1. スケジュールどおりに更新するインデクサーを設定します。
1. S1 （数量= 1）とS2 （数量= 1）の2つのシンプルな商品を生成し、新しい在庫と新しいweb サイトに割り当てます。
1. *bundled1*&#x200B;製品を作成し、新しいweb サイトに関連付けて、カテゴリ *CAT*&#x200B;に配置します。
1. 2つの必須ドロップダウンオプションを定義し、単純な製品&#x200B;*S1*&#x200B;をoption1に、および&#x200B;*S2*&#x200B;をoption2にリンクします。
1. 製品を保存します。
1. **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]**&#x200B;に移動し、*ストア コードをURLに追加* = *はい*&#x200B;を有効にします。
1. ストアフロントを開き、同梱商品を購入します。
1. cronを2回実行します。
1. *CAT* カテゴリに戻ります。

<u>期待される結果</u>:

*bundle1*&#x200B;商品は在庫切れです。

<u>実際の結果</u>:

*bundle1*&#x200B;商品は、価格= *$0*&#x200B;で表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
