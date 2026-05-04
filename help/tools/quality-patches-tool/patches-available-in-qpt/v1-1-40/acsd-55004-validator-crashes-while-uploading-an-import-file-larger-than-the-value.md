---
title: ACSD-55004：値より大きいインポートファイルをアップロードすると、バリデータがクラッシュする
description: 「php.ini」で設定された値よりも大きいインポートファイルをアップロードする際にバリデータがクラッシュするAdobe Commerceの問題を修正するには、ACSD-55004 パッチを適用します。
feature: Data Import/Export
role: Admin, Developer
exl-id: c889f645-a3ae-4330-8ca9-45f8b6616ac8
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-55004：値より大きいインポートファイルをアップロードすると、バリデータがクラッシュする

ACSD-55004 パッチは、`php.ini`で設定された値よりも大きいインポートファイルをアップロードする際にバリデータがクラッシュする問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.40がインストールされている場合に利用できます。 パッチ IDはACSD-55004です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`php.ini`で設定された値より大きいインポートファイルをアップロードすると、バリデータがクラッシュします。

<u>複製する手順</u>:

`php.ini`で設定されたサイズを超えるインポートファイルをアップロードしてみてください。

<u>期待される結果</u>:

ファイルサイズはエラーなしで検証されます。

<u>実際の結果</u>:

検証プログラムがクラッシュします。

`var/log/exception.log`の内容：

```shell
[2023-10-06T21:36:30.470618+00:00] report.CRITICAL: Error: Class "Zend_Validate_File_Upload" not found in ../module-import-export/Model/Source/Upload.php:81
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
