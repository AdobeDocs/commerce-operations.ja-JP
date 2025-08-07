---
title: ACSD-66441：マルチストア設定で、レイヤーナビゲーションに間違った属性オプションが表示される
description: ACSD-66441 パッチを適用すると、マルチストアの設定でレイヤーナビゲーションに他のストアの属性が正しく表示されないAdobe Commerceの問題が修正されます。
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
source-git-commit: 5a8b30d1fac953ff5d921b7a7d3f12619b03bc81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# ACSD-66441：マルチストア設定で、レイヤーナビゲーションに間違った属性オプションが表示される

ACSD-66441 パッチは、マルチストア設定でレイヤードナビゲーションが他のストアの属性を誤って表示する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 がインストールされている場合に使用できます。 パッチ ID は ACSD-66441 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p5

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.7-p6

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ストアフロントのレイヤードナビゲーションには、他のストアの属性値が含まれます。これらの製品は、現在のストア表示では使用できません。

<u> 再現手順 </u>:

1. セカンダリ web サイト、ストア、ストア表示を作成します。
1. カスタム属性（size など）を使用して設定可能な製品を作成します。
1. 設定可能な製品をメインの web サイトとカテゴリに割り当てます。
1. すべてのデータのインデックスを再作成します。
1. ストアフロントで割り当てられたカテゴリに移動します。 すべてのサイズオプションは、レイヤーナビゲーションで正しく表示されます。
1. メイン Web サイトから 2 つのシンプルな製品の割り当てを解除して、セカンダリ Web サイトに割り当てるか、メイン Web サイトから削除します。
1. すべてのデータのインデックスを再作成します。
1. ストアフロントのカテゴリページに再度アクセスし、レイヤー化されたナビゲーションを確認します。

<u> 期待される結果 </u>:

レイヤーナビゲーションでは、現在のストアまたは web サイトに割り当てられている製品の属性オプションのみが表示されます。

<u> 実際の結果 </u>:

レイヤーナビゲーションは、他のストアや web サイトに割り当てられた製品の属性オプション（サイズ）を表示します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
