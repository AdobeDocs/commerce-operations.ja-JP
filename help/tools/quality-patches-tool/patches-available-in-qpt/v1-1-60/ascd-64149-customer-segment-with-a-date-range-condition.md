---
title: 'ACSD-64149: [!UICONTROL Date range]条件を持つ顧客セグメントは、1つの日付のみが編集されたときに保存できます'
description: ACSD-64149 パッチを適用して、**[!UICONTROL Date range]**条件を持つ顧客セグメントを保存できるAdobe Commerceの問題を修正します。
feature: Customers, Admin Workspace
role: Admin, Developer
exl-id: 5423bbd3-75e9-4137-b2d5-3a0ceb3384ad
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-64149: [!UICONTROL Date range]条件を持つ顧客セグメントは、1つの日付のみが編集されたときに保存できます

ACSD-64149 パッチでは、日付の一部しか編集されていない場合に、日付範囲の条件を持つ顧客セグメントを保存できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60がインストールされている場合に利用できます。 パッチ IDはACSD-64149です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

日付範囲で指定されたショッピングカート内の製品に関する条件を含む既存の顧客セグメントを編集する場合、コンシューマー`matchCustomerSegmentProcessor`はSQL エラーで失敗します。

<u>複製する手順</u>:

1. コンシューマー`matchCustomerSegmentProcessor`が実行されていることを確認します。

   ```shell
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. **[!UICONTROL Magento backend]**&#x200B;に移動します。
1. **[!UICONTROL Customers]** > **[!UICONTROL Segments]**&#x200B;に移動します。
1. **[!UICONTROL Add Segment]**&#x200B;をクリックします。
1. **[!UICONTROL Segment Name]**&#x200B;を入力し、**[!UICONTROL Assigned to Website]**&#x200B;の下にあるweb サイトを選択し、**[!UICONTROL Status]**&#x200B;が&#x200B;*アクティブ*&#x200B;に設定されていることを確認します。
1. **[!UICONTROL Save and Continue Edit]**&#x200B;をクリックします。
1. **[!UICONTROL Conditions]** タブに移動し、新しい条件を追加します：*製品{} > {}製品リスト*{*}*。
1. **[!UICONTROL Date range]**&#x200B;のサブ条件を追加し、有効な&#x200B;**[!UICONTROL Date range]**&#x200B;を設定します。
1. **[!UICONTROL Date range]**&#x200B;の横にある緑色の確認ボタンをクリックします。
1. もう一度&#x200B;**[!UICONTROL Date range]**&#x200B;をクリックし、日付選択ツールを選択し、日付値のいずれかを編集して、緑色のボタンをクリックして確定します。

<u>期待される結果</u>:

**[!UICONTROL Date range]** セレクターは、編集時に日付に時間を追加しないでください。

<u>実際の結果</u>:

* **[!UICONTROL Date range]** セレクターは、日付に時間を追加します。
   * 一方の日付には日付のみが指定され、もう一方の日付には日付と時刻の両方が指定されます。
* ログに次のエラーが表示されます。

  ```yaml
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Adobe Commerce オンクラウドインフラストラクチャ：アップグレードとパッチ/パッチの適用については、Commerce オンクラウドインフラストラクチャガイドを参照してください。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
