---
title: ACSD-62979:GraphQL ヘッダーのストア ID が正しくないと、致命的なメモリエラーが発生する
description: ACSD-62979 パッチを適用すると、Adobe Commerce ヘッダーで誤ったストア ID を使用すると致命的なメモリエラーが発生するGraphQLの問題を修正できます
feature: GraphQL
role: Admin, Developer
exl-id: 832baae1-34b4-4ca8-bfa9-221aa60da67e
source-git-commit: 187a0056971e6bec324b5cc9d374375bbfb84dd8
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-62979:GraphQL ヘッダーのストア ID が正しくないと、致命的なメモリエラーが発生する

ACSD-62979 パッチでは、GraphQL ヘッダーで誤ったストア ID を使用すると致命的なメモリエラーが発生する問題を修正しています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-62979 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6、2.4.6-p7、2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQL ヘッダーで誤ったストア ID を使用すると、致命的なメモリエラーが発生する問題を修正しました。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]**/**[!UICONTROL Configuration]**/**[!UICONTROL General]**/**[!UICONTROL Web]**/**[!UICONTROL Url Options]**）に移動します。 **[!UICONTROL Add Store Code to Urls]** を有効にします。
1. 次のGraphQL クエリを実行します。ストアヘッダーの値が正しくありません。

```graphql
{
  categoryList(filters: { ids: { eq: "2" } }) {
    uid
    level
    name
    url_path
    image
    children {
      uid
      level
      name
      url_path
      image
      children {
        uid
        level
        name
        url_path
        image
        children {
          uid
          level
          name
          url_path
          image
        }
      }
    }
  }
}
```

<u> 期待される結果 </u>:

エラーメッセージ：「リクエストされたストアが見つかりませんでした。 ストアを確認して、もう一度試してください」

<u> 実際の結果 </u>:

次のような致命的エラー：

```Allowed memory size of 792723456 bytes exhausted```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
