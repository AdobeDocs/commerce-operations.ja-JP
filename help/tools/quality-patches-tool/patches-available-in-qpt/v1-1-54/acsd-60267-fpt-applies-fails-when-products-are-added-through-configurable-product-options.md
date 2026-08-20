---
title: ACSD-60267：設定可能な製品オプションを通じて製品が追加されると、FPTが正しく適用されない
description: ACSD-60267 パッチを適用して、シンプルな商品をカートに直接追加する際に固定商品税（FPT）が正しく適用されますが、設定可能な商品オプションを使用して同じ商品を選択すると失敗するAdobe Commerceの問題を修正します。
feature: Taxes
role: Admin, Developer
exl-id: 919b3b96-1995-4faf-aaf1-b5cbb20e46bf
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-60267：設定可能な製品オプションを通じて製品が追加されると、FPTが正しく適用されない

ACSD-60267 パッチは、単純な製品をカートに直接追加する際に固定製品税（FPT）が正しく適用されますが、設定可能な製品オプションを使用して同じ製品を選択する際に失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-60267です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

固定製品税（FPT）は、FPTを含むシンプルな製品がカートに追加された場合は正しく機能しますが、設定可能な製品選択を介して製品が追加された場合はFPTが追加されません。

<u>複製する手順</u>:

1. *[!UICONTROL Enable FPT]*&#x200B;を&#x200B;*Yes*&#x200B;に設定し、*Admin* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]**&#x200B;に移動します。
1. FPT属性を作成し、*[!UICONTROL Attribute Set]*&#x200B;に割り当てます。
1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;を開きます。
1. *[!UICONTROL Default Label]*&#x200B;に、属性を識別するラベルを入力します。
1. *[!UICONTROL Catalog Input for Store Owner]*&#x200B;を&#x200B;*[!UICONTROL Fixed Product Tax]*&#x200B;に設定します。
1. 新しい税とゾーンを作成し、新しい&#x200B;*[!UICONTROL Tax Rule]*&#x200B;に割り当てます。
1. シンプルな2つの商品から構成できる商品を作成する。
1. 次に、これらのシンプルな製品に2つの異なるFPT値を割り当てます。
1. ストアフロントの価格をインデックス再作成して確認します。
1. 商品をカートに追加し、小計を確認します。

<u>期待される結果</u>:

* *[!UICONTROL Catalog]* ページには、FPTを含む価格が表示されます。
* 買い物かごの小計にはFPTが含まれます。

<u>実際の結果</u>:

* *[!UICONTROL Catalog]* ページには、FPT値を含む価格が表示されません。
* 小計と概要が無効です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
