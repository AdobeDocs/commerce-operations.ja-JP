---
source-git-commit: b30fe4ed4d910ac3a99d3bcf4ff94103bcbd1369
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# 2024 年 10 月Adobe Commerce 2.4.7 – ベータ版のハイライト

## ハイライト

このリリースのAdobe Commerceには、いくつかの重要なセキュリティ修正とプラットフォームの改善が含まれています。

### セキュリティ

このリリースでは、次のようなセキュリティの強化により、最新のセキュリティのベストプラクティスへの準拠が向上しています。

>[!NOTE]
>
>セキュリティのバグ修正の最新情報については、[Adobeセキュリティ速報 APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html) を参照してください。

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>設定</strong></td>
            <td>このリリースには、セキュリティ設定に対する次の機能強化が含まれています。
              <ul>
                <li><strong> 暗号化キーのローテーション </strong>：暗号化キーを変更するための新しい CLI コマンドが使用できるようになりました。 詳しくは、<a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102"> 暗号化キーのローテーションのトラブルシューティング：CVE-2024-34102</a> ナレッジベースの記事を参照してください。<!-- AC-12589 --></li>
                <li><strong> ワンタイムパスワード（OTP）設定 </strong>：この更新は、2.4.7 での <a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value"> 後方互換性のない変更 </a> によって発生したエラーを解決するために必要です。<strong>[!UICONTROL OTP Window]</strong> フィールドの説明で設定の正確な説明が提供されるようになり、デフォルト値は <code>1</code> から <code>29</code> に変更されました。<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Platform

このリリースでは、次のプラットフォームアップグレードにより、Adobe Commerceが堅牢で信頼性の高いプラットフォームのままになり、最新のコマース環境の需要に対応できるようになります。

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>データベース</strong></td>
            <td>Adobe Commerceは、アドビの <a href="/help/release/lifecycle-policy.md"> サポートライフサイクルポリシー </a> に準拠して、次のデータベーステクノロジーの長期サポート（LTS）バージョンと互換性を持つようになりました。
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_（2029 年までサポート）_</em>：以前のバージョン（MariaDB 10.6）は 2026 年に提供終了となり、このアップグレードはシステムの整合性とパフォーマンスを維持するために不可欠です。 MariaDB 10.6 は引き続きサポートされますが、AdobeはAdobe Commerce 2.4.8 にアップグレードする場合に MariaDB 11.4 にアップグレードすることをお勧めします。</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_（2032 年までサポート）_</em>：以前のバージョン（MySQL 8.0）は 2026 年に提供終了となり、このアップグレードはシステムの整合性とパフォーマンスを維持するために不可欠です。 MySQL 8.0 は引き続きサポートされますが、AdobeはAdobe Commerce 2.4.8 にアップグレードする場合に MySQL 8.4 にアップグレードすることをお勧めします</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>このリリースには、次の PHP 機能強化が含まれています。
            <ul>
              <li><strong>PHP 8.1</strong>：このリリースでは、PHP 8.1 とAdobe Commerce 2.4.8 の互換性が失われます。Adobe Commerce 2.4.8 にアップグレードする前に、PHP 8.3 にアップグレードする必要があります。</li>
              <li><strong>PHP 8.2</strong>: PHP 8.2 の重要な変更点の 1 つは、null を nullable でない内部関数パラメータに渡すことの廃止です。 このリリースは、コアプラットフォームコンポーネントにおける PHP 8.1 の非推奨の機能に対応し、PHP 8.2 との互換性を確保します。</li>
              <li><strong>PHPUnit 10</strong>：このリリースでは、いくつかの重要な問題に対処し、互換性を強化し、Adobe Commerce テストフレームワークが最新の業界標準に準拠していることを確認します。 Adobeでは、カスタマイズを行っているすべてのCommerce Marketplaceベンダーおよびお客様に、単体テストと統合テストが 9 ではなく PHPUnit 10 で実行されることを確認することをお勧めします。</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Components</strong></td>
            <td>次のサードパーティ <a href="/help/release/packages/adobe-commerce.md"> コンポーネントと依存関係 </a> は、プラットフォームの安定性とパフォーマンスを向上させるために、最新の安定したバージョンに更新されました。
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>モノローグ/モノローグ 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>検索</strong></td>
            <td>Adobe Commerceは OpenSearch 2.x 用に最適化され、Elasticsearchとの互換性がなくなりました。 すべてのElasticsearch 7 および 8 のモジュールおよびクラスは、コードベースで非推奨（廃止予定）になりました。 Adobeでは、継続的なサポートと互換性を確保するために、オンプレミスとクラウドインフラストラクチャの両方のデプロイメントを OpenSearch に移行することを強くお勧めします。 <a href="/help/upgrade/prepare/opensearch-migration.md">OpenSearch への移行 </a> を参照してください。
              <ul>
                <li>Elasticsearch 7 およびElasticsearch 8 のオプションは、管理者の設定で「（非推奨）」というラベルが付けられました。</li>
                <li>管理者設定でユーザーが検索エンジンとして「Elasticsearch」を選択すると、Commerceで「この検索エンジンオプションは、Adobeではサポートされていません <em> という通知が表示されます。 代わりに、OpenSearch を検索エンジンとして使用することをお勧めします。」 </em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### パフォーマンス

このリリースでは、次のパフォーマンスが強化されています。

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>インデクサー</strong></td>
            <td>新しいバージョンのAdobe Commerceをインストールする場合や、以前のバージョンからアップグレードする場合、すべてのインデクサーに対してデフォルトの <a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule"> インデクサーモード </a> が [!UICONTROL **Update by Schedule**] 新されました。 新しいデフォルトでは、インデクサーが推奨設定に確実に含まれるので、システムのパフォーマンスが向上し、潜在的な問題が軽減されます。</td>
        </tr>
    </tbody>
</table>

### 画質

このリリースには、次の品質強化が含まれています。

<table style="table-layout-auto">
    <tbody>
        <tr>
           <td><strong>在庫</strong></td>
           <td>このシステムは、InventoryIndexer によって導入されたカタログから非表示の依存関係なしで動作するようになり、製品の作成、表示モードの切り替え、在庫ステータスの変更、およびその他の関連機能が期待どおりに動作することを確認します。 以前は、この非表示の依存関係により、異なるエンティティが同期され、インデクサーが異なるエンティティを使用するので、不整合が発生していました。</td>
        </tr>
        <tr>
            <td><strong>注文件数</strong></td>
            <td>混乱を最小限に抑えるために、<a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order"> 注文詳細 </a> ページで [!UICONTROL **Submit Comment**] ボタンのラベルが [!UICONTROL **Update**] に変更されました。</td>
        </tr>
    </tbody>
</table>

### GraphQL

このリリースには、次のGraphQL機能強化が含まれています。

<table style="table-layout-auto">
    <tbody>
        <tr>
           <td><strong>一般的な機能強化</strong></td>
           <td>このリリースには、GraphQL API に関する次の一般的な機能強化が含まれています。
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>:<code>grouped_product_image</code> フィールドと <code>configurable_product_image</code> フィールドを <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a> タイプに追加しました。</li>
              <li><!--LYNX-387--><strong>CartItemPrices</strong>：正確な価格設定表示と割引計算をサポートするために、次の新しいフィールドを <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> タイプに追加しました。
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>CartPrices</strong>:<code>grand_total_excluding_tax</code> フィールドを <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a> タイプに追加し、明確な税を含む価格を提供しました。</li>
              <li><!--LYNX-542--><strong>updateCartItems ミューテーション </strong>:<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a> ミューテーションを更新して、例外ではなくエラーの詳細を含む成功応答を返すようにしました。 ユーザー通知の明確さを向上させるために、エラーマッピングを強化しました。</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config クエリ </strong>:<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a> クエリに <code>theme</code> フィールドが導入されました。 このフィールドでは、reCaptcha のレンダリングに使用するテーマの名前を指定できます。</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>：在庫レベルの詳細を提供する <code>quantity</code> フィールドが <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a> に導入されました。 利用可能な在庫が表示されるか、管理設定に基づいて null が表示されます。</li>
               <li><!--LYNX-460--><strong> バンドル製品 </strong>：バンドル製品の価格表示が修正され、正確な価格と通貨に関する情報が提供されるようになりました。</li>
               <li><!--LYNX-547--><strong> 数量 </strong>：不十分な数量通知と使用できない数量通知に関するメッセージを絞り込みました。</li>
               <li><!--LYNX-541--><strong>InsufficientStockError タイプ </strong>：在庫レベルが不十分な場合に対処するために、新しい <code>InsufficientStockError</code> タイプを追加しました。 新しいエラータイプをサポートするようにスキーマを調整し、エラーレポート機能を強化しました。</li>
               <li><!--LYNX-476--><strong> 在庫金額 </strong>：使用可能な在庫金額を含めるようにエラーメッセージを強化しました。 ユーザーは、注文の更新中に在庫レベルについてより明確なインサイトを得ることができます。</li>
               <li><!--LYNX-377--><strong> 要求数量 </strong>:<code>not_available_message</code> を <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a> に追加しました。</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>顧客管理</strong></td>
           <td>このリリースには、顧客管理に関する次の機能強化が含まれています。
             <ul>
               <li><!--LYNX-391--><strong>generateCustomerToken mutation</strong>：確認されていないメールに特定のメッセージを提供するために、<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a> ールのミューテーションでのエラー処理を絞り込みました。 ユーザーガイダンスとエラー解決を向上させます。</li>
               <li><!--LYNX-390--><strong>resendConfirmationEmail mutation</strong>：メール確認を再送信するための新しい <code>resendConfirmationEmail</code> ミューテーションを追加しました。</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>注文管理</strong></td>
           <td>このリリースには、次のユーザー受注管理の機能拡張が含まれています。
             <ul>
              <li><!--LYNX-470--><strong>1 番目の注文の日付 </strong>:<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a> 番目のタイプに新しい <code>date_of_first_order</code> フィールドを追加しました。</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong>：カスタム属性を含むように <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a> タイプが拡張され、注文の詳細の表示が強化されました。 注文確認ページでの追加情報表示をサポートします。</li>
              <li><!--LYNX-458--><strong>guestOrder クエリと guestOrderByToken クエリ </strong>：カスタムアドレス属性を含むように <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a> クエリと <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a> クエリを更新して、新しいアカウントの完全なアドレス情報を確保しました。</li>
              <li><!--LYNX-450--><strong>CustomerOrder タイプ </strong>:<code>is_virtual</code> フィールドを <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> タイプに追加し、仮想製品の ID をサポートするようになりました。 仮想製品と物理製品を区別することにより、オーダー処理を強化します。</li>
              <li><!--LYNX-449--><strong>orderItemPrices</strong>：価格に複数の新しいフィールドがある <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a> に、<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> と同様の <code>OrderItemPrices</code> タイプを追加しました。</li>
              <li><!--LYNX-448--><strong> ゲスト注文の結合 </strong>：電子メールのマッチングに基づいてゲスト注文を顧客アカウントと結合する API 機能を改善しました。 再訪問者の注文管理を合理化します。</li>
              <li><!-- LYNX-523: --><strong>available_actions フィールド </strong>：注文管理を向上させるために、<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> タイプを拡張して <code>available_actions</code> フィールドを含めました。 「available_actions」フィールドは、注文に対して実行できるアクションをリストする列挙にマッピングされます。</li>
              <li><!-- LYNX-524 --><strong>CustomerOrder タイプ </strong>:<code>customer_info</code> フィールドを <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> タイプに追加しました。 このフィールドには、と <code>OrderCustomerInfo</code> が必要です。これは、顧客名の詳細を定義します。</li>
              <li><!--LYNX-519--><strong> 注文キャンセルのエラーコード </strong>:<a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a> タイプに詳細なエラーコードが追加されました。 注文キャンセルプロセスのエラー処理とユーザーフィードバックを改善しました。</li>
              <li><!--LYNX-515--><strong> ゲストユーザーが注文の返品を作成できるようにする </strong>：ゲストの注文返品をサポートするように <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a> のミューテーションを調整しました。</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder mutation</strong>：ゲストユーザーの注文キャンセルを容易にする新しい <code>confirmCancelOrder</code> mutation を追加しました。</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
