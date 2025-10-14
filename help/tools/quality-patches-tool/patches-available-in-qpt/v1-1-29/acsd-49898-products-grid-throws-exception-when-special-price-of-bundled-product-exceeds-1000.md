---
title: ACSD-49898：製品グリッドが例外をスロー
description: ACSD-49898 パッチを適用すると、バンドルされた商品の特別価格が 1000 を超えると商品グリッドが例外をスローするAdobe Commerceの問題を修正できます。
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: adc8f12e-73e4-4ed5-8081-a9907ec13342
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-49898：製品グリッドが例外をスロー

ACSD-49898 パッチは、バンドルされた製品の価格が 1000 を超える特別価格の場合に、製品グリッドが例外をスローする問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 がインストールされている場合に使用できます。 パッチ ID は ACSD-49898 です。 この問題はAdobe Commerce 2.4.6 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

バンドルされた製品の特別価格が 1000 を超えると、製品グリッドが例外をスローする。 この問題は、特定のロケールで、小数値にドットではなくコンマを使用することに関連しています。

<u> 再現手順 </u>:

1. バンドルされた製品を作成します。
1. 特別価格を 9999 に設定し、保存して閉じます。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動します。

>[!NOTE]
>
>バンドルされた製品 SKU が表示されない場合は検索します。

<u> 期待される結果 </u>:

* ユーザーは、バンドルされた製品を特別価格でフィルタリングまたは表示できます。
* 特別価格は、バンドル製品の割合および他の製品タイプの価格として表示されます。

<u> 実際の結果 </u>:

次のエラーがスローされます。*数値以外の値が発生しました*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [&#x200B; を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja): Search for patches[!DNL Quality Patches Tool]」を参照してください。
