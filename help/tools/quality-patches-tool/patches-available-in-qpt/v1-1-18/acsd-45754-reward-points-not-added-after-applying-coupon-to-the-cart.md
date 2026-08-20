---
title: ACSD-45754：クーポンをカートに適用した後に報酬ポイントが追加されない
description: ACSD-45754 パッチは、クーポンをカートに適用した後に報酬ポイントが追加されない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.18がインストールされている場合に利用できます。 パッチ IDはACSD-45754です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Orders, Rewards, Shopping Cart
role: Admin
exl-id: 02f3bfc4-440b-4d77-adf5-0824d1b21073
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-45754：クーポンをカートに適用した後に報酬ポイントが追加されない

ACSD-45754 パッチは、クーポンをカートに適用した後に報酬ポイントが追加されない問題を解決します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.18がインストールされている場合に使用できます。 パッチ IDはACSD-45754です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.1 - 2.4.5

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

クーポンをカートに適用した後は、特典ポイントは追加されません。

<u>前提条件</u>:

PayPal支払い方法が設定されています。

<u>複製する手順</u>:

1. **ストア** > **その他の設定** > **ポイント換算レート**&#x200B;に移動して、ポイント換算レートを作成します。
1. クーポンコードを使用してカート価格ルールを作成し、ログインした顧客に100 リワードポイントを適用します。
1. PayPalとクーポンコードを利用して、ログイン顧客として商品をチェックアウトできます。
1. 管理画面の顧客アカウントで、報酬ポイントの履歴を確認します。

<u>期待される結果</u>:

価格ルールに従って、顧客に報酬ポイントが追加されます。

<u>実際の結果</u>:

顧客に報酬ポイントは追加されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
