---
title: 'MDVA-41164: カスタム顧客属性を持つ会社を保存または編集できない'
description: MDVA-41164 パッチを使用すると、管理者ユーザーが、ファイルまたは画像のカスタム顧客属性を持つ会社を保存または編集できない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.5 がインストールされている場合に利用できます。 パッチ ID は MDVA-41164。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
exl-id: 9d1792e0-ba7b-444b-b1b1-771fd0e328eb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-41164: カスタム顧客属性を持つ会社を保存または編集できない

MDVA-41164 パッチを使用すると、管理者ユーザーが、ファイルまたは画像のカスタム顧客属性を持つ会社を保存または編集できない問題を解決できます。 このパッチは、[Quality Patches Tool （QPT） ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)1.1.5 がインストールされている場合に使用できます。 パッチ ID は MDVA-41164。 この問題はAdobe Commerce 2.4.4 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.3

>[!NOTE]
>
>パッチは、新しい Quality Patches Tool リリースを使用する他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

管理者ユーザーが、どのタイプのファイルまたは画像のカスタム顧客属性を持つ会社を保存または編集できません。

<u> 前提条件 </u>:

B2B モジュールがインストールされています。

<u> 再現手順 </u>:

1. **Stores**/**Config**/**B2B Features** で Company を有効にします。
1. **Stores**/**Attributes**/**Customers**/**Add New Attribute** で顧客属性を作成します。
   * 入力タイプ : ファイル（添付）
   * ストアフロントに表示：はい
   * 並べ替え順：任意
   * で使用するForms：すべてを選択
1. **顧客**/**会社**/**新しい会社を追加** で新しい会社を作成し、上記で作成した新しい属性のファイルをアップロードします。

<u> 期待される結果 </u>:

ユーザーが会社の作成を完了でき、添付ファイルがエラーなくアップロードされる。

<u> 実際の結果 </u>:

* 「*ファイルの保存中に問題が発生しました。* というエラーメッセージが表示されます。
* 例外ログには、次のようなレコードが含まれます。

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

品質向上パッチツールの詳細については、次を参照してください。

* [ 品質向上パッチツールがリリースされました：品質向上パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/ja/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) がサポートナレッジベースに追加されました。
* [Quality Patches Tool を使用して、Adobe Commerceの問題に対するパッチが使用可能かどうかを確認します ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!DNL Quality Patches Tool] ガイド）。

QPT で使用可能なその他のパッチについては、[QPT で使用可能なパッチ ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) の節を参照してください。
