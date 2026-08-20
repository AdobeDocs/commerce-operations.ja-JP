---
title: 'ACSD-64178: [!UICONTROL Edit Attribute Set] ページは、何千もの製品属性を使用して読み込みが遅い'
description: ACSD-64178 パッチを適用して、[!UICONTROL Edit Attribute Set] ページが数千の製品属性がある場合に読み込みが遅くなるAdobe Commerceの問題を修正します。
feature: Catalog Management
role: Admin, Developer
exl-id: 959d825d-1b7b-49f0-b49f-64e149106e91
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-64178: [!UICONTROL Edit Attribute Set] ページは、何千もの製品属性を使用して読み込みが遅い

ACSD-64178 パッチは、製品属性が数千ある場合に&#x200B;**[!UICONTROL Edit Attribute Set]** ページの読み込みが遅くなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61がインストールされている場合に利用できます。 パッチ IDはACSD-64178です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

数千もの製品属性がある場合、**[!UICONTROL Edit Attribute Set]** ページの読み込みが遅くなります。

<u>複製する手順</u>:

1. いずれかの属性セットに割り当てられていない少なくとも4200個の属性を作成します。
1. 管理者サイドバーで、**[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Attribute Set]**&#x200B;に移動します。 編集する任意の属性セットをクリックします。

<u>期待される結果</u>:

ページは合理的な時間で読み込まれます。

<u>実際の結果</u>:

ページの読み込みに数分かかります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
