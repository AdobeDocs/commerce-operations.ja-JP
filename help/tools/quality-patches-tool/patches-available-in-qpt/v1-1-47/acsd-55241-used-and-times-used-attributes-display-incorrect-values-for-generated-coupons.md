---
title: 'ACSD-55241: **Used**および**Times Used**属性には、生成されたクーポンの誤った値が表示される'
description: ACSD-55241 パッチを適用すると、**Used**属性と**Times Used**属性で生成されたクーポンの値が正しく表示されないAdobe Commerceの問題が修正されます
feature: Price Rules
role: Admin, Developer
exl-id: a156f03c-c939-4ea7-bd34-03c2234edbff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# ACSD-55241:**使用中** および **使用回数** 属性には、生成されたクーポンの誤った値が表示される

ACSD-55241 パッチでは、「**Used**」属性と「**Times Used** 属性に表示されるクーポンの値が正しくない問題が修正されています。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.47 がインストールされている場合に使用できます。 パッチ ID は ACSD-55241 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**使用済み** 属性と **使用回数** 属性には、生成されたクーポンに間違った値が表示されます。

<u> 再現手順 </u>:

1. **[!UICONTROL Cart Price Rules]**/**[!UICONTROL Admin]**/**[!UICONTROL Marketing]** から **[!UICONTROL Promotion]** を作成し、注文の際に一致する条件を追加します（例：小計が *5$* を超える）

   * 割引を適用します。
   * 「**[!UICONTROL Auto Coupon]**」を選択します。
   * **Manage クーポンコード** からいくつかのクーポンコードを生成します。
   * キャッシュの再インデックスとクリーンアップを行います。

1. **[!UICONTROL customer account]** を作成し、フロントエンドにログインします。
1. 買い物かごに *2* を超える数量の製品を 1 つ追加し、1 つのクーポンを適用します。
1. 「**[!UICONTROL Check Out with Multiple Addresses]**」をクリックします。
1. 数量ごとに個別の所在地を選択し、発注して精算プロセスを完了します。
1. 管理者から注文の合計を確認し、適用された割引を確認します。
1. 別のクーポンで別の注文を行います。
1. `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` コマンドを実行して、クーポンコードの使用状況を更新します。

<u> 期待される結果 </u>:

正しい数は、管理者の **の** の **Yes** 値を持つ **使用時間** 列と **[!UICONTROL manage coupon]** 使用 **[!UICONTROL cart price rule]** 列に表示される必要があります。

<u> 実際の結果 </u>:

複数の配送先住所で注文を行った場合、クーポングリッドの **使用時間** 列の使用済みクーポンコード数が更新されず、**使用** 列には *いいえ* 値が表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
