---
title: ACSD-47054：すべてのストアのインデックスを再作成するとコンテンツのプレビューが遅くなる
description: ACSD-47054 パッチを適用して、すべてのストアのインデックスを再作成したためにプレビューページの読み込みが遅くなるAdobe Commerceの問題を修正してください。
feature: Page Content
role: Admin, Developer
exl-id: bfbda95a-354b-4b67-8081-84aefbbd7cb4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47054：すべてのストアのインデックスを再作成するとコンテンツのプレビューが遅くなる

ACSD-47054 パッチを使用すると、ストアが多数ある場合にコンテンツのステージングのプレビューの読み込みに時間がかかる問題を修正できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.37 がインストールされている場合に使用できます。 パッチ ID は ACSD-47054 です。 この問題はAdobe Commerce 2.4.6 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法）:2.4.2-p2、2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法）:2.4.2 ～ 2.4.5-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

すべてのストアのインデックスが再作成されるので、プレビューページの読み込みに時間がかかる。

<u> 再現手順 </u>:

1. Commerce管理者に移動します。
1. スケジュールされている更新を作成します。
1. **[!UICONTROL Content]**/**[!UICONTROL Dashboard]** に移動します。
1. スケジュールされた更新をプレビューします。
1. 任意のカテゴリを開きます。

<u> 期待される結果 </u>:

プレビューページは、許容可能な時間内に読み込まれます。

<u> 実際の結果 </u>:

コンテンツのステージングのプレビューに時間がかかる。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
