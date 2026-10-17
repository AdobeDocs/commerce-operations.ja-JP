---
title: 'ACSD-46213: カテゴリツリーリクエストが20 カテゴリに制限されました'
description: 'ACSD-46213 パッチでは、カテゴリツリーのリクエストが20 カテゴリに制限されている問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.19がインストールされている場合に利用できます。 パッチ IDはACSD-46213です。 '
feature: Categories
role: Admin
exl-id: 2cd4b102-db52-424f-9a7f-d775cb2b2c49
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%
---
# ACSD-46213: カテゴリツリーリクエストが20 カテゴリに制限されました

ACSD-46213 パッチでは、カテゴリツリーのリクエストが20 カテゴリに制限されている問題を修正します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.19がインストールされている場合に使用できます。 パッチ IDはACSD-46213です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。


## イシュー

カテゴリツリーのリクエストは20個のカテゴリに制限されています。

<u>複製する手順</u>:

1. ルートカテゴリの下にカテゴリを作成します。
1. 手順1で作成したルートカテゴリの下に24個のサブカテゴリを作成します。
1. 次のGraphQL リクエストを実行します。

   <pre>
    <code class="language-graphql">
    &lbrace;
      categoryList(filters: { parent_id: { in: ["3"] } }) &lbrace;
        name
        level
        path
        url_path
        children &lbrace;
          id
          level
          name
          path
          url_path
          url_key
          children &lbrace;
            uid
            level
            name
            path
            url_path
            url_key
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. 結果を確認します。

<u>期待される結果</u>:

24のカテゴリが表示されます。

<u>実際の結果</u>:

20のカテゴリのみが表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
