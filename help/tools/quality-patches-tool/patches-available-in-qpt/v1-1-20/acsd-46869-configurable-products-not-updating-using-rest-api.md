---
title: ACSD-46869：設定可能な製品が、チェックアウト時に REST API を使用して更新されない
description: ACSD-46869 パッチを適用すると、チェックアウト時に設定可能な製品が REST API を使用して更新されない問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.20 がインストールされている場合に利用できます。 パッチ ID は ACSD-46869 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-46869：設定可能な製品が、チェックアウト時に REST API を使用して更新されない

ACSD-46869 パッチにより、チェックアウト時に設定可能な製品が REST API を使用して更新されない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 がインストールされている場合に使用できます。 パッチ ID は ACSD-46869 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがお使いのAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL QPT]  ランディングページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

設定可能な製品は、チェックアウト時に REST API を使用して更新されません。

<u> 再現手順 </u>:

1. カラー属性とサイズ属性を使用して設定可能な商品を作成します。
1. **[!UICONTROL Options]** を選択し、商品を買い物かごに追加します。
1. **[!UICONTROL Checkout]** に移動し、数量を除いてサイズを複数回更新し、リクエストと応答を確認します。
1. サイズを更新すると、次の応答が表示されます。

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u> 期待される結果 </u>:

値は変更に従って更新されます。

<u> 実際の結果 </u>:

`option_value` は更新されないので、注文されると、古いサイズ値になります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tools] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) （品質パッチツールガイド）。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
