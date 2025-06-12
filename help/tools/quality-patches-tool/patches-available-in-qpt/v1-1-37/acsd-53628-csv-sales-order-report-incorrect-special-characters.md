---
title: ACSD-53628:CSV 販売注文レポートに間違った特殊文字が表示される
description: ACSD-53628 パッチを適用すると、CSV 販売注文レポートに間違った特殊文字が表示されるAdobe Commerceの問題を修正できます。
feature: Orders, Data Import/Export
role: Admin, Developer
exl-id: b6293efe-fbeb-4b1e-b408-34dc86228b8e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-53628:CSV 販売注文レポートに間違った特殊文字が表示される

ACSD-53628 パッチでは、CSV 販売注文レポートに間違った特殊文字が表示される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.37 がインストールされている場合に使用できます。 パッチ ID は ACSD-53628 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法）:2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法）:2.3.7～2.4.6-p2

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

CSV 販売注文レポートに間違った特殊文字が表示される。

<u> 再現手順 </u>:

1. 通貨設定で **[!UICONTROL Base Currency]** と **[!UICONTROL Default Display Currency]** をユーロに変更します。
1. 注文します。
1. 管理者サイドバーで、**[!UICONTROL Reports]**/**[!UICONTROL Sales]**/**[!UICONTROL Orders]** に移動します。
1. 日付を選択します。 「**[!UICONTROL Show Report]**」をクリックします。 「**[!UICONTROL Export]**」をクリックして、CSV を書き出します。

<u> 期待される結果 </u>:

書き出された CSV ファイル内の特殊文字は Excel で正しく表示されます。

<u> 実際の結果 </u>:

CSV 販売注文レポートで、特殊文字が正しく表示されません。


## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
