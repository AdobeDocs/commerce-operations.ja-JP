---
title: ACSD-51294：価格、数量、税金、送料、文字列として [!DNL Google Analytics] およびGTMに送信された収益
description: ACSD-51294 パッチを適用して、価格、数量、税金、送料、収益が文字列として [!DNL Google Analytics] およびGTMに送信されるAdobe Commerceの問題を修正します。
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 99d2a311-2543-4007-99fd-6c34a2950773
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51294：価格、数量、税金、送料、文字列として[!DNL Google Analytics]およびGTMに送信された収益

ACSD-51294 パッチは、価格、数量、税金、送料、収益が文字列として[!DNL Google Analytics]およびGTMに送信される問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-51294です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

価格、数量、税金、送料、収益は、文字列として[!DNL Google Analytics]およびGTMに送信されます。

<u>複製する手順</u>:

1. [!DNL Google Tag Manager]を設定するには、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**&#x200B;に移動します。
2. シンプルな商品の作成。
3. 決済プロセスを完了します。
4. チェックアウトの成功ページで`dataLayer` JavaScript変数を確認します。

<u>期待される結果</u>

価格と数量の値は数値です。

<u>実際の結果</u>

価格と数量の値は文字列です。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
