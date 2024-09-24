---
title: 「ACSD-47179：制限付きユーザーの役割でログインした場合、製品レビューの一括削除が機能しない」
description: ACSD-47179 パッチを適用すると、制限付きユーザーロールとしてログインした際に商品レビューの一括削除が機能しないAdobe Commerceの問題を修正できます。
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-47179：制限付きユーザーの役割でログインした場合、製品レビューの一括削除が機能しない

ACSD-47179 パッチは、制限付きユーザーの役割でログインした場合、製品レビューの一括削除が機能しない問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23 がインストールされている場合に使用できます。 パッチ ID は ACSD-47179 です。 この問題はAdobe Commerce 2.4.6 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 ～ 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

制限付きユーザーの役割でログインした場合、製品レビューの一括削除が機能しない。

<u> 再現手順 </u>:

1. セカンダリ web サイトを作成します。
1. セカンダリ Web サイトに制限されたユーザーの役割を、次のセクションへの完全な権限で作成します。
   * カタログ
   * 顧客
   * Marketing
1. 製品を作成してセカンダリ web サイトに割り当てます。
1. フロントエンドから製品に 2 つのレビューを追加します。
1. 先ほど作成した制限付き管理者ユーザーを使用して [!DNL Commerce] Admin にログインします。
1. 保留中のレビューを一括削除してみてください。

<u> 期待される結果 </u>:

十分な権限を持つ管理者は、保留中のレビューを一括削除できます。

<u> 実際の結果 </u>:

次のエラーが発生します。_問題が発生しました。 support_report.log で生成された例外_

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Sourceオンプレミス：[[!DNL Quality Patches Tool] > Usage](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in the [!DNL Quality Patches Tool] guide.
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
