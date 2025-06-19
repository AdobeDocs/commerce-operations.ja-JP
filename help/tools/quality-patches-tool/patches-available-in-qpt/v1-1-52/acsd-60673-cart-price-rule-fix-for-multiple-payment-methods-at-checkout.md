---
title: ACSD-60673：チェックアウト時 [!UICONTROL Cart Price Rule] 複数の支払い方法に関する問題を修正しました
description: ACSD-60673 パッチを適用すると、支払い方法条件を使用する [!UICONTROL Cart Price Rule] からの割引が合計に常に表示されるとは限らないAdobe Commerceの問題を修正できます。
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673：チェックアウト時 [!UICONTROL Cart Price Rule] 複数の支払い方法に関する問題を修正しました

ACSD-60673 パッチは、支払い方法の条件を使用する [!UICONTROL Cart Price Rule] からの割引が常に合計に表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 がインストールされている場合に使用できます。 パッチ ID は ACSD-60673 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

チェックアウト時の複数の支払い方法の [!UICONTROL Cart Price Rule] が、特定の支払い方法に正しく適用されない。

<u> 前提条件 </u>

**[!UICONTROL Multiple Payment Methods]**/**[!UICONTROL Money Order]** で、**[!UICONTROL Bank Transfer]** が有効になっていることを確認します。

<u> 再現手順 </u>:

1. **[!UICONTROL Multiple Payment Methods]** を有効にします。
1. *[!UICONTROL Cart Price Rule]* を作成します。
   * Set **[!UICONTROL Conditions]** :**[!UICONTROL Money Order]** （または銀行振替）への支払方法
   * **[!UICONTROL Actions]** を選択=すべての製品に対して *25%* 割引
1. 仮想製品を作成します。
1. 新しい見積もりとゲストの顧客 *[!UICONTROL Status]* をコピーするには、ストアフロントに移動して Cookie をクリアします。
1. 仮想商品を買い物かごに追加します。
1. *チェックアウト* に進みます。
1. *[!UICONTROL Cart Price Rule]* で定義された支払い方法をクリックします。
1. *[!UICONTROL Billing Address]* を更新します。
1. 割引額が合計金額で表示されていることを確認します。
1. チェックボックスをクリックして、支払い方法を変更します。
1. 割引が表示されていることを確認します。

<u> 期待される結果 </u>:

該当する支払い方法に切り替えるためにチェックボックスをクリックすると、割引が *合計* に表示されます。

<u> 実際の結果 </u>:

割引は「合計 *に表示され* せん。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
