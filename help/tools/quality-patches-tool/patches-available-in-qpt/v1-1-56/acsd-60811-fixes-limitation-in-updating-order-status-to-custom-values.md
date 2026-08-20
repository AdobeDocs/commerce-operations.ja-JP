---
title: ACSD-60811：注文ステータスをカスタム値に更新する際の制限を修正
description: 現在のステータスが「処理中」または「不正」の場合にのみ、カスタム値またはコメントで注文ステータスを更新できるAdobe Commerceの問題を修正するには、ACSD-60811 パッチを適用します。
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 6d5391b3-7014-4d0a-b4ab-799f0733bbca
type: Troubleshooting
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-60811：注文ステータスをカスタム値に更新する際の制限を修正

ACSD-60811 パッチは、現在のステータスが&#39;[!UICONTROL Processing]&#39;または&#39;[!UICONTROL Suspected Fraud]&#39;の場合にのみ、カスタム値またはコメントで注文ステータスを更新できる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56がインストールされている場合に利用できます。 パッチ IDはACSD-60811です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7. 2.4.7-p1、2.4.7-p2、2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

カスタム値またはコメントを使用して注文ステータスを更新できるのは、現在のステータスが&#x200B;*処理中*&#x200B;または&#x200B;*不正行為*&#x200B;の場合のみです。 新しいステータスを選択して送信しても、注文ステータスは変更されません。

<u>複製する手順</u>:

1. **[!UICONTROL Stores]** > **[!UICONTROL Order Status]**&#x200B;に移動して、管理パネルでカスタム注文ステータスを作成します。
1. 「**[!UICONTROL Assign Status to State]**」をクリックして、カスタムステータスを注文状態に割り当てます。
1. 管理パネルの注文表示ページから注文ステータスを変更します。

<u>期待される結果</u>:

管理者ユーザーは、管理パネルで注文ステータスをカスタム注文ステータスに変更できます。

<u>実際の結果</u>:

新しい注文ステータスを選択して送信しても、注文ステータスは同じままになります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
