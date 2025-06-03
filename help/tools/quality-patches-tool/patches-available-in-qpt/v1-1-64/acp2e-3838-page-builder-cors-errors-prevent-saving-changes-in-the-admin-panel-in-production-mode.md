---
title: 'ACP2E-3838: [!DNL Page Builder] CORS エラーにより、実稼動モードの管理パネルに変更が保存されない'
description: ACP2E-3838 パッチを適用して、Adobe Commerceの問題を修正してください。この問題では、 [!DNL Page Builder] CORS エラーが原因で、実稼動モードの管理パネルに変更が保存されません。
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
source-git-commit: 1b9c721c8200f38b6ce5d1b4de87b1f10e07e8d2
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACP2E-3838:[!DNL Page Builder] CORS エラーにより、実稼動モードの管理パネルに変更が保存されない

ACP2E-3838 パッチでは、[!DNL Page Builder] CORS エラーによって実稼動モードの管理パネルに変更が保存されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3838 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p9 - 2.4.4-p12、2.4.5-p8 - 2.4.5-p11、2.4.6-p6 - 2.4.6-p9、2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

CORS エラー [!DNL Page Builder]、実稼動モードの管理パネルに変更を保存できません。

<u> 再現手順 </u>:

1. 管理パネルにログインします。
1. **[!UICONTROL Content]**/**[!UICONTROL Pages]** に移動します。
1. 「**[!UICONTROL Add New Page]**」をクリックするか、既存のCMSページを選択して「**[!UICONTROL Edit]**」をクリックします。
1. 新しいコンテンツブロックを追加するか、既存のブロックを編集するには、「**[!UICONTROL Edit with Page Builder]**」をクリックします。
1. テキスト、画像、その他の要素の追加など、コンテンツに変更を加えます。
1. **[!UICONTROL Save]** ボタンをクリックします。

<u> 期待される結果 </u>:

ページコンテンツは、エラーなしで正常に保存されます。

<u> 実際の結果 </u>:

1. [!DNL Page Builder] の変更を保存できませんでした。
1. ブラウザーコンソールは、CORS 関連のエラーをログに記録します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
