---
title: 'ACSD-63182: バンドル製品の複製後に製品を保存するとエラーが発生する'
description: ACSD-63182 パッチを適用して、バンドル製品がMSIを有効にして複製された後に製品を保存する際にエラーが発生するAdobe Commerceの問題を修正します。
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-63182: バンドル製品の複製後に製品を保存するとエラーが発生する

ACSD-63182 パッチでは、バンドルオプションとして使用される単純な製品が、バンドル製品の複製後に保存できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-63182です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

バンドル製品を複製した後に、バンドルオプションとして使用される単純な製品を保存すると、エラーが発生します。

<u>複製する手順</u>:

1. 新しいMSI ソースと在庫を作成します。
1. 2つのシンプルな製品（**p1**&#x200B;と&#x200B;**p2**）を作成します。
1. バンドルオプションとして&#x200B;**p1**&#x200B;および&#x200B;**p2**&#x200B;を含むバンドル製品&#x200B;**b1**&#x200B;を作成します。
1. **バンドル製品b1**&#x200B;を編集し、***[!UICONTROL Save and Duplicate]***&#x200B;をクリックします。
1. **シンプル製品p1**&#x200B;を編集し、**[!UICONTROL Save]**&#x200B;をクリックします。

<u>期待される結果</u>:

製品はエラーなく保存されます。

<u>実際の結果</u>:

次のエラーが表示されます。
*例外：同じID &#39;XXX&#39;の項目（Magento\Catalog\Model\Product\Interceptor）が既に存在します。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
