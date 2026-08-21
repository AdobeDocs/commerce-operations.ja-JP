---
title: ACSD-57565：注文ダッシュボードに誤った注文情報が表示される
description: ACSD-57565 パッチを適用して、期間が更新されるまで注文ダッシュボードに誤った注文情報が表示されるAdobe Commerceの問題を修正します。
feature: Roles/Permissions
role: Admin, Developer
exl-id: dc4ad263-725e-4605-9b85-fc4305ab9a29
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-57565：注文ダッシュボードに誤った注文情報が表示される

ACSD-57565 パッチでは、期間が更新されるまで、注文ダッシュボードに誤った注文情報が表示される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-57565です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを見つけます

## イシュー

注文ダッシュボードに誤った注文情報が表示される。

<u>複製する手順</u>:

1. **[!UICONTROL dashboard charts]**&#x200B;を有効にします。
1. 注文を作成し、請求書を作成します。
1. 注文の作成後、少なくとも24時間待ちます。
1. **[!UICONTROL dashboard chart]** データを確認してください。
1. 注文完了数をメモします。
1. 時間を&#x200B;*現在の月*&#x200B;に変更し、それを&#x200B;*今日*&#x200B;に戻します。

<u>期待される結果</u>:

ダッシュボードのグラフには、常に正しい統計情報が表示される必要があります。

<u>実際の結果</u>:

ダッシュボードのグラフに、初回読み込み時の誤った統計が表示されます。 グラフの正確な統計は、期間の後に更新されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
