---
title: MDVA-41236：製品の新しいスケジュールされた更新を作成または既存のスケジュールされた更新を編集できない
description: MDVA-41236 パッチは、「終了日」が以前に削除された場合に、ユーザーが製品の新しいスケジュール更新を作成したり、既存のスケジュール更新を編集したりできない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5がインストールされている場合に利用できます。 パッチ IDはMDVA-41236です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。
feature: Products, Staging
role: Admin
exl-id: 82192778-4f25-40a0-882e-d52d32c433c2
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# MDVA-41236：製品の新しいスケジュールされた更新を作成または既存のスケジュールされた更新を編集できない

MDVA-41236 パッチは、「終了日」が以前に削除された場合に、ユーザーが製品の新しいスケジュール更新を作成したり、既存のスケジュール更新を編集したりできない問題を修正します。 このパッチは、[品質パッチツール （QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5がインストールされている場合に使用できます。 パッチ IDはMDVA-41236です。 この問題は、Adobe Commerce 2.4.5で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

「終了日」が以前に削除されている場合、ユーザーは新しいスケジュールを作成したり、製品の既存のスケジュールを編集したりすることはできません。

<u>複製する手順</u>:

1. ステータスが&#x200B;*disable*&#x200B;に設定された製品を作成します。
1. スケジュールされた更新を追加して、この製品を有効にします。
   * 今後の開始日と終了日を追加します。
1. **終了日**&#x200B;を削除して、スケジュールされた更新を編集します。
1. スケジュールをもう一度編集し、**終了日**&#x200B;を追加してみてください。 エラーが発生します。
1. ページを更新して、**スケジュールされた更新を編集**&#x200B;に再度移動します。
1. 「**アップデートから削除**」 > 「**アップデートを削除**」をクリックします。
1. これで、製品編集ページの上にスケジュールされた更新が表示されなくなります。
1. 以前の期間と重なる新しいスケジュール更新を作成してみてください。

<u>期待される結果</u>:

* 手順4にエラーはありません。 スケジュールがまだアクティブではないため、管理者はエラーなしでスケジュールされた更新を更新できます。
* 管理者ユーザーは、以前の更新プログラムを削除し、新しい更新プログラムを作成できます。

<u>実際の結果</u>:

ユーザーに次のエラーメッセージが表示されます。

*エラー：今後の更新は、既にこの時間範囲に存在します。 別の範囲を設定して、もう一度試してください。*


## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、「QPT[&#128279;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で使用可能な パッチ」セクションを参照してください。
