---
title: ACSD-56741：カスタム MySQL トリガーを使用したデータベース設定エラーのトラブルシューティング
description: ACSD-56741 パッチを適用すると、「setup:upgrade」の間、インデックスおよび  [!DNL MView] に関連しないデータベース内のカスタム MySQL トリガーが原因で、「null 型の値で配列オフセットにアクセスしようとしています」というエラーメッセージが表示されるAdobe Commerceの問題を修正できます。
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56741：カスタム MySQL トリガーを使用したデータベース設定エラーのトラブルシューティング

ACSD-56741 パッチでは、インデックスおよび *に関連しないデータベース内のカスタム MySQL トリガーが原因で、* 行中にエラーメッセージ `setup:upgrade`null 型の値で配列オフセットにアクセスしようとしています [!DNL MView] が表示される問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 がインストールされている場合に使用できます。 パッチ ID は ACSD-56741 です。 この問題はAdobe Commerce 2.5.0 で修正される予定です

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

インデックスおよび *に関連しないデータベース内のカスタム MySQL トリガーが原因で、* 行中にエラーメッセージ `setup:upgrade` 型 null の値で配列オフセットにアクセスしようとしています [!DNL MView] が表示されます。

<u> 再現手順 </u>:

1. `php bin/magento indexer:set-mode schedule` を実行します。

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. `php bin/magento c:f` を実行します。
1. `php bin/magento setup:upgrade` を実行します。

<u> 期待される結果 </u>:

セットアップのアップグレードはエラーなしで完了します。

<u> 実際の結果 </u>:

セットアップのアップグレードが終了し、次のエラーメッセージが表示されます。

*警告：null 型の値の配列オフセットにアクセスしようとしています*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
