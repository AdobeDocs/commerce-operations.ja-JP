---
title: ACSD-51041：物価指数（PRICE INDEX）は非常に時間がかかる
description: ACSD-51041 パッチを適用すると、非常に大きな製品セットで価格インデックスが完成するまでに時間がかかるAdobe Commerceの問題を修正できます。
feature: Configuration
role: Admin
exl-id: d45d4042-06a1-445d-bed3-803085626dd3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51041：物価指数（PRICE INDEX）は非常に時間がかかる

ACSD-51041 パッチは、非常に大きな製品セットで価格インデックスが完了するまでに時間がかかる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 がインストールされている場合に使用できます。 パッチ ID は ACSD-51041 です。 この問題はAdobe Commerce 2.4.6 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.3.7-p4、2.4.1 ～ 2.4.5-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

非常に大きな製品セットを使用すると、価格指数の完了に非常に長い時間がかかります。

<u> 再現手順 </u>:

1. *[!UICONTROL Inventory]* モジュールを有効にします。
1. 複数の在庫ソースがある（在庫のほとんどを提供するデフォルト以外のソースを使用）。
1. 約 200,000 個の製品を生成します。
1. 在庫索引を実行します。

<u> 期待される結果 </u>:

`deleteIndexData` は、パフォーマンスを最適化するために一意の ID のみを処理します。

<u> 実際の結果 </u>:

`deleteIndexData` ではすべての ID を処理しますが、処理に時間がかかります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
