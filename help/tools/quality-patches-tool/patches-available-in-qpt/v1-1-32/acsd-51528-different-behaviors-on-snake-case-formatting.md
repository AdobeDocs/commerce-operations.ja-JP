---
title: 'ACSD-51528: snake_case 形式の異なる動作'
description: ACSD-51528 パッチを適用して、snake_case 形式で異なる動作が発生するAdobe Commerceの問題を修正してください。
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51528: snake_case 形式の異なる動作

ACSD-51528 パッチは、snake_case 形式の様々な動作を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32 がインストールされている場合に使用できます。 パッチ ID は ACSD-51528 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

snake_case フォーマット設定の異なる動作。

<u> 再現手順 </u>:

1. 様々なプロパティ名を使用して `\Magento\Framework\Api\DataObjectHelper::populateWithArray` 関数をテストします。
1. *NewPName* のような名前を持つプロパティは、*new_p_name* に変換する必要があります。代わりに、*new_pname* に変換されます。
1. また、オブジェクトで *getNewPName* 関数を使用すると、*Abstract モデル* が *new_p_name* への呼び出しを正しく変換し、両方の関数が互いに互換性を持たなくなるので、*null* が返されます。

<u> 期待される結果 </u>

**[!UICONTROL populateWithArray]** 関数は、オブジェクトのプロパティを snake_case に正しく変換し、**[!DNL AbstractModel's]** `Getters` および `Setters` と互換性を持たせる必要があります。

<u> 実績 </u>

**[!UICONTROL populateWithArray]** 関数を使用する場合、名前に 2 つ以上の大文字が行に含まれているオブジェクトプロパティにより、最終的なデータ配列で snake_case 変換が正しく行われなくなります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
