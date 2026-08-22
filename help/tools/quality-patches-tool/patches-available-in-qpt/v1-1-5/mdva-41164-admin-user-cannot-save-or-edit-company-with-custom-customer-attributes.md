---
title: MDVA-41164：カスタム顧客属性を持つ会社を保存または編集できない
description: MDVA-41164 パッチは、管理者ユーザーがファイルまたは任意のタイプの画像のカスタム顧客属性を持つ会社を保存または編集できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5がインストールされている場合に利用できます。 パッチ IDはMDVA-41164です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
exl-id: 9d1792e0-ba7b-444b-b1b1-771fd0e328eb
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# MDVA-41164：カスタム顧客属性を持つ会社を保存または編集できない

MDVA-41164 パッチは、管理者ユーザーがファイルまたは任意のタイプの画像のカスタム顧客属性を持つ会社を保存または編集できない問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5がインストールされている場合に使用できます。 パッチ IDはMDVA-41164です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーは、任意のタイプのファイルまたは画像のカスタム顧客属性を持つ会社を保存または編集できません。

<u>前提条件</u>:

B2B モジュールがインストールされています。

<u>複製する手順</u>:

1. **Stores** > **Config** > **B2B機能**&#x200B;で会社を有効にします。
1. **ストア** > **属性** > **顧客** > **新しい属性を追加**&#x200B;で顧客属性を作成します。
   * 入力タイプ：ファイル（添付）
   * ストアフロントで表示：はい
   * 並べ替え順序：任意
   * 使用するForms：すべて選択
1. **Customers** > **Companies** > **Add New Company**&#x200B;に新しい会社を作成し、上記で作成した新しい属性のファイルをアップロードします。

<u>期待される結果</u>:

ユーザーは会社の作成を完了することができ、添付ファイルはエラーなくアップロードされます。

<u>実際の結果</u>:

* 次のエラーメッセージが表示されます：*ファイルの保存中に問題が発生しました。*
* 例外ログには、次のようなレコードが含まれます。

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-)で使用可能な パッチ」セクションを参照してください。
