---
title: 'ACSD-63454: ドロップダウンおよび複数選択の属性のデフォルト値がデータベースに正しく保存されない'
description: ドロップダウンおよび複数選択の属性のデフォルト値がデータベースに正しく保存されないAdobe Commerceの問題を修正するには、ACSD-63454 パッチを適用します。
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 2%

---

# ACSD-63454: [!UICONTROL Dropdown]および[!UICONTROL Multiple Select]属性のデフォルト値がデータベースに正しく保存されない

ACSD-63454 パッチは、[!UICONTROL Dropdown]属性と[!UICONTROL Multiple Select]属性のデフォルト値がデータベースに正しく保存されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59がインストールされている場合に利用できます。 パッチ IDはACSD-63454です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!UICONTROL Dropdown]および[!UICONTROL Multiple Select]属性のデフォルト値がデータベースに正しく保存されません。デフォルト値を更新する代わりに、新しい値が古い値に追加され、コンマで区切られます。

<u>複製する手順</u>:

1. バックエンドにログインし、**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]**&#x200B;に移動します。
1. **[!UICONTROL Add New Attribute]**&#x200B;をクリックします。
1. 「**[!UICONTROL Properties]**」タブで、次の値を設定します。
   * **[!UICONTROL Default Label]**: *テスト*
   * **[!UICONTROL Catalog Input Type for Store Owner]**: *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**: **[!UICONTROL Is Default]**&#x200B;を選択せずに2つのオプションを追加します。
1. **[!UICONTROL Save Attribute]**&#x200B;をクリックします。
1. データベースで、`default_value`列が空であることを確認してください。

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. 戻って、2つのオプションのうちの1つを&#x200B;**[!UICONTROL Is Default]**&#x200B;に設定します。
1. データベースをもう一度確認して、`default_value`に選択したオプション IDが含まれていることを確認します。
1. 他のオプションを選択して、戻ってデフォルトオプションを変更します。

<u>期待される結果</u>:

新しいデフォルト値は、データベース内の古い値を置き換える必要があります。

<u>実際の結果</u>:

デフォルト値を新しい値に置き換える代わりに、新しい値をコンマで区切って古い値に追加します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
