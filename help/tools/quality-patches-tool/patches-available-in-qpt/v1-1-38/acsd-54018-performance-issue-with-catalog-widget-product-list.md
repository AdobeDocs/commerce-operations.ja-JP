---
title: ACSD-54018：カタログウィジェット製品リストのパフォーマンスの問題
description: ACSD-54018 パッチを適用して、条件と属性タイプのブール値を含むカタログウィジェット製品リストを追加する際にページの読み込みが遅くなるAdobe Commerceの問題を修正します。
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 2fb7ca37-78cc-45f4-86a3-d922cf4d1457
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-54018：カタログウィジェット製品リストのパフォーマンスの問題

ACSD-54018 パッチは、条件と属性タイプのブール値を含むカタログウィジェット製品リストを追加する際に、ページの読み込みが遅くなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.38がインストールされている場合に利用できます。 パッチ IDはACSD-54018です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

条件と属性タイプのブール値を持つカタログウィジェット製品リストを追加すると、ページの読み込みが遅くなります。

<u>複製する手順</u>:

1. 10万もの商品を生み出す。
1. スコープが[!UICONTROL Store View]に設定されたbool属性を作成します。
1. すべての属性セットに属性を割り当てます。
   * すべての製品に属性値&#x200B;*Yes*&#x200B;を割り当てます。
1. 次に、**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、100,000の製品をすべて選択します。
   * **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**&#x200B;を選択します。
   * bool属性を&#x200B;*Yes*&#x200B;に設定して保存します。
   * この手順でログアウトした場合は、*メモ*&#x200B;を確認してください。
1. CLIに移動し、`php bin/magento queue:con:start product_action_attribute.update`を実行します。
   * すべての製品の属性が更新されていることを確認します。
1. 次に、**[!UICONTROL Content]** > **[!UICONTROL Pages]**&#x200B;に移動し、新しいページを作成します。
1. **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**&#x200B;を開きます。
1. *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*&#x200B;を選択してください。
1. 条件&#x200B;*[!UICONTROL Created attribute]*&#x200B;を&#x200B;*[!UICONTROL Yes]*&#x200B;に設定して保存します。
1. フロントエンドに移動し、作成したページを開きます。
1. フルページキャッシュを無効にし、HTML キャッシュをブロックします。
1. ページの読み込み速度を確認します。
1. ページを数回再読み込みして、平均読み込み時間を計算します。

<u>期待される結果</u>:

ページの読み込みが速くなります。

<u>実際の結果</u>:

ページの読み込みに5～10秒かかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
