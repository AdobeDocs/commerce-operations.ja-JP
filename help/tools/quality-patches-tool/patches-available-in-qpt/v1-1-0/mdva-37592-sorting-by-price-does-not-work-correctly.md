---
title: MDVA-37592：価格がゼロの製品で価格による並べ替えが機能しない
description: MDVA-37592 Adobe Commerce パッチは、共通カタログに価格ゼロが割り当てられている商品の価格による並べ替えが正しく機能しない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.0 がインストールされている場合に利用できます。 パッチ ID は MDVA-37592。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37592：価格がゼロの製品で価格による並べ替えが機能しない

MDVA-37592 Adobe Commerce パッチは、共通カタログに価格ゼロが割り当てられている商品の価格による並べ替えが正しく機能しない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.0 がインストールされている場合に使用できます。 パッチ ID は MDVA-37592。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* クラウドアーキテクチャ 2.4.0-p1 上のAdobe Commerce

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメントタイプ） 2.3.6-2.4.2-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

共有カタログに価格ゼロが割り当てられている製品の場合、価格で並べ替えても正しく機能しません。

<u> 前提条件 </u>:

B2B がインストールされています。

<u> 再現手順 </u>:

1. 共有カタログを有効にします。
1. 次の価格の 4 つの製品を作成して、カテゴリ（$50、$60、$70 および$80）に割り当てます。
1. 上記の製品で共有カタログを作成します。
1. 価格が 70 ドルの製品については、カスタム価格をゼロに設定します。
1. 次に、会社ユーザーを作成し、作成した共有カタログに割り当てます。
1. 会社アカウントを使用してログインし、製品が割り当てられているカテゴリを参照します。
1. 価格で並べ替えてみてください。

<u> 期待される結果 </u>:

価格がゼロの製品は正しく並べ替えられています。

<u> 実際の結果 </u>:

価格がゼロの商品が正しく並べ替えられていません。 代わりに、元の価格に従って並べ替えられます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
