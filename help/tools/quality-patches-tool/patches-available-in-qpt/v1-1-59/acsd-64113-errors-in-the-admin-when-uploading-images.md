---
title: 'ACSD-64113: [!DNL Media Gallery] の方法で、高さよりも幅が小さい画像をアップロードする際に、管理者でエラーが発生しました'
description: ACSD-64113 パッチを適用すると、 [!DNL Media Gallery] を介して高さと比較して幅が比較的小さい（またはその逆の）画像をアップロードする際に、管理者でエラーが発生するAdobe Commerceの問題を修正できます。
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113:[!DNL Media Gallery] を使用して、高さよりも幅が小さい画像をアップロードする際に、管理者でエラーが発生しました

ACSD-64113 パッチは、[!DNL Media Gallery] を介して高さと比較して幅が比較的小さい（またはその逆の）画像をアップロードすると、管理者でエラーが発生する問題を修正しました。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 がインストールされている場合に使用できます。 パッチ ID は ACSD-64113 です。 この問題はAdobe Commerce 2.4.8 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

Adobe Commerce（すべてのデプロイメント方法） 2.4.7-p3

**Adobe Commerce バージョンとの互換性：**

Adobe Commerce（すべてのデプロイメント方法） 2.4.5 ～ 2.4.7-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

[!DNL Media Gallery] を使用して、高さと比較して幅が比較的小さい（またはその逆の）画像をアップロードすると、管理者でエラーが発生します。

<u> 再現手順 </u>:

1. **[!UICONTROL Content]**/**[!UICONTROL Media]**/**[!UICONTROL Media Gallery]** に移動し、**[!UICONTROL wysiwyg]** ディレクトリを選択します。
1. 高さと比較して幅が比較的小さい画像をアップロードします（またはその逆）。

<u> 期待される結果 </u>:

画像がエラーなしでアップロードされます。

<u> 実際の結果 </u>:

1. 次のエラーメッセージが表示されます。

   *サーバーの技術的な問題によりエラーが発生しました。 やり直して、今までの作業を続けてください。 問題が解決しない場合は、後でもう一度試してください。*
1. `var/log/exception.log` には次が含まれます。

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   または

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 &#x200B;](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [&#x200B; アップグレードとパッチ &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=ja)/ パッチの適用」を参照してください。


## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]: 『ツールガイド』にあるクオリティパッチ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) セルフサービスツール。
