---
title: ACSD-58108：結合テーブル名がないために、SQL エラーが順序グリッドのカスタムモジュール拡張で発生します
description: ACSD-58108 パッチを適用すると、注文グリッドのカスタムモジュール拡張機能に結合テーブル名が見つからず、特定の列をフィルタリングする際に SQL エラーが発生するAdobe Commerceの問題を修正できます。
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 26009fee51fb81e2517ad09319bac1190d127564
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-58108：結合テーブル名がないために、SQL エラーが順序グリッドのカスタムモジュール拡張で発生します

ACSD-58108 パッチでは、注文グリッドのカスタムモジュール拡張機能に結合テーブル名が見つからない場合、特定の列をフィルタリングする際に SQL エラーが発生する問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-58108 です。 この問題はAdobe Commerce 2.5.0 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

カスタムモジュール拡張機能を使用する場合、元の取得テーブルに結合テーブル名がないと、順序グリッドで SQL エラーが発生します。 この問題は、`addFilterToMap` テーブルを結合した後、特定の列に対して **[!UICONTROL sales_order_item]** 関数が機能せず、フィルタリング中にエラーが発生することが原因で発生します。

<u> 再現手順 </u>:

&#x200B;01. 2.4 開発インスタンスをインストールします。
&#x200B;02. 新しい注文を作成します。
&#x200B;03. SQL 拡張機能を持つカスタムモジュールをインストールします。
&#x200B;04. **[!UICONTROL Admin]**/**[!UICONTROL Sales]**/**[!UICONTROL Orders]** に移動します。
&#x200B;05. **[!UICONTROL Purchase Date]** フィルターを適用して、結果が出るまで待ちます。
&#x200B;06. フィルター **[!UICONTROL Product SKU]** 適用します。

<u> 期待される結果 </u>:

注文グリッド内の注文のフィルタリングは、エラーなしで機能します。

<u> 実際の結果 </u>:

順序グリッドでフィルターを適用すると、エラーが発生します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
