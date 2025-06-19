---
title: MDVA-40401：注文に失敗すると、クーポンの使用価値が変更される
description: MDVA-40401 パッチは、注文に失敗した後もクーポンの使用値が変更される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.4 がインストールされている場合に利用できます。 パッチ ID は MDVA-40401。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Orders
role: Admin
exl-id: bc8eedd6-977f-4f21-bcd1-b5f6c4a6704f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-40401：注文に失敗すると、クーポンの使用価値が変更される

MDVA-40401 パッチは、注文に失敗した後もクーポンの使用値が変更される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.4 がインストールされている場合に使用できます。 パッチ ID は MDVA-40401。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.6 ～ 2.3.7-p2、2.4.1 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーは、失敗した順序でクーポンを使用すると、クーポンを再適用できません。

<u> 再現手順 </u>:

1. 自動生成されたクーポンを含む買い物かごルールを作成します。
1. 商品を買い物かごに追加し、クーポンを適用します。
1. **チェックアウト** に移動します。
1. 注文する前に、追加した製品を「在庫切れ」にします。
1. *在庫切れ* エラーが発生する必要があります。
1. cron を実行します。
1. 買い物かごに移動し、その製品を削除します。
1. 別の製品を追加してクーポンを適用します。

<u> 期待される結果 </u>:

以前の注文が行われなかったので、クーポンコードは正常に適用されます。

<u> 実際の結果 </u>:

*クーポンコードが無効です* エラーが発生します。

## パッチの適用

個々のパッチを適用するには、デプロイメントタイプに応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) の節を参照してください。
