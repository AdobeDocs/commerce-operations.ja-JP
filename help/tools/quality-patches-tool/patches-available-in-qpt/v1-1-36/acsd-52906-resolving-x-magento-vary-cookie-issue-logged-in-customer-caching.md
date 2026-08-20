---
title: ACSD-52906：ログインカスタマーキャッシュのX-Magento-Vary Cookieの問題を解決する
description: X-Magento-Vary cookieがログインユーザーに対して誤って設定されるAdobe Commerceの問題を修正するには、ACSD-52906 パッチを適用します。
feature: Cache
role: Admin, Developer
exl-id: 487b7588-7131-4502-b714-05f37520991f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-52906:X-Magento-Vary Cookieの問題を解決する

ACSD-52906 パッチは、X-Magento-Vary Cookieがログインしているユーザーに対して正しく設定されない問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.36がインストールされている場合に利用できます。 パッチ IDはACSD-52906です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

同じカスタマーセグメントに属するログイン顧客に対して、X-Magento-Vary Cookieが正しく設定されないため、一部のページでキャッシュが不適切になる。

<u>前提条件</u>:

Adobe Commerce Inventory management（MSI）モジュールがインストールされ、有効になります。

<u>複製する手順</u>:

1. [!DNL Varnish]または[!DNL Fastly] キャッシュを設定します。
1. 新しい顧客セグメントを作成し、*登録済み*&#x200B;の顧客に割り当てます。
1. 2つの顧客を作成（例：customer1とcustomer2）
1. キャッシュをクリアします。
1. customer1としてログインし、ホームページに移動します。
1. ブラウザーでシークレットページを開きます。
1. ホームページ以外のページに移動します。
1. customer2としてログインします。
1. ホームページに移動します。
1. ページがブラウザー開発コンソールにキャッシュされているかどうかを確認します。

<u>期待される結果</u>:

ページはキャッシュから取得されます。

<u>実際の結果</u>:

ページはキャッシュされません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
