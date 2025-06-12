---
title: MDVA-44044：製品が新しい Web サイトに割り当てられた後、カテゴリページに表示されない
description: MDVA-44044 パッチを適用すると、新しい Web サイトに製品を割り当てた後、製品がカテゴリ ページに表示されない問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.16 がインストールされている場合に利用できます。 パッチ ID は MDVA-44044。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。
feature: Categories, Products
role: Admin
exl-id: ae797cdc-5977-40b8-82da-ccf364466bdf
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44044：製品が新しい Web サイトに割り当てられた後、カテゴリページに表示されない

MDVA-44044 パッチを適用すると、新しい Web サイトに製品を割り当てた後、製品がカテゴリ ページに表示されない問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.16 がインストールされている場合に使用できます。 パッチ ID は MDVA-44044。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

製品を新しい web サイトに割り当てると、カテゴリページに製品が表示されません。

<u> 再現手順 </u>:

1. インデクサーモードをスケジュールに設定します。
1. セカンダリ web サイト、ストア、ストア表示を作成します。
1. `index.php` にセカンダリストアコードを追加します。

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. 新しいカテゴリを作成します。
1. 新しく作成されたカテゴリに割り当てる新しい製品を作成します。 必ずプライマリ web サイトにのみ割り当ててください。
1. cron を実行します。
1. ストアフロントからカテゴリを開きます。
1. 製品をセカンダリ web サイトに割り当てます。
1. cron を再度実行します。

<u> 期待される結果 </u>:

スケジュールされたインデクサーの後、製品がカテゴリページに表示されます。

<u> 実際の結果 </u>:

製品は、完全に再インデックス化されるまで、カテゴリページに表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
