---
title: ACSD-56246：製品アップデートのスケジュール設定の複数選択属性値のクリア
description: ACSD-56246 パッチを適用して、製品アップデートのスケジュールで複数選択属性値がクリアされるAdobe Commerceの問題を修正してください。
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: 1751a03d-2610-423f-be2f-b9d060452904
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-56246：製品アップデートをスケジュールすると、複数選択の属性値がクリアされる

ACSD-56246 パッチでは、製品アップデートのスケジュールによって複数選択属性の値がクリアされる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 がインストールされている場合に使用できます。 パッチ ID は ACSD-56246 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

スケジュールされた製品アップデートにより、複数選択の属性値がクリアされます。

<u> 再現手順 </u>:

1. Adobe Commerceをインストールします。
1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Attributes]**/**[!UICONTROL Product]** に移動し、次の属性を作成します。

   * デフォルトのラベル：プログラム
   * 店舗所有者のカタログ入力タイプ：複数選択
   * オプション （属性の値）の管理：Choice、Sunscape、Safetyshield
   * 属性コード：customer_program
   * 範囲：グローバル
   * 列に追加オプション：いいえ
   * フィルターオプションで使用：なし
   * ストアフロント プロパティ
   * 位置：*333*
   * ストアフロントでのHTML タグの許可：いいえ

1. 実行
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`。
1. 実行
   `bin/magento setup:upgrade`。
1. **[!UICONTROL Admin]** / シンプルな製品を選択/ プログラム属性のすべての項目を選択/**[!UICONTROL Save the product]** をクリックに移動します。
1. 次分にこの製品のアップデートをスケジュールし、次のコマンドを実行してコンテンツのステージングを機能させます。
   `for i in {1..100}; do bin/magento cron:run; done`。

<u> 期待される結果 </u>:

製品の **[!UICONTROL program]** 属性は変更しないでください。

<u> 実際の結果 </u>:

製品の **[!UICONTROL program]** 属性がクリアされます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
