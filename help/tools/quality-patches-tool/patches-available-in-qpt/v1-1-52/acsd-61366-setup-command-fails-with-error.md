---
title: 'ACSD-61366: ''bin/magento setup:static-content:deploy —jobs 4'' コマンドで、エラーが発生して複数のジョブエラーが発生する'
description: 「bin/magento setup:static-content:deploy —jobs 4」コマンドで複数のジョブエラーが発生し、DB接続のポートを指定しているにもかかわらず、*Portをhost parameter* エラー内で設定する必要があるAdobe Commerceの問題を修正するには、ACSD-61366 パッチを適用します。
feature: SCD
role: Admin, Developer
exl-id: d71a4833-a236-429b-a4e5-7d7d51c2caeb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d05f97c9-0a96-5792-92cf-f66ce7326e3a
    internal-label: SCD
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
source-wordcount: '403'
ht-degree: 0%
---
# ACSD-61366: `bin/magento setup:static-content:deploy --jobs 4` コマンドで、エラーを伴う複数のジョブの失敗が発生しました

ACSD-61366 パッチでは、DB接続のポートを指定しているにもかかわらず、*ポートで複数のジョブエラーが発生し、ホストパラメーター* エラー内で設定する必要がある`bin/magento setup:static-content:deploy --jobs 4` コマンドが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52がインストールされている場合に利用できます。 パッチ IDはACSD-61366です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p1

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`bin/magento setup:static-content:deploy --jobs 4` コマンドでは、DB接続用のポートを指定しているにもかかわらず、*ポートをホストパラメーター* エラー内で設定する必要がある、複数のジョブエラーが発生しました。

<u>複製する手順</u>:

1. `app/etc/env.php`のデータベース接続でポートを指定してください。
1. `bin/magento setup:static-content:deploy --jobs 4` コマンドを実行します。

<u>期待される結果</u>:

静的コンテンツのデプロイメントが正常に完了しました。

<u>実際の結果</u>:

コマンドが失敗し、*ポートをホストパラメーター*&#x200B;内で設定する必要があります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
