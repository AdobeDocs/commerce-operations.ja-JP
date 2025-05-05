---
title: ACSD-60267：設定可能な製品オプションを通じて製品が追加された場合、FPT が正しく適用されません
description: ACSD-60267 パッチを適用すると、Adobe Commerceの問題を修正できます。この問題では、単純な商品を買い物かごに直接追加すると固定商品税（FPT）が正しく適用されますが、設定可能な商品オプションを使用して同じ商品を選択すると失敗します。
feature: Taxes
role: Admin, Developer
source-git-commit: c18ff9dd75ec6002c6461fcd3abd98ac8b97a9f7
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267：設定可能な製品オプションを通じて製品が追加された場合、FPT が正しく適用されません

ACSD-60267 パッチは、単純な製品を買い物かごに直接追加すると固定製品税（FPT）が正しく適用され、設定可能な製品オプションを使用して同じ製品を選択すると失敗する問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=ja) 1.1.54 がインストールされている場合に使用できます。 パッチ ID は ACSD-60267 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

FPT （固定製品税）は、FPT のシンプルな製品が買い物かごに追加されると正しく機能しますが、設定可能な製品の選択で製品が追加されると、FPT は追加されません。

<u> 再現手順 </u>:

1. *管理者*/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Tax]**/**[!UICONTROL Fixed Product Taxes]** に移動して、「*[!UICONTROL Enable FPT]*」を *はい* に設定します。
1. FPT 属性を作成して *[!UICONTROL Attribute Set]* に割り当てます。
1. **[!UICONTROL Stores]**/**[!UICONTROL Attributes]**/**[!UICONTROL Product]** を開きます。
1. *[!UICONTROL Default Label]*：属性を識別するラベルを入力します。
1. *[!UICONTROL Catalog Input for Store Owner]* を *[!UICONTROL Fixed Product Tax]* に設定します。
1. 新しい税金およびゾーンを作成し、それを新しい *[!UICONTROL Tax Rule]* に割り当てます。
1. 2 つのシンプルな製品で設定可能な製品を作成します。
1. 次に、これらの単純な製品に 2 つの異なる FPT 値を割り当てます。
1. インデックスを再作成し、ストアフロントで価格を確認します。
1. 商品を買い物かごに追加し、小計を確認します。

<u> 期待される結果 </u>:

* *[!UICONTROL Catalog]* ページは FPT を含む価格です。
* 買い物かごの小計には FPT が含まれます。

<u> 実際の結果 </u>:

* *[!UICONTROL Catalog]* ページには、FPT 値を含む価格は表示されません。
* 小計と概要が無効です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。

