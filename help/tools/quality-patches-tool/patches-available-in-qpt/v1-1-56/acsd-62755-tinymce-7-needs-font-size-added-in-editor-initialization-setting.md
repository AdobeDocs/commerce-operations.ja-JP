---
title: 'ACSD-62755: [!DNL TinyMCE] 7 では、フォントサイズとフォントをエディターの初期化設定に追加する必要があります'
description: ACSD-62755 パッチを適用して、Adobe Commerceの問題を修正してください。 [!DNL TinyMCE] 7 では、エディタの初期設定で*font size*と*font family*を追加する必要があります。
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# ACSD-62755:[!DNL TinyMCE] 7 では、フォントサイズとフォントをエディターの初期化設定に追加する必要があります

ACSD-62755 パッチは、[!DNL TinyMCE] 7 で *フォントサイズ* および *フォントファミリー* のセレクターをエディターの初期化設定内で特別に追加する必要がある問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-62755 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p10

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p11、2.4.5-p10、2.4.6-p8、2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL TinyMCE] 7 では、エディターの初期化設定内で *フォントサイズ* および *フォントファミリー* セレクターを特別に追加する必要があります。

<u> 再現手順 </u>:

**[!UICONTROL Catalog]**/**[!UICONTROL Products]**/**[!UICONTROL Content]** に移動し、「*[!UICONTROL Show Editor]*」を選択します。

<u> 期待される結果 </u>:

*フォントサイズ* および *フォントファミリー* セレクターがWYSIWYG エディターに表示されます。

<u> 実際の結果 </u>:

*フォントサイズ* セレクターがWYSIWYG エディターに表示されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
