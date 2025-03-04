---
title: ACSD-63454：ドロップダウンと複数の選択属性のデフォルト値がデータベースに正しく保存されない
description: ACSD-63454 パッチを適用すると、ドロップダウン属性と複数選択の属性のデフォルト値がデータベースに正しく保存されないAdobe Commerceの問題が修正されます。
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
source-git-commit: cb73a5a346ec0e8acd59accf73605e25ef35c3ca
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-63454: [!UICONTROL Dropdown] および [!UICONTROL Multiple Select] 属性のデフォルト値がデータベースに正しく保存されない

ACSD-63454 パッチでは、[!UICONTROL Dropdown] および [!UICONTROL Multiple Select] 属性のデフォルト値がデータベースに正しく保存されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 がインストールされている場合に使用できます。 パッチ ID は ACSD-63454 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!UICONTROL Dropdown] 属性と [!UICONTROL Multiple Select] 属性のデフォルト値は、データベースに正しく保存されていません。デフォルト値を更新する代わりに、新しい値が古い値にコンマで区切って追加されます。

<u> 再現手順 </u>:

1. バックエンドにログインし、**[!UICONTROL Stores]**/*[!UICONTROL Attributes]*/**[!UICONTROL Product]** に移動します。
1. 「**[!UICONTROL Add New Attribute]**」をクリックします。
1. 「**[!UICONTROL Properties]**」タブで以下を設定します。
   * **[!UICONTROL Default Label]**: *test*
   * **[!UICONTROL Catalog Input Type for Store Owner]**: *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**:**[!UICONTROL Is Default]** を選択せずに 2 つのオプションを追加します。
1. 「**[!UICONTROL Save Attribute]**」をクリックします。
1. データベースの `default_value` 列が空であることを確認します。

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. 戻って、2 つのオプションの 1 つを **[!UICONTROL Is Default]** のように設定します。
1. データベースを再度確認し、選択したオプション ID`default_value` 含まれていることを確認します。
1. 戻って、もう一方のオプションを選択してデフォルトのオプションを変更します。

<u> 期待される結果 </u>:

新しいデフォルト値は、データベース内の古い値を置き換える必要があります。

<u> 実際の結果 </u>:

デフォルト値を新しい値に置き換える代わりに、古い値に新しい値をコンマで区切って追加します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
