---
title: セキュリティインシデントの防止と対応
description: クラウドインフラストラクチャプロジェクト上のAdobe Commerceで発生したセキュリティ上の問題を回避し、対応するためのベストプラクティスについて説明します。
role: Admin, Developer, Leader, User
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 19ff1fee74e3c5ece13da49648252b32e549eafd
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 0%

---

# セキュリティインシデントの防止と対応に役立つベストプラクティス

Adobe Commerceのセキュリティは、 [共有された責任](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) モデル。 Adobeと技術チームが何を担当しているかを理解することが重要です。 次の記事では、セキュリティのベストプラクティスをまとめて、プロジェクトに最適なセキュリティ制御を確実に適用し、セキュリティインシデントに対する最適な対応を計画できるようにします。

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure

## インシデントに応答

セキュリティ上の問題に対応する際には、多くの考慮事項があります。 Cloud Infrastructure プロジェクトでAdobe Commerceの最近のセキュリティインシデントが発生したと思われる場合は、すべての管理者ユーザーアカウントのアクセスを監査し、高度な多要素認証 (MFA) コントロールを有効にし、重要なログを保持し、Adobe Commerceのバージョンのセキュリティアップグレードを確認します。

その他の推奨事項については、以下で詳しく説明します。 不正なアクセスを防ぎ、さらなるインシデント分析のプロセスを開始するのに役立ちます。

## セキュリティインシデントを防ぐ方法

Adobe Commerceのサイトやストアフロントに影響を与えるセキュリティインシデントを事前に防ぐには、次のセキュリティのベストプラクティスに従います。

- [管理者アクセス用の 2FA の有効化](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
2 要素認証は広く使用されており、同じアプリで異なる Web サイトのアクセスコードを生成するのが一般的です。 これにより、自分だけが自分のユーザーアカウントにログインできるようになります。 パスワードを失った場合や、ボットがパスワードを推測した場合、2 要素認証によって保護の層が 1 層追加されます。
- [MFA を SSH アクセス用に有効化](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
プロジェクトで MFA を有効にした場合、SSH アクセスを使用するすべてのAdobe Commerce Cloud Infrastructure アカウントは、2 要素認証 (2FA) コードまたは API トークンと SSH 証明書を必要とする認証ワークフローに従って環境にアクセスする必要があります。
- Adobe Commerceの最新リリースにアップグレードします。
Adobeは、サポートされる各リリースAdobe Commerceのセキュリティと機能パッチをリリースします。
- のセットアップと使用 [デフォルト以外の管理者 URL](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobeでは、デフォルトの URL の代わりに一意のカスタム管理 URL を使用することをお勧めします `admin` または一般的な用語 *backend*. この設定の変更は、決定された悪役から直接サイトを保護するわけではありませんが、不正なアクセスを得ようとするスクリプトに対する露出を減らすことができます。
- 管理者で設定値を編集または更新できないようにするには、  [`bin/magento config:set` CLI コマンドを `lock env` 設定オプション](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). このオプションは、設定値を管理者で編集できないようにロックするか、既にロックされている設定の変更を禁止します。 このオプションを使用すると、設定の変更は `<Commerce base dir>/app/etc/env.php` ファイル。
- のセットアップと実行 [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html).
拡張セキュリティスキャンを使用すると、PWAを含む各Adobe Commerceサイトを監視して、既知のセキュリティリスクとマルウェアを確認したり、パッチ更新やセキュリティ通知を受け取ったりできます。
- [管理者ユーザーアクセスの確認と更新](https://docs.magento.com/user-guide/system/permissions-users-all.html) および [セキュリティ設定](https://docs.magento.com/user-guide/stores/security-admin.html).
   - 古い、未使用または疑わしいアカウントを削除し、すべての管理者ユーザーのパスワードをローテーションします。
   - プロジェクトの「セキュリティの詳細設定 &lt;」を確認し、更新します。 管理セキュリティ設定を使用すると、URL に秘密鍵を追加したり、パスワードの大文字と小文字を区別したり、パスワードの有効期間や、管理者ユーザーアカウントがロックされるまでに許可されるログイン試行回数を制限したりできます。 セキュリティを強化するために、現在のセッションが期限切れになるまでのキーボードの操作不能時間を設定し、ユーザー名とパスワードで大文字と小文字を区別するように設定できます。
- 次の日にAdobe Commerceを監査 [クラウドプロジェクトユーザー](https://devdocs.magento.com/cloud/project/user-admin.html).
古い、未使用または疑わしいアカウントを削除し、ユーザーにパスワードの変更を要求します。
- 監査 [SSH キー](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) クラウドインフラストラクチャ上のAdobe Commerce向け
SSH キーを確認、削除、回転します。
- 管理者用のアクセス制御リスト (ACL) を実装します。
受信リクエストをフィルタリングし、カスタム ACL と組み合わせて Fastly Edge ACL リストを実装することで、IP アドレスで管理者アクセスを設定できます [VCL コードスニペット](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).

## インシデントの分析

インシデント分析の最初のステップは、できるだけ多くの事実を、できるだけ早く収集することです。 インシデントを取り巻く情報を収集すると、インシデントの潜在的な原因を特定するのに役立つ場合があります。 Adobe Commerceは、インシデント分析を支援する以下のツールを提供します。

- [監査管理アクションログ](https://docs.magento.com/user-guide/system/action-log-report.html).
アクションログレポートには、ログに対して有効になっているすべての管理者アクションの詳細が表示されます。 各レコードにはタイムスタンプが付き、IP アドレスとユーザー名が登録されます。 ログの詳細には、管理者ユーザーデータと、アクション中に加えられた関連する変更が含まれます。
- 次を使用してイベントを分析 [Adobe Commerceツールの監視](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
「 Observation for Adobe Commerce 」ツールを使用すると、複雑な問題を分析して、根本原因を特定できます。 異なるデータを追跡する代わりに、イベントとエラーを関連付ける時間を費やして、パフォーマンスのボトルネックの原因に関するより深い洞察を得ることができます。
このツールは、サイトの潜在的な問題の一部を明確に把握し、根本原因を特定してサイトのパフォーマンスを最適に維持するのに役立つようにすることを目的としています。 上記の「 Adobe Commerceの監視」ツールドキュメントへのリンクをクリックして、ツールのドキュメントにアクセスします。 ドキュメントには、 **セキュリティ** タブをクリックします。
- 次を使用してログを分析 [New Relic Logs](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Adobe Commerce on cloud infrastructure Pro プロジェクトには以下が含まれます。 [New Relic Logs](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) サービス。 このサービスは、ステージング環境と実稼動環境からすべてのログデータを集計して、一元化されたログ管理ダッシュボードに表示するように事前に設定されています。
New Relic Logs サービスを使用して、次のタスクを実行できます。
   - 用途 [New Relicクエリ](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) をクリックして、集計ログデータを検索します。
   - New Relic Logs アプリケーションでログデータを視覚化します。

## 追加情報

- [根本原因分析フレームワーク](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
