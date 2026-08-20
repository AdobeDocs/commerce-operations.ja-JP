---
title: MDVA-41350：管理者がアクセス以外の場所に製品を追加する場合の例外
description: MDVA-41350 パッチでは、管理者ユーザーがSKUで製品を追加する際に、アクセスが制限されたアクセス通知ではなく例外エラーがスローされる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.11がインストールされている場合に利用できます。 パッチ IDはMDVA-41350です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Admin Workspace, Products
role: Admin
exl-id: 4dc5ee5c-bd93-42e1-9c63-93ffb8e5f21c
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-41350：管理者がアクセス以外の場所に製品を追加する場合の例外

MDVA-41350 パッチでは、管理者ユーザーがSKUで製品を追加する際に、アクセスが制限されたアクセス通知ではなく例外エラーがスローされる問題を修正します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.11がインストールされている場合に使用できます。 パッチ IDはMDVA-41350です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.3.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

アクセスが制限された管理者ユーザーが、SKUによって製品をアクセス以外の順序で追加すると、制限されたアクセスをユーザーに通知するメッセージではなく、例外が発生します。

<u>複製する手順</u>:

1. 特定のweb サイトのみにアクセスできるユーザーとして管理者にログインします。
1. **Sales** > **Orders**&#x200B;に移動し、**Create New Order**&#x200B;をクリックします。
1. 顧客とストアビューを選択します。
1. 「**SKU**&#x200B;で製品を追加」をクリックします。
1. どのweb サイトにも割り当てられていない、またはアクセス権のあるweb サイトに割り当てられていないSKUを検索します。
1. 「**注文に追加**」をクリックします。

<u>期待される結果</u>:

適切なエラーメッセージが表示されます。

<u>実際の結果</u>:

例外が発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
