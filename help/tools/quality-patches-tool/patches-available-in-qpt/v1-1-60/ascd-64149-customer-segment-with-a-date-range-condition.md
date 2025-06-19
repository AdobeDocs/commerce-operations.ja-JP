---
title: ACSD-64149：編集する日付が 1 つだけの場合、[!UICONTROL Date range] 条件を持つ顧客セグメントを保存できます
description: ACSD-64149 パッチを適用すると、**[!UICONTROL Date range]**条件を持つ顧客セグメントを、1 つの日付のみを編集した場合に保存できるAdobe Commerceの問題を修正できます。
feature: Customers, Admin Workspace
role: Admin, Developer
exl-id: 5423bbd3-75e9-4137-b2d5-3a0ceb3384ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-64149：編集する日付が 1 つだけの場合、[!UICONTROL Date range] 条件を持つ顧客セグメントを保存できます

ACSD-64149 パッチでは、いずれかの日付のみを編集した場合に、日付範囲条件を持つ顧客セグメントを保存できる問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 がインストールされている場合に使用できます。 パッチ ID は ACSD-64149 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

日付範囲で指定された買い物かご内の製品に関する条件を使用して既存の顧客セグメントを編集すると、消費者 `matchCustomerSegmentProcessor` ードが SQL エラーで失敗します。

<u> 再現手順 </u>:

1. コンシューマー `matchCustomerSegmentProcessor` が実行されていることを確認します。

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. **[!UICONTROL Magento backend]** に行きなさい。
1. **[!UICONTROL Customers]**/**[!UICONTROL Segments]** に移動します。
1. 「**[!UICONTROL Add Segment]**」をクリックします。
1. **[!UICONTROL Segment Name]** を入力し、「**[!UICONTROL Assigned to Website]**」の下の web サイトを選択し、「**[!UICONTROL Status]**」が *アクティブ* に設定されていることを確認します。
1. 「**[!UICONTROL Save and Continue Edit]**」をクリックします。
1. 「**[!UICONTROL Conditions]**」タブに移動して、新しい条件 *製品 {}/{} 製品リスト*{*}* を追加します。
1. **[!UICONTROL Date range]** のサブ条件を追加し、有効な **[!UICONTROL Date range]** を設定します。
1. **[!UICONTROL Date range]** の横にある緑の確認ボタンをクリックします。
1. もう一度 **[!UICONTROL Date range]** をクリックし、日付選択を選択し、日付値の 1 つを編集して、緑のボタンをクリックして確認します。

<u> 期待される結果 </u>:

**[!UICONTROL Date range]** セレクターを使用して、編集時に日付に時間を追加しないでください。

<u> 実際の結果 </u>:

* **[!UICONTROL Date range]** セレクターを使用すると、日付に時間を追加できます。
   * 一方の日付には日付のみが含まれ、もう一方の日付には指定された日付と時刻の両方が含まれます。
* ログに次のエラーが表示されます。

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* Adobe Commerce on Cloud Infrastructure: アップグレードとパッチ > Commerce on Cloud Infrastructure ガイドのパッチの適用

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
