---
title: 'ACSD-47497: ストア / 構成/ サービス [!UICONTROL OAuth]のACLがありません'
description: ACSD-47497 パッチを適用して、特定のロールに対して権限が設定されていて、コンフィギュレーションセクションへのアクセスを定義できない場合のAdobe Commerceの問題を修正します。
feature: Configuration, Identity Management, Services
role: Admin
exl-id: 4dbbd7df-f34b-4db8-a207-3de40fb39c6f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 23bc8570-95c6-5ef5-a563-2e4a4e6b4853
    internal-label: Identity Management
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%
---
# ACSD-47497: ストア / 構成/ サービス [!UICONTROL OAuth]のACLがありません

ACSD-47497 パッチは、Adobe Commerce Adminの&#x200B;**[!UICONTROL Configuration]** セクションに「**[!UICONTROL Services]**」タブが表示されない問題を解決します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.23がインストールされている場合に利用できます。 パッチ IDはACSD-47497です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました
* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**
* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

特定の役割に対して権限が設定されている場合、**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;へのアクセスを定義することはできません。

<u>複製する手順</u>:

1. Adobe Commerce Adminにログインします。 **[!UICONTROL System]** > **[!UICONTROL Permissions]** > **[!UICONTROL User Roles]**&#x200B;に移動します。
1. 管理者の役割で&#x200B;**[!UICONTROL Role Resources]**&#x200B;を選択し、**[!UICONTROL Roles Resources]**&#x200B;の&#x200B;**[!UICONTROL Resource Access]**&#x200B;を&#x200B;_カスタム_&#x200B;に設定してから、すべてのチェックボックスを選択します。 **[!UICONTROL Save Role]**&#x200B;を選択します。
1. **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]**&#x200B;を選択します。 **[!UICONTROL OAuth]**&#x200B;設定セクションは使用できません。

<u>期待される結果</u>:

**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;では、設定セクションが表示されます。

<u>実際の結果</u>:

**[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Services]** > **[!UICONTROL OAuth]**&#x200B;では、設定セクションがありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce: [ アップグレードとパッチ > パッチの適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) （開発者用ドキュメント）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
