---
title: ACSD-67347：クーポンコードを使用すると、「ロックを取得できません」エラーで注文が失敗する
description: クーポンコードに特殊文字（BIT/123456など）が含まれ、ファイルロックが有効になっている場合に「ロックを取得できません」エラーが表示され、注文が失敗するAdobe Commerceの問題にACSD-67347 パッチを適用します。
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: a439e163-8b09-456c-91bd-6ee67528744e
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-67347: クーポンコードを使用すると、*ロックを取得できません* エラーが発生し、注文が失敗します

ACSD-67347 パッチは、クーポンコードに特殊文字（BIT/123456など）が含まれ、ファイルロックが有効になっている場合に&#x200B;*ロックを取得できない* エラーで注文が失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-67347です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p12

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

特殊文字を含むクーポンが使用され、ファイルのロックが有効になっている場合、*ロックを取得できません* エラーが発生して注文が失敗します。

<u>複製する手順</u>:

1. 2.4-developをインストールします。
1. `env.php` ファイルでファイル ロック設定を設定します。

   ```text
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. クーポンコード形式&#x200B;*BIT/123456*&#x200B;を使用して、クーポン付きのカートルールを作成します。
1. シンプルな商品の作成。
1. 商品をカートに追加し、クーポンコードを適用します。
1. チェックアウトに進み、注文します。

<u>期待される結果</u>:

クーポンコードの作成制限がないため、正常に注文できます。

<u>実際の結果</u>:

注文できません。 次のエラーが表示されます：*ロックを取得できません。*

```text
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
