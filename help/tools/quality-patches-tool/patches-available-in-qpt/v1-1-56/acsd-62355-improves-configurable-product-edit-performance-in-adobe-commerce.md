---
title: ACSD-62355:Adobe Commerceの設定可能な製品編集パフォーマンスを向上
description: ACSD-62355 パッチを適用すると、多数の値を持つ多数の属性に基づいた商品が、設定可能な商品編集ページの読み込みに時間がかかる、Adobe Commerceの問題を修正できます。
feature: Admin Workspace
role: Admin, Developer
exl-id: cd934aa9-901a-4f03-ab83-716131e6bd85
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355:Adobe Commerceの設定可能な製品編集パフォーマンスを向上

多数の値を持つ属性が多数ある場合に、設定可能な製品編集ページで読み込み時間が遅くなりメモリ消費が多くなる問題が、ACSD-62355 パッチで修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-62355 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

設定可能な製品が多数の値を持つ複数の属性に基づいている場合、設定可能な製品の編集ページの読み込みに時間がかかり、遅延が発生したり、タイムアウトやメモリの制限に関する問題が発生したりする可能性があります。

<u> 再現手順 </u>:

1. デフォルトの属性セットに 9 つの新しい属性を作成します。各属性は [!UICONTROL Filterable] で、[!UICONTROL Scope] は [!UICONTROL Global] です。
   * 属性 1:50 オプション
   * 属性 2:20 オプション
   * 属性 3:10 オプション
   * 属性 4:5 つのオプション
   * 属性 5:5 つのオプション
   * 属性 6:5 つのオプション
   * 属性 7:5 つのオプション
   * 属性 8:3 つのオプション
   * 属性 9:2 つのオプション

1. 新しく作成した属性から、オプションを組み合わせて 9 つのシンプルな製品を作成します。
   * 製品 1：各属性からの最初のオプション
   * 製品 2：各属性からの 2 番目のオプション
   * 製品 3：各属性からの 3 番目のオプション
   * 製品 4：各属性からの 4 番目のオプション
   * 属性のオプション数が製品数よりも少ない場合は、残りの製品をその属性内のランダムオプションに割り当てます。

1. 新しく作成した属性を使用する、設定可能な製品を作成します。
   * 次の設定で 1 つの子製品を追加します。
      * 属性 1 の最後のオプションと、属性 2 ～ 9 の最初のオプションを使用します。
      * これにより、設定可能な製品 1 つと子製品 1 つが生成されます。
1. 設定可能な製品の「**[!UICONTROL Configurations]**」タブに移動します。
1. 手動 **[!UICONTROL Add Products]** クリックし、以前に作成したシンプルな製品を 1 つずつ追加し始めます。
1. 各追加後の変更を保存します。
1. 製品を追加する際に、設定可能な製品を編集ページの読み込み時間を確認します。
1. 7 つの製品を追加すると、RAM 消費とページ読み込み時間が大幅に増加しています

<u> 期待される結果 </u>:

製品の編集フォームは、過度のメモリ消費を伴わずに迅速かつ効率的に読み込まれる必要があります。

<u> 実際の結果 </u>:

設定可能な製品の編集は、読み込みに時間がかかり、メモリの制限またはタイムアウトエラーに達する可能性があります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
