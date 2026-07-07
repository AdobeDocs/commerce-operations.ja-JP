---
title: 'ACSD-62591: **[!UICONTROL User Agent Rules]**が設定されている場合にテーマが切り替わらない'
description: ACSD-62591 パッチを適用して、**[!UICONTROL User Agent Rules]**が設定されているときにテーマが正しく切り替わらないAdobe Commerceの問題を修正します。
feature: Themes
role: Admin, Developer
exl-id: 7b206b25-8918-40a6-a956-d38d5058d38f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-62591: [!UICONTROL User Agent Rules]が設定されている場合、テーマが正しく切り替わりません

ACSD-62591 パッチは、**[!UICONTROL User Agent Rules]**&#x200B;が設定されているときにテーマが正しく切り替わらない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55がインストールされている場合に利用できます。 パッチ IDはACSD-62591です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL User Agent Rules]**&#x200B;が設定されている場合、テーマが正しく切り替わりません。

<u>複製する手順</u>:

1. Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**&#x200B;を開きます。
1. ストアビューのテーマを編集します。
1. **[!UICONTROL User Agent Rules]**&#x200B;で`/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i`を設定し、別のテーマを選択します。
1. 変更を保存してキャッシュをクリアします。
1. モバイルデバイスでストアフロントページを開きます。
1. デスクトップブラウザーから同じページを開きます。

<u>期待される結果</u>:

デスクトップブラウザーとモバイルデバイスは、それぞれのテーマを使用してページを表示します。

<u>実際の結果</u>:

デスクトップブラウザーには、モバイルテーマを含むキャッシュされたページが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。

