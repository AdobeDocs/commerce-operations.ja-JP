---
title: 'ACSD-62689: [!UICONTROL Related Product Rules]のカテゴリと深度4の後のウィジェットを追加できない'
description: ACSD-62689 パッチを適用して、お客様が[!UICONTROL Related Product Rules]にカテゴリを追加できず、深度4のネストの後にウィジェットを追加できないAdobe Commerceの問題を修正します。
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-62689: *[!UICONTROL Related Product Rules]*&#x200B;のカテゴリと深度4の後のウィジェットを追加できない

>[!NOTE]
>
>このパッチは[ACP2E-3689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md)に置き換えられます。

ACSD-62689 パッチは、顧客が&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;にカテゴリを追加できず、深度4のネスト後にウィジェットを追加できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57がインストールされている場合に利用できます。 パッチ IDはACSD-62689です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

顧客は&#x200B;*[!UICONTROL Related Product Rules]*&#x200B;にカテゴリを追加できず、深度4のネストの後にウィジェットを追加できません。

<u>複製する手順</u>:

1. 既定のルート カテゴリの下に&#x200B;*[!UICONTROL Anchor]*&#x200B;と&#x200B;*[!UICONTROL Non-Anchor]*&#x200B;という名前の2つのカテゴリを作成します。
   * *[!UICONTROL Non-Anchor]* カテゴリの&#x200B;*[!UICONTROL Is Anchor]* フラグが無効になっていることを確認します。
1. **[!UICONTROL Content]** > **[!UICONTROL Widgets]**&#x200B;に移動し、ウィジェットを作成します。
1. *[!UICONTROL Layout Updates]*&#x200B;で、*[!UICONTROL Display on]* フィールドの&#x200B;**[!UICONTROL Non-Anchor Categories]**&#x200B;を選択します。
1. **[!UICONTROL Specific Categories]**&#x200B;をクリックします。
1. カテゴリ選択アイコンをクリックします。
1. ルートカテゴリを展開します。
1. カテゴリを確認します。 両方を無効にし、選択できません。
1. *[!UICONTROL Layout Updates]*&#x200B;で、*[!UICONTROL Display on]* フィールドの&#x200B;**[!UICONTROL Anchor Categories]**&#x200B;を選択します。 次に、手順5と6に従います。
1. カテゴリを確認します。 両方を有効にして選択可能にする必要があります。

<u>期待される結果</u>:

手順7では、*[!UICONTROL Non-Anchor]* カテゴリのみを選択可能にする必要があります。 手順9では、*[!UICONTROL Anchor]* カテゴリを選択可能にする必要があります。

<u>実際の結果</u>:

手順7では、両方のカテゴリは選択できません。 手順9では、両方のカテゴリを選択できます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。

