---
title: ACP2E-3964:REST APIを介してリストされていないビデオを含む設定可能な子製品
description: ACP2E-3964 パッチを適用して、[!UICONTROL Media Gallery]のビデオを含む設定可能な製品の子製品がREST APIを介してリストされないAdobe Commerceの問題を修正します。
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
exl-id: 61c5b97c-79aa-4ee7-96b3-70924d2c85a0
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACP2E-3964:REST APIを介してリストされていないビデオを含む設定可能な子製品

ACP2E-3964 パッチは、**[!UICONTROL Media Gallery]**&#x200B;のビデオを含む設定可能な製品の子製品がREST APIを介してリストされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACP2E-3964です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Media Gallery]**&#x200B;内にビデオを含む設定可能な製品の子製品をREST API経由で一覧表示できないため、エラー応答が発生します。

<u>複製する手順</u>:

1. 新しい設定可能な製品を作成し、1つの子製品を追加します。
1. 子製品を編集し、**[!UICONTROL Images and Videos]**&#x200B;の下にビデオを追加します（例：[https://vimeo.com/1084537](https://vimeo.com/1084537)）。
1. 子製品を保存します。
1. 管理者ベアラートークンを使用して、REST API エンドポイント `rest/v1/configurable-products/%sku%/children`にGET リクエストを送信します。

<u>期待される結果</u>:

REST APIは、**[!UICONTROL Media Gallery]**&#x200B;のビデオ情報を含め、エラーなく子製品データを返す必要があります。

<u>実際の結果</u>:

REST APIが次のエラーを返します。

```text
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
