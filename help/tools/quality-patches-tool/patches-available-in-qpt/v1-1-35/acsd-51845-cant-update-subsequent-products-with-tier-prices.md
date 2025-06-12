---
title: ACSD-51845：非同期一括を使用して、階層価格と異なる属性セットで後続の製品を更新できない  [!DNL API]
description: ACSD-51845 パッチを適用すると、非同期の一括  [!DNL REST API] を使用して階層価格や異なる属性セットで後続の製品を更新できないAdobe Commerceの問題を修正できます。
feature: REST, Products
role: Admin
exl-id: 83d97946-83da-4c1b-8f2a-21a64ee84e93
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51845：非同期バルクサー [!DNL API] スを使用して、階層価格と異なる属性セットを持つ後続の製品を更新できない

ACSD-51845 パッチを適用すると、非同期の一括アップデートを使用して、階層価格や異なる属性セットで後続の製品を [!DNL REST API] 新できない問題が修正されます。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35 がインストールされている場合に使用できます。 パッチ ID は ACSD-51845 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

階層の価格が設定され、非同期の一括アップデートを使用して属性セットが異なる後続の製品の [!DNL REST API] 新が失敗します。

<u> 再現手順 </u>:

1. [!DNL RabbitMQ] の設定
1. 2 つの属性セットを作成します。
1. 各製品を異なる属性セットに割り当てて、2 つの **シンプルな製品** を作成します。
1. 各製品の **顧客グループ価格** を追加します。
1. 同じ一括アップデートで両方の製品 [!DNL API] アップデートします。
1. `bin/magento queue:consumers:start async.operations.all` コマンドが実行中であることを確認します。
1. 一括 [!DNL API] ールステータスを確認します。

<u> 期待される結果 </u>:

サービスが正常に実行されました。

<u> 実際の結果 </u>:

「*製品を保存できませんでした。 もう一度やり直してください。*

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
