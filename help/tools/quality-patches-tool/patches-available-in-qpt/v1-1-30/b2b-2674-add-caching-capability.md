---
title: 'B2B-2674: customAttributeMetadata GraphQL クエリにキャッシュ機能を追加します'
description: B2B-2674 パッチを適用して、customAttributeMetadata GraphQL クエリにキャッシュ機能を追加します。
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: b49633f3-b144-405f-a21d-726e222a7bfe
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# B2B-2674:`customAttributeMetadata` GraphQL クエリにキャッシュ機能を追加しました

B2B-2674 パッチでは、`customAttributeMetadata` のGraphQL クエリにキャッシュ機能が追加されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 がインストールされている場合に使用できます。 パッチ ID は B2B-2674 です。 この問題はAdobe Commerce 2.4.7-beta1 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

GraphQL クエリ `customAttributeMetadata` キャッシュできません。

<u> 前提条件 </u>:

* サーバーは、Adobe Commerce バックエンドへ [!DNL Varnish] プロキシを指しています。
* 構成設定 `system/full_page_cache/caching_application` が *2* （[!DNL Varnish]）に設定されているか、Adobe Commerce管理/**[!UICONTROL Stores]**/**[!UICONTROL System]**/**[!UICONTROL Full Page Cache]**/**[!UICONTROL Caching Application]** に移動して、[!DNL Varnish] に設定してください。

パッチを適用した後、次の手順を実行して、キャッシュ機能が使用可能になっていることを確認します。

1. 任意 `GET` フィールドを使用して、上記のGraphQL クエリにリクエストを送信します。
1. 変更を加えずにリクエストを再送信します。ずっと速くなっていることがわかります。 リクエストはバックエンドに送信されませんが、キャッシュヒットとして [!DNL Varnish] で完全に処理されます。
1. さらにプルーフが必要な場合は、[VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239) に存在する `X-Magento-Debug` ヘッダーの未設定をコメントアウトし、[!DNL Varnish] を再起動して、上記の手順を再実行します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
