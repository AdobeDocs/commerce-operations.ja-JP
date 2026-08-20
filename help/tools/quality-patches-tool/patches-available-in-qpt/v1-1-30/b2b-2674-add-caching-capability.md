---
title: B2B-2674:customAttributeMetadata GraphQL クエリにキャッシュ機能を追加
description: B2B-2674 パッチを適用して、customAttributeMetadata GraphQL クエリにキャッシュ機能を追加します。
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: b49633f3-b144-405f-a21d-726e222a7bfe
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# B2B-2674: `customAttributeMetadata` GraphQL クエリにキャッシュ機能を追加

B2B-2674 パッチでは、`customAttributeMetadata`個のGraphQL クエリにキャッシュ機能が追加されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30がインストールされている場合に利用できます。 パッチ IDはB2B-2674です。 この問題は、Adobe Commerce 2.4.7-beta1で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`customAttributeMetadata` GraphQL クエリはキャッシュできません。

<u>前提条件</u>:

* サーバーがAdobe Commerce バックエンドに[!DNL Varnish] プロキシを指定しています。
* 設定設定`system/full_page_cache/caching_application`は&#x200B;*2* （[!DNL Varnish]）に設定されているか、Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** >に移動して[!DNL Varnish]に設定します。

パッチが適用されたら、次の手順を実行して、キャッシュ機能が使用可能になったことを確認します。

1. 任意のフィールドを使用して、上記のGraphQL クエリに`GET` リクエストを送信します。
1. 変更を加えずにリクエストを再送信します。はるかに速くなります。 リクエストはバックエンドに送信されませんが、キャッシュヒットとして[!DNL Varnish]によって完全に処理されます。
1. さらにプルーフが必要な場合は、[VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239)に存在する`X-Magento-Debug` ヘッダーのアンセットをコメントし、[!DNL Varnish]を再起動して、上記の手順を再度実行します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
