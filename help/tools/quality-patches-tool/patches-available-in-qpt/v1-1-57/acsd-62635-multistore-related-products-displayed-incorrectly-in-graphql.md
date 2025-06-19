---
title: ACSD-62635：マルチストア関連製品が  [!DNL GraphQL] の場所で正しく表示されません。
description: ACSD-62635 パッチを適用すると、マルチストア関連商品が商品クエリに正しく表示されないAdobe Commerceの問題を修正でき  [!DNL GraphQL]  す。
feature: B2B
role: Admin, Developer
exl-id: 540cd37b-4dc5-42d1-a968-2989262effdd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-62635:[!DNL GraphQL] でマルチストア関連製品が正しく表示されない

ACSD-62635 パッチにより、マルチストア関連製品が [!DNL GraphQL] 製品クエリに正しく表示されない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-62635 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

B2B が有効になっている場合、リクエストでストアビュー範囲 [!DNL GraphQL] 使用されている場合でも、すべての web サイトからすべての関連製品が返されます。

<u> 再現手順 </u>:

1. 2 つの web サイト、ストア、ストア表示を作成します。
1. 次のシンプルな製品を作成します。
   * すべての web サイトに SKU *product1* が割り当てられている 1 つのメイン
   * 1 つは *Web サイト 1* にのみ割り当てられています
   * 1 つは *Web サイト 2* にのみ割り当てられます
   * 1 つは *Web サイト 1* と *Web サイト 2* の両方に割り当てられました
1. *product1* に関連するようにすべての製品を追加します。
1. [!UICONTROL B2B] と [!UICONTROL Shared Catalog] を有効にします。
1. すべての製品をデフォルトの共有カタログに追加します。
1. *Web サイト 1*[!DNL GraphQL] ストアコードをヘッダーに含む、*product1* とその関連製品を取得するリクエストを送信します。

<u> 期待される結果 </u>:

応答には、リクエストヘッダーで送信されたストアコードに対応する web サイトからの関連製品のみが含まれます。

<u> 実際の結果 </u>:

応答には、リクエストで指定されたストアコードに関係なく、すべての web サイトのすべての関連製品が含まれます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
