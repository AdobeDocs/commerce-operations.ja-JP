---
title: Commerceのサイトとインフラストラクチャを保護
description: Adobe Commerce インストールを設定、設定、更新する際に、セキュリティのベストプラクティスを導入して、セキュリティを維持します。
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: a00b7b66beb6499f7fb19fda2dfd450799f73728
workflow-type: tm+mt
source-wordcount: '2006'
ht-degree: 0%

---

# Commerceのサイトとインフラストラクチャを保護

クラウドインフラストラクチャー上にデプロイされたAdobe Commerce プロジェクトに対してセキュリティで保護された環境を構築および維持することは、Adobe Commerceのお客様、ソリューションパートナーおよびAdobe間で共有される責務です。 このガイドの目的は、顧客側の方程式に関するベストプラクティスを提供することです。

すべてのセキュリティリスクを排除することはできませんが、これらのベストプラクティスを適用すると、Commerce インストールのセキュリティ体制が強化されます。 安全なサイトとインフラストラクチャは、悪意のある攻撃に対するターゲットとしての魅力を損ない、ソリューションと顧客の機密情報のセキュリティを確保し、サイトの中断や高コストな調査を引き起こす可能性のあるセキュリティ関連のインシデントを最小限に抑えます。

>[!NOTE]
>
>クラウドインフラストラクチャー上のAdobe Commerce プロジェクトを保護および保守するための役割と責務について詳しくは、を参照してください。 [共有責任モデル](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart)） _Adobe Commerce セキュリティおよびコンプライアンスガイド_.

[サポートされているすべてのバージョン](../../../release/versions.md) （件中）:

- クラウドインフラストラクチャー上のAdobe Commerce
- Adobe Commerce オンプレミス

## 優先度の推奨事項

Adobeでは、次の推奨事項をすべての顧客にとって最も優先度が高いと見なしています。 すべてのCommerceのデプロイメントで、次の主要なセキュリティのベストプラクティスを実装します。

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **管理者およびすべての SSH 接続の二要素認証を有効にする**

- [Commerce管理者のセキュリティ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html)

- [セキュアな SSH 接続](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html) （クラウドインフラストラクチャ）

プロジェクトで MFA が有効な場合、SSH アクセス権を持つクラウドインフラストラクチャアカウント上のすべてのAdobe Commerceは、認証ワークフローに従う必要があります。 このワークフローでは、環境にアクセスするために 2 要素認証（2FA）コードまたは API トークンと SSH 証明書が必要です。

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **管理者を保護**

- [デフォルト以外の管理者 URL の設定](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) デフォルトを使用する代わりに、 `admin` または、次のような一般的な用語 `backend`. この設定により、サイトへの不正アクセスを試みるスクリプトの危険性が軽減されます。

- [セキュリティの詳細設定](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html) – 秘密鍵を URL に追加し、パスワードでは大文字と小文字を区別することを要求し、管理者セッションの長さ、パスワードの有効期間、管理者ユーザーアカウントをロックするまでに許可されるログイン試行回数を制限します。 セキュリティを強化するには、現在のセッションの有効期限が切れる前にキーボードが非アクティブであった期間を設定し、ユーザー名とパスワードで大文字と小文字を区別する必要があります。

- [ReCAPTCHA の有効化](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html) 自動化されたブルートフォース攻撃から管理者を保護します。

- 割り当て時は、最小権限の原則に従います [管理者権限](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html) 役割および役割を管理者ユーザーアカウントに追加できます。

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Adobe Commerceの最新リリースへのアップグレード**

コードの更新者 [Commerce プロジェクトの最新リリースへのアップグレード](#upgrade-to-the-latest-release) （Adobeが提供するセキュリティパッチ、ホットフィックス、その他のパッチを含む） Adobe Commerce、Commerce サービス、拡張機能の機能。

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **機密性の高い設定値を保護**

使用方法 [設定管理](../../../configuration/cli/set-configuration-values.md) 重要な設定値をロックします。

この `lock config` および `lock env` CLI コマンドは、環境変数を設定して、環境変数が管理者から更新されないようにします。 このコマンドは、値を `<Commerce base dir>/app/etc/env.php` ファイル。 （クラウドインフラストラクチャプロジェクトのCommerceについては、 [ストア構成の管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html#sensitive-data).）

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **セキュリティスキャンの実行**

の使用 [Commerce セキュリティスキャンサービス](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) すべてのAdobe Commerce sites で既知のセキュリティリスクとマルウェアを監視し、新規登録してパッチの更新とセキュリティ通知を受け取るには、次の手順を実行します。

## 拡張機能とカスタムコードのセキュリティを確保する

Adobe Commerce Marketplace からサードパーティの拡張機能を追加してAdobe Commerceを拡張する場合、またはカスタムコードを追加する場合、次のベストプラクティスを適用して、カスタマイズのセキュリティを確保します。

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **セキュリティに精通したパートナーまたはソリューションインテグレーター（SI）を選択する** – 安全な開発手法に従い、セキュリティ上の問題の防止と対処に関して確かな実績を持つ組織を選択することにより、安全な統合とカスタム・コードの安全な配信を確保します。

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **セキュアな拡張機能を使用** – ソリューションインテグレーターまたは開発者に相談して、以下の手順を実行することにより、Commerce デプロイメントに最も適切で安全な拡張機能を特定します [Adobe拡張機能のベストプラクティス](../planning/extensions.md).

- Adobe Commerce Marketplace またはソリューションインテグレーターを通じたソース拡張機能のみ。 拡張機能がインテグレーターを通じて提供されている場合は、インテグレーターが変更した場合に拡張機能ライセンスの所有権が譲渡可能であることを確認します。

- 拡張機能とベンダーの数を制限することで、リスクを軽減します。

- 可能な場合は、Commerce アプリケーションと統合する前に、セキュリティのための拡張機能コードを確認します。

- PHP Extension Developers が、Adobe Commerceの開発ガイドライン、プロセス、およびセキュリティのベストプラクティスに従っていることを確認してください。 特に、開発者は、リモートコードの実行や暗号化の脆弱性を引き起こす可能性のある PHP の機能を使用しないでください。 参照： [セキュリティ](https://developer.adobe.com/commerce/php/best-practices/security/) が含まれる *拡張機能開発者ガイドのベストプラクティス*.

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **監査コード** – 開発の残りについて、サーバーとソースコードリポジトリを確認します。 アクセス可能なログファイル、公開されている.git ディレクトリ、SQL 文を実行するトンネル、データベースダンプ、php 情報ファイル、その他の保護されていない必要のない、攻撃で使用される可能性のあるファイルがないことを確認します。

## 最新リリースへのアップグレード

Adobeは、セキュリティを強化し、潜在的な侵害からお客様をより適切に保護するために、更新されたソリューションコンポーネントを継続的にリリースしています。 Adobe Commerce アプリケーション、インストール済みサービスおよび拡張機能の最新バージョンにアップグレードし、最新のパッチを適用することは、セキュリティの脅威に対する最初かつ最善の防御策です。

Commerceは通常、セキュリティアップデートを四半期ごとにリリースしますが、優先度などの要因に基づいて、主要なセキュリティ上の脅威に対するホットフィックスをリリースする権利を留保します。

使用可能なAdobe Commerceのバージョン、リリースサイクル、アップグレードおよびパッチプロセスについて詳しくは、次のリソースを参照してください。

- [リリース済みバージョン](../../../release/versions.md)
- [製品の可用性](../../../release/product-availability.md) （Adobe Commerce サービスおよびAdobeが作成した拡張機能）
- [Adobe Commerce ライフサイクルポリシー](../../../release/lifecycle-policy.md)
- [アップグレードガイド](../../../upgrade/overview.md)
- [パッチの適用方法](../../../upgrade/patches/overview.md)

>[!TIP]
>
>最新のセキュリティ情報を取得し、をサブスクライブすることで、既知のセキュリティ問題を軽減します。 [Adobeセキュリティ通知サービス](https://www.adobe.com/subscription/adbeSecurityNotifications.html).

## ディザスタリカバリ計画の作成

Commerce サイトが危険にさらされた場合は、包括的なディザスタリカバリ計画を策定して実装することで、被害を抑制し、通常の業務を迅速に復旧します。

障害が原因でCommerce インスタンスを復元する必要があるお客様には、Adobeからバックアップファイルを提供できます。 お客様とソリューションインテグレーターは、該当する場合、復元を実行できます。

Adobeでは、ディザスタリカバリ計画の一環として、次のことを強くお勧めします [Adobe Commerce アプリケーション設定の書き出し](../../../configuration/cli/export-configuration.md) ビジネス継続性の目的で必要な場合に、再導入を容易にします。 設定をファイルシステムにエクスポートする主な理由は、システム設定がデータベース設定よりも優先されるためです。 読み取り専用のファイルシステムでは、アプリケーションを再デプロイして機密性の高い設定を変更し、保護レイヤーを追加する必要があります。

### 追加情報

**クラウドインフラストラクチャにデプロイされたAdobe Commerce**

- [バックアップと障害回復](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)

- [クラウドインフラストラクチャー上のAdobe Commerce用のストア設定の管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)

**Adobe Commerceがオンプレミスにデプロイされました**

- [災害復旧のアイデア](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [バックアップと回復](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [構成設定のエクスポート](../../../configuration/cli/export-configuration.md)

   - [設定を読み込み](../../../configuration/cli/import-configuration.md)

   - [ファイル・システム、メディア、データベースのバックアップとロールバック](../../../installation/tutorials/backup.md)

## 安全なサイトとインフラストラクチャの維持

このセクションでは、Adobe Commerce インストールのサイトおよびインフラストラクチャのセキュリティを維持するためのベストプラクティスの概要を説明します。 これらのベストプラクティスの多くは、コンピューターインフラストラクチャの一般的なセキュリティ保護に重点を置いているので、推奨事項の一部は既に実装されている可能性があります。

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **未認証のアクセスをブロック** – ホスティングパートナーと協力して、Commerce サイトおよびお客様のデータへの不正なアクセスをブロックする VPN トンネルを設定します。 Commerce アプリケーションへの不正アクセスをブロックする SSH トンネルを設定します。

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Web アプリケーションファイアウォールの使用** – トラフィックを分析し、Web アプリケーション ファイアウォールを使用して不明な IP アドレスにクレジット カード情報が送信されるなど、疑わしいパターンを検出します。

クラウドインフラストラクチャにデプロイされたAdobe Commerceのインストールでは、で使用できるビルトイン WAF サービスを使用できます。 [Fastly サービスの統合](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **パスワード セキュリティの詳細設定を構成する**—PCI Data Security Standard の 8.2.4 節で推奨されているように、強力なパスワードを設定し、少なくとも 90 日ごとに変更します。参照： [Admin Security 設定の指定](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html).

![Checklist](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **HTTPS を使用**—Commerce サイトを新たに実装する場合は、HTTPS を使用してサイト全体を起動します。 Googleでは、ランキング要因として HTTPS を使用するだけでなく、HTTPS で保護されていない限り、多くのユーザーはサイトからの購入さえ検討しません。

## マルウェアに対するProtect

e コマースサイトを狙ったマルウェア攻撃は非常に一般的であり、脅威アクターはトランザクションからクレジットカードと個人情報を収集する新しい方法を継続的に開発しています。

しかし、Adobeは、ほとんどのサイトの侵害は革新的なハッカーによるものではないことがわかりました。 むしろ、脅威アクターは、多くの場合、既存のパッチが適用されていない脆弱性、パスワードの不備、ファイルシステム内の所有権と権限の設定の脆弱性を利用します。

最も一般的に経験される攻撃では、悪意のあるコードが顧客ストアの絶対ヘッダーまたは絶対フッターに挿入されます。 コードは、顧客のログイン資格情報やチェックアウトフォームデータなど、顧客がストアフロントに入力するフォームデータを収集します。 その後、このデータは、Commerce バックエンドではなく、悪意のある目的で別の場所に送信されます。 また、マルウェアは、元の支払いフォームを支払いプロバイダーが設定した保護を上書きする偽のフォームに置き換えるコードを管理者に実行させる可能性があります。

クライアントサイドのクレジットカードスキマーは、次の図に示すように、マーチャントの web サイトコンテンツにコードを埋め込み、ユーザーのブラウザーで実行できるマルウェアの一種です。

![e コマースサイトをターゲットとしたマルウェア攻撃のデータフロー](../../../assets/playbooks/malware-data-flow.svg)

ユーザーによるフォームの送信やフィールド値の変更など、特定のアクションが発生した後、スキマーはデータをシリアル化し、サードパーティのエンドポイントに送信します。 これらのエンドポイントは、通常、最終的な宛先にデータを送信するためのリレーとして機能する、その他の侵害された web サイトです。


>[!TIP]
>
>Commerce サイトがマルウェア攻撃の影響を受ける場合は、次のAdobe Commerceのベストプラクティスに従います [セキュリティ上の問題への対応](../maintenance/respond-to-security-incident.md).

### 最も一般的な攻撃を把握

以下は、Commerceのすべてのユーザーが認識し、対策を講じることをAdobeが推奨する攻撃の一般的なカテゴリのリストです。

- **サイトのデファインド** – 攻撃者が、サイトの外観を変更したり、独自のメッセージを追加したりして、Web サイトに損害を与える可能性があります。 サイトやユーザーアカウントへのアクセスは侵害されていますが、多くの場合、支払い情報は安全なままです。

- **ボットネット** – 顧客のCommerce サーバーが、スパムメールを送信するボットネットの一部になる。 通常、ユーザーデータは侵害されませんが、顧客のドメイン名がスパムフィルターでブロックリストに加えるされ、ドメインからのメールの配信が妨げられる可能性があります。 または、お客様のサイトがボットネットの一部になり、別のサイトに対して分散型サービス拒否（DDoS）攻撃を引き起こします。ボットネットは、Commerce サーバーへのインバウンド IP トラフィックをブロックし、お客様が買い物できないようにする可能性があります。

- **直接的なサーバ攻撃** – データが危険にさらされ、バックドアやマルウェアがインストールされ、サイトの運用に影響が及びます。 サーバーに保存されていない支払い情報は、これらの攻撃によって侵害される可能性が低くなります。

- **サイレントカードキャプチャ** – この最も悲惨な攻撃では、侵入者は隠されたマルウェアやカードの取り込みソフトウェアをインストールするか、さらに悪いことに、チェックアウトプロセスを変更してクレジットカードのデータを収集します。 その後、データはダークウェブ上の販売のために別のサイトに送信されます。 このような攻撃は、長期間、気付かれず、顧客アカウントや財務情報の大きな漏洩につながる可能性があります。

- **サイレントキーログ** – 脅威アクターは、管理者ユーザーの資格情報を収集するために、キーログコードを顧客サーバーにインストールします。これにより、ユーザーは検出されることなくログインしたり、他の攻撃を開始したりできます。

### パスワード推測攻撃に対するProtect

ブルートフォースパスワード推測攻撃により、管理者に不正アクセスが行われる可能性があります。 次のベストプラクティスに従って、これらの攻撃からサイトをProtect化します。

- Commerceのインストールに外部からアクセスできるすべてのポイントを特定して保護します。

  管理者へのアクセスを保護できます。管理者は通常、次のAdobeに従って、最も保護が必要です [優先度の高い推奨事項](#priority-recommendations) Commerce プロジェクトの設定時。

- 指定した IP アドレスまたはネットワークからのユーザーのみにアクセスを許可するアクセス制御リストを設定して、Commerce サイトへのアクセスを制御します。

  Fastly Edge ACL をカスタム VCL コードスニペットと共に使用して、着信要求をフィルタリングし、IP アドレスによるアクセスを許可できます。 参照： [リクエストを許可するカスタム VCL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).


  >[!TIP]
  >
  >リモートワーカーを採用している場合は、Commerce サイトへのアクセス権を持つアドレスのリストにリモート社員の IP アドレスが含まれていることを確認してください。

### クリックジャッキング攻撃の防止

Adobeは、 `X-Frame-Options` ストアフロントへのリクエストに含めることができる HTTP リクエストヘッダー。 参照： [クリックジャッキング攻撃の防止](../../../configuration/security/xframe-options.md) が含まれる *Adobe Commerce設定ガイド*.
