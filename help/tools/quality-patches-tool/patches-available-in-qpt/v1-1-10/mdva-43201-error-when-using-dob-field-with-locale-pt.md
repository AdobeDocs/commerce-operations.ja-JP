---
title: MDVA-43201：ロケール PTでDOB フィールドを使用するとエラーが発生する
description: MDVA-43201 パッチは、ポルトガル語ロケールの顧客登録フォームでDOB顧客属性を使用する際にエラーが発生する問題を解決します。 このパッチは、[Quality Patches Tool （QPT） ] （https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches） 1.1.10がインストールされている場合に利用できます。 パッチ IDはMDVA-43201です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。
feature: B2B, Cache
role: Admin
exl-id: be087420-1ee3-40cc-8ff7-62c5641609cc
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%
---
# MDVA-43201：ロケール PTでDOB フィールドを使用するとエラーが発生する

MDVA-43201 パッチは、ポルトガル語ロケールの顧客登録フォームでDOB顧客属性を使用する際にエラーが発生する問題を解決します。 このパッチは、[品質パッチツール（QPT） &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10がインストールされている場合に使用できます。 パッチ IDはMDVA-43201です。 この問題は、Adobe Commerce 2.4.4で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>パッチは、新しい品質パッチツールのリリースを含む他のバージョンに適用される場合があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

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
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

品質パッチツールについて詳しくは、以下を参照してください。

* [品質パッチツールがリリースされました：サポートナレッジベースで品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [品質パッチツール &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題にパッチが適用されているかどうかを、[!DNL Quality Patches Tool] ガイドで確認してください。

QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
