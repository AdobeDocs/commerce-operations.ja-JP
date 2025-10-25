---
source-git-commit: e625670e741c0669050ab758d4f87c5ca06fe3df
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---
# スニペット

## Commerceのみ {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool] は、Adobe Commerce インスタンスでのみ使用できます。

<!-- Configuration guide snippets -->

## ファイルシステムの所有者 {#file-system-owner}

>[!WARNING]
>
>すべてのMagento CLI コマンドは、[ ファイルシステムの所有者 ](/help/configuration/cli/config-cli.md#prerequisites) によって実行される必要があります。

## バックアップコマンド {#tip-backup-command}

>[!TIP]
>
>`support:backup` コマンドは、_コマンドで実行されるコード バックアップと同じ_`setup:backup` ではない）です。 `support:backup` コマンドは、Adobe Commerce サポートが調査するコードをバックアップすることを目的としています。

## B2B パッチ {#b2b-patches}

>[!NOTE]
>
>このセキュリティパッチをインストールした後、Adobe Commerce B2B マーチャントも、互換性のある最新の B2B セキュリティパッチリリースに更新する必要があります。 [B2B リリースノート ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes) を参照してください。

## Adobe Commerceのみ {#ee-only}

>[!NOTE]
>
>この機能は、Adobe Commerce インスタンスでのみ使用できます。

## Split DB の廃止 {#deprecate-split-db}

>[!IMPORTANT]
>
>Adobe Commerceのバージョン 2.4.2 では、分割データベース機能は [ 非推奨 ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) となりました。 [ 分割データベースから単一データベースへの復帰 ](/help/configuration/storage/revert-split-database.md) を参照してください。

<!-- End of Configuration guide snippets -->

## 後方互換性のない変更 {#bics}

>[!NOTE]
>
>Adobe Commerce リリースには、後方互換性のない変更（BIC）が含まれている場合があります。 後方互換性のない変更を確認するには、[BIC リファレンス ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/) を参照してください。 後方互換性のない主な問題については、[BIC ハイライト ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/) で説明しています。 すべてのリリースで主要な BIC が導入されるわけではありません。

## Alpha免責事項 {#alpha}

>[!IMPORTANT]
>
>[Alpha](/help/release/versioning-policy.md#alpha-patch-release) のリリースは不完全な場合があり、欠陥が含まれている可能性があります。 それらは「現状のまま」で、いかなる保証もなく提供されます。 Adobeは、（Adobe サポートサービスまたはその他の方法を通じて）Alpha リリースを保守、修正、更新、変更、変更、その他の方法でサポートする義務を負いません。 お客様は、Alpha リリース、およびそれに付随するドキュメントや資料が正しく機能し、動作することを信頼しないでください。 Alpha リリースの使用は、完全にお客様自身の責任で行います。

## Beta免責事項 {#beta}

>[!IMPORTANT]
>
>Beta リリースには不具合が含まれている場合があり、いかなる保証もなく「現状のまま」提供されます。 Adobeは、ベータ版リリースの保守、修正、更新、変更、またはその他のサポート（Adobe サポートサービスまたはその他のサービスから）を行う義務を負いません。 お客様は、ベータ版リリースおよび/または付属のドキュメントや資料の正しい機能やパフォーマンスに対して、注意を払い、いかなる形でも依存しないようにしてください。 したがって、ベータ版リリースの使用は、完全にお客様自身の責任で行います。

## CVE 通知 {#cve-notice}

>[!NOTE]
>
>2.3.2 リリース以降、アドビは、外部関係者からアドビに報告された各セキュリティバグに対して、インデックス付きの Common Vulnerability and Exposures （CVE）番号を割り当て、公開します。 これにより、ユーザーはデプロイメント内の対処されていない脆弱性をより簡単に特定できます。 CVE 識別子について詳しくは、[CVE](https://cve.mitre.org/) を参照してください。

## その他のリリース情報 {#other-release-info}

>[!NOTE]
>
>これらのリリースノートで説明されている機能強化およびバグ修正のコードはAdobe Commerceにバンドルされていますが、これらのプロジェクトの一部（B2B、Page Builder、Progressive Web Applications （PWA） Studio など）も独立してリリースされています。 これらのプロジェクトのバグ修正は、各プロジェクトのドキュメントで利用できる別のプロジェクト固有のリリース情報に記載されています。 [ 製品リリースの概要 ](/help/release/release-notes/overview.md) を参照してください。

## PHP プロセスコントロール {#php-process-control}

インデクサーを並列モードで実行する前に、PHP でプロセス制御サポート （`pcntl`）を有効にする必要があります。 PHP ドキュメントの [ インストール ](https://www.php.net/manual/en/pcntl.installation.php) を参照してください。

## カスタムパッチ {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobeは、Adobeが提供する公式パッチをこの方式を使用して適用することはサポートしていません。 自己責任で以下の方法をご利用ください。 公式パッチを適用するには、[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"} を使用します。 カスタムパッチをデプロイする前に、必ず包括的なテストを実施してください。

## 2025 年 10 月のセキュリティパッチバックポート {#oct-2025-backports}

<!--These fixes were backported to 2.4.8-pe, 2.4.7-p8, and 2.4.6-p13-->

* **TinyMCE から Hugerte.org への移行**

  TinyMCE 5 および 6 のサポートが終了し、TinyMCE 7 との互換性がなくなったため、現在のAdobe Commerce WYSIWYG エディターの実装は、TinyMCE からオープンソースの [HugeRTE エディター ](https://hugerte.org/) に移行されています。

  この移行により、Adobe Commerceはオープンソースのライセンスに引き続き準拠し、既知の TinyMCE 6 の脆弱性を回避し、マーチャントやデベロッパー向けに最新のサポートされている編集機能を提供します。

* **Apache ActiveMQ Artemis STOMP プロトコルのサポートを追加**

  Simple Text Oriented Messaging Protocol （STOMP）を介した ActiveMQ Artemis オープンソースメッセージブローカーのサポートを追加しました。 信頼性と拡張性に優れたメッセージングシステムを提供し、STOMP ベースの統合に柔軟性を提供します。 [2}Commerce Configuration Guide](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework#apache-activemq-artemis-stomp) の {Apache ActiveMQ Artemis *を参照してください。*

## チェックアウトページで static.min.js と mixins.min.js の読み込みに失敗する {#checkout-page-fails-to-load-static-min-js-and-mixins-min-js}

JavaScriptのバンドルと縮小の両方が実稼働モードで有効になっている場合、CSP/SRI が最近変更された後、チェックアウトページで static.min.js と mixins.min.js が読み込まれません。 その結果、RequireJS mixin が実行されず、チェックアウトノックアウトテンプレートが解決されません（例：`"Failed to load the 'Magento_Checkout/shipping' template requested by 'checkout.steps.shipping-step.shippingAddress'"`）。

**回避策**:

* JavaScriptのバンドルを無効にする
* JavaScriptのバンドルを有効にしたままにする場合は、JavaScriptの縮小を無効にします。

>[!IMPORTANT]
>
>実稼動環境で CSP を無効にしたり、SRI 保護を削除したりしないでください。 プラグインレベルのバイパスは、ホットフィックスの最後の手段としてのみ使用してください。その際は、セキュリティチームのレビューを受ける必要があります。

**ホットフィックス**:

この問題に対処するホットフィックスが、できるだけ早くリリースされます。 詳しくは、このリリースノートページを監視してください。
