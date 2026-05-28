---
title: 'ACSD-56635: アカウント共有が [!DNL Global]に設定されている場合、インポートされた顧客が重複する'
description: アカウント共有を [!DNL Global]に設定してインポートを使用すると、インポートされたお客様が同じ電子メールアドレスで複製されるAdobe Commerceの問題を修正するには、ACSD-56635 パッチを適用します。
feature: Customers, Attributes
role: Admin, Developer
exl-id: 73abec4a-03b0-45d4-bfc6-f3c6862e733c
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# ACSD-56635: アカウント共有が[!DNL Global]に設定されている場合、インポートした顧客が同じ電子メールアドレスで重複する

ACSD-56635 パッチは、アカウント共有が[!DNL Global]に設定された状態でインポートを使用すると、インポートされた顧客が同じ電子メールアドレスで複製される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48がインストールされている場合に利用できます。 パッチ IDはACSD-56635です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6-p3

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

アカウント共有が[!DNL Global]に設定されている場合、インポートされた顧客は同じ電子メールアドレスで複製されます。

<u>複製する手順</u>:

1. Adobe Commerce （2.4-develop b2b） **[!UICONTROL Admin]**&#x200B;で、**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**&#x200B;にアクセスします。
1. *[!UICONTROL Share Customer Accounts]*&#x200B;設定を&#x200B;*[!DNL Global]*&#x200B;に設定します。
1. 複数のweb サイトとストアを作成する：

   * ws1 > s11、s12 > sw111、sw122
   * ws2 > s21、s22 > sw211、sw212

1. メールアドレスを<adb@yormail.com>として使用し、管理者から&#x200B;*メイン web サイト*&#x200B;の下に新しい顧客を作成します。
1. **[!UICONTROL Admin]**&#x200B;で、**[!UICONTROL System]** > **[!UICONTROL Import]**&#x200B;に移動します。
1. **[!UICONTROL Customer Entity Type]**&#x200B;を&#x200B;*[!UICONTROL Customers Main File]*&#x200B;として選択します。
1. 別のweb サイト（ws1など）で<adb@yormail.com>と同じ電子メールアドレスを使用します。 以下に示すCSV ファイルのサンプル customer.csvを参照してください。
1. インポートを完了すると、同じ電子メールアドレスを持つ&#x200B;*ws1* web サイトで作成された新しいユーザーが表示されます。

customer.csv コンテンツ：

```text
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>期待される結果</u>:

同じメールアドレスを持つインポートされた顧客は、重複することなく更新されます。

<u>実際の結果</u>:

顧客の読み込みを使用する場合、同じメールアドレスで重複する顧客が作成されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
