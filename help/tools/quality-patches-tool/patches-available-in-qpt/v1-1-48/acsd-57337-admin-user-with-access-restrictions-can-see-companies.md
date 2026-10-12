---
title: 'ACSD-57337: アクセス制限を持つ管理者ユーザーは、*Companies* グリッド内のすべての会社を表示できます'
description: 特定のweb サイトへのアクセス制限を持つ管理者ユーザーが*Companies*グリッドのすべてのweb サイトから会社を表示できるAdobe Commerceの問題を修正するには、ACSD-57337 パッチを適用します。
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '427'
ht-degree: 0%
---
# ACSD-57337: アクセス制限を持つ管理者ユーザーが、*会社* グリッド内のすべての会社を表示する可能性があります

ACSD-57337 パッチでは、特定のWeb サイトへのアクセス制限を持つ管理者ユーザーが、*会社* グリッドのすべてのWeb サイトの会社を表示できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-57337です。 この問題は、Adobe Commerce 2.5.0で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

特定のweb サイトへのアクセス制限を持つ管理者ユーザーは、*会社* グリッド内のすべてのweb サイトの会社を表示できます。

<u>複製する手順</u>:

1. 追加のweb サイト、ストア、ストアビューを作成する。
1. 複数の企業を作成し、さまざまなweb サイトに割り当て。
1. 管理者ユーザーの役割を作成し、作成したweb サイトに役割の範囲を設定します。
1. 管理者を作成し、作成した役割に割り当てます。
1. 新しい管理者でログインします。
1. **[!UICONTROL Customers]** > **[!UICONTROL Companies]**&#x200B;を開き、企業の一覧を確認します。

<u>期待される結果</u>:

追加のweb サイトに割り当てられた会社は、*会社*&#x200B;のグリッドに表示されます。

<u>実際の結果</u>:

すべての会社が&#x200B;*会社* グリッドに表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
