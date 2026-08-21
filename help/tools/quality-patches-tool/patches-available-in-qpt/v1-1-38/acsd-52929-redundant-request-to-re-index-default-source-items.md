---
title: ACSD-52929：デフォルトのソースアイテムを再インデックス化するための冗長なリクエスト
description: 在庫インデクサーが非同期モードで設定されている場合に、デフォルトのソース項目のインデックスを再作成する冗長なリクエストがあるAdobe Commerceの問題を修正するには、ACSD-52929 パッチを適用します。
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 904aed0e-a6cd-4a0f-949d-bb32fcd77356
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-52929：デフォルトのソースアイテムを再インデックス化するための冗長なリクエスト

ACSD-52929 パッチは、在庫インデクサーが非同期モードで設定されている場合に、デフォルトのソースアイテムを再インデックス化するリクエストが冗長になる問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.38がインストールされている場合に利用できます。 パッチ IDはACSD-52929です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

在庫インデクサーが非同期モードで設定されている場合、デフォルトのソースアイテムを再インデックス化するリクエストの冗長性があります。

<u>複製する手順</u>:

1. [!DNL RabbitMQ]を設定します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]**&#x200B;に移動し、**[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**&#x200B;を設定して、非同期インデックス戦略を有効にします。
1. カスタムの在庫ソースを作成。
1. [!DNL RabbitMQ] ダッシュボードにログインし、「キュー」タブに移動します。
1. `inventory.indexer.sourceItem` キューを確認し、メッセージが0であることを確認します。
1. バックエンドからシンプルな製品を開き、カスタムソースに&#x200B;*[!UICONTROL stock only]*&#x200B;を追加して製品を保存します。
1. [!DNL RabbitMQ] ダッシュボードに`inventory.indexer.sourceItem` キューを読み込み、メッセージを確認します。

<u>期待される結果</u>:

カスタムソースのキューにはメッセージが1つしかありません。

<u>実際の結果</u>:

キューには、デフォルトソース用とカスタムソース用の2つのメッセージが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
