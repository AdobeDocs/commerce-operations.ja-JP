---
title: ACSD-48204:*Yes/No*属性に基づいて作成されたカタログ価格ルールで、選択した範囲が考慮されない
description: ACSD-48204 パッチを適用すると、*Yes/No*属性に基づいて作成されたカタログ価格ルールが選択した範囲を考慮しないAdobe Commerceの問題が修正されます。
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-48204: *Yes/No* 属性に基づいて作成されたカタログ価格ルールで、選択した範囲が考慮されない

ACSD-48204 パッチは、*Yes/No* 属性に基づいて作成されたカタログ価格ルールが選択した範囲を考慮しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 がインストールされている場合に使用できます。 パッチ ID は ACSD-48204 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 ～ 2.4.2-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

*Yes/No* 属性に基づいて作成されたカタログ価格ルールでは、選択した範囲が考慮されません。

<u> 再現手順 </u>:

1. 2 つの web サイト（デフォルトと W2）を作成します。
1. *はい/いいえ* タイプの製品属性を作成します。
   * Set [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. 2 つのバリエーション（V1 と V2）を持つ任意の属性に基づいて、設定可能な製品を作成します。
   * 設定可能なバリエーション属性セットに *はい/いいえ* 属性を追加します
   * バリエーション（V1）の場合は、デフォルト以外の web サイト（W2）で値を *[!UICONTROL Yes]* に設定します
1. カタログルールを作成します。
   * 両方の web サイトに適用
   * 条件：*はい/いいえ* 属性値は *[!UICONTROL Yes]* です
   * 割引= 50%
1. 設定可能な製品を非デフォルト web サイト（W2）で開きます。
1. V1 バリエーションに 50% のディスカウントが適用されていることを確認します。
1. Adobe Commerce Admin で V1 バリエーションを開きます。
   * デフォルトの Web サイトに切り替える
   * 何も変更せず、商品を保存する
1. 設定可能な製品ストアフロントページを更新します。

<u> 期待される結果 </u>:

V1 バリエーションには、変更が行われていないので、引き続き 50% のディスカウントが適用されます。

<u> 実際の結果 </u>:

割引が消える。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
