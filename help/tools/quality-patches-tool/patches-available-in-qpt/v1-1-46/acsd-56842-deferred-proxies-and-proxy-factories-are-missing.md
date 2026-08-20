---
title: 'ACSD-56842: ''setup:di:compile''を実行すると、遅延プロキシとプロキシファクトリが見つかりません'
description: 「setup:di:compile」を実行した後に遅延プロキシとプロキシファクトリが見つからないAdobe Commerceの問題を修正するには、ACSD-56842 パッチを適用します。
feature: Deploy, Catalog Management
role: Admin, Developer
exl-id: cd29267f-e2f2-41b5-b374-ac96166af8ad
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-56842: `setup:di:compile`の実行後に遅延プロキシとプロキシ ファクトリが見つかりません

ACSD-56842 パッチは、`setup:di:compile`の実行後に遅延プロキシとプロキシファクトリが見つからない問題を修正します。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.46がインストールされている場合に利用できます。 パッチ IDはACSD-56842です。 この問題は、Adobe Commerce 2.4.7で修正される予定です。

## 影響を受ける製品とバージョン

**パッチはAdobe Commerceのバージョン**&#x200B;用に作成されました

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p6

**Adobe Commerceのバージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい[!DNL Quality Patches Tool] リリースを含む他のバージョンに適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]：パッチの検索ページ ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)で互換性を確認します。 パッチ IDを検索キーワードとして使用して、パッチを検索します。

## イシュー

`setup:di:compile`の実行後、遅延プロキシとプロキシ ファクトリが見つかりません。

<u>複製する手順</u>:

1. *Magento_CustomModule*&#x200B;という名前のカスタムモジュールを作成します。
1. モジュールの&#x200B;*[!UICONTROL etc]* フォルダーに、次の内容を含む`di.xml`を作成します。

   ```xml
    <?xml version="1.0"?>
     <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
        <type name="Magento\Catalog\Model\ProductLink\CollectionProvider">
           <arguments>
              <argument name="providers" xsi:type="array">
                 <item name="crosssell" xsi:type="object">
                      Magento\Catalog\Model\ProductLink\CollectionProvider\Crosssell\Proxy
                 </item>
                   <item name="upsell" xsi:type="object">Magento\Catalog\Model\ProductLink\CollectionProvider\Upsell\Proxy</item>
                     <item name="related" xsi:type="object">Magento\Catalog\Model\ProductLink\CollectionProvider\Related\Proxy</item>
              </argument>
           </arguments>
         </type>
            <type name="Magento\Catalog\Model\Product">
               <arguments>
                  <argument name="catalogProductStatus" xsi:type="object">
                   Magento\Catalog\Model\Product\Attribute\Source\Status\Proxy
                  </argument>
                   <argument name="productLink" xsi:type="object">
                     Magento\Catalog\Model\Product\Link\Proxy
                   </argument>
               </arguments>
             </type>
     </config>
   ```

1. [!UICONTROL Production] モードを設定：`bin/magento deploy:mode:set production`。
1. 生成されたフォルダーをmagento ルートから削除します。
1. コマンド `bin/magento setup:di:compile`を実行します。
1. 生成されたフォルダーを確認します。

<u>期待される結果</u>:

* プロキシファイルはコンパイル後に正常に作成されます。
* コンパイル後にファクトリファイルが正常に作成されます。

<u>実際の結果</u>:

生成されたフォルダーでは、プロキシ ファイルは、改行なしで指定されたプロキシ引数に対して生成されます。また、改行で指定された引数に対しては生成されません。

## パッチを適用する

個別のパッチを適用するには、デプロイメント方法に応じて次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[!DNL Quality Patches Tool] ガイドの[[!DNL Quality Patches Tool] >使用状況](/help/tools/quality-patches-tool/usage.md)。
* クラウドインフラストラクチャ上のAdobe Commerce:「[ アップグレードとパッチ > パッチを適用](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches)」（Commerce クラウドインフラストラクチャガイド）。

## 関連トピックス

[!DNL Quality Patches Tool]について詳しくは、次を参照してください。

* [[!DNL Quality Patches Tool] がリリースされました：サポート ナレッジベースの品質パッチをセルフサービスで提供する新しいツール ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md)。
* [[!UICONTROL Quality Patches Tool] ガイドの [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)を使用して、Adobe Commerceの問題に対してパッチが利用可能かどうかを確認します。


QPTで使用可能な他のパッチについて詳しくは、[[!DNL Quality Patches Tool]: [!DNL Quality Patches Tool] ガイドの「](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) パッチを検索する」を参照してください。
