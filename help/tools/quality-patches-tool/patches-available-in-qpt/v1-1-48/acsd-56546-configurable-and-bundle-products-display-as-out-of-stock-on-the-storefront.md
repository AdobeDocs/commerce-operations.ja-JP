---
title: ACSD-56546：設定可能な製品およびバンドル製品が、ストアフロントに在庫切れとして表示される
description: '*[!UICONTROL Display Out of Stock Products]* コンフィギュレーションオプションが無効になっている場合、設定可能なおよびバンドル製品がストアフロントに在庫切れとして表示されるAdobe Commerceの問題を修正するために、ACSD-56546 パッチを適用してください。'
feature: Storefront, Products
role: Admin, Developer
exl-id: d9bb05ca-a84e-48bb-957e-55b28631b3cb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-56546：設定可能な製品およびバンドル製品が、ストアフロントに在庫切れとして表示される

ACSD-56546 パッチでは、設定可能な製品とバンドル製品がストアフロントに在庫切れとして表示される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 がインストールされている場合に使用できます。 パッチ ID は ACSD-56546 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

*[!UICONTROL Display Out of Stock Products]* のオプションが無効になっている場合、設定可能な製品とバンドル製品は、ストアフロントに在庫切れとして表示されます。

<u> 再現手順 </u>:

1. **[!UICONTROL Display Out of Stock Products]** オプションを *いいえ* に設定します。
1. Web サイト、ストア、ストアレビューを作成します。
1. ソースと在庫を作成して、2 番目の web サイトに割り当てます。
1. 2 つの子製品を持つ *設定可能な* 製品を作成します。 子製品を両方のソースと両方の web サイトに割り当てます。
1. 最初の子製品を更新して、両方のソースを *qty=0* にします。
1. 2 つ目の子製品を更新し、2 つ目の web サイトで無効にします。
1. 完全な再インデックスを実行します。
1. 2 番目の web サイトで、設定可能な製品を含むカテゴリを確認します。

<u> 期待される結果 </u>:

在庫切れの設定可能な製品は、ストアフロントには表示されません。

<u> 実際の結果 </u>:

在庫切れの設定可能な製品は、「*[!UICONTROL Display Out of Stock Products]*」オプションが無効になっている場合でも、ストアフロントに表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
