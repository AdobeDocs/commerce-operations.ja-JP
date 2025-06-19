---
title: MDVA-38799：ステージング更新プログラムの作成後にダウンロード可能な製品が保存されない
description: MDVA-38799 パッチを使用すると、ステージング アップデートの作成後にダウンロード可能な製品が保存されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.0 がインストールされている場合に利用できます。 パッチ ID は MDVA-38799。 この問題は、Adobe Commerce バージョン 2.4.3 で修正されました。
feature: Products, Staging
role: Admin
exl-id: 0ae665a8-cda2-4340-91e7-5b9b969a6607
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799：ステージング更新プログラムの作成後にダウンロード可能な製品が保存されない

MDVA-38799 パッチを使用すると、ステージング アップデートの作成後にダウンロード可能な製品が保存されない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.0 がインストールされている場合に使用できます。 パッチ ID は MDVA-38799。 この問題は、Adobe Commerce バージョン 2.4.3 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* クラウドインフラストラクチャー 2.4.1 上のAdobe Commerce

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0-2.4.2-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ダウンロード可能な製品は、ステージングアップデートの作成後は保存されません。 次のエラーメッセージが表示されます。*ダウンロード可能なサンプルは製品に関連していません。 リンクを確認して、もう一度やり直してください*。

<u> 再現手順 </u>:

1. **カタログ**/**製品** に移動します。
1. 「製品を追加」の横のドロップダウンをクリックし、「ダウンロード可能な製品」を選択します。
   * 商品の名前、SKU、価格、数量を入力します。
1. ダウンロード可能な情報ページまでスクロールします。
1. 「サンプル」で、「**リンクを追加**」をクリックします。
   * タイトル、ファイルをアップロードを入力します（ファイルのタイプは関係ありません）。
1. **保存** をクリックします。 次のメッセージが表示されます。*製品を保存しました*。
1. ページ上部の「**新規更新をスケジュール**」をクリックします。
   * 更新名、および有効な開始日と終了日を入力します。
1. ステージングの更新で「**保存**」をクリックします。
1. 製品の **保存** をクリックします。

<u> 期待される結果 </u>:

製品はエラーなしで保存されます。

<u> 実際の結果 </u>:

次のエラーメッセージが表示されます。*ダウンロード可能なサンプルは製品に関連していません。 リンクを確認して、もう一度やり直してください*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
