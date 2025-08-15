---
title: MDVA-37984：ステージング更新が適用されている場合、ビジュアルマーチャンダイザーが正しく機能しない
description: MDVA-37984 パッチを使用すると、ステージングアップデートが適用される際に、ビジュアルマーチャンダイザーの「製品をルールで一致させる」機能で製品が正しくフィルタリングされない問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.9 がインストールされている場合に利用できます。 パッチ ID は MDVA-37984。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984：ステージング更新が適用されている場合、ビジュアルマーチャンダイザーが正しく機能しない

MDVA-37984 パッチを使用すると、ステージングアップデートが適用される際に、ビジュアルマーチャンダイザーの「製品をルールで一致させる」機能で製品が正しくフィルタリングされない問題が解決されます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.9 がインストールされている場合に使用できます。 パッチ ID は MDVA-37984。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ステージングアップデートが適用される場合、ビジュアルマーチャンダイザーの「ルールで製品を一致させる」機能で、製品が正しくフィルタリングされません。

<u> 再現手順 </u>:

1. 既存の製品のスケジュール更新を作成します。
   * `entity_id` と `row_id` に異なる値を設定します。
1. 新しい設定可能な製品を作成してから、単純な製品を作成します（新しい製品 `entity_id` と `row_ids` も異なります）。
   * 問題の再現を容易にするには、シンプルな製品に識別可能な数量の値（例：5000）を設定します。
1. カテゴリ/**カテゴリの製品** に移動し、「**ルールで製品を一致** を有効にします。
1. 次に、属性として「数量」、演算子として「より大きい」、値として「4500」を選択します。
1. **保存** をクリックします。

<u> 期待される結果 </u>:

新しく作成された設定可能なプロダクトがリストされます。

<u> 実際の結果 </u>:

新しく作成された設定可能なプロダクトはリストされません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[[!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html): Search for patches[!DNL Quality Patches Tool]」を参照してください。
