---
title: 'ACSD-63323: [!UICONTROL Select All]機能を解決し、製品カテゴリのポップアップでページネーションとレコード数を強化します'
description: ACSD-63323 パッチを適用して、商品をカテゴリに追加する際に[!UICONTROL Select All] オプションが機能しないAdobe Commerceの問題を修正します。 さらに、ポップアップグリッドを使用して製品をカテゴリに追加する際に、ページネーションとレコード数ラベルが正しく機能するようになります。
feature: Products
role: Admin, Developer
exl-id: 96e318fd-f1dd-4b15-b171-78ae1c8e4e0d
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-63323: [!UICONTROL Select All]機能を解決し、製品カテゴリのポップアップでページネーションとレコード数を強化します

ACSD-63323 パッチは、カテゴリに製品を追加する際に&#x200B;**[!UICONTROL Select All]** オプションが機能しない問題を修正します。 さらに、ポップアップグリッドを使用して製品をカテゴリに追加する際に、ページネーションとレコード数ラベルが正しく機能するようになります。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60がインストールされている場合に利用できます。 パッチ IDはACSD-63323です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者/ **[!UICONTROL Categories]** / カテゴリを選択/ **[!UICONTROL Products in Category]** / **[!UICONTROL Add Products]**&#x200B;で&#x200B;**[!UICONTROL Select All]** オプションが機能しない問題を修正しました。 また、ポップアップグリッドを使用して商品をカテゴリに追加する際に、ページネーションとレコード数ラベルが正しく機能するように役立ちます。


<u>複製する手順</u>:

1. 次のコマンドを使用して、*1200*&#x200B;製品を生成します。

   ```shell
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;を開き、製品数を確認します：*1200* レコードが見つかりました。
1. 既定のカテゴリ > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**&#x200B;を開きます。
1. **[!UICONTROL Assign]** > **[!UICONTROL Select All]**&#x200B;をクリックします。
1. ページ上の製品数を値= *5*&#x200B;に変更します。


**期待される結果**:

*メッセージは次のようになります：1200件のレコードが見つかりました（1200件を選択）*

**実際の結果**:

* ページネーションが機能しない。
* 間違ったメッセージが表示されます：*5*&#x200B;件のレコードが見つかりました（*20*&#x200B;件を選択）

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
