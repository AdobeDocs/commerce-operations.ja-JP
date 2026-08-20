---
title: MDVA-39043：管理者ユーザーがCMS ページにウィジェットを追加する際にエラーが発生する
description: MDVA-39043 パッチは、アクセスが制限された管理者ユーザーがCMS ページに「製品」ウィジェットを追加する際にエラーが発生する問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.2がインストールされている場合に利用できます。 パッチ IDはMDVA-39043です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Admin Workspace, CMS, Products
role: Admin
exl-id: 82488249-cca3-4a28-bdc1-fa93a4c9dc2f
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-39043：管理者ユーザーがCMS ページにウィジェットを追加する際にエラーが発生する

MDVA-39043 パッチは、アクセスが制限された管理者ユーザーがCMS ページに「製品」ウィジェットを追加する際にエラーが発生する問題を修正します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2がインストールされている場合に使用できます。 パッチ IDはMDVA-39043です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.4 - 2.4.3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

アクセス権が制限されている管理者ユーザーは、CMS ページに「製品」ウィジェットを追加する際にエラーが発生します。

<u>複製する手順</u>:

1. 管理者を使用してバックエンドにログインし、コンテンツを編集するアクセス権のみを持ちます。
1. **コンテンツ** > **ページ**&#x200B;に移動します。
1. 編集するページを開きます。
1. **ページビルダー**&#x200B;でコンテンツを編集します。
1. **コンテンツを追加** セクションから&#x200B;**製品** ウィジェットを追加します。
1. **製品** ウィジェットの&#x200B;**設定**&#x200B;をクリックします。

<u>期待される結果</u>:

エラーは表示されません。

<u>実際の結果</u>:

次のエラーメッセージが表示されます。

`*A technical problem with the server created an error. Try again to continue what you were doing. If the problem persists, try again later.*`

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
