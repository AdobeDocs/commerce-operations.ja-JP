---
title: ACSD-60804：削除された会社に関連付けられている顧客を編集すると、エラーが発生する
description: 削除された会社に関連付けられたお客様を編集すると、null*で*メンバー関数getSuperUserId （）への呼び出しが発生するAdobe Commerceの問題を修正するには、ACSD-60804 パッチを適用します。
feature: Companies, Customers, B2B
role: Admin, Developer
exl-id: 09241160-f5ed-41f8-8bb6-2bb8ed5cccd5
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-60804：削除された会社に関連付けられている顧客を編集すると、エラーが発生する

ACSD-60804 パッチは、削除された会社に関連付けられている顧客を編集すると、null *でメンバー関数getSuperUserId （）への呼び出しがエラーになる問題を修正します。*&#x200B;このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53がインストールされている場合に利用できます。 パッチ IDはACSD-60804です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

削除された会社に関連付けられている顧客を編集すると、null *のメンバー関数getSuperUserId （）への呼び出しがエラーになります。*

<u>前提条件：</u>:

Adobe Commerce B2B モジュールをインストールして有効にする。

<u>複製する手順</u>:

1. **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**&#x200B;に移動します。
1. **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**&#x200B;に移動します。
1. インスタンスの`mysql`にログインします。
1. `entity_id` = *1*&#x200B;の会社を削除します。
1. **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;に移動します。
1. 会社の作成時に自動的に作成された顧客を編集します。

<u>期待される結果</u>:

例外エラーが発生することなく、お客様が編集されます。

<u>実際の結果</u>:

エラーが発生します。*会社が顧客に関連付けられていない場合、null*&#x200B;のメンバー関数getSuperUserId （）への呼び出し。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
