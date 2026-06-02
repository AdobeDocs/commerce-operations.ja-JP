---
title: ACSD-62355:Adobe Commerceで設定可能な商品編集のパフォーマンスを向上
description: ACSD-62355 パッチを適用して、設定可能な商品編集ページで、多数の属性と値を持つ多数の商品に基づく商品の読み込みが遅くなるAdobe Commerceの問題を修正します。
feature: Admin Workspace
role: Admin, Developer
exl-id: cd934aa9-901a-4f03-ab83-716131e6bd85
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 0%

---

# ACSD-62355:Adobe Commerceで設定可能な商品編集のパフォーマンスを向上

ACSD-62355 パッチは、製品に多数の値を持つ多くの属性がある場合に、設定可能な製品編集ページで読み込み時間が遅くメモリ消費量が多い問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-62355です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定可能な製品が多くの値を持つ複数の属性に基づく場合、設定可能な製品編集ページの読み込みに時間がかかり、遅延やタイムアウトまたはメモリ制限の問題が発生する可能性があります。

<u>複製する手順</u>:

1. デフォルトの属性セットに9つの新しい属性を作成します。それぞれ[!UICONTROL Filterable]で、[!UICONTROL Scope]があります：[!UICONTROL Global]。
   * 属性1:50 オプション
   * 属性2:20 オプション
   * 属性3:10 オプション
   * 属性4:5つのオプション
   * 属性5:5つのオプション
   * 属性6:5つのオプション
   * 属性7:5つのオプション
   * 属性8:3つのオプション
   * 属性9:2つのオプション

1. 新しく作成した属性からオプションを組み合わせて、9つのシンプルな商品を作成します。
   * 製品1：各属性の最初のオプション
   * 製品2：各属性の2番目のオプション
   * 製品3：各属性の3番目のオプション
   * 製品4：各属性からの4番目のオプション
   * 属性のオプション数が製品数よりも少ない場合は、その属性内のランダムなオプションに残りの製品を割り当てます。

1. 新しく作成した属性を使用する設定可能な製品を作成します。
   * 次の設定で1つの子製品を追加します。
      * 属性1の最後のオプションと、属性2から9の最初のオプションを使用します。
      * この結果、1つの設定可能な製品と1つの子製品が得られます。
1. 設定可能な製品の「**[!UICONTROL Configurations]**」タブに移動します。
1. **[!UICONTROL Add Products]**&#x200B;を手動でクリックし、以前に作成したシンプルな製品を1つずつ追加します。
1. 各追加後に変更を保存します。
1. 製品を追加する際は、設定可能な製品を編集ページの読み込み時間を確認してください。
1. 7つの製品を追加すると、RAMの消費量とページの読み込み時間が大幅に増加します

<u>期待される結果</u>:

製品編集フォームは、メモリを大量に消費することなく、迅速かつ効率的に読み込む必要があります。

<u>実際の結果</u>:

設定可能な製品を編集するには読み込みに時間がかかり、メモリ制限やタイムアウトエラーに達する可能性があります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
