---
title: ACSD-66153：誤ったレイアウト構造がキャッシュされているので、ページが 500 エラーを返す
description: ACSD-66153 パッチを適用すると、キャッシュされた誤ったレイアウト構造が原因でページが 500 エラーコードを返すAdobe Commerceの問題が修正されます。
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: 70c7255e369ef366407d539488f0d815eb93f48a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACSD-66153：誤ったレイアウト構造がキャッシュされているので、ページが 500 エラーを返す

ACSD-66153 パッチでは、キャッシュされた誤ったレイアウト構造が原因でページが 500 エラーコードを返す問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-66153 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p10

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

キャッシュされた誤ったレイアウト構造が原因で、ページが 500 エラーを返します。

<u> 再現手順 </u>:

1. `2.4-develop` のインストール
1. カスタムモジュールを作成してインストールします。
1.1 `catalog_category_view` レイアウトにカスタム ブロックを追加します。
1.1 コンストラクターを使用してカスタムブロックに `Magento\Framework\View\Result\Layout` を挿入する。
1. カテゴリ **[!UICONTROL shop]** を作成します。
1. **[!UICONTROL two terminal windows]** を開きます。
   1. **ターミナル 1**：レイアウトキャッシュを継続的に消去します。

      ```
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **ターミナル 2**：カテゴリページに対する同時リクエストのシミュレーション：

      ```
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. 一部のリクエストは 500 ステータスコードでランダムに失敗し、`var/log/support_report.log` に次のエラーが表示されます。

   ```
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u> 期待される結果 </u>:

すべてのリクエストが 200 OK を返します。

<u> 実際の結果 </u>:

一部のリクエストでは、断続的に 500 件の内部サーバーエラーが返されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
