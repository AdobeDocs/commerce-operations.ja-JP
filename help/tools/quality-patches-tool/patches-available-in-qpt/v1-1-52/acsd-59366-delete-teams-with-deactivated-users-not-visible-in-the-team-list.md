---
title: ACSD-59366：非アクティブ化されたユーザーがチームリストに表示されていないチームを削除する
description: チーム リストに表示されない非アクティブ化されたユーザーを含むチームを削除しようとしたときにエラーが発生するAdobe Commerceの問題を修正するには、ACSD-59366 パッチを適用します。
feature: GraphQL, Companies
role: Admin, Developer
exl-id: 406d2242-38f9-4852-b311-0ee57c4a7c26
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-59366：非アクティブ化されたユーザーがチームリストに表示されていないチームを削除する

ACSD-59366 パッチは、チームリストに表示されない非アクティブ化されたユーザーを含むチームを削除しようとしたときにエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52がインストールされている場合に利用できます。 パッチ IDはACSD-59366です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

チーム リストに表示されない非アクティブ化されたユーザーを含むチームを削除すると、エラーが発生します。

<u>前提条件</u>:

Adobe Commerce B2B モジュールがインストールされ、企業が有効になります。

<u>複製する手順</u>:

1. 会社のユーザーを作成してログインします。
1. 会社体制の下に新しいチームを作成します。
1. 新しいチームの下に新しいユーザーを作成します。
1. 新しいユーザーを編集して非アクティブ化します。
1. チームを選択して削除します。

<u>期待される結果</u>:

チームには、1人以上の非アクティブユーザーがいます。 チームを削除すると、これらのユーザーの割り当てが解除されます。 非アクティブなユーザーは、[!UICONTROL Company Users] セクションで見つけることができます。

<u>実際の結果</u>:

非アクティブ化されたユーザーを持つチームを削除しようとすると、エラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
