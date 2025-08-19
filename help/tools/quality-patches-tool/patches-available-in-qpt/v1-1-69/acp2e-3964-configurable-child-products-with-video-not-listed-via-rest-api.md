---
title: ACP2E-3964:REST API 経由でリストされないビデオを含む、設定可能な子製品
description: ACP2E-3964 パッチを適用すると、[!UICONTROL Media Gallery] ージ内のビデオを含む設定可能な商品の子商品が、REST API で一覧表示されないAdobe Commerceの問題が修正されます。
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f48ced28035c65db561f4700113652574d302ec9
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACP2E-3964:REST API 経由でリストされないビデオを含む、設定可能な子製品

ACP2E-3964 パッチでは、**[!UICONTROL Media Gallery]** ージ内のビデオを含む設定可能な製品の子製品が、REST API で一覧表示されない問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 がインストールされている場合に使用できます。 パッチ ID は ACP2E-3964 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Media Gallery]** ージ内のビデオを含む設定可能な製品の子製品は、REST API 経由でリストできず、エラー応答が発生します。

<u> 再現手順 </u>:

1. 新しい設定可能な製品を作成し、1 つの子製品を追加します。
1. 子製品を編集し、**[!UICONTROL Images and Videos]** の下にビデオを追加します（例：[https://vimeo.com/1084537](https://vimeo.com/1084537)）。
1. 子製品を保存します。
1. REST API エンドポイントにGET リクエストを送信します：管理者ベアラートークンを使用して `rest/v1/configurable-products/%sku%/children`。

<u> 期待される結果 </u>:

REST API は、**[!UICONTROL Media Gallery]** ージ内のビデオ情報を含め、エラーのない子製品データを返す必要があります。

<u> 実際の結果 </u>:

REST API がエラーを返します。

```
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
