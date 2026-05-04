---
title: 'ACSD-52148: Google v3 reCAPTCHA管理者ログインが失敗することがあります'
description: ACSD-52148 パッチを適用して、Google v3 reCAPTCHA管理者ログインが時々失敗するAdobe Commerceの問題を修正します。
feature: Admin Workspace
role: Admin
exl-id: a114d39e-0aad-45c8-9e64-2b559373b228
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-52148: Google v3 reCAPTCHA管理者ログインが失敗することがあります

ACSD-52148 パッチは、Google v3 reCAPTCHA管理者ログインが失敗する問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-52148です。 この問題は、Adobe Commerce 2.4.6で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

Google v3 reCAPTCHA管理者ログインが失敗することがあります。

<u>複製する手順</u>:

1. 管理者ログインの場合は、Google v3 reCAPTCHAをオンにします。
1. Captchaを渡す管理者にログインします。

<u>期待される結果</u>

管理者は正常にログインしました。

<u>実際の結果</u>

* *reCAPTCHAの検証に失敗しました。* エラーが表示される場合があります。
* エラーが記録されました – 

  ```yaml
  report.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []
  ```

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
