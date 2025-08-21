---
title: ACP2E-3731：表示が [!UICONTROL Catalog, Search] い製品の書き出しには、他のストア表示のレコードが含まれます
description: ACP2E-3731 パッチを適用して、「表示フィルター」を「[!UICONTROL Catalog, Search]」に設定した商品の書き出しに、ストアスコープ属性のバリエーションが原因でマルチストアの設定で誤った行が含まれるAdobe Commerceを修正します。
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731：表示が [!UICONTROL Catalog, Search] い製品の書き出しには、他のストア表示のレコードが含まれます

ACP2E-3731 パッチでは、*[!UICONTROL Catalog, Search]* 表示の製品エクスポートが、マルチストア環境で他のストアビューのレコードを正しく含まない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3731 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p9

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

商品の書き出しには、ストアスコープの属性のバリエーションが原因で、マルチストアの設定で表示フィルターが *[!UICONTROL Catalog, Search]* に設定されている場合、誤った行が含まれます。

<u> 再現手順 </u>:

1. 管理パネルで、**[!UICONTROL Stores]** / **[!UICONTROL Settings]** / **[!UICONTROL All Stores]** に移動して、追加の web サイト、ストア、ストア表示を作成します。
1. **[!UICONTROL Stores]**/*[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]** に移動します。 「**[!UICONTROL Add Attribute Set]**」をクリックして、属性を作成します。 **[!UICONTROL Based On]** を *デフォルト* に設定します。
1. 製品を作成してメイン web サイトとセカンダリ web サイトの両方に割り当てます。
1. **[!UICONTROL Scope]** すべてのストアビュー *に設定した新しく作成* た属性のテキスト値を設定します。
1. スコープをセカンダリ ストア ビューに変更し、属性を別の値で更新します。
1. 範囲をデフォルトのストア表示とセカンダリストア表示に変更し、製品の表示を *個別に表示しない* に設定します。
1. **[!UICONTROL System]**/**[!UICONTROL Export]** に移動し、ドロップダウンメニューから *製品* を選択します。
1. **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]* のフィルターを設定し、「**[!UICONTROL Continue]**」をクリックします。
1. 次のコマンドを実行して書き出しを処理します。

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. 書き出したファイルを確認します。

<u> 期待される結果 </u>:

フィルターされたレコードのみがエクスポートされます。

<u> 実際の結果 </u>:

書き出されたファイルには、書き出し時に設定されたフィルタ条件に一致しないセカンダリ ストア ビューの行が含まれています。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
