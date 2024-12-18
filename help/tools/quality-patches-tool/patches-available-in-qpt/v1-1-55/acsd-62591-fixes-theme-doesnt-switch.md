---
title: ACSD-62591:**[!UICONTROL User Agent Rules]**が設定されている場合、テーマが切り替わらない
description: ACSD-62591 パッチを適用して、**[!UICONTROL User Agent Rules]**が設定されている場合にテーマが正しく切り替わらないAdobe Commerceの問題を修正してください。
feature: Themes
role: Admin, Developer
source-git-commit: 319ac7ea1fb8f33f4ed7bfa440477cf6d6657cb5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# ACSD-62591：設定 [!UICONTROL User Agent Rules] に、テーマが正しく切り替わらない

ACSD-62591 パッチは、テー **[!UICONTROL User Agent Rules]** が設定されている場合にテーマが正しく切り替わらない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 がインストールされている場合に使用できます。 パッチ ID は ACSD-62591 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

テー **[!UICONTROL User Agent Rules]** が設定されている場合、テーマが正しく切り替わらない。

<u> 再現手順 </u>:

1. Commerce **[!UICONTROL Admin]**/**[!UICONTROL Content]**/**[!UICONTROL Design]**/**[!UICONTROL Configuration]** を開きます。
1. ストア表示テーマを編集します。
1. **[!UICONTROL User Agent Rules]** で `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i` を設定し、別のテーマを選択してください。
1. 変更を保存し、キャッシュをクリアします。
1. モバイルデバイスでストアフロントページを開きます。
1. デスクトップブラウザーから同じページを開きます。

<u> 期待される結果 </u>:

デスクトップブラウザーとモバイルデバイスは、それぞれのテーマを使用してページを表示します。

<u> 実際の結果 </u>:

デスクトップブラウザーは、キャッシュされたページをモバイルテーマで表示します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
