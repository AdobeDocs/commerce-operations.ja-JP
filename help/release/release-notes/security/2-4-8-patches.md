---
title: Adobe Commerce 2.4.8 セキュリティパッチリリースノート
description: Adobe Commerce バージョン 2.4.8のセキュリティパッチリリースに含まれているセキュリティバグの修正、セキュリティの強化、およびその他のセキュリティ関連アップデートについて説明します。
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: 95333e271e6f7a8e782d6a40b754fe29ac280414
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---

# Adobe Commerce 2.4.8 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p5

Adobe Commerce 2.4.8-p5 セキュリティリリースには、以前のリリース 2.4.8で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB26-49](https://helpx.adobe.com/jp/security/products/magento/apsb26-49.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

#### MariaDB 11.8との互換性

Adobe Commerce 2.4.8は、MariaDB 11.4のサポートを維持しながら、MariaDB 11.8との互換性が検証されています。 このアップデートは、プラットフォームの安定性を維持するためにMariaDB 11.8で導入されたSQL動作の変更、デフォルトのアップデート、および非推奨化に対応します。

#### OpenSearch 3の最新マイナーバージョンのサポート

Adobe Commerce 2.4.8では、クラウドインフラストラクチャ、クラウドネイティブおよびオンプレミスのデプロイメントで、Adobe Commerce上のOpenSearch 3の最新マイナーバージョンがサポートされるようになりました。 OpenSearch 2との互換性は保持されます。

#### Valkey 8.1 LTS サポート

Adobe Commerce 2.4.8はValkey 8.1 LTSと互換性を持つようになり、クラウドインフラストラクチャ上のAdobe Commerceでサポートされている長期的なキャッシュバックエンドオプションを提供します。

#### RabbitMQ 4.2のサポート

Adobe Commerce 2.4.8は、2026年2月に予定されているRabbitMQ 4.1のサポート終了日に対応するRabbitMQ 4.2と互換性を持つようになりました。 Apache ActiveMQ Artemisとの互換性は保持され、ActiveMQはこのセキュリティのみのリリースラインのデフォルトのメッセージキューサービスのままです。

#### USPS REST APIのサポート

USPS出荷統合では、従来のWeb ツール APIに加えて、最新のRESTful USPS APIがサポートされるようになりました。 管理者は、管理者設定から使用するUSPS統合APIを選択できます。 このアップデートは、USPS Web Tools APIの非推奨化に備えています。

#### Magento所有のラミナス MVC フォーク

Laminas MVCの退職に対処するため、Adobe CommerceはMagentoが所有する`laminas-mvc` （公開名：`magento/magento-zf-mvc`）のフォークを使用するようになりました。 このフォークは、Adobe Commerce 2.4.8の継続的なパッチ適用と長期的なセキュリティコンプライアンスを保証します。

## 2.4.8-p4

Adobe Commerce 2.4.8-p4 セキュリティリリースには、以前のリリース 2.4.8で特定された脆弱性に対するセキュリティバグ修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB26-05](https://helpx.adobe.com/jp/security/products/magento/apsb26-05.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

#### DHL配送の統合のためのMyDHL REST API サポート

DHL出荷統合では、既存のDHL Express XML統合に加えて、MyDHL REST APIがサポートされるようになりました。 このアップデートはDHLの現在のAPI スタックに合っており、古いXML APIの廃止に備えています。

#### 最新バージョンのComposerとの互換性の追加

Adobe Commerce 2.4.8が更新され、Composer 2.9.xがサポートされるようになりました。ただし、Composer 2.2 LTSとの互換性は維持されます。

## 2.4.8-p3

Adobe Commerce 2.4.8-p3 セキュリティリリースには、以前のリリース 2.4.8で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-94](https://helpx.adobe.com/jp/security/products/magento/apsb25-94.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

* ACP2E-3874の修正：複数の同じアイテムが注文された場合に備えて、注文の詳細に対するREST API応答に`base_row_total`および`row_total`属性の正しい値が含まれるようになりました。

* AC-15446の修正：`Magento\Framework\Mail\EmailMessage`のエラーを修正しました。`getBodyText()`が`Symfony\Component\Mime\Message`に存在しない`getTextBody()` メソッドを呼び出そうとし、Magento 2.4.8-p2および`magento/framework` 103.0.8-p2との互換性を確保しました。

{{oct-2025-backports}}

### 既知の問題

#### チェックアウトページでstatic.min.jsとmixins.min.jsの読み込みに失敗する

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.8-p2

Adobe Commerce 2.4.8-p2 セキュリティリリースには、以前のリリース 2.4.8で特定された脆弱性に対するセキュリティバグ修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-71](https://helpx.adobe.com/jp/security/products/magento/apsb25-71.html)を参照してください。

{{b2b-patches}}

## 2.4.8-p1

Adobe Commerce 2.4.8-p1 セキュリティリリースには、以前のリリース 2.4.8で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB25-50](https://helpx.adobe.com/jp/security/products/magento/apsb25-50.html)を参照してください。

{{b2b-patches}}

### ハイライト

このリリースには、次のハイライトが含まれています。

* **API パフォーマンスの向上** – 以前のセキュリティ パッチの後に導入された一括非同期web API エンドポイントのパフォーマンス低下を解決します。<!-- AC-14078 -->

* **CMS ブロック アクセス修正** – 制限された権限（マーチャンダイジング専用アクセスなど）を持つ管理者ユーザーが[!UICONTROL CMS Blocks]の一覧ページを表示できなかった問題を解決します。

  以前は、以前のセキュリティ パッチをインストールした後、構成パラメーターが欠落しているため、これらのユーザーでエラーが発生していました。<!-- AC-14087 -->

* **Cookie制限の互換性** - フレームワークの`MAX_NUM_COOKIES`定数に関する後方互換性のない変更を解決します。 この更新プログラムは、期待される動作を復元し、cookieの制限と相互作用する拡張機能またはカスタマイズの互換性を確保します。<!-- AC-14475 -->

* **非同期操作** – 以前の顧客の注文を上書きするための非同期操作が制限されています。<!-- AC-13917 -->

* **CVE-2025-47110**&#x200B;の修正 – メールテンプレートの脆弱性を解決します。<!-- AC-14695 -->

* **VULN-31547**&#x200B;の修正 – カテゴリの正規リンクの脆弱性を解決します。<!-- AC-14713 -->

>[!BEGINSHADEBOX]

CVE-2025-47110およびVULN-31547の修正プログラムは、独立したパッチとしても利用できます。 詳しくは、[&#x200B; ナレッジベース記事](https://experienceleague.adobe.com/ja/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50)を参照してください。

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2026-04-08 15:01:38 -->
