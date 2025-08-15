---
title: MDVA-43859：削除された顧客がログインしたときに、「No such entity with customerId =」というエラーが記録される
description: MDVA-43859 パッチでは、削除されたお客様がログインしようとすると、エラー*No such entity with customerId =*がログに記録される問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.14 がインストールされている場合に利用できます。 パッチ ID は MDVA-43859。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Variables
role: Admin
exl-id: b8451b08-978a-44a2-8664-4369e832423b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-43859：削除された顧客がログインしたときに、「No such entity with customerId =」というエラーが記録される

MDVA-43859 パッチでは、削除されたユーザがログインしようとすると、エラー *No such entity with customerId =* がログに記録される問題が修正されています。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.14 がインストールされている場合に使用できます。 パッチ ID は MDVA-43859。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.4

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

削除された顧客がログインしようとすると、エラー *customerId が* のそのようなエンティティがログに記録されません。

<u> 再現手順 </u>:

1. フロントエンドから顧客アカウントを作成します。
1. 手順 1 で作成した顧客アカウントからログアウトしてログインします。
1. 別のブラウザーでバックエンドを読み込み、カスタマーグリッドに移動します。
1. 手順 1 で作成した顧客を削除します。
1. 最初のブラウザーに戻り、ログアウトしてみてください。

<u> 期待される結果 </u>:

ユーザーはエラーなくログインページにリダイレクトされます。

<u> 実際の結果 </u>:

*customerId =を持つそのようなエンティティがありません* というエラーが発生します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
