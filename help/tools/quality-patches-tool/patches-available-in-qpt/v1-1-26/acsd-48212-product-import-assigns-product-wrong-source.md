---
title: ACSD-48212：製品の読み込みで、間違ったソースに製品が割り当てられる
description: ACSD-48212 パッチを適用して、製品の読み込みが間違ったソースに製品を割り当てるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-48212：製品の読み込みで、間違ったソースに製品が割り当てられる

ACSD-48212 パッチは、製品のインポートで製品が間違ったソースに割り当てられる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26がインストールされている場合に利用できます。 パッチ IDはACSD-48212です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品の読み込みでは、間違ったソースに製品が割り当てられます。

<u>複製する手順</u>:

1. セカンダリ在庫ソースを作成。
1. デフォルトの在庫ソースのみを使用して商品を作成します。
1. 製品をエクスポートします。
1. `bin/magento cron:run`を実行します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**&#x200B;を開きます。
1. グリッドから商品を選択します。
1. *[!UICONTROL mass action]* メニューを使用して在庫の割り当てを解除します。
1. `bin/magento cron:run`を実行します。
1. *[!UICONTROL mass action]* メニューを使用してセカンダリ ソースを割り当てます。
1. `bin/magento cron:run`を実行します。
1. *[!UICONTROL mass action]* メニューを使用して製品を削除します。
1. `bin/magento cron:run`を実行します。
1. 以前に書き出したCSVを使用して製品を読み込みます。
1. ソース割り当てを確認します。

<u>期待される結果</u>:

製品はデフォルトのソースにのみ割り当てられます。

<u>実際の結果</u>:

製品はデフォルトとセカンダリの両方のソースに割り当てられます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
