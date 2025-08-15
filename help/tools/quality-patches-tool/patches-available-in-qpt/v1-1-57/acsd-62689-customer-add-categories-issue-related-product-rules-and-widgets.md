---
title: ACSD-62689：深さ 4 の後で、[!UICONTROL Related Product Rules] およびウィジェットにカテゴリを追加できない
description: ACSD-62689 パッチを適用すると、ユーザーが深さ 4 のネストの後に [!UICONTROL Related Product Rules] および widgets にカテゴリを追加できないというAdobe Commerceの問題を修正できます。
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-62689：深さ 4 の後で、*[!UICONTROL Related Product Rules]* およびウィジェットにカテゴリを追加できない

>[!NOTE]
>
>このパッチは [ACP2E-3689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md) に置き換えられています。

ACSD-62689 パッチでは、ユーザーが深さ 4 のネストの後に *[!UICONTROL Related Product Rules]* およびウィジェットにカテゴリを追加できない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 がインストールされている場合に使用できます。 パッチ ID は ACSD-62689 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーが、深さ 4 のネストの後に、*[!UICONTROL Related Product Rules]* およびウィジェットでカテゴリを追加できません。

<u> 再現手順 </u>:

1. デフォルトのルートカテゴリの下に、*[!UICONTROL Anchor]* と *[!UICONTROL Non-Anchor]* という名前の 2 つのカテゴリを作成します。
   * *[!UICONTROL Is Anchor]* カテゴリに対して *[!UICONTROL Non-Anchor]* フラグが無効になっていることを確認します。
1. **[!UICONTROL Content]**/**[!UICONTROL Widgets]** に移動し、ウィジェットを作成します。
1. 「*[!UICONTROL Layout Updates]*」の下の「**[!UICONTROL Non-Anchor Categories]**」フィールドで「*[!UICONTROL Display on]*」を選択します。
1. 「**[!UICONTROL Specific Categories]**」をクリックします。
1. カテゴリ選択アイコンをクリックします。
1. ルートカテゴリを展開します。
1. カテゴリを確認します。 両方とも無効にし、選択できないようにする必要があります。
1. 「*[!UICONTROL Layout Updates]*」の下の「**[!UICONTROL Anchor Categories]**」フィールドで「*[!UICONTROL Display on]*」を選択します。 次に、手順 5 と 6 に従います。
1. カテゴリを確認します。 両方とも有効かつ選択可能である必要があります。

<u> 期待される結果 </u>:

手順 7 では、*[!UICONTROL Non-Anchor]* カテゴリのみを選択可能にする必要があります。 手順 9 では、*[!UICONTROL Anchor]* カテゴリを選択可能にする必要があります。

<u> 実際の結果 </u>:

手順 7 では、両方のカテゴリを選択できません。 ステップ 9 では、両方のカテゴリを選択可能にする。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。

