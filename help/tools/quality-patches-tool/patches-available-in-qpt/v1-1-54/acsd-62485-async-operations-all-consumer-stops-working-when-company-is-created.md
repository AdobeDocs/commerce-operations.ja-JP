---
title: 'ACSD-62485: ''async.operations.all'' コンシューマーが会社の作成時に動作しなくなる'
description: ACSD-62485 パッチを適用して、B2B企業が作成されたときに「async.operations.all」コンシューマーが機能しなくなるAdobe Commerceの問題を修正します。
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-62485: `async.operations.all` コンシューマーは、会社が作成されたときに機能しなくなります

ACSD-62485 パッチは、B2B企業が作成されたときに`async.operations.all` コンシューマーが機能しなくなる問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54がインストールされている場合に利用できます。 パッチ IDはACSD-62485です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p7

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.4 - 2.4.6-p7、2.4.7 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

コンシューマーの実行中にB2B企業が非同期で作成された場合、`async.operations.all` コンシューマーはメッセージの処理を停止します。

<u>前提条件</u>:

B2B モジュールがインストールされ、有効になっている。

<u>複製する手順</u>:

1. 2つの顧客を作成する。
1. REST一括リクエストを送信して2つの会社を作成し、作成した顧客を会社管理者として割り当てます。
1. 次のコマンドを使用してコンシューマーを起動します。

   `bin/magento queue:consumer:start async.operations.all --max-messages=20000`

<u>期待される結果</u>:

消費者は2万件のメッセージを処理し、正常に終了しました。

<u>実際の結果</u>:

消費者は、実行時にすぐに作業を停止します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
