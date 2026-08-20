---
title: 'ACSD-49513: リモートストレージの同期が失敗する'
description: ACSD-49513 パッチを適用して、0 バイトのファイルが原因でリモートストレージの同期が失敗するAdobe Commerceの問題を修正します。
feature: Iaas, Storage
role: Admin
exl-id: 94dacfc4-d2d6-47b9-be0a-5bb55225af9a
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-49513: 0 バイトのファイルが原因でリモートストレージの同期が失敗する

ACSD-49513 パッチは、0 バイトのファイルが原因でリモートストレージの同期が失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-49513です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.4-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

0 バイトのファイルが原因で、リモート ストレージの同期が失敗します。

<u>複製する手順</u>:

1. AWS S3をリモートストレージとして設定します。
1. `[bin/magento remote-storage:sync]`を実行して、同期が最初に正しく機能することを確認します。
1. `[pub/media]`内に0 バイトのファイルを作成します。
1. もう一度`[bin/magento remote-storage:sync]`を実行します。

<u>期待される結果</u>:

AWS S3はS3 ダイレクトプッシュで0 バイトのファイルを受け入れるので、エラーはありません。

<u>実際の結果</u>:

次のエラーが発生します。

```PHP
Uploading media files to remote storage.
In File.php line 387:
  The file or directory "pub/media/xxxx.file" cannot be copied to "*.amazonaws.com/media/xxxx.file"
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## パッチのインストール後に必要な追加手順

（このセクションはオプションです。問題を修正するためにパッチを適用した後に必要な手順がいくつかある場合があります）。 

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
