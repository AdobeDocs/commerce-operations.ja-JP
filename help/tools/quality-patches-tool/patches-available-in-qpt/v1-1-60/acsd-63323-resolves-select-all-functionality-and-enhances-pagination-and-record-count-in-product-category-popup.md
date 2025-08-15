---
title: ACSD-63323:[!UICONTROL Select All] 機能を解決し、製品カテゴリポップアップのページネーションとレコード数を強化します
description: ACSD-63323 パッチを適用すると、商品をカテゴリに追加する際に [!UICONTROL Select All] オプションが機能しないAdobe Commerceの問題を修正できます。 さらに、ポップアップグリッドを使用してカテゴリに製品を追加する際に、ページネーションとレコード数ラベルが正しく機能するようにします。
feature: Products
role: Admin, Developer
exl-id: 96e318fd-f1dd-4b15-b171-78ae1c8e4e0d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-63323:[!UICONTROL Select All] 機能を解決し、製品カテゴリポップアップのページネーションとレコード数を強化します

ACSD-63323 パッチは、製品をカテゴリに追加すると **[!UICONTROL Select All]** オプションが機能しない問題を修正します。 さらに、ポップアップグリッドを使用してカテゴリに製品を追加する際に、ページネーションとレコード数ラベルが正しく機能するようにします。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 がインストールされている場合に使用できます。 パッチ ID は ACSD-63323 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理者/**[!UICONTROL Select All]**/カテゴリを選択/**[!UICONTROL Categories]**/**[!UICONTROL Products in Category]** で「**[!UICONTROL Add Products]**」オプションが機能しない問題を修正しました。 また、ポップアップグリッドを使用して商品をカテゴリに追加する際に、ページネーションとレコード数ラベルが正しく機能するのにも役立ちます。


<u> 再現手順 </u>:

1. 次のコマンドを使用して *1200* 製品を生成します。

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]** を開き、製品数を確認します。見つかったレコード数は *1200* です。
1. デフォルトのカテゴリ/**[!UICONTROL Products in Category]**/**[!UICONTROL Add Products]** を開きます。
1. **[!UICONTROL Assign]**/**[!UICONTROL Select All]** をクリックします。
1. ページ上の製品数を value = *5* に変更します。


**期待される結果**:

*メッセージは次のようになります。1200 件のレコードが見つかりました（1200 件選択済み）*

**実際の結果**:

* ページネーションが機能しない。
* 間違ったメッセージが表示されます：*5* 件のレコードが見つかりました（*20* 件選択済み）

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
