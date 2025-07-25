---
title: ACSD-51792：ページにインプレッションイベントがありません
description: Google Tag Manager 4 が有効になっているときにページにインプレッションイベントが発生しないAdobe Commerceのパフォーマンスの問題を修正するため、ACSD-51792 パッチを適用してください。
exl-id: f9465a44-2c65-4af0-b949-1fe1f4a942ae
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-51792：ページにインプレッションイベントがありません

ACSD-51792 パッチは、[!DNL Google Tag Manager] 4 が有効な場合に、ページにインプレッションイベントが含まれないパフォーマンスの問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33 がインストールされている場合に使用できます。 パッチ ID は ACSD-51792 です。 この問題はAdobe Commerce 2.4.6 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.5-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL Google Tag Manager] 4 が有効になっている場合、ページにインプレッションイベントは発生しません。

<u> 再現手順 </u>:

1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL Sales]**/**[!UICONTROL Google API]** に移動します。
1. **[!DNL GoogleTag Manager]** 統合を設定します。
1. [Googleタグアシスタント ](https://tagassistant.google.com/) に移動し、Web サイトに接続するために必要な手順を完了します。
1. ストアフロントに製品リストが表示されているカテゴリページを開きます。
1. Tag Assistant オブザーバーでインプレッションイベントを確認します。

<u> 期待される結果 </u>:

インプレッションイベントは、ページ上のすべての製品から始める必要があります。

<u> 実際の結果 </u>:

ページには、タグアシスタントオブザーバー内のインプレッションイベントがありません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
