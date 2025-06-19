---
title: 'ACSD-64627: [!UICONTROL Company Structure] でカスタム顧客属性を保存できません'
description: ACSD-64627 パッチを適用すると、[!UICONTROL Company Structure] 内のユーザーを追加または編集する際にカスタムカスタマー属性が保存されないAdobe Commerceの問題を修正できます。
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-64627: [!UICONTROL Company Structure] でカスタム顧客属性を保存できません

ACSD-64627 パッチは、**[!UICONTROL Company Structure]** ページ内でユーザーを追加または編集する際に、カスタム顧客属性を保存できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 がインストールされている場合に使用できます。 パッチ ID は ACSD-64627 です。 この問題はAdobe Commerce 2.4.9 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3、2.4.7-p4、2.4.8

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p8、2.4.7-p3、2.4.7-p4、2.4.8

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

**[!UICONTROL Company Structure]** ページでユーザーを追加または編集する際に、カスタム顧客属性が保存されない。

<u> 再現手順 </u>:

1. B2B 機能が有効になっているAdobe Commerce インスタンスをインストールします。
1. **[!UICONTROL Input Type]** を *[!UICONTROL File (attachment)]* に設定して、*custom_upload* という名前の新しい顧客属性を作成します。
1. **[!UICONTROL Input Type]** が *[!UICONTROL Image File]* に設定された *image_attachment* という名前の別の顧客属性を作成します。
1. **[!UICONTROL Show on Storefront]** を *はい* に設定して、両方の属性をストアフロントに表示します。 すべてのフォームを選択：
   * 顧客登録
   * 顧客アカウントの編集
   * 管理チェックアウト
1. 新しい会社を作成してアクティブ化します。
1. 会社管理者としてストアフロントにログインします。
1. **[!UICONTROL Customer Account]**/**[!UICONTROL Company Structure]** または **[!UICONTROL Customer Account]**/**[!UICONTROL Company Users]** に移動します。
1. 「**[!UICONTROL Add New User]**」をクリックします。
1. *custom_upload* 属性の **[!UICONTROL Upload]** をクリックします。
1. *image_attachment* 属性の **[!UICONTROL Select file]** をクリックします。

<u> 期待される結果 </u>:

両方の属性に対してエクスプローラーが開きます。 保存時に値が保存され、ファイルは正常にアップロードされます。

<u> 実際の結果 </u>:

ボタンが応答しない。 エクスプローラーが開かれないか、データが保存されていません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
