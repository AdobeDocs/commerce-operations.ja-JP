---
title: ACSD-66441：複数ストア設定でレイヤーナビゲーションに誤った属性オプションが表示される
description: ACSD-66441 パッチを適用して、レイヤーナビゲーションがマルチストア設定で他のストアの属性を誤って表示するAdobe Commerceの問題を修正します。
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
exl-id: d61c6b9e-bbcf-4285-b97b-b1fee67048e5
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
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
source-wordcount: '411'
ht-degree: 0%
---
# ACSD-66441：複数ストア設定でレイヤーナビゲーションに誤った属性オプションが表示される

ACSD-66441 パッチでは、マルチストア設定で他のストアの属性がレイヤーナビゲーションで正しく表示されない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67がインストールされている場合に利用できます。 パッチ IDはACSD-66441です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ストアフロントの階層型ナビゲーションには、現在のストアビューでこれらの製品が使用できない場合でも、他のストアの属性値が含まれます。

<u>複製する手順</u>:

1. ふたつ目のweb サイト、実店舗ビューの作成。
1. カスタム属性（サイズなど）を使用して、設定可能な製品を作成します。
1. メイン web サイトとカテゴリに設定可能な製品を割り当てます。
1. すべてのデータのインデックスを再作成します。
1. ストアフロントで割り当てられたカテゴリに移動します。 レイヤーナビゲーションでは、すべてのサイズオプションが正しく表示されます。
1. メイン web サイトから2つのシンプルな製品の割り当てを解除して、セカンダリ web サイトに割り当てるか、メイン web サイトから削除します。
1. すべてのデータのインデックスを再作成します。
1. ストアフロントのカテゴリーページに戻り、レイヤーナビゲーションを確認します。

<u>期待される結果</u>:

レイヤーナビゲーションには、現在のストアまたはweb サイトに割り当てられた製品の属性オプションのみが表示されます。

<u>実際の結果</u>:

階層型ナビゲーションでは、他の店舗やweb サイトに割り当てられた商品の属性オプション（サイズ）が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
