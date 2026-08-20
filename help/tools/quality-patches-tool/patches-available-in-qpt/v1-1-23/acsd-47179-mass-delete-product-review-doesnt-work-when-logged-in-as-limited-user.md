---
title: ACSD-47179：制限付きユーザーロールとしてログインすると、製品レビューの一括削除が機能しない
description: ACSD-47179 パッチを適用して、制限付きユーザーロールとしてログインした場合に製品レビューの一括削除が機能しないAdobe Commerceの問題を修正します。
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
exl-id: 7131ee47-fadc-4e93-b8b2-5b2e0521ad97
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-47179：制限付きユーザーロールとしてログインすると、製品レビューの一括削除が機能しない

ACSD-47179 パッチは、制限付きユーザーの役割としてログインした場合に製品レビューの一括削除が機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.23がインストールされている場合に利用できます。 パッチ IDはACSD-47179です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

製品レビューの一括削除は、限られたユーザーの役割としてログインすると機能しません。

<u>複製する手順</u>:

1. セカンダリ web サイトの構築：
1. 次のセクションに対する完全な権限を持つセカンダリ web サイトに制限されたユーザーロールを作成します。
   * カタログ
   * お客様
   * マーケター
1. 商品を作成し、セカンダリ web サイトに割り当てる。
1. フロントエンドから2つのレビューを製品に追加します。
1. 作成したばかりの制限付き管理者ユーザーを使用して、[!DNL Commerce]管理者にログインします。
1. 保留中のレビューを一括削除してみてください。

<u>期待される結果</u>:

十分な権限を持つ管理者は、保留中のレビューを一括削除できます。

<u>実際の結果</u>:

次のエラーが表示されます：_問題が発生しました。 support_ report.log_で例外が生成されました

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
