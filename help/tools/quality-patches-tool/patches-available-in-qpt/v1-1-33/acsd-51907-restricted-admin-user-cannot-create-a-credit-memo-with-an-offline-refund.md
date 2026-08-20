---
title: ACSD-51907：制限付きの管理者ユーザーが、オフラインの払い戻し用のクレジットメモを作成できない
description: ACSD-51907 パッチを適用して、制限された管理者ユーザーがオフラインの払い戻しを含むクレジットメモを作成できないAdobe Commerceの問題を修正します。
exl-id: 1c44d99b-7633-4768-b7e7-332f3666a5d9
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# ACSD-51907：制限付きの管理者ユーザーが、オフラインの払い戻し用のクレジットメモを作成できない

ACSD-51907 パッチは、制限された管理者ユーザーがオフラインの払い戻しを含むクレジットメモを作成できないパフォーマンスの問題を修正します。 このパッチは、[!DNL Quality Patches Tool (QPT)] 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51907です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

制限付き管理者ユーザーは、オフライン払い戻しを含むクレジットメモを作成できません。

<u>複製する手順</u>:

1. 既定のweb サイトに&#x200B;**顧客**&#x200B;を作成します。
1. 関連する&#x200B;*ストア*&#x200B;と&#x200B;*ストアビュー*&#x200B;を使用して&#x200B;**新しいweb サイト**&#x200B;を作成します。
1. デフォルトのweb サイトを新しいweb サイトに設定し、キャッシュをクリアします。
1. 顧客設定の変更：**管理者** > **店舗** > **設定** > **顧客** > **顧客設定** > **顧客アカウントの共有= グローバル**。
1. **管理者** > **システム** > **権限**&#x200B;で、役割の範囲が新しく作成されたweb サイト *（セールスデータへのアクセスのみ）*&#x200B;に設定された新しい管理者ユーザーの役割を作成します。
1. この役割を持つ新しい管理者アカウントを作成します。
1. オンライン支払い方法&#x200B;*（例：Auth.netまたはPayPal）*&#x200B;を使用して新しい注文を作成します。
1. 制限付き管理者ユーザーとしてログインします。
1. **Sales** > **Orders** > then **order view page**&#x200B;に移動します。
1. 請求書を作成します。
1. 「請求書」タブに移動します。
1. **請求書**&#x200B;をクリックします。
1. **[!UICONTROL Credit Memo]**&#x200B;をクリックします。
1. 「**[!UICONTROL Refund to Store Credit]**」チェックボックスをオンにし、その近くのテキストフィールドを&#x200B;*1*&#x200B;値に設定します。
1. 「**[!UICONTROL Refund Offline]**」ボタンをクリックします。

<u>期待される結果</u>:

クレジットメモが作成され、*$1*&#x200B;が店舗のクレジットに返金されます。

<u>実際の結果</u>:

エラーメッセージ「*この項目を表示するには、さらに権限が必要です*」が表示されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
