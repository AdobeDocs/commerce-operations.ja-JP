---
title: ACSD-51114：非同期インデックス作成が有効になっている場合、ランダムな商品が大きなカタログから消える
description: 非同期インデックス作成が有効になっている場合に、大きなカタログからランダムな商品が消えてしまうAdobe Commerceの問題を修正するには、ACSD-51114 パッチを適用します。
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-51114：非同期インデックス作成が有効になっている場合、ランダムな商品が大きなカタログから消える

>[!NOTE]
>
>このパッチは非推奨です。

非同期インデックス作成が有効になっている場合に、ACSD-51114 パッチで大きなカタログからランダムな製品が消える問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-51114です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]:Search パッチ ページ ]の互換性を確認します。パッチ IDを検索キーワードとして使用して、パッチを見つけます。

## イシュー

非同期インデックス作成が有効になっている場合、ランダムな商品が大きなカタログから消えてしまいます。

<u>複製する手順</u>:

1. 10個の商品セットを作成する。
1. すべてのインデクサーを&#x200B;**[!UICONTROL Update on Save]** モードに設定します。
1. カテゴリを作成し、すべての製品をカテゴリに割り当てます。
1. すべての製品を無効にします。
1. カテゴリを開き、製品がないことを確認します。
1. すべてのインデクサーを&#x200B;**[!UICONTROL Update on Schedule]** モードに設定します。
1. `DEFAULT_BATCH_SIZE`を`lib/internal/Magento/Framework/Mview/View.php#L31`の2に設定します。
1. 1st、9th、2nd、5th、10th、3rdの順序で製品を有効にします。
1. cron コマンドを実行します。
1. カテゴリをもう一度開きます。

<u>期待される結果</u>:

有効なすべての製品が表示されます。

<u>実際の結果</u>:

有効な製品はすべて表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
