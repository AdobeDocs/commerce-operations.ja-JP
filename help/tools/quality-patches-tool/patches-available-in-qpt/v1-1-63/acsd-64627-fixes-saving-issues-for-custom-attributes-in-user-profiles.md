---
title: 'ACSD-64627: カスタム顧客属性を[!UICONTROL Company Structure]に保存できません'
description: ACSD-64627 パッチを適用して、[!UICONTROL Company Structure]内のユーザーを追加または編集する際にカスタム顧客属性を保存できないAdobe Commerceの問題を修正します。
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-64627: カスタム顧客属性を[!UICONTROL Company Structure]に保存できません

ACSD-64627 パッチは、**[!UICONTROL Company Structure]** ページ内でユーザーを追加または編集する際にカスタム顧客属性を保存できない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63がインストールされている場合に利用できます。 パッチ IDはACSD-64627です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方式） 2.4.7-p3、2.4.7-p4、2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方式） 2.4.6-p8、2.4.7-p3、2.4.7-p4、2.4.8

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

**[!UICONTROL Company Structure]** ページでユーザーを追加または編集する際に、カスタム顧客属性が保存されない。

<u>複製する手順</u>:

1. B2B機能が有効になっているAdobe Commerce インスタンスをインストールします。
1. **[!UICONTROL Input Type]**&#x200B;が&#x200B;*[!UICONTROL File (attachment)]*&#x200B;に設定された&#x200B;*custom_upload*&#x200B;という名前の新しい顧客属性を作成します。
1. **[!UICONTROL Input Type]**&#x200B;が&#x200B;*[!UICONTROL Image File]*&#x200B;に設定された&#x200B;*image_attachment*&#x200B;という名前の別の顧客属性を作成します。
1. **[!UICONTROL Show on Storefront]**&#x200B;を&#x200B;*Yes*&#x200B;に設定して、両方の属性をストアフロントに表示します。 すべてのフォームを選択：
   * お客様登録
   * 顧客アカウント編集
   * 管理者チェックアウト
1. 新しい会社を作成し、アクティブ化する。
1. 会社の管理者としてストアフロントにログインします。
1. **[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]**&#x200B;または&#x200B;**[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**&#x200B;に移動します。
1. **[!UICONTROL Add New User]**&#x200B;をクリックします。
1. *custom_upload*&#x200B;属性の&#x200B;**[!UICONTROL Upload]**&#x200B;をクリックします。
1. *image_attachment*&#x200B;属性の&#x200B;**[!UICONTROL Select file]**&#x200B;をクリックします。

<u>期待される結果</u>:

両方の属性に対してファイルエクスプローラーが開きます。 保存時に、値が保存され、ファイルが正常にアップロードされます。

<u>実際の結果</u>:

ボタンが応答しません。 ファイルエクスプローラーが開かない、またはデータが保存されない。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
