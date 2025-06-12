---
title: MDVA-27456:Swagger の読み込み時にエラーが発生する
description: MDVA-27456 パッチでは、Swagger を読み込もうとするとエラーが発生する問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.6 がインストールされている場合に利用できます。 パッチ ID は MDVA-27456。 この問題はAdobe Commerce 2.3.7 で修正されました。
feature: Tools and External Services
role: Admin
exl-id: a7d5dc7d-b916-4a09-9068-646f8474bba4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-27456:Swagger の読み込み時にエラーが発生する

MDVA-27456 パッチでは、Swagger を読み込もうとするとエラーが発生する問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.6 がインストールされている場合に使用できます。 パッチ ID は MDVA-27456。 この問題はAdobe Commerce 2.3.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.3.5-p1

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.5 ～ 2.3.6-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Swagger の読み込み時にエラーが発生する。

<u> 再現手順 </u>:

`../swagger.` に移動

<u> 期待される結果 </u>:

Swagger はエラーなしで読み込まれます。

<u> 実際の結果 </u>:

ユーザーに「*API 定義の読み込みに失敗しました*」エラーが表示される。 エラーログには次が含まれます。

*report.CRITICAL: レポート ID: webapi-5ea9c6da19cb1; メッセージ：「\DateTime」パラメータータイプが無効です。 パラメーターを確認して、もう一度試してください。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) の節を参照してください。
