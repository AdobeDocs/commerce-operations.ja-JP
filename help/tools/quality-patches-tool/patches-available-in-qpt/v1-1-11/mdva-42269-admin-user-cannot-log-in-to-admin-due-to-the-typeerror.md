---
title: MDVA-42269：管理者ユーザーが「TypeError」エラーにより管理者にログインできない
description: MDVA-42269 パッチは、TypeErrorが原因で管理者ユーザーが管理者にログインできない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.11がインストールされている場合に利用できます。  パッチ IDはMDVA-42269です。  最新のパッチアップデートはQPT 1.1.15です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Admin Workspace
role: Admin
exl-id: 42ad4bb5-950f-476d-bf55-931b38bcb937
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-42269：管理者ユーザーが「TypeError」エラーにより管理者にログインできない

MDVA-42269 パッチは、TypeErrorが原因で管理者ユーザーが管理者にログインできない問題を修正します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.11がインストールされている場合に使用できます。  パッチ IDはMDVA-42269です。  最新のパッチアップデートはQPT 1.1.15です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1、2.3.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.3-p1 - 2.4.3-p2、2.3.7-p3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

次のエラーにより、管理者ユーザーは管理者にログインできません。*TypeError: strtotime （）は、パラメーター1が文字列であることを想定しています。nullが指定されています。*

<u>複製する手順</u>:

Commerce Adminにログインします。

<u>期待される結果</u>:

管理者ユーザーは、正しいユーザー名とパスワードでログインできます。

<u>実際の結果</u>:

管理者ユーザーはログインできません。 次のエラーが記録されます：*TypeError: strtotime （）は、パラメーター1が文字列であることを想定しています。nullが指定されています。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
