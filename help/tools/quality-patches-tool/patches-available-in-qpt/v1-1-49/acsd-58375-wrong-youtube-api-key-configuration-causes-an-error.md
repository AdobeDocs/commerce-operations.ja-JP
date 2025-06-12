---
title: ACSD-58375:YouTube API キーの設定が正しくない場合、ストアビューレベルでビデオを追加するとエラーが発生する
description: ACSD-58375 パッチを適用して、Adobe Commerceの問題を修正してください。この問題では、誤ったYouTube API キー設定が、ストア表示レベルでYouTube ビデオを追加する際にエラーが発生します。
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: 24187308-d9dc-4ce2-9cfa-70ccb7726a5b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-58735:YouTube API キーの設定が正しくない場合、ストアビューレベルでビデオを追加するとエラーが発生する

ACSD-58735 パッチでは、YouTube API キーの設定を間違えると、ストア表示レベルでYouTube ビデオを追加する際にエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 がインストールされている場合に使用できます。 パッチ ID は ACSD-58735 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

YouTube API キーの設定が間違っていると、ストア表示レベルでYouTube ビデオを追加する際にエラーが発生します。

<u> 再現手順 </u>:

1. 管理者/ **[!UICONTROL Stores]** / **[!UICONTROL Configuration]** / **[!UICONTROL Catalog]** / **[!UICONTROL Product Video]** に移動します。
1. *範囲* を *[!UICONTROL Main Website]* レベルに変更します。
1. YouTube API キーを追加します。
1. **[!UICONTROL Catalog]**/**[!UICONTROL Products]** に移動します。
1. 任意の製品を選択し、スクロールして *[!UICONTROL Images and Video]* に移動します。 「**[!UICONTROL Add Video]**」をクリックします。
1. YouTube ビデオリンクをコピーして、「ビデオリンク」フィールドに貼り付けます。 フィールドから移動します。

<u> 期待される結果 </u>:

YouTube API キーはグローバルスコープを持ち、web サイトレベルで非表示になっています。

<u> 実際の結果 </u>:

次のエラーがスローされます。*次の理由により、ビデオが表示されません：API キーが無効です。 有効な API キーを渡してください*。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)」を参照してください。
