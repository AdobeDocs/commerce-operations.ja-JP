---
title: 'ACSD-67039: rp_token システム属性の検証により、顧客レコードが保存されない'
description: ACSD-67039 パッチを適用して、rp_tokenのエンコード時にダイアクリティクスが発生するAdobe Commerceの問題を修正します。
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: e5995e28-b6b5-4955-a52a-895842c6b6e8
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 1%

---

# ACSD-67039: `rp_token` システム属性の検証により、顧客レコードが保存されませんでした

ACSD-67039 パッチは、`rp_token` システム属性の検証により顧客レコードが保存されず、結果として生成される顧客メールにのみ発音区別検証が適用された問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68がインストールされている場合に利用できます。 パッチ IDはACSD-67039です。 この問題は、Adobe Commerce 2.4.7で修正されています。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p9

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ダイアクリティクスをエンコードすると、`rp_token`の検証エラーが発生し、検証から除外されます。 発音区間は、意図されたとおりに電子メールアドレスに対してのみ許可されます。

<u>複製する手順</u>:

1. Adobe Commerce 2.4.4版をインストールします。
1. 顧客の構築：
1. お客様が既に作成された2.4.4以前のバージョンから、Adobe Commerceをバージョン 2.4.6にアップグレードします。
1. 暗号化キーを`env.php`に設定=
   *d337b914e91ff703b1e94ba4156aadf0*
1. `customer_entity` テーブルの下にある任意の顧客のデータベースに次の値を設定します。
*`rp_token` = *incr4869*
*`rp_token_created_at` =* 2021-04-29 20:06:14*
1. 管理パネルで、**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;に移動します。
1. 上記の値を更新したばかりの顧客を編集します。
1. **[!UICONTROL Save Customer]**&#x200B;または&#x200B;**[!UICONTROL Save and Continue Edit]**&#x200B;をクリックします。

<u>期待される結果</u>:

お客様の値が正常に保存されました。

<u>実際の結果</u>:

顧客レコードが保存されず、管理者ユーザーにエラーメッセージ「*お客様の保存中に問題が発生しました」が表示されます。*
`system.log`に次のエラーが含まれています：

```text
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール
