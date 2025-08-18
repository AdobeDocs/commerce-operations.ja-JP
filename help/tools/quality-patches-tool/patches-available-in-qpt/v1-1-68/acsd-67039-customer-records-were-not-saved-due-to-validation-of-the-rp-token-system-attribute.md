---
title: 'ACSD-67039: rp_token システム属性の検証により、顧客レコードが保存されませんでした'
description: ACSD-67039 パッチを適用して、発音区別符号のエンコーディングによって rp_token で妥当性検査が中断されるAdobe Commerceの問題を修正してください。
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: e5995e28-b6b5-4955-a52a-895842c6b6e8
source-git-commit: 17c35f6da57440c2704879309a58c46b2c4eea25
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039: システム属性の検証により、顧客レコードが保存 `rp_token` れませんでした

ACSD-67039 パッチは、`rp_token` システム属性の検証が原因で顧客レコードが保存されず、得られた顧客の電子メールにのみ発音区別化検証が適用されていた問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 がインストールされている場合に使用できます。 パッチ ID は ACSD-67039 です。 この問題はAdobe Commerce 2.4.7 で修正されました。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p9

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

Diacritic のエンコードは、検証から除外される `rp_token` での検証エラーの原因となります。 分音記号は、意図したとおり、メールアドレスに対してのみ使用できます。

<u> 再現手順 </u>:

1. Adobe Commerce 2.4.4 バージョンをインストールします。
1. 顧客を作成します。
1. Adobe Commerceを、お客様が既に作成された 2.4.4 以前のバージョンから 2.4.6 にアップグレードします。
1. 暗号化キーを `env.php` に設定=
   *d337b914e91ff703b1e94ba4156aadf0*
1. `customer_entity` テーブルの下の任意の顧客について、データベースに次の値を設定します。
*`rp_token` = *incr4869*
*`rp_token_created_at` = *2021-04-29 20:06:14*
1. 管理パネルで、**[!UICONTROL Customers]**/**[!UICONTROL All Customers]** に移動します。
1. 上記の値を更新したばかりの顧客を編集します。
1. **[!UICONTROL Save Customer]** または **[!UICONTROL Save and Continue Edit]** をクリックします。

<u> 期待される結果 </u>:

顧客値は正常に保存されました。

<u> 実際の結果 </u>:

顧客レコードは保存されず、管理者ユーザーに「顧客の保存中に問題が発生しました *というエラーメッセージが表示されます。*
`system.log` には、次のエラーが含まれています。

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドの
* クラウドインフラストラクチャー上のAdobe Commerce:[ アップグレードとパッチ適用 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja) クラウドインフラストラクチャー上のCommerce ガイド

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]：品質向上パッチを適用するためのセルフサービス ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) ツール（『ツールガイド』）
