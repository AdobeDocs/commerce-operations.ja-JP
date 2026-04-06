---
source-git-commit: c297996273c42481fe9d3ee20ec3b9256e27fb5f
workflow-type: tm+mt
source-wordcount: '761'
ht-degree: 0%

---
# スニペット

## 拡張サポート用のセキュリティパッチ {#extended-support}

>[!NOTE]
>
>2.4.5の拡張サポートセキュリティパッチは、Adobe Commerceのお客様のみが利用できます。 これらのパッチは、Magento Open Source コードベースでは使用できません。 [拡張サポート ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy#extended-support)を参照してください。

## Commerceのみ {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool]は、Adobe Commerce インスタンスでのみ使用できます。

<!-- Configuration guide snippets -->

## ファイルシステム所有者 {#file-system-owner}

>[!WARNING]
>
>すべてのMagento CLI コマンドは、[ ファイルシステム所有者](/help/configuration/cli/config-cli.md#prerequisites)によって実行する必要があります。

## バックアップコマンド {#tip-backup-command}

>[!TIP]
>
>`support:backup` コマンドは、_コマンドで実行したコード バックアップと同じ_ not`setup:backup`です。 `support:backup` コマンドは、Adobe Commerce サポートによるテスト用にコードをバックアップすることを目的としています。

## B2B パッチ {#b2b-patches}

>[!NOTE]
>
>このセキュリティパッチをインストールした後、Adobe Commerce B2B マーチャントは、互換性のある最新のB2B セキュリティパッチリリースにアップデートする必要があります。 [B2B リリースノート ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes)を参照してください。

## Adobe Commerceのみ {#ee-only}

>[!NOTE]
>
>この機能は、Adobe Commerce インスタンスでのみ使用できます。

## DBの分割は非推奨 {#deprecate-split-db}

>[!IMPORTANT]
>
>Adobe Commerceのバージョン 2.4.2では、分割データベース機能は[非推奨](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157)でした。 [分割データベースから単一データベースへの復帰](/help/configuration/storage/revert-split-database.md)を参照してください。

<!-- End of Configuration guide snippets -->

## 後方互換性のない変更 {#bics}

>[!NOTE]
>
>Adobe Commerce リリースには、下位互換性のない変更（BIC）が含まれている場合があります。 後方互換性のない変更を確認するには、[BIC reference](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)を参照してください。 後方互換性のない主要な問題については、[BIC ハイライト ](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/)で説明しています。 すべてのリリースが主要なBICを導入しているわけではありません。

## Alphaの免責事項 {#alpha}

>[!IMPORTANT]
>
>[Alpha](/help/release/versioning-policy.md#alpha-patch-release) リリースは不完全な可能性があり、欠陥が含まれている可能性があります。 彼らは、いかなる種類の保証もなく「現状のまま」提供されます。 Adobeは、Alpha リリースを（Adobe サポートサービスまたはその他の方法で）維持、修正、更新、変更、またはその他の方法でサポートする義務を負いません。 お客様は、Alpha リリースの正しい機能やパフォーマンス、または付随するドキュメントや資料に依存してはなりません。 Alpha リリースの使用は、完全にお客様の責任で行います。

## Betaの免責事項 {#beta}

>[!IMPORTANT]
>
>Beta リリースには欠陥が含まれている可能性があり、いかなる保証もなしに「現状のまま」提供されます。 Adobeは、ベータ版のリリースを維持、修正、更新、変更、その他のサポート（Adobe サポートサービスまたはその他のサービス）する義務を負いません。 お客様は、ベータ版リリースおよび/または付随するドキュメントや資料の正しい機能やパフォーマンスに依存しないように注意してください。 したがって、ベータ版リリースの使用は、完全にお客様の責任で行います。

## CVEのお知らせ {#cve-notice}

>[!NOTE]
>
>2.3.2 リリース以降、外部の関係者から報告された各セキュリティバグに対して、インデックス付きのCommon Vulnerabilities and Exposures （CVE）番号を割り当てて公開します。 これにより、ユーザーはデプロイメントの未解決の脆弱性をより簡単に特定できます。 CVE IDの詳細については、[CVE](https://cve.mitre.org/)を参照してください。

## その他のリリース情報 {#other-release-info}

>[!NOTE]
>
>これらのリリースノートに記載されている機能強化とバグ修正のコードはAdobe Commerceにバンドルされていますが、これらのプロジェクトのいくつか（B2B、Page Builder、Progressive Web Applications （PWA） Studioなど）も個別にリリースされています。 これらのプロジェクトのバグ修正は、各プロジェクトのドキュメントに記載されている、プロジェクト固有の個別のリリース情報に記載されています。 [製品リリースの概要](/help/release/release-notes/overview.md)を参照してください。

## PHP プロセス制御 {#php-process-control}

並列モードでインデクサーを実行する前に、PHPでプロセス制御サポート （`pcntl`）を有効にする必要があります。 PHP ドキュメントの[ インストール ](https://www.php.net/manual/en/pcntl.installation.php)を参照してください。

## カスタムパッチ {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobeでは、この方法を使用したAdobeが提供する公式のパッチの適用はサポートされていません。 ご自身のリスクで次の方法を使用してください。 公式パッチを適用するには、[[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}を使用します。 カスタムパッチをデプロイする前に、必ず包括的なテストを実行してください。

## 2025年10月のセキュリティパッチバックポート {#oct-2025-backports}

<!--These fixes were backported to 2.4.8-pe, 2.4.7-p8, and 2.4.6-p13-->

* **TinyMCEからHugerte.orgへの移行**

  TinyMCE 5および6のサポートの終了と、TinyMCE 7との非互換性のライセンスが原因で、Adobe Commerce WYSIWYG エディターの現在の実装は、TinyMCEからオープンソースの[HugeRTE エディター](https://hugerte.org/)に移行されます。

  この移行により、Adobe Commerceはオープンソースライセンスに準拠し、既知のTinyMCE 6の脆弱性を回避し、最新のサポートされた編集体験をマーチャントと開発者に提供できます。

* **Apache ActiveMQ Artemis STOMP プロトコルのサポートを追加しました**

  Simple Text Oriented Messaging Protocol （STOMP）によるActiveMQ Artemis オープンソースのメッセージブローカーのサポートを追加しました。 信頼性の高いスケーラブルなメッセージングシステムを提供し、STOMP ベースの統合に柔軟に対応できます。 [Commerce Configuration Guide](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework#apache-activemq-artemis-stomp)の&#x200B;*Apache ActiveMQ Artemis*&#x200B;を参照してください。

## チェックアウトページでstatic.min.jsとmixins.min.jsの読み込みに失敗する {#checkout-page-fails-to-load-static-min-js-and-mixins-min-js}

JavaScriptのバンドルと縮小の両方が実稼動モードで有効になっている場合、最近のCSP/SRIの変更後、チェックアウトページにstatic.min.jsとmixins.min.jsが読み込まれません。 その結果、RequireJS Mixinが実行されず、チェックアウト ノックアウト テンプレートが解決されません（例：`"Failed to load the 'Magento_Checkout/shipping' template requested by 'checkout.steps.shipping-step.shippingAddress'"`）。

**回避策**:

* JavaScript バンドルを無効にする。または
* JavaScript バンドルを有効にしておく場合は、JavaScriptの縮小を無効にします。

>[!IMPORTANT]
>
>本番環境でCSPを無効にしたり、SRI保護を削除したりしないでください。 プラグインレベルのバイパスは、ホットフィックスの最後の手段としてのみ使用し、セキュリティチームが確認する必要があります。

**ホットフィックス**:

ホットフィックスが利用可能です。 パッチの詳細については、ナレッジベースで「[JSの縮小とバンドルが有効になっている場合にチェックアウトが失敗する](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27997)」を参照してください。
