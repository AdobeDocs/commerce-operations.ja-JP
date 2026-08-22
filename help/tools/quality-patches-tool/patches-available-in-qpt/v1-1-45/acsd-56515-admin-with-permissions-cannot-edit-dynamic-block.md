---
title: 'ACSD-56515: web サイト レベルの権限を持つ管理者は[!UICONTROL Dynamic Block]を編集できません'
description: Web サイト レベルの権限を持つ管理者が[!UICONTROL Dynamic Block]を追加または編集できないAdobe Commerceの問題を修正するには、ACSD-56515 パッチを適用します。
feature: Roles/Permissions, Admin Workspace
role: Admin, Developer
exl-id: dd3e61a4-aba4-4f86-b4fe-88ca4276ace5
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-56515: web サイト レベルの権限を持つ管理者は[!UICONTROL Dynamic Block]を編集できません

ACSD-56515 パッチは、web サイト レベルの権限を持つ管理者が[!UICONTROL Dynamic Block]を追加または編集できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45がインストールされている場合に利用できます。 パッチ IDはACSD-56515です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Web サイト レベルの権限を持つ管理者は、[!UICONTROL Dynamic Block]を追加または編集できません。

<u>複製する手順</u>:

1. ストアとストアビューでセカンダリ web サイトを作成する。
1. **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**&#x200B;に移動し、利用可能なすべてのリソースを使用して、セカンダリ web サイト スコープに制限されるユーザーの役割を作成します。
1. 上記で作成した役割を持つ管理者ユーザーを作成します。
1. 制限付き管理者ユーザーでログインし、[!UICONTROL Dynamic Block]を作成します。

<u>期待される結果</u>:

Web サイトに制限がある管理者ユーザーは、[!UICONTROL Dynamic Block]を作成できます。

<u>実際の結果</u>:

次のエラーが表示されます：*この項目を表示するには、さらに権限が必要です*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
