---
title: 'MDVA-39713: ユーザーは、アクティブなスケジュールされた更新の開始時刻を編集できます'
description: MDVA-39713 パッチは、ユーザーがアクティブなスケジュールされた更新の開始時刻を編集できる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.12 がインストールされている場合に利用できます。 パッチ ID は MDVA-39713。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。
feature: CMS
role: Admin
exl-id: 450a968f-a5ed-478f-a857-579fea1eb3b7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39713: ユーザーは、アクティブなスケジュールされた更新の開始時刻を編集できます

MDVA-39713 パッチは、ユーザーがアクティブなスケジュールされた更新の開始時刻を編集できる問題を修正します。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.12 がインストールされている場合に使用できます。 パッチ ID は MDVA-39713。 この問題はAdobe Commerce 2.4.5 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.3

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.0 ～ 2.3.6

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

ユーザーは、スケジュールされたアクティブな更新の開始時刻を編集できます。

<u> 再現手順 </u>:

1. 新しいCMSページを作成します。
1. **新規更新をスケジュール** を選択し、**開始日** を現在の+1 分に設定します。
1. ローカル環境でコマンド `bin/magento cron:run --group=staging` を実行して、スケジュールされたアップデートをアクティベートします。 数分待ってから、スケジュールがアクティブかどうかを確認します。
1. スケジュールがアクティブになったら、ページを更新します。
1. 「スケジュールされた変更」セクションの「**表示/編集**」をクリックします。
1. +2 分を追加して時間を編集し、変更を保存します。
1. CMSページを保存します。
1. 再び、次のコマンドを実行します：`bin/magento cron:run --group=staging`。
1. スケジュールされている更新の **表示/編集** をクリックします。

<u> 期待される結果 </u>:

ユーザーは、スケジュールされたアクティブな更新の開始時刻を編集できません。

<u> 実際の結果 </u>:

同じ ID 「11」の *Item （Magento\Cms\Model\Page） already exists* のようなエラーがユーザーに表示されます。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md)[!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
