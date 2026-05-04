---
title: ACSD-48417：スケジュール変更作成後のSQL エラー
description: ACSD-48417 パッチを適用して、製品のスケジュール変更を作成し、別の製品を保存した後にSQL エラーが表示されるAdobe Commerceの問題を修正します。
feature: Storage
role: Admin
exl-id: c8e7c7aa-ac53-4218-8c3c-ea2240af17c9
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-48417：スケジュール変更作成後のSQL エラー

ACSD-48417 パッチは、製品のスケジュール変更を作成し、別の製品を保存した後にSQL エラーが表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26がインストールされている場合に利用できます。 パッチ IDはACSD-48417です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品のスケジュール変更を作成し、別の製品を保存すると、SQL エラーが表示されます。

<u>複製する手順</u>:

1. Magento 2.4-develop EE + Sample Dataをインストールします。
1. 管理パネル > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動します。
1. 任意の商品を編集します（例：ジャーストダッフルバッグ [SKU: 24-MB01]）。
1. 新しい更新をスケジュール：
   * **[!UICONTROL Save as a New Update]**&#x200B;を選択
   * 更新名：「更新1」
   * 開始日：現在の時間+1分
   * 終了日：現在の時間+1時間
   * 製品名を「Joust Duffle Bag 2」に変更
   * 製品を保存します。
1. CLIに移動してcronを実行し、スケジュールが適用されるまで待ちます。

   ```shell
   bin/magento cron:run && bin/magento cron:run
   ```

1. 繰り返しますが、**[!UICONTROL Catalog]** > **[!UICONTROL Products]**&#x200B;に移動し、設定可能な製品を編集します（例：Chaz Kangeroo Hoodie [SKU: MH01]）。

   * すべてのバリエーションを無効にします。 アクション列> **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**&#x200B;に移動します。
   * 設定可能なものを保存します。

<u>期待される結果</u>:

製品の保存時にエラーが発生しません。

<u>実際の結果</u>:

次のエラーが発生します。

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
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
