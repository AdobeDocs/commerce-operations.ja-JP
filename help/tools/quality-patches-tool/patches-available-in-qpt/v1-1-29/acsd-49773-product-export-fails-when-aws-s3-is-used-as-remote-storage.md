---
title: ACSD-49773:AWS S3をリモートストレージとして使用すると、製品の書き出しが失敗する
description: ACSD-49773 パッチを適用して、AWS S3をリモートストレージとして使用すると製品の書き出しが失敗するAdobe Commerceの問題を修正します。
feature: Data Import/Export, Iaas, Products, Storage
role: Admin
exl-id: 82f1299f-52b6-4f87-b01c-072d1661c022
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-49773:AWS S3をリモートストレージとして使用すると、製品の書き出しが失敗する

ACSD-49773 パッチは、AWS S3をリモートストレージとして使用すると、製品の書き出しが失敗する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29がインストールされている場合に利用できます。 パッチ IDはACSD-49773です。 この問題は、Adobe Commerce 2.4.6で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

AWS S3をリモートストレージとして使用すると、製品の書き出しが失敗する。

<u>複製する手順</u>:

1. 大規模なデータプロファイルのインストール。
1. AWS アカウントを作成し、S3 バケットとIAM ユーザーを設定します。
1. 設定を使用して`app/etc/env.php`を更新します。
1. `bin/magento setup:upgrade`を実行します。
1. バックエンドに移動し、完全な製品エクスポートを実行します。
1. `[queue_message_status]` テーブルからキューのメッセージ状態を監視します。
1. システムログを確認します。

<u>期待される結果</u>:

製品の書き出しはエラーなく完了します。

<u>実際の結果</u>:

システムのログにエラーが記録されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]  リリース：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを確認します
* [Commerce実装プレイブックのデータベーステーブルを修正するためのベストプラクティス ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications)

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
