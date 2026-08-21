---
title: ACSD-51291：制限付き管理者は、複数のweb サイトに割り当てられた製品に画像/ビデオを追加できます
description: 1つのweb サイトへのアクセス権を持つ制限付き管理者が、複数のweb サイトに割り当てられた製品に画像/ビデオを追加できるAdobe Commerceの問題を修正するには、ACSD-51291 パッチを適用します。
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-51291：制限付き管理者は、複数のweb サイトに割り当てられた製品に画像/ビデオを追加できます

ACSD-51291 パッチでは、単一のweb サイトへのアクセス権を持つ制限付き管理者が、複数のweb サイトに割り当てられた製品に画像やビデオを追加できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-51291です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4 - 2.4.4-p3、2.4.5 - 2.4.5-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

1つのweb サイトへのアクセス権を持つ制限付き管理者は、複数のweb サイトに割り当てられた製品に画像/ビデオを追加できます。

<u>複製する手順</u>

1. 管理者としてログインします。
1. 2つ目のweb サイト、ストア、ストアビューを作成する。
1. 2つ目のweb サイト、ストア、ストアビューのリソースのみを含む2つ目の管理者ロールを作成します。
1. 2人目の管理者を作成し、新しい制限付き管理者ロールに割り当てます。
1. 新しい製品を作成し、デフォルトのweb サイトと新しいweb サイトの両方に割り当てます。
1. メインの管理者プロファイルからログアウトします。
1. 新しい制限付き管理者としてログインします。
1. 作成した製品を編集します。この製品は両方のweb サイトに割り当てられています。
1. 「**[!UICONTROL Images and Videos]**」タブを開きます。

<u>期待される結果</u>:

* 次のメッセージが表示されます。

  *制限付き管理者は、製品が割り当てられているすべてのweb サイトに対する権限を管理者が持っている場合にのみ、画像またはビデオを使用してアクションを実行できます。*

* **[!UICONTROL Add Video]** ボタンはアクティブではありません。

<u>実際の結果</u>:

制限付き管理者は、製品がアクセス権のないweb サイトに割り当てられている場合でも、画像やビデオを追加できます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
