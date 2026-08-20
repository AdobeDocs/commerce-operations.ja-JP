---
title: ACSD-46938:「setup:upgrade」時のDB トリガーのパフォーマンスの問題
description: 「setup:upgrade」コマンドでインデクサーモードがスケジュールからセーブに変わり、パフォーマンスが大幅に低下するAdobe Commerceの問題を修正するには、ACSD-46938 パッチを適用します。
feature: Upgrade
role: Admin, Developer
exl-id: a4e88329-c5bb-4666-8738-b78b86056b71
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46938: `setup:upgrade`中のDB トリガーのパフォーマンスの問題

ACSD-46938 パッチは、`setup:upgrade` コマンドがインデクサーモードをスケジュールから保存に変更し、パフォーマンスが大幅に低下する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-46938です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p9

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`setup:upgrade`でのDB トリガーの再作成中にパフォーマンスが低下しました。

<u>複製する手順</u>:

1. 多くの商品とカテゴリーを含む大規模なカタログを作成する。
1. [!UICONTROL Admin]にログインします。
1. すべてのインデクサーを[!UICONTROL Update By Schedule] モードに設定します。
1. 任意の製品を開きます。
1. 更新します。 例えば、新しいカテゴリを割り当てます。
1. [!UICONTROL Save]をクリックします。
1. `bin/magento setup:upgrade`と`bin/magento cron:run`個のコマンドを並行して実行します。

<u>期待される結果</u>:

`bin/magento cron:run` コマンドを同時に実行すると、`bin/magento setup:upgrade` コマンドの実行時間が大幅に増加します。

<u>実際の結果</u>:

コマンドの実行時間は増加しません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
