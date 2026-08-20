---
title: MDVA-25631：顧客セグメントを保存して更新できない
description: MDVA-25631 パッチは、ユーザーが多数の顧客を含む顧客セグメントを保存および更新できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.4がインストールされている場合に利用できます。 パッチ IDはMDVA-25631です。 この問題はAdobe Commerce 2.4.2で修正されています。
feature: Customer Service
role: Admin
exl-id: 3cf40538-822a-4d3e-b8fa-20f9ef9228ae
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-25631：顧客セグメントを保存して更新できない

MDVA-25631 パッチは、ユーザーが多数の顧客を含む顧客セグメントを保存および更新できない問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4がインストールされている場合に使用できます。 パッチ IDはMDVA-25631です。 この問題はAdobe Commerce 2.4.2で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3 - 2.3.5-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ユーザーは、多数の顧客を含む顧客セグメントを保存および更新できません。

<u>前提条件</u>:

顧客数が多い（300万人以上）。

<u>複製する手順</u>:

1. 顧客セグメントを作成し、保存してみます。

<u>期待される結果</u>:

顧客セグメントはエラーなく保存されます。

<u>実際の結果</u>:

許可されているメモリ サイズが使い果たされているため、*500* エラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
