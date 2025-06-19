---
title: 'ACSD-56842: ''setup:di:compile''の実行後、遅延プロキシおよびプロキシ ファクトリが見つかりません'
description: ACSD-56842 パッチを適用して、「setup:di:compile」を実行した後に遅延プロキシとプロキシファクトリが欠落するAdobe Commerceの問題を修正してください。
feature: Deploy, Catalog Management
role: Admin, Developer
exl-id: cd29267f-e2f2-41b5-b374-ac96166af8ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-56842:`setup:di:compile` を実行した後、遅延プロキシとプロキシファクトリが見つからない

ACSD-56842 パッチを適用すると、`setup:di:compile` を実行した後に遅延プロキシとプロキシファクトリが欠落する問題が修正されます。 このパッチは、[[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46 がインストールされている場合に使用できます。 パッチ ID は ACSD-56842 です。 この問題はAdobe Commerce 2.4.7 で修正される予定であることに注意してください。

## 影響を受ける製品とバージョン

**Adobe Commerce バージョン用のパッチが作成されます。**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.4-p6

**Adobe Commerce バージョンとの互換性：**

* Adobe Commerce（すべてのデプロイメント方法） 2.4.2 ～ 2.4.6-p3

>[!NOTE]
>
>このパッチは、新しい [!DNL Quality Patches Tool] リリースを含む他のバージョンにも適用される可能性があります。 パッチがAdobe Commerceのバージョンと互換性があるかどうかを確認するには、`magento/quality-patches` パッケージを最新バージョンに更新し、[[!DNL Quality Patches Tool]: Search for patches page](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) で互換性を確認します。 パッチ ID を検索キーワードとして使用して、パッチを見つけます。

## 問題

`setup:di:compile` を実行した後、遅延プロキシとプロキシファクトリが見つかりません。

<u> 再現手順 </u>:

1. *Magento_CustomModule* という名前のカスタムモジュールを作成します。
1. モジュールの *[!UICONTROL etc]* フォルダーで、次の内容の `di.xml` を作成します。

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

1. [!UICONTROL Production] モードを `bin/magento deploy:mode:set production` に設定します。
1. 生成したフォルダーを magento ルートから削除します。
1. コマンド `bin/magento setup:di:compile` を実行します。
1. 生成されたフォルダーを確認します。

<u> 期待される結果 </u>:

* コンパイル後、プロキシファイルは正常に作成されます。
* コンパイル後、ファクトリ ファイルは正常に作成されます。

<u> 実際の結果 </u>:

生成されたフォルダーでは、プロキシファイルが、改行なしで指定されたプロキシ引数に対して生成されます。改行で指定された引数に対しては生成されません。

## パッチの適用

個々のパッチを適用するには、デプロイメント方法に応じて、次のリンクを使用します。

* Adobe CommerceまたはMagento Open Source オンプレミス：[[!DNL Quality Patches Tool] > 使用状況 ](/help/tools/quality-patches-tool/usage.md) [!DNL Quality Patches Tool] ガイドに記載されています。
* クラウドインフラストラクチャー上のAdobe Commerce：クラウドインフラストラクチャー上のCommerce ガイドの [ アップグレードとパッチ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)/ パッチの適用」を参照してください。

## 関連資料

[!DNL Quality Patches Tool] について詳しくは、以下を参照してください。

* [[!DNL Quality Patches Tool]  リリース済み：品質パッチをセルフサービスで提供する新しいツール ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) をサポートナレッジベースから入手できます。
* [ を使用して、Adobe Commerceの問題にパッチが適用できるかどうかを確認します  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) （[!UICONTROL Quality Patches Tool] ガイド）。


QPT で使用可能なその他のパッチの詳細については、[!DNL Quality Patches Tool] ガイドの「[[!DNL Quality Patches Tool]: Search for patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html)」を参照してください。
