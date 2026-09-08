---
title: ACSD-64732：顧客セグメントでサードパーティコントローラーが正しくキャッシュされない
description: ACSD-64732 パッチを適用して、お客様のセグメントでサードパーティ製コントローラが正しくキャッシュされないAdobe Commerceの問題を修正します。
feature: Cache
role: Admin, Developer
exl-id: 378e5a96-06dd-4796-9e45-a67cf539fcce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-64732：顧客セグメントでサードパーティコントローラーが正しくキャッシュされない

ACSD-64732 パッチは、お客様のセグメントでサードパーティコントローラが正しくキャッシュされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62がインストールされている場合に利用できます。 パッチ IDはACSD-64732です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客セグメントでサードパーティ製コントローラが正しくキャッシュされない。

<u>複製する手順</u>:

1. カスタムコントローラー（/catalog/category/vary）に移動します。
1. 「**[!UICONTROL Network]**」タブに移動し、**[!DNL X-Magento-Vary]**&#x200B;の値を確認します。

<u>期待される結果</u>:

**[!UICONTROL X-Magento-Vary]**&#x200B;の値は、カスタムコントローラーで同じである必要があります。

<u>実際の結果</u>:

**[!UICONTROL X-Magento-Vary]**&#x200B;の値が異なるため、キャッシュ ミスが発生します。 つまり、以前に生成されたキャッシュは、カスタムコントローラーにアクセスする際に使用できません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Adobe Commerce オンクラウドインフラストラクチャ：アップグレードとパッチ/パッチの適用については、Commerce オンクラウドインフラストラクチャガイドを参照してください。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
