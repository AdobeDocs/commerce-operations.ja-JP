---
title: 「ACSD-59366：チームリストに表示されていないディアクティベートされたユーザーのチームを削除する」
description: ACSD-59366 パッチを適用すると、チームリストに表示されない非アクティブ化されたユーザーを含むチームを削除しようとしたときにエラーが発生するAdobe Commerceの問題を修正できます。
feature: GraphQL, Companies
role: Admin, Developer
source-git-commit: 8037db7a89cd850385dc88750e881f68ae62172f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366：チームリストに表示されていないディアクティベートされたユーザーのチームを削除

ACSD-59366 パッチでは、チームリストに表示されていない非アクティブ化されたユーザーを含むチームを削除しようとしたときにエラーが発生する問題が修正されています。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 がインストールされている場合に使用できます。 パッチ ID は ACSD-59366 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

チームリストに表示されていないディアクティベートされたユーザーを含むチームを削除すると、エラーが発生します。

<u> 前提条件 </u>:

Adobe Commerce B2B モジュールがインストールされ、会社が有効になります。

<u> 再現手順 </u>:

1. 会社のユーザーを作成してログインします。
1. 会社構造で、新しいチームを作成します。
1. 新しいチームの下で、新しいユーザーを作成します。
1. 新しいユーザーを編集し、非アクティブにします。
1. チームを選択して削除します。

<u> 期待される結果 </u>:

チームに 1 人以上の非アクティブユーザーがあります。 チームを削除すると、これらのユーザーの割り当てが解除されます。 [!UICONTROL Company Users] のセクションで、非アクティブなユーザーを検索できます。

<u> 実際の結果 </u>:

ユーザーがアクティベート解除されたチームを削除しようとすると、エラーが発生します。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](/help/tools/quality-patches-tool/usage.md) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。


