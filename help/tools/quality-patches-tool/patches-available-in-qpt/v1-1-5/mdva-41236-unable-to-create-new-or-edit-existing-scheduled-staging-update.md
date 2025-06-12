---
title: MDVA-41236：製品のスケジュールされた更新を新規作成または編集できない
description: MDVA-41236 パッチは、「終了日」が既に削除されている場合、ユーザーが製品の新しいスケジュール済み更新を作成したり、既存のスケジュール済み更新を編集したりできない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5 がインストールされている場合に利用できます。 パッチ ID は MDVA-41236。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: Products, Staging
role: Admin
exl-id: 82192778-4f25-40a0-882e-d52d32c433c2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-41236：製品のスケジュールされた更新を新規作成または編集できない

MDVA-41236 パッチは、「終了日」が既に削除されている場合、ユーザーが製品の新しいスケジュール済み更新を作成したり、既存のスケジュール済み更新を編集したりできない問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.5 がインストールされている場合に使用できます。 パッチ ID は MDVA-41236。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

「終了日」が以前に削除されている場合、ユーザーが製品の新しいスケジュールを作成したり、既存のスケジュールを編集したりできない。

<u> 再現手順 </u>:

1. ステータスが *無効* に設定された製品を作成します。
1. スケジュールされた更新を追加してこの製品を有効にします。
   * 未来の開始日と終了日を追加します。
1. **終了日** を削除して、スケジュールされた更新を編集します。
1. スケジュールを再度編集し、**終了日** を追加してみてください。 エラーが発生します。
1. ページを更新して、「スケジュール済み更新を編集 **に再び移動し** す。
1. **更新から削除**/**更新を削除** をクリックします。
1. これで、製品の編集ページの上部にスケジュール済み更新が表示されなくなります。
1. 前の期間と重なる新しいスケジュール済み更新を作成してみてください。

<u> 期待される結果 </u>:

* 手順 4 でエラーは発生しません。 スケジュールがまだアクティブでないので、管理者はエラーなくスケジュールされた更新を更新できます。
* 管理者ユーザーは、以前の更新を削除して新しい更新を作成できます。

<u> 実際の結果 </u>:

次のエラーメッセージが表示されます。

*エラー：この時間範囲には将来の更新が既に存在します。 別の範囲を設定して、もう一度やり直してください。*


## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) の節を参照してください。
