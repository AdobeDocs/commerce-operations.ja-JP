---
title: 'ACSD-62415: Adobe Commerce バックエンドで[!UICONTROL Categories]の読み込みが非常に遅い'
description: ACSD-62415 パッチを適用して、多数のアンカーカテゴリが存在する場合に[!UICONTROL Admin] パネルの[!UICONTROL Categories] ページのパフォーマンスが非常に遅く読み込まれるAdobe Commerceの問題を修正します。
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 3101723d-dcc0-49fa-a823-2a2d37037534
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-62415: アンカーカテゴリが存在する場合、Adobe Commerce バックエンドで&#x200B;**[!UICONTROL Categories]**&#x200B;の読み込みが非常に遅くなる

ACSD-62415 パッチは、多数のアンカーカテゴリが存在する場合に、**[!UICONTROL Admin]** パネルの&#x200B;**[!UICONTROL Categories]** ページのパフォーマンスが非常に遅く読み込まれる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-62415です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

多数のアンカーカテゴリが存在する場合、**[!UICONTROL Admin]** パネルの&#x200B;**[!UICONTROL Categories]** ページの読み込みが非常に遅くなります。

<u>複製する手順</u>:

1. 3K アンカーカテゴリを生成します。
1. **[!UICONTROL Admin]** パネルで&#x200B;**[!UICONTROL Catalog]** > **[!UICONTROL Categories]** ページを開きます。

<u>期待される結果</u>:

**[!UICONTROL Categories]** ページの読み込みが速いため、クエリを1,000回繰り返す必要はありません。

<u>実際の結果</u>:

読み込みに7～20秒かかり、クエリが1,000回以上実行されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
