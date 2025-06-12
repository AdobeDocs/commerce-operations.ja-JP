---
title: MDVA-41046：割り当てにカスタムオプションを使用できないシンプルな製品
description: MDVA-41046 パッチは、カスタム オプションを持つシンプルな製品を設定可能/グループ化された製品に割り当てることができない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5 がインストールされている場合に利用できます。 パッチ ID は MDVA-41046。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Products
role: Developer
exl-id: 7fd7a9db-f834-4aea-a9d7-6e9535c037c8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-41046：割り当てにカスタムオプションを使用できないシンプルな製品

MDVA-41046 パッチは、カスタム オプションを持つシンプルな製品を設定可能/グループ化された製品に割り当てることができない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.5 がインストールされている場合に使用できます。 パッチ ID は MDVA-41046。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

カスタムオプションを使用したシンプルな製品は、設定可能/グループ化された製品に割り当てることはできません。

<u> 再現手順 </u>:

1. カスタマイズ可能なオプションを含むシンプルな製品を作成し、configurable 属性の値を設定します。
   * 設定可能な属性として *カラー* を使用し、カラー値として *イエロー* を選択します。
1. シンプルな製品を保存します。
1. 次に、設定可能な製品を作成ページに移動します。
1. 「設定の作成」ウィザードを実行し、属性カラーとして *イエロー* を選択していることを確認します。
1. 設定可能な製品を保存せずに、「選択」ドロップダウンから「別の製品を選択」オプションを選択します。
1. これにより、色属性イエローでフィルタリングされた製品グリッドが開きます。 次に、カスタマイズ可能なオプションを使用して以前に作成したシンプルな製品を選択します。
1. 設定可能な商品を保存します。

<u> 期待される結果 </u>:

カスタムオプションを含むシンプルな製品は、手順 6 の割り当て（グリッドに表示）に使用できます。

<u> 実際の結果 </u>:

構成セクションが空です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) の節を参照してください。
