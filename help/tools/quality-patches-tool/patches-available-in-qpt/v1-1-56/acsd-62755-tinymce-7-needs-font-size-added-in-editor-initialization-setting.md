---
title: 'ACSD-62755: [!DNL TinyMCE] 7には、フォントサイズとフォントがエディター初期化設定に追加されている必要があります'
description: ACSD-62755 パッチを適用して、 [!DNL TinyMCE] 7で*font size*と*font family*がエディターの初期化設定内に特別に追加されるAdobe Commerceの問題を修正します。
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-62755: [!DNL TinyMCE] 7には、フォントサイズとフォントがエディター初期化設定に追加されている必要があります

ACSD-62755 パッチでは、[!DNL TinyMCE] 7で&#x200B;*フォントサイズ*&#x200B;と&#x200B;*フォントファミリー*&#x200B;のセレクターをエディターの初期化設定内に特別に追加する必要がある問題が修正されました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-62755です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p10

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方式） 2.4.4-p11、2.4.5-p10、2.4.6-p8、2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL TinyMCE] 7では、*フォントサイズ*&#x200B;および&#x200B;*フォントファミリー*&#x200B;のセレクターをエディターの初期化設定内に追加する必要があります。

<u>複製する手順</u>:

**[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]**&#x200B;に移動し、*[!UICONTROL Show Editor]*&#x200B;を選択します。

<u>期待される結果</u>:

*フォントサイズ*&#x200B;および&#x200B;*フォントファミリー*&#x200B;のセレクターがWYSIWYG エディターに表示されます。

<u>実際の結果</u>:

WYSIWYG エディターに&#x200B;*フォントサイズ* セレクターがありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
