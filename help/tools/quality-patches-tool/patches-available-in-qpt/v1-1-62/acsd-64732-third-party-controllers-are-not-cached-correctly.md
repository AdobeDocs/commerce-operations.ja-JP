---
title: ACSD-64732：サードパーティのコントローラーが顧客セグメントと共に正しくキャッシュされない
description: ACSD-64732 パッチを適用すると、サードパーティのコントローラーがカスタマーセグメントで正しくキャッシュされないAdobe Commerceの問題を修正できます。
feature: Cache
role: Admin, Developer
source-git-commit: 047de42098f711036f1f5252d2cbc4a329ebbfb2
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# ACSD-64732：サードパーティのコントローラーが顧客セグメントと共に正しくキャッシュされない

ACSD-64732 パッチにより、サードパーティのコントローラが顧客セグメントと共に正しくキャッシュされない問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 がインストールされている場合に使用できます。 パッチ ID は ACSD-64732 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

サードパーティのコントローラーは、顧客セグメントと共に正しくキャッシュされません。

<u> 再現手順 </u>:

1. カスタムコントローラー（/catalog/category/vary）に移動します。
1. 「**[!UICONTROL Network]**」タブに移動して、**[!DNL X-Magento-Vary]** の値を確認します。

<u> 期待される結果 </u>:

**[!UICONTROL X-Magento-Vary]** の値は、カスタムコントローラーで同じである必要があります。

<u> 実際の結果 </u>:

**[!UICONTROL X-Magento-Vary]** の値が異なるため、キャッシュミスの原因になります。 つまり、カスタムコントローラーにアクセスする場合、以前に生成したキャッシュは使用できません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* Adobe Commerce on Cloud Infrastructure: アップグレードとパッチ > Commerce on Cloud Infrastructure ガイドのパッチの適用

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
