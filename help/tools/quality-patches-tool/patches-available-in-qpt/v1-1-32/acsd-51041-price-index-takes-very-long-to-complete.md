---
title: ACSD-51041：物価指数の完成に時間がかかる
description: ACSD-51041 パッチを適用して、価格指数が非常に大きな商品セットで完了するのに長い時間がかかるAdobe Commerceの問題を修正します。
feature: Configuration
role: Admin
exl-id: d45d4042-06a1-445d-bed3-803085626dd3
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-51041：物価指数の完成に時間がかかる

ACSD-51041 パッチは、非常に大きな製品セットで物価指数の完了に時間がかかる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-51041です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.3.7 - 2.3.7-p4、2.4.1 - 2.4.5-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

非常に大きな商品セットを使用すると、物価指数は完了するのに非常に長い時間がかかります。

<u>複製する手順</u>:

1. *[!UICONTROL Inventory]* モジュールを有効にします。
1. 複数の在庫ソースを持つ（デフォルト以外のソースで在庫のほとんどを提供する）。
1. 約20万の商品を生み出す。
1. 在庫インデックスを実行します。

<u>期待される結果</u>:

`deleteIndexData`は、パフォーマンスを最適化するために一意のIDのみを処理します。

<u>実際の結果</u>:

`deleteIndexData`はすべてのIDを処理します。完了するには長い時間がかかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
