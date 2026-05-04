---
title: ACSD-63325：構文エラー：空の [!DNL GraphQL]  リクエストの送信時に予期しない<EOF&gt；エラーが発生しました
description: 空の [!DNL GraphQL]  リクエストを送信する際に構文エラーが発生するAdobe Commerceの問題を修正するには、ACSD-63325 パッチを適用します。
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# ACSD-63325：空の[!DNL GraphQL] リクエストを送信する際に「構文エラー：予期しない&lt; EOF >」エラーが発生する

ACSD-63325 パッチは、「構文エラー：予期しない&lt; EOF >」エラーと、空の[!DNL GraphQL] リクエストの送信時に200以外の応答コードが返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58がインストールされている場合に利用できます。 パッチ IDはACSD-63325です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

空の[!DNL GraphQL] リクエストを送信すると、200の応答コードではなくHTTP内部サーバーエラーが発生します。

<u>複製する手順</u>:

1. 空のGraphQL リクエストを送信する

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>期待される結果</u>:

リクエストの応答コードは200です。

```shell
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>実際の結果</u>:

次の図に示すように、500の内部サーバーエラーが発生します。

```text
HTTP/1.1 500 Internal Server Error
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* Cloud Infrastructure上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce Cloud Infrastructure ガイドのパッチを適用](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches)」。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
