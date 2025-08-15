---
title: Commerceのサイトとインフラストラクチャを保護
description: Adobe Commerce インストールを設定、設定、更新する際に、セキュリティのベストプラクティスを導入して、セキュリティを維持します。
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# Commerceのサイトとインフラストラクチャを保護

クラウドインフラストラクチャー上にデプロイされたAdobe Commerce プロジェクトに対してセキュリティで保護された環境を構築および維持することは、Adobe Commerceのお客様、ソリューションパートナー、Adobeの間で共有される責務です。 このガイドの目的は、顧客側の方程式に関するベストプラクティスを提供することです。

すべてのセキュリティリスクを排除することはできませんが、これらのベストプラクティスを適用すると、Commerce インストールのセキュリティ体制が強化されます。 安全なサイトとインフラストラクチャは、悪意のある攻撃に対するターゲットとしての魅力を損ない、ソリューションと顧客の機密情報のセキュリティを確保し、サイトの中断や高コストな調査を引き起こす可能性のあるセキュリティ関連のインシデントを最小限に抑えます。

>[!NOTE]
>
>クラウドインフラストラクチャ上のAdobe Commerce プロジェクトをセキュリティで保護および維持管理する役割と責務について詳しくは、[Adobe Commerce セキュリティおよびコンプライアンスガイド ](https://experienceleague.adobe.com/ja/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart) の _Shared Responsibility Model_）を参照してください。

[ サポートされているすべてのバージョン ](../../../release/versions.md):

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## 優先度の推奨事項

Adobeでは、以下の推奨事項をすべての顧客にとって最も優先度の高いものとみなしています。 すべてのCommerceのデプロイメントで、次の主要なセキュリティのベストプラクティスを実装します。

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**管理者およびすべての SSH 接続に対して 2 要素認証を有効にする**

- [Commerce管理者のセキュリティ ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html?lang=ja)

- [ セキュアな SSH 接続 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html?lang=ja) （クラウドインフラストラクチャ）

プロジェクトで MFA が有効な場合、SSH アクセス権を持つクラウドインフラストラクチャアカウント上のすべてのAdobe Commerceは、認証ワークフローに従う必要があります。 このワークフローでは、環境にアクセスするために 2 要素認証（2FA）コードまたは API トークンと SSH 証明書が必要です。

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) 管理者 **保護**

- [ デフォルトの ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=ja#use-a-custom-admin-url) や一般的な用語（`admin` など）を使用する代わりに `backend` デフォルト以外の管理者 URL を設定します。 この設定により、サイトへの不正アクセスを試みるスクリプトの危険性が軽減されます。

- [ セキュリティの詳細設定 ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=ja) - URL に秘密鍵を追加し、パスワードでは大文字と小文字を区別することを要求し、管理者セッションの長さ、パスワードの有効期間、管理者ユーザーアカウントをロックするまでに許可されるログイン試行回数を制限します。 セキュリティを強化するには、現在のセッションの有効期限が切れる前にキーボードが非アクティブであった期間を設定し、ユーザー名とパスワードで大文字と小文字を区別する必要があります。

- [ReCAPTCHA を有効にする ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html?lang=ja) で、自動ブルートフォース攻撃から管理者を保護します。

- [ 管理者権限 ](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html?lang=ja) をロールに割り当て、ロールを管理者ユーザーアカウントに割り当てる場合は、最小権限の原則に従います。

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**Adobe Commerceの最新リリースへのアップグレード**

Commerce Adobe Commerce、Commerce Services および拡張機能の [ 最新リリースへのアップグレード ](#upgrade-to-the-latest-release) を行うことで、コードが常にアップデートされます。これには、Adobeで提供されるセキュリティパッチ、ホットフィックス、その他のパッチが含まれます。

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**Secure sensitive configuration values**

[ 構成管理 ](../../../configuration/cli/set-configuration-values.md) を使用して、重要な設定値をロックします。

`lock config` および `lock env` CLI コマンドは、環境変数を設定して、管理者から更新されないようにします。 このコマンドは、`<Commerce base dir>/app/etc/env.php` ファイルに値を書き込みます。 （クラウドインフラストラクチャプロジェクト上のCommerceについては、[Store Configuration Management](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=ja#sensitive-data) を参照してください）。

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) セキュリティスキャン **実行**

[Commerce セキュリティスキャンサービス ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=ja) を使用すると、すべてのAdobe Commerce サイトを監視して既知のセキュリティリスクやマルウェアがないか確認し、サインアップしてパッチの更新やセキュリティの通知を受けることができます。

## 拡張機能とカスタムコードのセキュリティを確保する

Adobe Commerce Marketplace からサードパーティの拡張機能を追加してAdobe Commerceを拡張する場合、またはカスタムコードを追加する場合、次のベストプラクティスを適用して、カスタマイズのセキュリティを確保します。

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**セキュリティに精通したパートナーまたはソリューションインテグレーター（SI）を選択してください** – 安全な開発手法に従い、セキュリティ上の問題の防止と対処に関する確かな実績を持つ組織を選択することで、安全な統合とカスタムコードの安全な配信を確保します。

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**セキュアな拡張機能を使用** - ソリューションインテグレーターまたは開発者に相談し、[Commerce拡張機能のベストプラクティスに従って、Adobe デプロイメントに最も適切でセキュアな拡張機能を特定します ](../planning/extensions.md)。

- Adobe Commerce Marketplace またはソリューションインテグレーターを通じたソース拡張機能のみ。 拡張機能がインテグレーターを通じて提供されている場合は、インテグレーターが変更した場合に拡張機能ライセンスの所有権が譲渡可能であることを確認します。

- 拡張機能とベンダーの数を制限することで、リスクを軽減します。

- 可能な場合は、Commerce アプリケーションと統合する前に、セキュリティのための拡張機能コードを確認します。

- PHP Extension Developers が、Adobe Commerceの開発ガイドライン、プロセス、およびセキュリティのベストプラクティスに従っていることを確認してください。 特に、開発者は、リモートコードの実行や暗号化の脆弱性を引き起こす可能性のある PHP の機能を使用しないでください。 [ 拡張機能開発者ガイドのベストプラクティス ](https://developer.adobe.com/commerce/php/best-practices/security/) セキュリティ *を参照してください*

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**監査コード** - サーバーとソースコードリポジトリで、開発の残り部分を確認します。 アクセス可能なログファイル、公開されている.git ディレクトリ、SQL 文を実行するトンネル、データベースダンプ、php 情報ファイル、その他の保護されていない必要のない、攻撃で使用される可能性のあるファイルがないことを確認します。

## 最新リリースへのアップグレード

Adobeは、セキュリティを強化し、潜在的な侵害からお客様をより適切に保護するために、更新されたソリューションコンポーネントを継続的にリリースしています。 Adobe Commerce アプリケーション、インストール済みサービスおよび拡張機能の最新バージョンにアップグレードし、最新のパッチを適用することは、セキュリティの脅威に対する最初かつ最善の防御策です。

Commerceは通常、セキュリティアップデートを四半期ごとにリリースしますが、優先度などの要因に基づいて、主要なセキュリティ上の脅威に対するホットフィックスをリリースする権利を留保します。

使用可能なAdobe Commerceのバージョン、リリースサイクル、アップグレードおよびパッチプロセスについて詳しくは、次のリソースを参照してください。

- [リリース済みバージョン](../../../release/versions.md)
- [ 製品の提供 ](../../../release/product-availability.md) （Adobe Commerce サービスおよびAdobeが作成した拡張機能）
- [Adobe Commerce ライフサイクルポリシー](../../../release/lifecycle-policy.md)
- [アップグレードガイド](../../../upgrade/overview.md)
- [パッチの適用方法](../../../upgrade/patches/overview.md)

>[!TIP]
>
>[Adobe Security Notification Service](https://www.adobe.com/subscription/adbeSecurityNotifications.html) を登録することで、最新のセキュリティ情報を取得し、セキュリティの既知の問題を軽減できます。

## ディザスタリカバリ計画の作成

Commerce サイトが危険にさらされた場合は、包括的なディザスタリカバリ計画を策定して実装することで、被害を抑制し、通常の業務を迅速に復旧します。

災害が原因でCommerce インスタンスを復元する必要がある場合は、Adobeからバックアップファイルを提供できます。 お客様とソリューションインテグレーターは、該当する場合、復元を実行できます。

Adobeでは、ディザスタリカバリ計画の一環として、ビジネス継続性の目的で再導入が必要な場合に、再導入を容易に行うために [Adobe Commerce アプリケーション設定をエクスポート ](../../../configuration/cli/export-configuration.md) することを強くお勧めします。 設定をファイルシステムにエクスポートする主な理由は、システム設定がデータベース設定よりも優先されるためです。 読み取り専用のファイルシステムでは、アプリケーションを再デプロイして機密性の高い設定を変更し、保護レイヤーを追加する必要があります。

### 追加情報

**クラウドインフラストラクチャにデプロイされたAdobe Commerce**

- [ バックアップと災害復旧 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=ja#backup-and-disaster-recovery)

- [ クラウドインフラストラクチャー上でのAdobe Commerceのストア設定管理 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=ja)

**Adobe Commerceがオンプレミスにデプロイされました**

- [構成設定のエクスポート](../../../configuration/cli/export-configuration.md)

   - [設定を読み込み](../../../configuration/cli/import-configuration.md)

   - [ファイル・システム、メディア、データベースのバックアップとロールバック](../../../installation/tutorials/backup.md)

## 安全なサイトとインフラストラクチャの維持

このセクションでは、Adobe Commerce インストールのサイトおよびインフラストラクチャのセキュリティを維持するためのベストプラクティスの概要を説明します。 これらのベストプラクティスの多くは、コンピューターインフラストラクチャの一般的なセキュリティ保護に重点を置いているので、推奨事項の一部は既に実装されている可能性があります。

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**不正アクセスのブロック** - ホスティングパートナーと協力して、Commerce サイトとお客様のデータへの不正なアクセスをブロックする VPN トンネルを設定します。 Commerce アプリケーションへの不正アクセスをブロックする SSH トンネルを設定します。

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**Web アプリケーションファイアウォールを使用** - トラフィックを分析し、不明な IP アドレスにクレジットカード情報が送信されるなど、不審なパターンを Web アプリケーションファイアウォールで検出します。

クラウドインフラストラクチャにデプロイされたAdobe Commerceのインストールでは、[Fastly サービス統合 ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=ja) で利用可能なビルトイン WAF サービスを使用できます

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**高度なパスワードセキュリティ設定を設定** – 強力なパスワードを設定し、PCI Data Security Standard の 8.2.4 節で推奨されているように、少なくとも 90 日ごとに変更します。[Admin Security 設定の指定 ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=ja) を参照してください。

![ チェックリスト ](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg)**HTTPS を使用** - Commerce サイトを新たに実装した場合は、HTTPS を使用してサイト全体を起動します。 Googleでは、ランキング要因として HTTPS を使用するだけでなく、HTTPS で保護されていない限り、多くのユーザーはサイトからの購入さえ検討しません。

## マルウェアからの保護

e コマースサイトを狙ったマルウェア攻撃は非常に一般的であり、脅威アクターはトランザクションからクレジットカードと個人情報を収集する新しい方法を継続的に開発しています。

ただし、Adobeは、ほとんどのサイトの侵害は、革新的なハッカーによるものではないことがわかりました。 むしろ、脅威アクターは、多くの場合、既存のパッチが適用されていない脆弱性、パスワードの不備、ファイルシステム内の所有権と権限の設定の脆弱性を利用します。

最も一般的に経験される攻撃では、悪意のあるコードが顧客ストアの絶対ヘッダーまたは絶対フッターに挿入されます。 コードは、顧客のログイン資格情報やチェックアウトフォームデータなど、顧客がストアフロントに入力するフォームデータを収集します。 その後、このデータは、Commerce バックエンドではなく、悪意のある目的で別の場所に送信されます。 また、マルウェアは、元の支払いフォームを支払いプロバイダーが設定した保護を上書きする偽のフォームに置き換えるコードを管理者に実行させる可能性があります。

クライアントサイドのクレジットカードスキマーは、次の図に示すように、マーチャントの web サイトコンテンツにコードを埋め込み、ユーザーのブラウザーで実行できるマルウェアの一種です。

![e コマースサイトを狙ったマルウェア攻撃のデータフロー ](../../../assets/playbooks/malware-data-flow.svg)

ユーザーによるフォームの送信やフィールド値の変更など、特定のアクションが発生した後、スキマーはデータをシリアル化し、サードパーティのエンドポイントに送信します。 これらのエンドポイントは、通常、最終的な宛先にデータを送信するためのリレーとして機能する、その他の侵害された web サイトです。


>[!TIP]
>
>Commerce サイトがマルウェア攻撃の影響を受ける場合は、Adobe Commerceのベストプラクティスに従って [ セキュリティインシデントへの対応 ](../maintenance/respond-to-security-incident.md) してください。

### 最も一般的な攻撃を把握

以下は、AdobeがCommerceのお客様に認識し、対策を講じることをお勧めする、一般的なカテゴリの攻撃のリストです。

- **サイトデファリング** – 攻撃者がサイトの外観を変更したり、独自のメッセージを追加したりして、Web サイトに損害を与えます。 サイトやユーザーアカウントへのアクセスは侵害されていますが、多くの場合、支払い情報は安全なままです。

- **ボットネット** – 顧客のCommerce サーバーは、スパムメールを送信するボットネットの一部になります。 通常、ユーザーデータは侵害されませんが、顧客のドメイン名がスパムフィルターでブロックリストに加えるされ、ドメインからのメールの配信が妨げられる可能性があります。 または、お客様のサイトがボットネットの一部になり、別のサイトに対して分散型サービス拒否（DDoS）攻撃を引き起こします。ボットネットは、Commerce サーバーへのインバウンド IP トラフィックをブロックし、お客様が買い物できないようにする可能性があります。

- **直接のサーバ攻撃**：データが侵害され、バックドアやマルウェアがインストールされ、サイトの運用に影響が及びます。 サーバーに保存されていない支払い情報は、これらの攻撃によって侵害される可能性が低くなります。

- **サイレントカードのキャプチャ** – この最も悲惨な攻撃では、侵入者は隠されたマルウェアやカードのキャプチャソフトウェアをインストールするか、さらに悪いことに、クレジットカードデータを収集するためにチェックアウトプロセスを変更します。 その後、データはダークウェブ上の販売のために別のサイトに送信されます。 このような攻撃は、長期間、気付かれず、顧客アカウントや財務情報の大きな漏洩につながる可能性があります。

- **サイレントキーログ** – 脅威アクターは、管理者ユーザーの資格情報を収集するためにキーログコードを顧客サーバーにインストールして、検出されることなくログインしたり他の攻撃を開始したりできます。

### パスワード推測攻撃からの保護

ブルートフォースパスワード推測攻撃により、管理者に不正アクセスが行われる可能性があります。 次のベストプラクティスに従って、これらの攻撃からサイトを保護します。

- Commerceのインストールに外部からアクセスできるすべてのポイントを特定して保護します。

  管理者へのアクセスを保護するには、Commerce プロジェクトの設定時にAdobeの [ 優先度の高い推奨事項 ](#priority-recommendations) に従うことで、通常は最も保護が必要になります。

- 指定した IP アドレスまたはネットワークからのユーザーのみにアクセスを許可するアクセス制御リストを設定して、Commerce サイトへのアクセスを制御します。

  カスタム VCL コードスニペットと共に Fastly Edge ACL を使用して、受信リクエストをフィルタリングし、IP アドレスによるアクセスを許可できます。 [ リクエストを許可するためのカスタム VCL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html?lang=ja) を参照してください。


  >[!TIP]
  >
  >リモートワーカーを採用している場合は、Commerce サイトへのアクセス権を持つアドレスのリストにリモート社員の IP アドレスが含まれていることを確認してください。

### クリックジャッキング攻撃の防止

Adobeは、ストアフロントへのリクエストに含めることができる `X-Frame-Options` HTTP リクエストヘッダーを提供することで、クリックジャッキング攻撃からストアを保護します。 [2&rbrace;Adobe Commerce設定ガイド ](../../../configuration/security/xframe-options.md) の「クリックジャッキングの悪用の防止 *を参照してください。*
