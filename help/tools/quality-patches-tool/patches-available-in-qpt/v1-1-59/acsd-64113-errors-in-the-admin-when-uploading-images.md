---
title: 'ACSD-64113:  [!DNL Media Gallery]を介して幅が高さより小さい画像をアップロードする際に、管理者がエラーを起こしました'
description: ACSD-64113 パッチを適用して、 [!DNL Media Gallery]を介して高さと比較して幅が比較的小さい画像をアップロードする際に管理者でエラーが発生するAdobe Commerceの問題を修正します。
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-64113: [!DNL Media Gallery]を介して、幅が高さより小さい画像をアップロードすると、管理者がエラーを起こす

ACSD-64113 パッチは、[!DNL Media Gallery]を介して高さと比較（またはその逆）した幅が比較的小さい画像をアップロードする際に管理者でエラーが発生する問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59がインストールされている場合に利用できます。 パッチ IDはACSD-64113です。 この問題は、Adobe Commerce 2.4.8で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerceのバージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

[!DNL Media Gallery]を介して高さ（またはその逆）と比較して幅が比較的小さい画像をアップロードすると、管理者でエラーが発生します。

<u>複製する手順</u>:

1. **[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]**&#x200B;に移動し、**[!UICONTROL wysiwyg]** ディレクトリを選択します。
1. 画像を、その高さと比較して比較的小さな幅でアップロードします（またはその逆）。

<u>期待される結果</u>:

画像はエラーなくアップロードされます。

<u>実際の結果</u>:

1. 次のエラーメッセージがスローされます。

   *サーバーの技術的な問題により、エラーが発生しました。 もう一度試して、今やっていることをやり続けてください。 問題が解決しない場合は、後でもう一度やり直してください。*
1. `var/log/exception.log`の内容：

   ```yaml
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   または

   ```yaml
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)」（Commerce クラウドインフラストラクチャガイド）。


## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool]: ツール ガイドの品質パッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)のセルフサービス ツール。
