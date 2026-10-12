---
title: ACSD-51149：有効な[!UICONTROL Catalog Permissions]でスケジュールされた[!UICONTROL ImportExport]がインデクサーを無効にします
description: 有効な[!UICONTROL Catalog Permissions]を含むスケジュールされた[!UICONTROL ImportExport]でインデクサーが無効になるAdobe Commerce パフォーマンスの問題を修正するには、ACSD-51149 パッチを適用します。
feature: Cache, Data Import/Export
role: Admin
exl-id: eafc69ab-ec81-4192-85f8-a235f0a131a9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%
---
# ACSD-51149：有効な[!UICONTROL Catalog Permissions]でスケジュールされた[!UICONTROL ImportExport]がインデクサーを無効にします

ACSD-51149 パッチは、有効な[!UICONTROL Catalog Permissions]を含むスケジュールされた[!UICONTROL ImportExport]がインデクサーを無効にする問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.35がインストールされている場合に利用できます。 パッチ IDはACSD-51149です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

有効な[!UICONTROL Catalog Permissions]を含むスケジュール済み[!UICONTROL ImportExport]は、インデクサーを無効にします。

<u>複製する手順</u>:

1. *[!UICONTROL Catalog Permissions]*&#x200B;を有効にします。
1. すべてのインデクサーを&#x200B;*[!UICONTROL Update by Schedule]*&#x200B;に設定します。
1. シンプルな商品の作成。
1. **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**&#x200B;経由でこの製品をエクスポートします。
1. 書き出したCSVをダウンロードし、`<AC root folder>/var/import`に入力します。
1. ダウンロードしたCSVを使用して、スケジュールされた製品インポートを作成します。
1. 完全なインデックス再作成を実行します。
1. インデクサーのステータスを確認します。 すべてのインデクサーは&#x200B;*[!UICONTROL Ready]* ステータスである必要があります。
1. 作成したスケジュール済み読み込みをグリッドから実行します。
1. インデクサーのステータスを確認します。

<u>期待される結果</u>:

すべてのインデックスは&#x200B;*[!UICONTROL Ready]* ステータスにあります。

<u>実際の結果</u>:

一部のインデックスは&#x200B;*[!UICONTROL Reindex Required]* ステータスです。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
