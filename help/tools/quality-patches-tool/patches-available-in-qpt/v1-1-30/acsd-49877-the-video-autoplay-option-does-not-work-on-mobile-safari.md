---
title: 'ACSD-49877: モバイルでビデオ自動再生が機能しない [!DNL Safari]'
description: 'ビデオがリモート ビデオ ファイルに直接リンクされている場合に、モバイルでビデオ自動再生オプションが機能しないAdobe Commerceの問題を修正するには、ACSD-49877 パッチを適用します。 [!DNL Safari] '
feature: CMS
role: Admin
exl-id: aa2557e2-4bed-4004-b9bc-36c59f1e9cdc
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-49877: モバイル [!DNL Safari]でビデオ自動再生が機能しない

ACSD-49877は、ビデオがリモート ビデオ ファイルに直接リンクされている場合に、モバイル [!DNL Safari]の自動再生オプションが機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30がインストールされている場合に利用できます。 パッチ IDはACSD-49877です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.3.7 - 2.4.6

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、[ !magento/quality-patches] パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: パッチを検索]で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

ビデオがストリーミングサービスではなくリモートのビデオファイルに直接リンクされている場合、モバイル [!DNL Safari]でビデオ自動再生が機能しません。

<u>前提条件</u>:
[!DNL Page Builder]個のモジュールがインストールされています。

<u>複製する手順</u>:

1. 新しいCMS ページを作成し、**[!UICONTROL Content Value]**&#x200B;を[!DNL Page Builder]で編集します。
1. コンテンツに&#x200B;*Tab*&#x200B;要素を追加し、*Tab*&#x200B;内に&#x200B;*Video Element*&#x200B;を追加します。
1. 次に、歯車ボタンをクリックして、*ビデオ要素*&#x200B;を編集します。
1. MP4 ビデオファイルへのリンクを[!UICONTROL Video URL] フィールドに追加します。
1. **[!UICONTROL Autoplay]** フィールドに「*はい*」のマークを付けます。
1. **[!UICONTROL Save]**&#x200B;をクリックします。
1. IPhoneを使用して、[!DNL Safari]で最近作成したページを開きます。

<u>期待される結果</u>

自動再生オプションは、iPhoneを使用して[!DNL Safari]で機能します。

<u>実際の結果</u>

IPhoneを使用している[!DNL Safari]では、自動再生オプションは機能しません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/ja/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=ja) パッチを検索する」を参照してください。
