---
title: 'ACP2E-3838: [!DNL Page Builder] CORS エラーにより、実稼動モードの管理パネルに変更を保存できません'
description: ACP2E-3838 パッチを適用して、 [!DNL Page Builder] CORS エラーにより実稼動モードの管理パネルに変更を保存できないAdobe Commerceの問題を修正します。
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
exl-id: 0d590c0e-e21c-4553-a0a3-9332e22796f3
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACP2E-3838: [!DNL Page Builder] CORS エラーにより、実稼動モードで管理パネルに変更を保存できません

ACP2E-3838 パッチは、[!DNL Page Builder] CORS エラーにより、実稼動モードの管理パネルに変更を保存できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64がインストールされている場合に利用できます。 パッチ IDはACP2E-3838です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p9 - 2.4.4-p12、2.4.5-p8 - 2.4.5-p11、2.4.6-p6 - 2.4.6-p9、2.4.7 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL Page Builder]個のCORS エラーにより、実稼動モードの管理パネルに変更を保存できません。

<u>複製する手順</u>:

1. 管理パネルにログインします。
1. **[!UICONTROL Content]** > **[!UICONTROL Pages]**&#x200B;に移動します。
1. **[!UICONTROL Add New Page]**&#x200B;をクリックするか、既存のCMS ページを選択して&#x200B;**[!UICONTROL Edit]**&#x200B;をクリックします。
1. **[!UICONTROL Edit with Page Builder]**&#x200B;をクリックして、新しいコンテンツブロックを追加するか、既存のブロックを編集します。
1. テキスト、画像、その他の要素の追加など、コンテンツに変更を加えます。
1. 「**[!UICONTROL Save]**」ボタンをクリックします。

<u>期待される結果</u>:

ページの内容はエラーなく正常に保存されます。

<u>実際の結果</u>:

1. [!DNL Page Builder]件の変更を保存できませんでした。
1. ブラウザーコンソールは、CORS関連のエラーをログに記録します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
