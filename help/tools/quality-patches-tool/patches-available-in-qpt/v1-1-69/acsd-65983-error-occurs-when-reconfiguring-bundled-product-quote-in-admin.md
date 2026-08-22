---
title: ACSD-65983:Adminでバンドルされた製品の見積もりを再設定すると、エラーが発生する
description: バックエンドの[!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit]画面でバンドル製品を設定しようとしたときにエラーが発生するAdobe Commerceの問題を修正するには、ACSD-65983 パッチを適用します。
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
exl-id: d03d09bc-a444-486f-ad6b-fddbbf795d8a
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# ACSD-65983:Adminでバンドルされた製品の見積もりを再設定すると、エラーが発生する

ACSD-65983 パッチは、管理バックエンドでバンドルされた製品見積を再設定するとエラーが返される問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69がインストールされている場合に利用できます。 パッチ IDはACSD-65983です。 この問題は、Adobe Commerce 2.4.9で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

管理バックエンドでバンドルされた製品見積を再構成すると、エラーが返されます。

<u>複製する手順</u>:

1. 管理パネルに移動し、**[!UICONTROL B2B Feature]**: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**&#x200B;を有効にします。
1. 固定額のバンドル商品を作成し（例：*$10*）、**オプション 1**&#x200B;に&#x200B;*2*、**オプション 2**&#x200B;に&#x200B;*その他*&#x200B;の&#x200B;*0*&#x200B;額の3つ以上のシンプルな商品を追加します。
1. フロントエンドから企業アカウントを作成します。
1. **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]**&#x200B;に移動し、作成した会社と製品を新しい/カスタム共有カタログに割り当てます。
1. フロントエンドで&#x200B;**会社ユーザー**&#x200B;としてログインし、バンドルから1つのシンプルな製品をカートに追加します。
1. 買い物かごページを開き、**見積もりを依頼**&#x200B;として送信します。
1. バックエンドに移動し、作成した見積もりを編集します。
1. **見積もり項目** セクションで、「**設定**」ボタンをクリックします。
1. **オプション 2**&#x200B;から別のシンプルな製品を選択します。
1. 次に、**OK** ボタンをクリックして、エラーメッセージを確認します。

<u>期待される結果</u>:

管理者から要求された見積もり項目を正常に設定でき、エラーメッセージは表示されません。

<u>実際の結果</u>:

次のエラーメッセージが表示されます。

*サーバーの技術的な問題により、エラーが発生しました。 もう一度試して、今やっていることをやり続けてください。 問題が解決しない場合は、後でもう一度やり直してください。*

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > Commerce クラウドインフラストラクチャ上のパッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」ガイド

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール
