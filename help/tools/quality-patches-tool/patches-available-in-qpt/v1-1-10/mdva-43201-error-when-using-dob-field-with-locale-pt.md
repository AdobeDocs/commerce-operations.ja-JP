---
title: MDVA-43201：ロケール PTでDOB フィールドを使用するとエラーが発生する
description: MDVA-43201 パッチは、ポルトガル語ロケールの顧客登録フォームでDOB顧客属性を使用する際にエラーが発生する問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.10がインストールされている場合に利用できます。 パッチ IDはMDVA-43201です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: B2B, Cache
role: Admin
exl-id: be087420-1ee3-40cc-8ff7-62c5641609cc
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# MDVA-43201：ロケール PTでDOB フィールドを使用するとエラーが発生する

MDVA-43201 パッチは、ポルトガル語ロケールの顧客登録フォームでDOB顧客属性を使用する際にエラーが発生する問題を解決します。 このパッチは、[品質パッチツール（QPT） ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10がインストールされている場合に使用できます。 パッチ IDはMDVA-43201です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

DOB顧客属性がポルトガル語ロケールの顧客登録フォームに追加されると、フォームはエラー&#x200B;*引数1をiterator_to_array （）に渡し、インターフェイスをトラベラブルに実装する必要があることを示します。nullは*&#x200B;です。

<u>前提条件</u>:

B2B モジュールがインストールされている。

<u>複製する手順</u>:

1. 管理者/**ストア**/**設定**/**一般**/**ロケールオプション**&#x200B;に移動し、「**ポルトガル語（ポルトガル）**」にロケールを設定して、**保存**」をクリックします。
1. インデックスを再作成してキャッシュをクリアします。
1. **ストア** > **属性** > **顧客**&#x200B;に移動します。
1. DOB顧客属性を開き、**ストアフロントで表示**&#x200B;を&#x200B;**はい**&#x200B;に設定します。
1. **で使用する** フォームからすべてを選択します。
1. 属性を保存します。
1. フロントエンドの「新しいアカウントを作成」ページに移動します。

<u>期待される結果</u>:

ポルトガル語ストアの顧客登録フォームでは、DOB属性の追加にエラーは発生しません。

<u>実際の結果</u>:

ポルトガル語ストアの顧客登録フォームで、DOB属性を追加するとエラーが発生します。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
