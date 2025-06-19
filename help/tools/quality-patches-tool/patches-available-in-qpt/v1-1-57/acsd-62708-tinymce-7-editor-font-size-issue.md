---
title: '管理パネルの ACSD-62708: [!DNL TinyMCE] 7 エディターのフォントサイズが PT を表示'
description: ACSD-62708 パッチを適用すると、Adobe Commerceの問題が修正されます。この問題では、管理画面の  [!DNL TinyMCE] 7 エディターのフォントサイズに PX ではなく PT が表示されます。 現在は、フォントサイズを PT ではなく PX で設定することもできます。
feature: Admin Workspace
role: Admin, Developer
exl-id: 037a5831-dbc7-4834-ab8e-9b1f765b92b2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-62708：管理パネルの [!DNL TinyMCE] 7 エディターのフォントサイズが PT を表示

ACSD-62708 パッチを使用すると、管理パネルの [!DNL TinyMCE] 7 エディターのフォントサイズが PX ではなく PT で表示される問題が解決されます。 このパッチを使用すると、フォントサイズを PX で設定できます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-62708 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p11、2.4.5-p10、2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理パネルの [!DNL TinyMCE] 7 エディターには、フォントサイズが PX ではなく PT で表示されます。

<u> 再現手順 </u>:

1. 管理パネルで製品の編集ページを開きます。
1. 「[!UICONTROL Content]」セクションを展開します。
1. [!DNL TinyMCE] エディターでフォントコントロールを確認します。

<u> 期待される結果 </u>:

フォントサイズは PX にします。

<u> 実際の結果 </u>:

フォントサイズは PT 単位です。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
