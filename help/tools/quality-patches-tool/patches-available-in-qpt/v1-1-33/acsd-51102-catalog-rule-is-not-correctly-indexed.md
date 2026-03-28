---
title: ACSD-51102：多数の製品に適用されたカタログルールのインデックスが正しく作成されない
description: ACSD-51102 パッチを適用して、スケジュールされた更新によってルールが有効になっている場合に、多数の製品に適用されるカタログルールが正しくインデックス付けされないAdobe Commerceの問題を修正します。
feature: Catalog Management, Products
role: Admin
exl-id: 35a8078d-667b-4101-8562-ece052b44c9c
type: Troubleshooting
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# ACSD-51102：多数の製品に適用されたカタログルールのインデックスが正しく作成されない

ACSD-51102 パッチは、スケジュールされた更新によってルールが有効になっている場合に、多数の製品に適用されるカタログルールが正しくインデックス付けされない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33がインストールされている場合に利用できます。 パッチ IDはACSD-51102です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.3-p1

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p1

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

スケジュールされた更新によってルールが有効になっている場合、多数の製品に適用されるカタログルールに正しくインデックスが付けられません。

前提条件：

* Cron ジョブが設定され、毎分実行されます。

<u>複製する手順</u>:

1. カタログルールが有効になっている場合に、120秒以上の&#x200B;*カタログルール* インデックスの実行時間を達成するために、数千の製品を含む大規模なカタログを作成します。
2. *Active*&#x200B;のステータスが&#x200B;*No*&#x200B;に設定された2つのカタログルールを作成します。  例えば、*テスト 1*&#x200B;と&#x200B;*テスト 2*&#x200B;です。 各ルールは、カタログ内のすべての製品に影響を与え、インデクサーを120秒以上実行させる必要があります。
3. インデクサーのステータスが&#x200B;*準備完了*&#x200B;であることを確認します。
4. スケジュールされた更新を作成して、これらの2つのルールを有効にします。 *テスト 2*&#x200B;のスケジュールは、*テスト 1*&#x200B;の直後に開始する必要があります。 例えば、1分の違いがあります。
5. ストアフロントで商品価格をご確認ください。

<u>期待される結果</u>

両方のルールからの割引が適用されます。

<u>実際の結果</u>

最初のルール割引のみが適用されます。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool]  ガイドの](/help/tools/quality-patches-tool/usage.md)>使用状況[!DNL Quality Patches Tool]。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches)。
* [&#x200B; [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) ガイドの[!UICONTROL Quality Patches Tool]を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) ガイドの「[!DNL Quality Patches Tool] パッチを検索する」を参照してください。
