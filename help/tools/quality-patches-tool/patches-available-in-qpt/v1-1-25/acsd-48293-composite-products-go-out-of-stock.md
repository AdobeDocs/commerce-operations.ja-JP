---
title: ACSD-48293：売り切れた子商品が再入荷すると、複合商品の在庫が切れる
description: ACSD-48293 パッチを適用して、売り切れた子商品が在庫に戻ったときに複合商品が在庫切れになるAdobe Commerceの問題を修正します。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# ACSD-48293：売り切れた子商品が再入荷すると、複合商品の在庫が切れる

ACSD-48293 パッチは、売り切れた子商品が在庫に戻ったときに複合商品が在庫切れになる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25がインストールされている場合に利用できます。 パッチ IDはACSD-48293です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

コンポジット商品は、売り切れた子商品が在庫に戻されると在庫切れになります。

<u>複製する手順</u>:

1. ふたつ目のweb サイト、実店舗ビューの作成。
1. 2つのソースと在庫を作成し、各web サイトに割り当てます。
1. **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*&#x200B;の下にある在庫切れ製品を表示オプションを有効にします。
1. プライマリ web サイトの在庫ソースを使用して、1つの関連製品を持つ設定可能な製品を作成します（数量を設定= 1）。
1. 設定可能な製品を注文します。
1. cronを実行します。
1. ストアフロントから設定可能な商品を開き、在庫切れであることを確認します。
1. [!UICONTROL Admin]から設定可能な製品を開き、**[!UICONTROL Manage Stock Option]**&#x200B;を&#x200B;*[!UICONTROL No]*&#x200B;に設定します。
1. cronを実行します。
1. &#x200B;2. 注文を出荷し、在庫を作る簡単な製品に数量を追加します。
1. cronを実行します。
1. ストアフロントで製品の在庫状況を確認します。

<u>期待される結果</u>:

コンフィグ商品は在庫あり。

<u>実際の結果</u>:

コンフィグ商品は在庫切れです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
