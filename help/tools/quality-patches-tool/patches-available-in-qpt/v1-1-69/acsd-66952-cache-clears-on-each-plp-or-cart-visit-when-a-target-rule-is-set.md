---
title: ACSD-66952：ターゲットルールが設定されている場合、PLPまたはカート訪問ごとにキャッシュがクリアされる
description: ACSD-66952 パッチを適用して、ターゲットルールが設定された際に不要なパフォーマンスオーバーヘッドが発生する、各PLPまたはカート訪問でキャッシュがクリアされたAdobe Commerceの問題を修正します。
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
type: Troubleshooting
exl-id: abff5761-bcf1-4cfc-b5d9-6a7e1ca907e7
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-66952：ターゲットルールが設定されている場合、PLPまたはカート訪問ごとにキャッシュがクリアされる

ACSD-66952 パッチは、PLPまたはカート訪問のたびにキャッシュがクリアされ、ターゲットルールが設定されたときにパフォーマンスのオーバーヘッドが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-66952です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

各PLPまたはカート訪問でキャッシュがクリアされ、ターゲットルールが設定されたときにパフォーマンスのオーバーヘッドが発生する問題。

<u>複製する手順</u>:

1. 小さなサンプルデータセットを生成します。
1. ターゲットルールの値を次のように作成します。
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *関連製品*
      * **[!UICONTROL Status]** = *アクティブ*
      * **[!UICONTROL Apply to]** = *関連製品*
   1. **[!UICONTROL Products to Match]**
      * デフォルト値のままにします。
   1. **[!UICONTROL Products to Display]**
      * これらの条件のうち&#x200B;**ALL**&#x200B;が&#x200B;*true*&#x200B;の場合、**[!UICONTROL Product Category]** = *定数値111111*&#x200B;に設定します
1. キャッシュ無効化リクエストのログの監視を開始します。
1. 製品ページをご覧ください。
1. 商品をカートに追加し、カートページに移動します。

<u>期待される結果</u>:

アプリケーションは、サイトの閲覧中にキャッシュを無効にしないでください。

<u>実際の結果</u>:

キャッシュタグが無効化されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール
