---
title: ACSD-51036：同時REST API呼び出し中に競合条件が発生すると、配送状況が上書きされる
description: 同時REST API呼び出し中に競合状態が発生し、注文済みテーブルの配送ステータスが上書きされるAdobe Commerceの問題を修正するには、ACSD-51036 パッチを適用します。
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-51036：同時REST API呼び出し中に競合条件が発生すると、注文済みテーブルの配送状況が上書きされます

ACSD-51036 パッチでは、同時REST API呼び出し中の競合条件により、注文されたテーブルの出荷状況が上書きされる問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.31がインストールされている場合に利用できます。 パッチ IDはACSD-51036です。 この問題は、Adobe Commerce 2.4.5で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

同時REST API呼び出し中の競合条件により、注文されたテーブルの配送状況が上書きされます。

<u>複製する手順</u>:

1. 2つのアイテムを含む注文を作成します。
1. 請求書品目A.
1. 商品Aの返品リクエストをREST API経由で同時に送信すると同時に、商品Bの返品リクエストを送信します。
1. **[!UICONTROL Admin Panel]**&#x200B;の注文に移動します。

<u>期待される結果</u>

*[!UICONTROL Items]*&#x200B;件の注文テーブルのアイテム Bに&#x200B;*[!UICONTROL Shipped 1]*&#x200B;件のステータスが存在する必要があります。

<u>実際の結果</u>

*[!UICONTROL Items]*&#x200B;の順序付きテーブルのアイテム Bに&#x200B;*[!UICONTROL Shipped 1]*&#x200B;の状態がありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
