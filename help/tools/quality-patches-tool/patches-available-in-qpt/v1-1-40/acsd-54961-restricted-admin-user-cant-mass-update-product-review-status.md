---
title: ACSD-54961：制限付き管理者ユーザーが[!UICONTROL Product Review status]を一括更新できません
description: ACSD-54961 パッチを適用して、制限付き管理者ユーザーが製品レビューステータスを一括更新できないAdobe Commerceの問題を修正します。
feature: Products
role: Admin, Developer
exl-id: d303365c-d7c7-4aca-9f33-75d67bcbe573
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '381'
ht-degree: 0%
---
# ACSD-54961：制限付き管理者ユーザーが[!UICONTROL Product Review status]を一括更新できません

ACSD-54961 パッチは、制限付き管理者ユーザーが[!UICONTROL Product Review status]を一括更新できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.40がインストールされている場合に利用できます。 パッチ IDはACSD-54961です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

制限付き管理者ユーザーは[!UICONTROL Product Review status]を一括更新できません。

<u>複製する手順</u>:

1. web サイト、ストア、ストアビューを追加作成する。
1. 2番目のストアに商品を追加し、レビューを追加します。
1. 2番目のストアのみにアクセスできる制限付き管理者ユーザーを作成します。
1. 制限付き管理者ユーザーとしてログインし、**[!UICONTROL  Marketings]** > **[!UICONTROL Reviews]** > **[!UICONTROL Mass Update]**&#x200B;に移動し、**ステータス**&#x200B;を&#x200B;*承認済み*&#x200B;または&#x200B;*保留中*&#x200B;に設定します。

<u>期待される結果</u>:

制限付き管理者ユーザーは、**[!UICONTROL Mass Update]** アクションを使用してレビューを更新できます。

<u>実際の結果</u>:

**[!UICONTROL Mass Update]** アクションを使用してレビューを更新中にエラーが発生しました。<br>
`var/log/exception.log`には同様のエラーが含まれています：

```text
report.CRITICAL: TypeError: array_intersect(): Argument #1 ($array) must be of type array, null given in app/code/Magento/AdminGws/Model/Models.php:439
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
