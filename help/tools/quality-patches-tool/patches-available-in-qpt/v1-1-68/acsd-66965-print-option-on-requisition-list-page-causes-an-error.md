---
title: 'ACSD-66965: [!UICONTROL Requisition List] ページの[!UICONTROL Print] オプションでエラーが発生する'
description: ACSD-66965 パッチを適用して、[!UICONTROL Requisition List] ページの[!UICONTROL Print] オプションでエラーが発生するAdobe Commerceの問題を修正します。
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: ccd0920a-074c-4851-a45a-09c43b04fe64
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '338'
ht-degree: 0%
---
# ACSD-66965: **[!UICONTROL Requisition List]** ページの&#x200B;**[!UICONTROL Print]** オプションでエラーが発生する

ACSD-66965 パッチは、**[!UICONTROL Requisition List]** ページの&#x200B;**[!UICONTROL Print]** オプションでエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-66965です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Requisition List]** ページの&#x200B;**[!UICONTROL Print]** オプションは、`Grid.php`のnull オブジェクト参照によりエラーが発生します。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**&#x200B;に移動します。
1. **[!UICONTROL Enable Company]**、**[!UICONTROL Enable Shared Catalog]**、**[!UICONTROL Enable Requisition List]**&#x200B;を`Yes`に設定します。
1. シンプルな2つの商品を作成。
1. ストアフロントにログインし、**[!UICONTROL My Account]** ページを開きます。
1. 購買リストを作成。
1. 両方の製品を購買リストに割り当てます。
1. 購買リストにアクセスし、製品をリストアップします。
1. **[!UICONTROL Print]**&#x200B;をクリックします。

<u>期待される結果</u>:

**[!UICONTROL Requisition List]** ページの&#x200B;**[!UICONTROL Print]** オプションに、エラーのない印刷プレビューが表示されます。

<u>実際の結果</u>:

次のエラーメッセージが表示されます。*アプリケーションの実行中にエラーが発生しました。 詳細については、例外ログを参照してください。*

```text
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
