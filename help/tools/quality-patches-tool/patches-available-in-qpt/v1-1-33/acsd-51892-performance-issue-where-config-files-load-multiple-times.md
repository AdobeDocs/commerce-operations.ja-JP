---
title: ACSD-51892：設定ファイルが複数回読み込まれるパフォーマンスの問題
description: ACSD-51892 パッチを適用して、デプロイメント中に設定ファイルが複数回読み込まれるAdobe Commerceのパフォーマンスの問題を修正します。
feature: Observability
role: Admin
exl-id: ef3d3b85-b6a0-4037-95c0-e84125fa9088
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51892：設定ファイルが複数回読み込まれるパフォーマンスの問題

ACSD-51892 パッチは、1回のリクエスト内でデプロイメント設定値にアクセスするたびに`app/etc/env.php`および`app/etc/config.php` ファイルを読み込むことで発生するパフォーマンスの問題を修正します。 ファイルを読み込み過ぎると、システムに負担がかかり、全体的なパフォーマンスが低下します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51892です。 この問題は、Adobe Commerce 2.4.6-p2で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

設定ファイルが複数回ロードされるパフォーマンスの問題があります。

<u>複製する手順</u>:

1. デプロイメントを実行するか、Adobe Commerce 2.4.6以降にアップグレードします。
1. デプロイメントの実行中に`app/etc/env.php`および`app/etc/config.php` ファイルへのアクセスについて、ファイルシステムのログを確認します。

<u>期待される結果</u>:

通常の時間枠内でデプロイが成功します。

<u>実際の結果</u>:

* サーバーは、入力したコマンドに応答するのに苦慮しています。 この結果、Web サイトへのアクセス時に&#x200B;*エラー503の最初のバイトのタイムアウト*&#x200B;が発生します。
* `app/etc/env.php`および`app/etc/config.php`個のファイルにアクセスできるログファイルには、複数のエントリがあります。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
