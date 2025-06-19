---
title: ACSD-60811：注文ステータスをカスタム値に更新する際の制限を修正しました
description: ACSD-60811 パッチを適用すると、現在のステータスが「処理中」または「不正」の場合にのみ、カスタム値またはコメントを使用して注文ステータスを更新できるAdobe Commerceの問題を修正できます。
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-60811：注文ステータスをカスタム値に更新する際の制限を修正しました

ACSD-60811 パッチは、現在のステータスが「[!UICONTROL Processing]」または「[!UICONTROL Suspected Fraud]」の場合にのみ、カスタム値またはコメントで注文ステータスを更新できる問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 がインストールされている場合に使用できます。 パッチ ID は ACSD-60811 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7. 2.4.7-p1、2.4.7-p2、2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

注文ステータスをカスタム値またはコメントで更新できるのは、現在のステータスが *処理中* または *不正* の場合のみです。 新しいステータスを選択して送信しても、注文のステータスは変わりません。

<u> 再現手順 </u>:

1. **[!UICONTROL Stores]** / **[!UICONTROL Order Status]** に移動して、管理パネルにカスタム注文ステータスを作成します。
1. 「**[!UICONTROL Assign Status to State]**」をクリックして、カスタムステータスを注文状態に割り当てます。
1. 管理パネルの注文表示ページで注文ステータスを変更します。

<u> 期待される結果 </u>:

管理者ユーザーは、管理パネルで注文ステータスをカスタム注文ステータスに変更できる必要があります。

<u> 実際の結果 </u>:

新しい注文ステータスが選択されて送信された場合、注文ステータスは変わりません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
