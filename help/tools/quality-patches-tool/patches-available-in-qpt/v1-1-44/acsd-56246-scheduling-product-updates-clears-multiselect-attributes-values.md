---
title: ACSD-56246：製品の更新をスケジュールすると、複数の選択属性の値が明確になる
description: ACSD-56246 パッチを適用して、製品のスケジュールが更新され、複数の選択属性の値がクリアになるAdobe Commerceの問題を修正します。
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: 1751a03d-2610-423f-be2f-b9d060452904
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 5%

---

# ACSD-56246：製品の更新スケジュールを設定すると、複数選択の属性値がクリアされる

ACSD-56246 パッチでは、製品の更新スケジュールが複数選択属性の値をクリアする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44がインストールされている場合に利用できます。 パッチ IDはACSD-56246です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

スケジュールされた製品は、複数の選択属性の値をクリアして更新されます。

<u>複製する手順</u>:

1. Adobe Commerceをインストールします。
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**&#x200B;に移動し、次の属性を作成します。

   * デフォルトラベル：プログラム
   * ストア所有者のカタログ入力タイプ：複数選択
   * オプションの管理（属性の値）：選択、Sunscape、Safetyshield
   * 属性コード：customer_program
   * 範囲：グローバル
   * 列に追加オプション：いいえ
   * フィルターオプションで使用：いいえ
   * ストアフロントのプロパティ
   * 位置：*333*
   * ストアフロントでHTML タグを許可する：いいえ

1. 実行
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. 実行
   `bin/magento setup:upgrade`.
1. **[!UICONTROL Admin]**/任意のシンプルな製品を選択/プログラム属性のすべての項目を選択/**[!UICONTROL Save the product]**&#x200B;をクリックします。
1. この製品のアップデートを次の分でスケジュールし、以下のコマンドを実行してコンテンツステージングを機能させます。
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>期待される結果</u>:

製品の&#x200B;**[!UICONTROL program]**&#x200B;属性は変更できません。

<u>実際の結果</u>:

製品の&#x200B;**[!UICONTROL program]**&#x200B;属性がクリアされました。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
