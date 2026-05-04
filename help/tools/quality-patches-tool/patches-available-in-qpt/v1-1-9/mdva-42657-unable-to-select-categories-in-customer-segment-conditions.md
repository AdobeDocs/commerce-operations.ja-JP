---
title: MDVA-42657：顧客セグメント条件でカテゴリを選択できません
description: MDVA-42657 パッチは、管理者ユーザーが顧客セグメント条件でカテゴリを選択できない問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.9がインストールされている場合に利用できます。 パッチ IDはMDVA-42657です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# MDVA-42657：顧客セグメント条件でカテゴリを選択できません

MDVA-42657 パッチは、管理者ユーザーが顧客セグメント条件でカテゴリを選択できない問題を解決します。 このパッチは、[品質パッチツール （QPT） &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9がインストールされている場合に使用できます。 パッチ IDはMDVA-42657です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理者ユーザーは、顧客セグメント条件でカテゴリを選択できません。

<u>複製する手順</u>:

1. **顧客** > **セグメント**&#x200B;に移動します。
1. 新しいセグメントを作成します。
1. 新しく作成したセグメントに移動し、左側のナビゲーションで「**条件**」をクリックします。
1. 緑色のプラス記号をクリックします。
1. 「製品」で「製品履歴」を選択します。
1. 「閲覧済み」を「注文済み」に変更します。
1. 「ALL」を「ANY」に変更します。
1. ネストされた緑のプラス記号をクリックし、「カテゴリ」を選択します。
1. **...**&#x200B;記号をクリックし、選択アイコン（チェックマークの左側）をクリックします。
1. ブラウザーの開発コンソールを開きます。
1. 任意または複数のカテゴリのチェックボックスをオンにし、コンソールに表示されるJavaScript エラーを確認します。
1. 「**保存**」ボタンをクリックします。
1. 条件に戻り、選択したカテゴリが保存されているかどうかを確認します。

<u>期待される結果</u>:

選択したカテゴリは、セグメント条件の表示または編集時に保存され、選択されます。

<u>実際の結果</u>:

選択したカテゴリが見つからないため、正しく保存されませんでした。 コンソールで次のエラーが発生します。

```text
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
