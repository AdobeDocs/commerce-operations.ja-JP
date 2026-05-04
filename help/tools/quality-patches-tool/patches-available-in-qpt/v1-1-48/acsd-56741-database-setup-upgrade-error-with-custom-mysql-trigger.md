---
title: ACSD-56741：カスタム MySQL トリガーを使用したデータベース設定エラーのトラブルシューティング
description: ACSD-56741 パッチを適用して、インデックス付けと [!DNL MView]に関係のないデータベース内のカスタム MySQL トリガーが原因で、「setup:upgrade」中に「setup:upgrade」タイプの値で配列オフセットにアクセスしようとすると、エラーメッセージ*が表示されるAdobe Commerceの問題を修正します。
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-56741：カスタム MySQL トリガーを使用したデータベース設定エラーのトラブルシューティング

ACSD-56741 パッチは、データベース内のカスタム MySQL トリガーがインデックスと[!DNL MView]に関連しないために、`setup:upgrade`中にエラーメッセージ *型null*&#x200B;の値で配列オフセットにアクセスしようとすると表示される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-56741です。 この問題は、Adobe Commerce 2.5.0で修正される予定です

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

データベース内のカスタム MySQL トリガーがインデックスと[!DNL MView]に関連しないため、`setup:upgrade`の間に、タイプ null *の値で配列オフセットにアクセスしようとするとエラーメッセージ*&#x200B;が表示されます。

<u>複製する手順</u>:

1. `php bin/magento indexer:set-mode schedule`を実行します。

   ```text
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. `php bin/magento c:f`を実行します。
1. `php bin/magento setup:upgrade`を実行します。

<u>期待される結果</u>:

セットアップのアップグレードはエラーなしで完了します。

<u>実際の結果</u>:

セットアップ アップグレードが終了すると、次のエラーメッセージが表示されます。

*警告：null*&#x200B;型の値で配列オフセットにアクセスしようとしています。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
