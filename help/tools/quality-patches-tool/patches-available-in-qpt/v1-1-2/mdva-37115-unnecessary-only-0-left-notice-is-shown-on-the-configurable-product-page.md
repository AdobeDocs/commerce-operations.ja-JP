---
title: MDVA-37115：製品ページに「左のみ0件」の通知が表示される
description: MDVA-37115 パッチは、設定可能な製品ページに不必要な*Only 0 left*の通知が表示される問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-37115です。 この問題は、Adobe Commerce 2.4.3で修正されています。
feature: Configuration, Products, Orders
role: Admin
exl-id: ba94b2fd-6a7d-4194-afd8-798854431b57
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%
---
# MDVA-37115：製品ページに「左のみ0件」の通知が表示される

MDVA-37115 パッチは、設定可能な製品ページに不必要な&#x200B;*左のみ*&#x200B;の通知が表示される問題を解決します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-37115です。 この問題は、Adobe Commerce 2.4.3で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメントタイプ） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメントタイプ） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定可能な製品ページには、不要な&#x200B;*左のみ*&#x200B;の通知が表示されます。

<u>前提条件</u>:

在庫モジュールが取り付けられています。

<u>複製する手順</u>:

1. 少ないオプションで設定可能な商品を作成します。
1. フロントエンドに移動します。
1. 設定可能な製品ページを開き、任意のオプションを選択します。

<u>期待される結果</u>:

製品ページには&#x200B;*左のみ*&#x200B;の通知は表示されません。

<u>実際の結果</u>:

製品ページには&#x200B;*左に0件の通知のみが表示されます*。

## パッチを適用する

個別のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：品質パッチをセルフサービスで提供するための新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します。

QPTで使用可能な他のパッチについて詳しくは、「QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な[ パッチ」セクションを参照してください。
