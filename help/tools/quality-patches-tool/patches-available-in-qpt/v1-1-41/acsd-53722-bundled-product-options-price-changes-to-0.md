---
title: 'ACSD-53722: バンドルされた製品オプションの価格が$0 に変更されました'
description: ACSD-53722 パッチを適用すると、異なる範囲のスケジュールされたアップデートがアクティブになると、バンドルされた製品オプションの価格が$0 に変わるAdobe Commerceの問題を修正できます。
feature: Products
role: Admin, Developer
exl-id: 2e974a6a-0c79-442f-9b45-b4edf831a052
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-53722: バンドルされた製品オプションの価格が$0 に変更されました

ACSD-53722 パッチは、異なるスコープのスケジュールされたアップデートがアクティブになると、バンドルされた製品オプションの価格が$0 に変更される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41 がインストールされている場合に使用できます。 パッチ ID は ACSD-53722 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

異なる範囲のスケジュールされたアップデートがアクティブになると、バンドルされた製品オプションの価格は$0 に変更されます。

<u> 再現手順 </u>:

1. A と B の 2 つの web サイトを作成します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]** で設定を指定します。
1. Web サイト A および B で、固定価格のバンドル製品を作成します。

   * バンドル製品価格=固定= *0*

1. バンドルのドロップダウンオプションとして 1 つのシンプルな製品を追加します。 次の価格を設定します。

   * シンプルな製品のすべての店舗ビュー価格はバンドルされたオプション = *120*
   * シンプルな製品のウェブサイト バンドルオプション内の価格= *130*
   * 単純な製品の Web サイト B の価格はバンドルされたオプション = *140*

1. Web サイト A でバンドルされた製品を無効にするアップデートをスケジュールします。

<u> 期待される結果 </u>:

Web サイト A の更新予定は、Web サイト B の価格には影響しません。

<u> 実際の結果 </u>:

スケジュールされた更新後、web サイト B のバンドルされた製品オプションの価格は **$0** に変更されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
