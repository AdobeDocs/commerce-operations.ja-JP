---
title: 'ACP2E-3731: [!UICONTROL Catalog, Search]個の表示可能な製品の書き出しには、他のストアビューのレコードが含まれます'
description: ACP2E-3731 パッチを適用して、表示フィルターが[!UICONTROL Catalog, Search]に設定された商品の書き出しに、ストア範囲の属性のバリエーションが原因でマルチストア設定に誤った行が含まれるAdobe Commerceを修正します。
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
exl-id: e363e63c-26fb-43eb-86f7-30057f7d9897
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACP2E-3731: [!UICONTROL Catalog, Search]個の表示可能な製品の書き出しには、他のストアビューのレコードが含まれます

ACP2E-3731 パッチは、*[!UICONTROL Catalog, Search]*&#x200B;の表示を含む製品の書き出しに、マルチストア環境の他のストアビューのレコードが誤って含まれる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACP2E-3731です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p9

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストア範囲の属性のバリエーションが原因で、マルチストア設定で表示フィルターが&#x200B;*[!UICONTROL Catalog, Search]*&#x200B;に設定されている場合、製品の書き出しに誤った行が含まれます。

<u>複製する手順</u>:

1. 管理パネルで、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]**&#x200B;に移動して、追加のweb サイト、ストア、ストアビューを作成します。
1. **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**&#x200B;に移動します。 **[!UICONTROL Add Attribute Set]**&#x200B;をクリックして属性を作成します。 **[!UICONTROL Based On]**&#x200B;を&#x200B;*Default*&#x200B;に設定します。
1. 商品を作成し、メインのweb サイトとセカンダリのweb サイトの両方に割り当てます。
1. **[!UICONTROL Scope]**&#x200B;が&#x200B;*すべてのストアビュー*&#x200B;に設定された、新しく作成した属性のテキスト値を設定します。
1. スコープをセカンダリストアビューに変更し、属性を別の値で更新します。
1. 範囲をデフォルトのストアビューとセカンダリストアビューに変更し、製品の表示を&#x200B;*個別に表示されない*&#x200B;に設定します。
1. **[!UICONTROL System]** > **[!UICONTROL Export]**&#x200B;に移動し、ドロップダウンメニューから&#x200B;*製品*&#x200B;を選択します。
1. **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]*&#x200B;のフィルターを設定し、**[!UICONTROL Continue]**&#x200B;をクリックします。
1. 次のコマンドを実行して、書き出しを処理します。

   ```shell
   php bin/magento queue:consumers:start exportProcessor
   ```

1. 書き出したファイルを確認します。

<u>期待される結果</u>:

フィルタリングされたレコードのみが書き出されます。

<u>実際の結果</u>:

書き出されたファイルには、セカンダリストアビューの行が含まれており、書き出し中に設定されたフィルター条件と一致しません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
