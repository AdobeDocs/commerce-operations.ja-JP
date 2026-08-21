---
title: 'ACSD-53628: CSV販売注文レポートに誤った特殊文字が表示される'
description: CSV受注レポートに誤った特殊文字が表示されるAdobe Commerceの問題を修正するには、ACSD-53628 パッチを適用します。
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: b6293efe-fbeb-4b1e-b408-34dc86228b8e
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-53628: CSV販売注文レポートに誤った特殊文字が表示される

ACSD-53628 パッチは、CSV販売注文レポートに誤った特殊文字が表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.37がインストールされている場合に利用できます。 パッチ IDはACSD-53628です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法）:2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法）:2.3.7 ～ 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

CSV販売注文レポートに誤った特殊文字が表示される。

<u>複製する手順</u>:

1. 通貨設定で&#x200B;**[!UICONTROL Base Currency]**&#x200B;と&#x200B;**[!UICONTROL Default Display Currency]**&#x200B;をユーロに変更します。
1. 注文する。
1. 管理者サイドバーで、**[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;に移動します。
1. 日付を選択します。 **[!UICONTROL Show Report]**&#x200B;をクリックします。 **[!UICONTROL Export]**&#x200B;をクリックしてCSVをエクスポートします。

<u>期待される結果</u>:

書き出したCSV ファイルの特殊文字がExcelで正しく表示される。

<u>実際の結果</u>:

CSV販売注文レポートで特殊文字が正しく表示されない。


## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
