---
title: ACSD-46869：チェックアウト時にREST APIを使用して設定可能な製品が更新されない
description: ACSD-46869 パッチは、チェックアウト時にREST APIを使用して、設定可能な製品が更新されない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.20がインストールされている場合に利用できます。 パッチ IDはACSD-46869です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-46869：チェックアウト時にREST APIを使用して設定可能な製品が更新されない

ACSD-46869 パッチは、チェックアウト時にREST APIを使用して設定可能な製品が更新されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20がインストールされている場合に利用できます。 パッチ IDはACSD-46869です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL QPT]  ランディングページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

チェックアウト時にREST APIを使用して設定可能な製品が更新されない。

<u>複製する手順</u>:

1. カラー属性とサイズ属性を使用して設定可能な商品を作成します。
1. **[!UICONTROL Options]**&#x200B;を選択し、商品をカートに追加します。
1. **[!UICONTROL Checkout]**&#x200B;に移動し、数量を除いてサイズを複数回更新し、リクエストと応答を確認します。
1. サイズを更新すると、次の応答が表示されます。

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>期待される結果</u>:

値は変更に従って更新されます。

<u>実際の結果</u>:

`option_value`は更新されないので、注文が行われると、古いサイズの値になります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：品質パッチツールガイドの[[!DNL Quality Patches Tools] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
