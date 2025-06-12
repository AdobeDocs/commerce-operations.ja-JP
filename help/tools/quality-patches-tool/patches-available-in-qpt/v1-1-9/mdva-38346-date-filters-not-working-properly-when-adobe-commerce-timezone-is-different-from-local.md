---
title: MDVA-38346:Adobe Commerceのタイムゾーンがローカルと異なる場合、日付フィルターが機能しない
description: MDVA-38346 パッチは、Adobe Commerceのタイムゾーンがローカル環境のタイムゾーンと異なる場合、日付フィルターが正しく機能しない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.9 がインストールされている場合に利用できます。 パッチ ID は MDVA-38346。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Configuration
role: Admin
exl-id: 6ed909be-81da-4e06-97c7-4eab8be2ddd2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-38346:Adobe Commerceのタイムゾーンがローカルと異なる場合、日付フィルターが機能しない

MDVA-38346 パッチは、Adobe Commerceのタイムゾーンがローカル環境のタイムゾーンと異なる場合、日付フィルターが正しく機能しない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.9 がインストールされている場合に使用できます。 パッチ ID は MDVA-38346。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1、2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Adobe Commerceのタイムゾーンがローカル環境のタイムゾーンと異なる場合、日付フィルターが正しく機能しません。

<u> 再現手順 </u>:

1. タイムゾーンをオーストラリア/シドニーに変更します。
1. 注文を少なくします。
1. それらの請求書を作成します。
1. **売上**/**請求書** に移動し、請求日（現在の日付 – 現在の日付）でフィルタリングします。
1. 日付を確認します。

<u> 期待される結果 </u>:

表示された請求書の日付と実際のフィルターの一致。

<u> 実際の結果 </u>:

表示された請求日は、実際のフィルターよりも 1 日早くなっています（現在の日付+ 1 日）。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
