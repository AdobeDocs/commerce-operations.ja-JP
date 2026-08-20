---
title: '[!DNL ACSD-47280]：共有カタログを無効にすると、間違った商品検索結果が表示される'
description: 共有カタログ機能が無効になっている場合に、正しい検索結果を表示するように修正するには、 [!DNL ACSD-47280]  パッチを適用します。
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# [!DNL ACSD-47280]：共有カタログを無効にすると、間違った商品検索結果が表示される

[!DNL ACSD-47280] パッチは、[!DNL shared catalog]機能が無効になっている場合の正しい検索結果の表示を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.22がインストールされている場合に利用できます。 [!DNL patch ID]は[!DNL ACSD-47280]です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 検索キーワードとして[!DNL patch ID]を使用して、パッチを検索します。

## イシュー

[!DNL shared catalog]を無効にすると、間違った商品検索結果が表示されます。

<u>前提条件</u>:

* [!DNL B2B]個のモジュールがインストールされました

<u>複製する手順</u>:

1. 2つ目のweb サイトの構築。
1. 2番目のweb サイトに製品を割り当てます。
1. [!DNL GraphQL]を使用して&#x200B;**秒のweb サイト**&#x200B;で製品を確認します：

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. 既定の[!DNL scope]で&#x200B;**[!UICONTROL Shared Catalog]**&#x200B;を有効にします。
1. [!DNL GraphQL] リクエストで、2番目のWeb サイトの製品が表示されなくなりました。これは正しい結果です。
1. 2番目のWeb サイトの[!DNL scope]に移動し、**[!UICONTROL Company]**&#x200B;を無効にします。

<u>期待される結果</u>:

[!DNL GraphQL] リクエストには、引き続き2番目のweb サイトの製品が表示されます。

<u>実際の結果</u>:

[!DNL GraphQL] リクエストには、2番目のweb サイトの製品が表示されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
