---
title: ACSD-63469：複数のルールで固定金額のカート割引が正しく適用されない
description: 複数のルールが適用される場合、カート全体の固定額の割引が正しく適用されないAdobe Commerceの問題を修正するには、ACSD-63469 パッチを適用します。
feature: Price Rules
role: Admin, Developer
exl-id: fb6dee57-281e-4165-8b70-7ff5949eb677
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-63469：複数のルールで固定金額のカート割引が正しく適用されない

ACSD-63469 パッチでは、複数のルールが適用された場合、カート全体の固定額の割引が正しく適用されない問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59がインストールされている場合に利用できます。 パッチ IDはACSD-63469です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

複数の&#x200B;**[!UICONTROL Fixed amount discount for whole cart]** ルールが同時に適用され、製品に割引または特別価格が適用されている場合、割引値は誤って計算されます。

<u>複製する手順</u>:

1. 850 ドルと85 ドルの2つの商品を制作し、それぞれの特別価格を765 ドルと68 ドルに設定します。
1. 次のように2つの&#x200B;**[!UICONTROL Cart Price Rules]**&#x200B;を作成します。
   * ルール 1
     * **[!UICONTROL Conditions]**: $850の商品の場合、*Qty*&#x200B;を&#x200B;*と設定し、2*&#x200B;以上とします
     * **[!UICONTROL Actions]**: **[!UICONTROL Fixed amount discount for whole cart]**&#x200B;を&#x200B;*$153*&#x200B;件中に適用
   * ルール 2
     * **[!UICONTROL Conditions]**: $85の商品の場合、*数量*&#x200B;を&#x200B;*と設定し、2*&#x200B;以上とします
     * **[!UICONTROL Actions]**: **[!UICONTROL Fixed amount discount for whole cart]**&#x200B;を&#x200B;*$14*&#x200B;件中に適用
1. 両方の商品をカートに追加し、それぞれの商品の数量を2にします。

<u>期待される結果</u>:

買い物かごに適用される割引は167 ドルです。

<u>実際の結果</u>:

カートに適用される割引は41 ドルです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## パッチのインストール後に必要な追加手順

（このセクションはオプションです。問題を修正するためにパッチを適用した後に必要な手順がいくつかある場合があります）。 

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
