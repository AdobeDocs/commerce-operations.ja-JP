---
title: ACSD-64467：カテゴリの説明をストア表示レベルで保存した後、WYSIWYG エディターが空になりました
description: ACSD-64467 パッチを適用すると、ストアビューレベルでカテゴリの説明を保存した後、WYSIWYG エディターが空のように表示されるAdobe Commerceの問題が修正されます。
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467：カテゴリの説明をストア表示レベルで保存した後、WYSIWYG エディターが空になりました

ACSD-64467 パッチでは、カテゴリの説明をストアビューレベルで保存した後、WYSIWYG エディターが空のように表示される問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 がインストールされている場合に使用できます。 パッチ ID は ACSD-64467 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ストアビューレベルでカテゴリの説明を保存すると、WYSIWYG エディターが空のように表示されます。

<u> 再現手順 </u>:

1. Commerce管理者のストア表示レベルでカテゴリを編集します。
1. カテゴリの説明の横にある「*[!UICONTROL Use default value]*」チェックボックスの選択を解除します。
1. WYSIWYG エディターに説明を入力します。
1. 「**[!UICONTROL Save]**」をクリックします。

<u> 期待される結果 </u>:

説明が保存され、正しく表示されます。

<u> 実際の結果 </u>:

ページをリロードすると、説明は空になります。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
