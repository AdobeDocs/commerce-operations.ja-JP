---
title: 'ACSD-48313: [!UICONTROL configurable_variations]列は、属性値にコンマが含まれている場合は解析されません'
description: 属性値にコンマが含まれている場合に[!UICONTROL configurable_variations]列が解析されないAdobe Commerceの問題を修正するには、ACSD-48313 パッチを適用します。
feature: Attributes, Configuration
role: Admin
exl-id: 1ce0c8dc-0d03-4ebd-b02a-08090b244190
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-48313: **[!UICONTROL configurable_variations]**&#x200B;列は、属性値にコンマが含まれている場合は解析されません

ACSD-48313 パッチは、属性値にコンマが含まれている場合、**[!UICONTROL configurable_variations]**&#x200B;列が解析されない問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-48313です。 この問題が修正されるバージョンはまだ利用できません。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定可能な製品を書き出した後、**[!UICONTROL configurable_variations]**&#x200B;属性の書式設定の問題により、結果のファイルを再び読み込むことができません。 これは、コンマを含む属性オプションがある場合に発生します。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;に移動し、新しい属性&#x200B;_サイズ_&#x200B;を作成します。
1. ストア所有者のカタログ入力タイプ：**[!UICONTROL Dropdown]**。
1. コンマを含むオプションを作成します。例：
   * 10,2cm
   * 15,5cm
1. **[!UICONTROL Advanced Attribute Properties]** – 範囲：_グローバル_。
1. 「設定を作成」機能を使用して、新しい設定可能な製品を作成します。
1. 上記の属性&#x200B;_サイズ_&#x200B;と、コンマを含む2つのオプションを選択します。
1. **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**&#x200B;に移動し、新しい商品エクスポートを作成します（CSV ファイルの生成をトリガーするためにcronを実行します）。
1. **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]**&#x200B;に移動し、上記で作成した同じCSV ファイルを再インポートしてみてください。

<u>期待される結果</u>:

ユーザーはファイルを読み込むことができます。

<u>実際の結果</u>:

```text
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
