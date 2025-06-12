---
title: MDVA-43491:CSV 経由で読み込むと、ベース画像ラベルが更新されない
description: MDVA-43491 パッチでは、マルチストア web サイトの CSV ファイルを使用して読み込んだ場合に「base_image_label」が更新されない問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.13 がインストールされている場合に利用できます。 パッチ ID は MDVA-43491。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Data Import/Export
role: Admin
exl-id: f6a5f641-aaf0-4b6e-afa9-7f436f8f59e6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-43491:CSV 経由で読み込むと、ベース画像ラベルが更新されない

MDVA-43491 パッチでは、マルチストア web サイトの CSV ファイルを介して読み込んだ場合に `base_image_label` が更新されない問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.13 がインストールされている場合に使用できます。 パッチ ID は MDVA-43491。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

マルチストア web サイトの CSV ファイルを使用して読み込んだ場合、`base_image_label` は更新されません。

<u> 前提条件 </u>:

1 つ以上の既存のデフォルト以外の web サイト、ストア、ストアビュー。

<u> 再現手順 </u>:

1. 新しい製品を作成します。

   * 画像をアップロードします。
   * 新しく作成した web サイトに製品を割り当てます。

1. 製品を CSV として書き出します。
1. CSV ファイルのデフォルトの行を複製して、各ストア表示の `base_image_label` を更新します。
1. CSV ファイルを読み込みます。 各ストアのラベルが正しく更新され、製品の編集ページの「**画像とビデオ**」タブで確認できます。
1. CSV ファイルを再度エクスポートし、`base_image_label` 列を異なる値で更新します。
1. CSV ファイルを再度読み込みます。
1. 管理で製品を開き、ストア表示ごとにラベルが更新されているかどうかを確認します。

<u> 期待される結果 </u>:

代替テキスト（画像ラベル）が、CSV ファイルに従って、ストア固有の値で更新されます。

<u> 実際の結果 </u>:

代替テキスト（画像ラベル）が、CSV ファイルの `base_image_label` 値で更新されない。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
