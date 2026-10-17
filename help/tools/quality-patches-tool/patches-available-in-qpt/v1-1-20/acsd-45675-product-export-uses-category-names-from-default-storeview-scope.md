---
title: ACSD-45675：製品の書き出しで、デフォルトのストアビュースコープからカテゴリ名が使用される
description: ACSD-45675 パッチでは、製品エクスポートでデフォルトのストアビュースコープからカテゴリ名が使用される問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.20がインストールされている場合に利用できます。 パッチ IDはACSD-45675です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%
---
# ACSD-45675：製品の書き出しで、デフォルトのストアビュースコープからカテゴリ名が使用される

ACSD-45675 パッチでは、製品エクスポートでデフォルトのストアビュースコープからカテゴリ名が使用される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20がインストールされている場合に利用できます。 パッチ IDはACSD-45675です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品エクスポートでは、デフォルトのストアビュースコープのカテゴリ名が使用されます。

<u>複製する手順</u>:

1. メインストア内にカスタムストアビュー&#x200B;**[!UICONTROL Thai]**&#x200B;を作成します。
1. **[!UICONTROL Thai]**&#x200B;をメイン web サイトの既定のストアビューに設定します。
1. **[!UICONTROL Default Category]**&#x200B;の下に次のカテゴリ構造を作成します。

   *[!UICONTROL Default category/Tea/Black]*

1. カテゴリ **[!UICONTROL Tea]**&#x200B;を選択し、**[!UICONTROL Scope]**&#x200B;を&#x200B;**[!UICONTROL Thai]**&#x200B;に変更します。
1. **[!UICONTROL Category Name]**&#x200B;を&#x200B;**[!UICONTROL ชาดำ]**&#x200B;に設定します。
1. シンプルな製品&#x200B;**[!UICONTROL SP001]**&#x200B;を作成し、カテゴリ **[!UICONTROL Black]**&#x200B;を割り当てます。
1. cronが実行されないことを確認します。
1. 製品の書き出しを行います。 SKUでフィルタリングして、**[!UICONTROL SP001]**&#x200B;を選択します。
1. 書き出されたCSVの&#x200B;**[!UICONTROL categories]**&#x200B;列を確認します。

<u>期待される結果</u>:

書き出し中にストアが選択されていないため、次のようなカテゴリーパスを取得する必要があります：*[!UICONTROL Default Category/Tea/Black]*。

<u>実際の結果</u>:

カテゴリーパスの言語が混在しています：*[!UICONTROL Default Category/ชาดำ/Black]*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：品質パッチツールガイドの[[!DNL Quality Patches Tools] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
