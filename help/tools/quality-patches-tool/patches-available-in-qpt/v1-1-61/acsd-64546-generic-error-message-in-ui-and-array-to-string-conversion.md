---
title: 'ACSD-64546: UPS ラベル作成時に、UIおよび配列の一般的なエラーメッセージが文字列変換の例外に変わる'
description: ACSD-64546 パッチを適用して、UIに汎用エラーメッセージが表示され、UPS ラベルの作成中に配列から文字列への変換例外が記録されるAdobe Commerceの問題を修正します。 パッチを適用すると、UIとログに正しいエラーが表示されます。
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-64546: UPS ラベル作成時に、UIの汎用エラーメッセージと&#x200B;*配列から文字列への変換*&#x200B;例外が発生する

ACSD-64546 パッチは、UIに汎用エラーメッセージが表示され、UPS ラベル作成中に&#x200B;*配列から文字列への変換*&#x200B;例外が記録される問題を修正し、UIとログに正しいエラーが表示されるようにします。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACSD-64546です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

汎用エラーメッセージがUIに表示され、UPS ラベルの作成中に&#x200B;*配列から文字列への変換*&#x200B;例外が発生します。

<u>複製する手順</u>:

1. 有効な住所を持つ顧客アカウントを作成します。
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]**&#x200B;に移動し、有効なアドレスを追加します。
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]**&#x200B;に移動し、有効なアドレスを追加します。
1. **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]**&#x200B;に移動し、UPSを設定します。
1. [!UICONTROL UPS]を使用して注文します。
1. データベースの`core_config_data`からUPS ユーザーIDとパスワードを削除します。
1. 設定キャッシュをクリアします。
1. 作成した順序を&#x200B;**[!UICONTROL Admin]**&#x200B;で開きます。
1. 新しい出荷を作成します。
   1. 「**[!UICONTROL Create Shipping Label]**」チェックボックスを選択します。
   1. **[!UICONTROL Submit shipment]**&#x200B;をクリックします。
   1. 製品をパッケージに追加します。 パッケージサイズ（長さ、幅、高さ）を指定します。
   1. **[!UICONTROL Save]**&#x200B;をクリックします。

<u>期待される結果</u>:

実際のエラーメッセージは、UIとログに表示されます。

<u>実際の結果</u>:

* UIに次のエラーが表示されます。
  *配送ラベルの作成中にエラーが発生しました。*
* *配列から文字列への変換*&#x200B;の例外は、実際のエラーメッセージが表示されたり、ログに保存されたりすることを防ぎます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。
* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Adobe Commerce オンクラウドインフラストラクチャ：アップグレードとパッチ/パッチの適用については、Commerce オンクラウドインフラストラクチャガイドを参照してください。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。
* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
