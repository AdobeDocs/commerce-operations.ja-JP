---
title: ACSD-45520：製品の詳細ページでスウォッチオプションが選択されない
description: ACSD-45520 パッチは、ユーザーが買い物かごから設定可能な製品を編集する際に、製品の詳細ページでスウォッチオプションが事前に選択されていない問題を修正しています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.17 がインストールされている場合に利用できます。 パッチ ID は ACSD-45520 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: Products
role: Admin
exl-id: a8b37dba-5a02-45a9-8e43-5288352a9d75
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-45520：製品の詳細ページでスウォッチオプションが選択されない

ACSD-45520 パッチは、ユーザーが買い物かごから設定可能な製品を編集する際に、製品の詳細ページでスウォッチオプションが事前に選択されていない問題を修正しています。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.17 がインストールされている場合に使用できます。 パッチ ID は ACSD-45520 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーが買い物かごから設定可能な製品を編集すると、製品の詳細ページでスウォッチオプションが選択されません。

<u> 再現手順 </u>:

1. 商品オプション（色など）を使用して設定可能な商品を作成します。
1. 設定可能な製品を買い物かごに追加します。
1. 自分の買い物かごページに移動します。
1. 手順 1 で追加した設定可能な製品の「編集」ボタンをクリックします。
1. 編集ページの製品オプションを確認します。

<u> 期待される結果 </u>:

製品オプションが選択されます。

<u> 実際の結果 </u>:

製品オプションが選択されていません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
