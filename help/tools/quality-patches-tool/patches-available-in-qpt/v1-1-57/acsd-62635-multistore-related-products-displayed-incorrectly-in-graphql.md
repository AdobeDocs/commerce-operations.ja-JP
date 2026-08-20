---
title: 'ACSD-62635: [!DNL GraphQL]でマルチストア関連商品が正しく表示されない'
description: マルチストア関連商品が [!DNL GraphQL] 商品クエリに正しく表示されないAdobe Commerceの問題を修正するには、ACSD-62635 パッチを適用します。
feature: B2B
role: Admin, Developer
exl-id: 540cd37b-4dc5-42d1-a968-2989262effdd
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-62635: [!DNL GraphQL]でマルチストア関連商品が正しく表示されない

ACSD-62635 パッチは、[!DNL GraphQL]製品クエリでマルチストア関連製品が正しく表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-62635です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

B2Bが有効になっている場合、[!DNL GraphQL] リクエストは、ストアビューの範囲がリクエストで使用されている場合でも、すべてのweb サイトからすべての関連製品を返します。

<u>複製する手順</u>:

1. 2つのweb サイト、ストア、ストアビューを作成します。
1. 以下のシンプルな製品を作成します。
   * すべてのweb サイトに割り当てられたSKU *product1*&#x200B;を持つ1つのメイン
   * *Web サイト 1*&#x200B;にのみ割り当てられている1人
   * *Web サイト 2*&#x200B;にのみ割り当てられている1人
   * *Web サイト 1*&#x200B;と&#x200B;*Web サイト 2*&#x200B;の両方に割り当てられている1人
1. *product1*&#x200B;に関連するすべての製品を追加します。
1. [!UICONTROL B2B]と[!UICONTROL Shared Catalog]を有効にします。
1. すべての製品をデフォルトの共有カタログに追加します。
1. [!DNL GraphQL] リクエストを送信して、*product1*&#x200B;とその関連製品を取得し、ストアコードが&#x200B;*Web サイト 1*&#x200B;のヘッダーに表示されるようにします。

<u>期待される結果</u>:

応答には、リクエストヘッダーで送信されたストアコードに対応するweb サイトからの関連製品のみが含まれます。

<u>実際の結果</u>:

応答には、リクエストで指定されたストアコードに関係なく、すべてのweb サイトのすべての関連製品が含まれます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
