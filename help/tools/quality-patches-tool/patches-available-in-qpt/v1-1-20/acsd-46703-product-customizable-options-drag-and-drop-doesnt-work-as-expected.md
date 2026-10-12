---
title: ACSD-46703：製品カスタマイズのドラッグ&ドロップが機能しない
description: この記事では、製品のカスタマイズ可能なオプションのドラッグ&ドロップが期待どおりに機能しない問題の解決策を提供します。
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%
---
# ACSD-46703：製品カスタマイズのドラッグ&amp;ドロップが機能しない

ACSD-46703 パッチは、製品のカスタマイズ可能なオプション（ドラッグ&amp;ドロップ）が期待どおりに機能しない問題を修正します。 このパッチは、[品質パッチツール （QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20がインストールされている場合に使用できます。 パッチ IDはACSD-46703です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4 - 2.4.5

>[!NOTE]
>
>このパッチは、新しい[品質パッチツール ] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ユーザーは、カスタマイズ可能なオプションをあるページから別のページにドラッグ&amp;ドロップすることはできません。

<u>複製する手順</u>:

1. シンプルな商品の作成。
1. カスタマイズ可能なオプションをシンプルな商品に追加し、20以上のオプションを追加してページネーションを作成します。
1. カスタマイズ可能なオプション（ドラッグ&amp;ドロップ）を同じページ内で移動してみてください。
1. 次に、カスタマイズ可能なオプションを2 ページ目から1 ページ目に移動します。

<u>期待される結果</u>:

* カスタマイズ可能なオプションをあるページから別のページにドラッグ&amp;ドロップできます。
* 複数ページの場合でも、ドラッグ&amp;ドロップ機能を使用して値を並べ替えることができます。

<u>実際の結果</u>:

ドラッグ&amp;ドロップ機能を使用して、値を別のページに移動することはできません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：品質パッチツールガイドの「[品質パッチツール/使用状況](/help/tools/quality-patches-tool/usage.md)」。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
