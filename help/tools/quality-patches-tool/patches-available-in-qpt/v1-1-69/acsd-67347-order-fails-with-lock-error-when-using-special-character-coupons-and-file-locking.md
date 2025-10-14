---
title: ACSD-67347：クーポンコード使用時に「ロックを取得できません」エラーが発生して注文が失敗する
description: クーポンコードに特殊文字（BIT/123456 など）が含まれ、ファイルロックが有効な場合、注文が「ロックを取得できません」エラーで失敗するAdobe Commerceの問題に ACSD-67347 パッチを適用します。
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347：クーポンコードの使用時に *ロックを取得できません* エラーが発生して注文が失敗する

クーポンコードに特殊文字（BIT/123456 など）が含まれ、ファイルロックが有効な場合、注文が *ロックを取得できません* エラーで失敗する問題が ACSD-67347 パッチで修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACSD-67347 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p12

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

特殊文字を含むクーポンが使用され、ファイルロックが有効になっている場合、注文は *ロックを取得できません* エラーで失敗します。

<u> 再現手順 </u>:

1. インストール 2.4-develop.
1. `env.php` ファイルのファイルロック設定を指定します。

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. クーポンコード形式：*BIT/123456* を使用して、クーポン付きの買い物かごルールを作成します。
1. シンプルな製品を作成します。
1. 商品を買い物かごに追加し、クーポンコードを適用します。
1. チェックアウトに進み、注文します。

<u> 期待される結果 </u>:

クーポンコードの作成に制限がないため、注文は正常に行われます。

<u> 実際の結果 </u>:

注文できません。 次のエラーが表示されます。*ロックを取得できません。*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
