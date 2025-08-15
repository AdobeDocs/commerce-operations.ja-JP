---
title: ACSD-64546:UPS ラベル作成中の UI および配列から文字列への変換例外の一般的なエラーメッセージ
description: ACSD-64546 パッチを適用すると、UI に一般的なエラーメッセージが表示され、UPS ラベルの作成中に文字列変換例外の配列がログに記録されるAdobe Commerceの問題が修正されます。 パッチを適用すると、UI とログに正しいエラーが表示されるようになります。
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-64546:UPS ラベル作成中の UI および *配列から文字列への変換* 例外の一般的なエラーメッセージ

ACSD-64546 パッチは、汎用のエラーメッセージが UI に表示され、UPS ラベルの作成中に *配列から文字列への変換* 例外がログに記録される問題を修正し、正しいエラーが UI とログに表示されるようにします。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 がインストールされている場合に使用できます。 パッチ ID は ACSD-64546 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

UI に一般的なエラーメッセージが表示され、UPS ラベルの作成中に *配列から文字列への変換* 例外が発生します。

<u> 再現手順 </u>:

1. 有効な住所で顧客アカウントを作成します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL GENERAL]**/**[!UICONTROL General]**/**[!UICONTROL Store Information]** に移動し、有効なアドレスを追加します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL SALES]**/**[!UICONTROL Shipping settings]**/**[!UICONTROL Origin]** に移動し、有効なアドレスを追加します。
1. **[!UICONTROL Admin]**/**[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL SALES]**/**[!UICONTROL Delivery methods]**/**[!UICONTROL UPS]** に移動し、UPS を設定します。
1. [!UICONTROL UPS] を使用して注文します。
1. UPS のユーザー ID とパスワードをデータベースの `core_config_data` から削除します。
1. 設定キャッシュをクリーンアップします。
1. 作成したオーダーを **[!UICONTROL Admin]** で開きます。
1. 新しい出荷を作成します。
   1. 「**[!UICONTROL Create Shipping Label]**」チェックボックスをオンにします。
   1. 「**[!UICONTROL Submit shipment]**」をクリックします。
   1. 製品をパッケージに追加します。 パッケージサイズ（長さ、幅、高さ）を指定します。
   1. 「**[!UICONTROL Save]**」をクリックします。

<u> 期待される結果 </u>:

実際のエラーメッセージは、UI とログに表示されます。

<u> 実際の結果 </u>:

* UI に次のエラーが表示されます。
  *配送ラベルの作成中にエラーが発生しました。*
* *配列から文字列への変換* 例外は、実際のエラーメッセージがログに表示または保存されるのを防ぎます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。
* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* Adobe Commerce on Cloud Infrastructure: アップグレードとパッチ > Commerce on Cloud Infrastructure ガイドのパッチの適用

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。
* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
