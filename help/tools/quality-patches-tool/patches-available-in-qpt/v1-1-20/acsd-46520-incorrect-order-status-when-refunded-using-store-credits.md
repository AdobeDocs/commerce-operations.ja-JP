---
title: ACSD-46520：ストアクレジットを使用して返金する際の誤った注文ステータス
description: この記事では、ストアクレジットを使用して返金する際にユーザーが誤った注文状況を受け取る問題の解決策を提供します。
feature: Orders, Returns
role: Admin
exl-id: 67740003-a71e-41bf-afda-ca3e32290115
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-46520：ストアクレジットを使用して返金する際の誤った注文ステータス

ACSD-46520 パッチは、ストアクレジットを使用して返金されたときにユーザーが誤った注文ステータスを取得する問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20がインストールされている場合に利用できます。 パッチ IDはACSD-46520です。 この問題はAdobe Commerce 2.4.5で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3および2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストアクレジットを使用して返金された場合、誤った注文ステータスが表示される。

<u>複製する手順</u>:

1. ストアフロントで顧客アカウントを作成し、ログインします。
1. 管理者から顧客にストアクレジットを割り当てます。 ストアクレジットは、注文全体をカバーする必要があります。
1. ストアクレジットを使用して注文します。
1. 注文の請求書を作成します。
1. クレジットメモを作成して、注文の全額を返金します。
「**[!UICONTROL Refund to store credit]**」チェックボックスを選択します。
1. 注文状況を確認します。

<u>期待される結果</u>:

注文ステータスは&#x200B;*クローズ*&#x200B;です。

<u>実際の結果</u>:

注文ステータスは&#x200B;*完了*&#x200B;です。正しいステータスではありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe Commerceまたはオンプレミス [!DNL Magento Open Source]:「Quality Patches Tool」ガイドの「[Quality Patches Tools > Usage](/help/tools/quality-patches-tool/usage.md)」。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
