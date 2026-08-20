---
title: 'ACSD-52714: y-m-dに設定すると、日付フィルターが管理者グリッドで機能しない'
description: 日付フォーマットがy-m-dに設定されている場合に、日付フィルターが管理者グリッドで機能しないAdobe Commerceの問題を修正するには、ACSD-52714 パッチを適用します。
feature: Attributes
role: Admin, Developer
exl-id: 4a34900b-9566-41bb-8d3e-18a440117907
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52714: y-m-dに設定すると、日付フィルターが管理者グリッドで機能しない

ACSD-52714 パッチは、日付形式がy-m-dに設定されている場合に、日付フィルターが管理者グリッドで機能しない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43がインストールされている場合に利用できます。 パッチ IDはACSD-52714です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.5-p2

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

日付形式がy-m-dに設定されている場合、日付フィルターは管理グリッドで機能しません。

<u>複製する手順</u>:

1. clean Adobe Commerceをインストールします。
1. Edit
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
ファイルと追加
   `<dateFormat>Y-MM-dd</dateFormat>`
へ
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
タグの下に
   `<dataType>date</dataType>`

1. キャッシュ `bin/magento c:f`をフラッシュします。
1. 管理者にログインして、**[!UICONTROL Customers]** > **[!UICONTROL All Customers]**&#x200B;から新しい顧客を作成します。

   * 差出人：現在の日付 – 1日
   * to：現在の日付

1. **[!UICONTROL Apply Filters]**&#x200B;をクリックします。

<u>期待される結果</u>:

グリッドの日付フィルターは、ロケールセットに関係なく適切に機能します。

<u>実際の結果</u>:

次のメッセージが表示されます：*レコードが見つかりませんでした*。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[&#x200B; アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
