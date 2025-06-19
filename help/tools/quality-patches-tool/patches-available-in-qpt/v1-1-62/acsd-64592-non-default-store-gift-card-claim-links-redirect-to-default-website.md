---
title: ACSD-64592：デフォルト以外のストアギフトカード請求リンクは、デフォルトの web サイトにリダイレクト
description: 複数の Web サイトを設定している場合、仮想ギフトカードをセカンダリ（デフォルト以外）の Web サイトから購入すると、メール内のギフトカードコードリンクにデフォルトの Web サイト URL が含まれる問題を修正するために、ACSD-64592 パッチを適用します。
feature: Gift, Products
role: Admin, Developer
exl-id: 1cc026c0-7487-48e8-a092-3e72085ca38a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-64592：デフォルト以外のストアギフトカード請求リンクは、デフォルトの web サイトにリダイレクト

マルチサイト環境で、仮想ギフトカードがセカンダリ（非プライマリ） web サイトから購入された場合、ギフトカードコードのリンクを含むメールによって、ユーザーがデフォルトの web サイトの URL に移動する問題が ACSD-64592 パッチによって修正されています。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

複数の Web サイトを設定する場合、仮想ギフトカードをセカンダリ（デフォルト以外の）サイトから購入すると、ギフトカードコードのリンクを含むメールで、デフォルト Web サイトの URL に移動します。

<u> 再現手順 </u>:

1. セカンダリ web サイト、ストア、ストア表示を作成します。
1. ベース Web サイトとセカンダリ Web サイトに異なるベース URL を設定します。
1. いくつかの金額のオプションを持つ仮想ギフトカードを作成します。
1. **[!UICONTROL Marketing]**/**[!UICONTROL Promotions]**/**[!UICONTROL Gift Card Accounts]** で新しいコードプールを生成します。
1. ギフトカード製品をセカンダリ web サイトに注文します。
1. Commerce管理者で注文を請求します。
1. *You&#39;ve been sent a gift from Two* メールのギフトカードコードリンクの URL を確認してください。

<u> 期待される結果 </u>:

ギフトカードコードのリンクは、2 番目の Web サイトへのリンクである必要があります。

<u> 実際の結果 </u>:

注文が 2 番目の web サイトに配置されている場合でも、ギフトカードコード リンクにはデフォルトの web サイト URL が表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。
* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
