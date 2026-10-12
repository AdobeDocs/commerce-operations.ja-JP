---
title: ACSD-60584：あるWeb サイト用に作成されたアクセストークンは、他のWeb サイトの情報にアクセスできます
description: ACSD-60584 パッチを適用して、あるweb サイトでユーザー用に作成されたアクセストークンが他のweb サイトの顧客情報にアクセスまたは変更できる問題を修正します。
feature: Customers, GraphQL
role: Admin, Developer
exl-id: ea30ba92-4b7b-44f9-a1b1-97946061d9e6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%
---
# ACSD-60584：あるWeb サイト用に作成されたアクセストークンは、他のWeb サイトの情報にアクセスできます

ACSD-60584 パッチでは、あるweb サイトでユーザー用に作成されたアクセストークンが、他のweb サイトの顧客情報にアクセスまたは変更できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.53がインストールされている場合に利用できます。 パッチ IDはACSD-60584です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ひとつのweb サイトでユーザー用に作成されたAPI トークンを使用すると、顧客情報にアクセスし、カートを作成し、ほかのweb サイトでは商品をカートに追加できます。

<u>複製する手順</u>:

1. **[!DNL Share Customer Accounts configuration]**&#x200B;が&#x200B;**[!UICONTROL Per Website]**&#x200B;に設定されていることを確認します。
1. 追加の&#x200B;*web サイト*、*ストア*、*ストアビュー*&#x200B;を作成します。
1. 前の手順で作成したメインの&#x200B;*web サイト*&#x200B;と&#x200B;*web サイト*&#x200B;で、同じ電子メールを持つ2人の顧客を作成します。
1. メイン web サイトの[!DNL GraphQL]を介して顧客トークンを生成します。
1. 生成されたトークンを使用して、ヘッダーに2番目のweb サイトを含む顧客&#x200B;**[!DNL GraphQL]** クエリを送信し、顧客情報を取得します。
1. 返された結果を確認します。

<u>期待される結果</u>:

メイン *web サイト*&#x200B;のトークンが[!DNL GraphQL]のクエリで使用されているため、メイン *web サイト*&#x200B;の顧客情報が返されます。

<u>実際の結果</u>:

2番目のweb サイトの顧客情報が返されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
