---
title: ACSD-51471：管理者ユーザーがバンドル製品のスケジュールされた更新を保存できない
description: ACSD-51471 パッチを適用して、シンプルな製品をスケジュール済みのアップデートと共に使用するバンドル製品のスケジュール済みアップデートを管理者ユーザーが保存できないAdobe Commerceの問題を修正します。
exl-id: d8134111-63f0-4476-a407-677bda52fa90
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# ACSD-51471：管理者ユーザーがバンドル製品のスケジュールされた更新を保存できない

ACSD-51471 パッチは、管理者ユーザーがスケジュールされた更新を含む単純な製品を使用するバンドル製品のスケジュールされた更新を保存できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51471です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Admin ユーザーは、自身がスケジュールされた更新を持つシンプルな製品を使用するバンドル製品のスケジュールされた更新を保存できません。

<u>複製する手順</u>:

1. シンプルな商品の作成。
1. *開始日*&#x200B;と&#x200B;*終了日*&#x200B;のみを含むシンプルな製品のスケジュールされた更新を追加します。
1. 更新が適用されたら、製品のSKUを変更します。
1. バンドル製品を作成し、手順1で作成したシンプルな製品を子製品として追加します。
1. バンドル製品のスケジュールされた更新を作成して、バンドル製品を有効にします。 スケジュールされた更新に対して&#x200B;*開始日*&#x200B;と&#x200B;*終了日*&#x200B;の両方を指定します。
1. スケジュールされた更新を保存します。

<u>期待される結果</u>:

スケジュールされた更新が正常に保存されました。

<u>実際の結果</u>:

スケジュールされた更新を保存すると、次のエラーが発生します：*リクエストされた製品が存在しません。 製品を確認して、もう一度試してください。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
