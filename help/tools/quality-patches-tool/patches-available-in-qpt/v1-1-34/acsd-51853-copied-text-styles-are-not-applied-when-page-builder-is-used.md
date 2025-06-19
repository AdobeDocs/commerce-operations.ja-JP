---
title: ACSD-51853：コピーしたテキストスタイルは、ページビルダーを使用して適用されない
description: ACSD-51853 パッチを適用すると、ページビルダーを使用したときにコピーしたテキストスタイルが適用されないAdobe Commerceの問題が修正されます。
feature: Page Builder
role: Admin
exl-id: fda5ba6e-4786-473c-a3a2-7356aa20f5ae
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-51853：コピーしたテキストスタイルは、ページビルダーを使用して適用されない

ACSD-51853 パッチでは、ページビルダーを使用したときに、コピーしたテキストスタイルが適用されない問題を修正しています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.34 がインストールされている場合に使用できます。 パッチ ID は ACSD-51853 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

コピーしたテキストスタイルは、ページビルダーが使用されている場合は適用されません

<u> 再現手順 </u>:

1. 管理者にログインします。
1. / **コンテンツ** / **ページ** / **任意のページを開く** / **ページビルダーを使用して編集** に移動します。
1. **[!UICONTROL Elements]** から行と *テキスト* をドラッグします。
1. **エンリッチメントコンテンツ** をコピーし、そのテキストを **[!UICONTROL Page Builder]** に貼り付けます。

<u> 期待される結果 </u>

コピーしたテキストは、すべてのスタイルと共に貼り付けられます。

<u> 実績 </u>

コピーされたテキストはプレーンテキストとして貼り付けられ、すべてのスタイルが失われます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
