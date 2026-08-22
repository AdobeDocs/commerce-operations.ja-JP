---
title: 'ACSD-58141: L2 Redis キャッシュが有効になっているログイン顧客向けのPOST リクエストでPHPSESSIDが再生成される'
description: L2 Redis キャッシュが有効になっているログインのお客様のストアフロント領域のPOST リクエストで「PHPSESSID」が再生成され、お客様が管理者から更新されるAdobe Commerceの問題を修正するには、ACSD-58141 パッチを適用します。
feature: Customers, Cache
role: Admin, Developer
exl-id: c188c215-204c-489f-8703-4c81ca8703b7
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-58141: L2 Redis キャッシュが有効になっている場合、ログイン顧客向けの[!DNL POST]要求でPHPSESSIDが再生成される

ACSD-58141 パッチは、L2 Redis キャッシュが有効になっていて、顧客が管理者から更新された場合に、ログイン顧客の[!DNL POST]要求で`PHPSESSID`が再生成される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50がインストールされている場合に利用できます。 パッチ IDはACSD-58141です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe CommerceおよびMagento Open Sourceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

L2 Redis キャッシュが有効になっているログイン顧客に対する[!DNL POST]件のリクエストで、`PHPSESSID`が再生成されます。

<u>前提条件</u>

環境は、少なくとも3つのノードを持つRedisで設定する必要があります。

<u>複製する手順</u>:

1. シンプルな商品の作成。
1. 顧客を作成し、ストアフロントにログインします。
1. `PHPSESSID`の値を確認してください。
1. いくつかの[!DNL POST] リクエストを送信します（たとえば、商品をカートに追加する）。`PHPSESSID`は変わりません。
1. **[!UICONTROL Admin]** パネルにログインし、お客様のミドルネームを変更します。
1. ミドルネームが保存されたら、変更して、もう一度保存します。
1. ストアフロントで、[!DNL POST] リクエストを送信します。 `PHPSESSID`を更新する必要があります。
1. ストアフロントで、別の[!DNL POST] リクエストを送信し、`PHPSESSID`を確認します。
1. 前の手順を数回繰り返します。

<u>期待される結果</u>

`PHPSESSID`は、顧客データを変更した後に1回だけ再生成されます。

<u>実際の結果</u>:

`PHPSESSID`は、[!DNL POST]要求が送信されるたびに再生成されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
