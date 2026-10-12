---
title: ACSD-51528:snake_caseの書式設定に関する異なる動作
description: snake_caseの書式設定で異なるビヘイビアーが発生するAdobe Commerceの問題を修正するには、ACSD-51528 パッチを適用します。
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%
---
# ACSD-51528:snake_caseの書式設定に関する異なる動作

ACSD-51528 パッチは、snake_caseの書式設定に対する異なる動作を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.32がインストールされている場合に利用できます。 パッチ IDはACSD-51528です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

snake_caseの書式設定に関する様々な動作。

<u>複製する手順</u>:

1. 様々なプロパティ名を使用して`\Magento\Framework\Api\DataObjectHelper::populateWithArray`関数をテストします。
1. *NewPName*&#x200B;のような名前のプロパティは、*new_pname*&#x200B;ではなく、*new_p_name*&#x200B;に変換する必要があります。
1. また、オブジェクトで&#x200B;*getNewPName*&#x200B;関数を使用する場合、*抽象モデル*&#x200B;が正しく&#x200B;*new_p_name*&#x200B;への呼び出しを変換するため、*null*&#x200B;が返され、両方の関数が互いに互換性がなくなります。

<u>期待される結果</u>

**[!UICONTROL populateWithArray]**&#x200B;関数は、オブジェクトのプロパティをsnake_caseに正しく変換し、**[!DNL AbstractModel's]** `Getters`および`Setters`と互換性を持たせます。

<u>実際の結果</u>

**[!UICONTROL populateWithArray]**&#x200B;関数を使用する場合、名前の行に2つ以上の大文字を含むオブジェクトプロパティは、最終的なデータ配列でsnake_case変換が正しくありません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
