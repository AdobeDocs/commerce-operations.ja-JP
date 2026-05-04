---
title: 'ACSD-66153: キャッシュされたレイアウト構造が正しくないため、ページが500 エラーを返す'
description: キャッシュされたレイアウト構造が正しくないため、ページが500 エラーコードを返すAdobe Commerceの問題を修正するには、ACSD-66153 パッチを適用します。
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
exl-id: 2d6f47cb-2244-40b6-b1b9-0d03f13adc43
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-66153: キャッシュされたレイアウト構造が正しくないため、ページが500 エラーを返す

ACSD-66153 パッチは、キャッシュされたレイアウト構造が正しくないため、ページが500 エラーコードを返す問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-66153です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p10

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

キャッシュされたレイアウト構造が正しくないため、ページから500 エラーが返されます。

<u>複製する手順</u>:

1. `2.4-develop`をインストールします。
1. カスタムモジュールを作成してインストールします。
1.1 `catalog_category_view` レイアウトにカスタムブロックを追加します。
1.1 コンストラクターを使用して`Magento\Framework\View\Result\Layout`をカスタムブロックに挿入します。
1. カテゴリ **[!UICONTROL shop]**&#x200B;を作成します。
1. **[!UICONTROL two terminal windows]**&#x200B;を開きます：
   1. **ターミナル 1**: レイアウト キャッシュを継続的にクリーニングします。

      ```shell
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **ターミナル 2**: カテゴリ ページに対する同時要求をシミュレートします：

      ```shell
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. 一部のリクエストは500 ステータスコードでランダムに失敗し、`var/log/support_report.log`に次のエラーが表示されます。

   ```yaml
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>期待される結果</u>:

すべてのリクエストは200 OKを返します。

<u>実際の結果</u>:

一部のリクエストでは、断続的に500の内部サーバーエラーが返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
