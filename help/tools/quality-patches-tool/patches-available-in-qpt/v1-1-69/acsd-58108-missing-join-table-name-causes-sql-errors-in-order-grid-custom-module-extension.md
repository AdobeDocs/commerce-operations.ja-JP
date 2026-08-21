---
title: ACSD-58108：結合テーブル名が欠落しているため、注文グリッドカスタムモジュール拡張機能でSQL エラーが発生する
description: ACSD-58108 パッチを適用して、特定の列をフィルタリングする際にorder grid カスタムモジュール拡張機能で結合テーブル名が欠落している場合にSQL エラーが発生するAdobe Commerceの問題を修正します。
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
exl-id: 1195e1c3-575c-48d6-8a10-c300f9bbb84a
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-58108：結合テーブル名が欠落しているため、注文グリッドカスタムモジュール拡張機能でSQL エラーが発生する

ACSD-58108 パッチでは、注文グリッドカスタムモジュール拡張機能で結合テーブル名が欠落している場合に、特定の列をフィルタリングする際にSQL エラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-58108です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

元の取得テーブルで結合テーブル名が見つからない場合、カスタムモジュール拡張機能を使用すると、注文グリッドでSQL エラーが発生します。 この問題は、**[!UICONTROL sales_order_item]** テーブルに参加した後、`addFilterToMap`関数が特定の列に対して機能せず、フィルタリング中にエラーが発生したことが原因で発生します。

<u>複製する手順</u>:

&#x200B;01. 2.4-develop インスタンスをインストールします。
&#x200B;02. 新しい注文を作成します。
&#x200B;03. SQL拡張機能を使用したカスタムモジュールのインストール。
&#x200B;04. **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**&#x200B;に移動します。
&#x200B;05. **[!UICONTROL Purchase Date]** フィルターを適用し、結果を待ちます。
&#x200B;06. **[!UICONTROL Product SKU]** フィルターを適用します。

<u>期待される結果</u>:

注文グリッドの注文のフィルタリングは、エラーなしで機能します。

<u>実際の結果</u>:

注文グリッドにフィルターを適用すると、エラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
