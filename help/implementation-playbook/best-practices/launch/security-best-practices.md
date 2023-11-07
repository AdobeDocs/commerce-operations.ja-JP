---
title: コマースサイトとインフラストラクチャを保護
description: Adobe Commerceインストールをセットアップ、設定および更新する際のセキュリティのベストプラクティスを実装して、セキュリティを維持します。
feature: Best Practices
source-git-commit: cea5868ee37317ae9adfd8b580cd38c33c19761e
workflow-type: tm+mt
source-wordcount: '2151'
ht-degree: 0%

---


# コマースサイトとインフラストラクチャを保護

クラウドインフラストラクチャ上にデプロイされたAdobe Commerceプロジェクトの安全な環境を確立し、維持することは、Adobe Commerceのお客様、ソリューションパートナーおよびAdobeの間で共有される責任です。 このガイドの目的は、お客様側での数式のベストプラクティスを提供することです。

すべてのセキュリティリスクを排除することはできませんが、これらのベストプラクティスを適用すると、Commerce インストールのセキュリティ姿勢が強化されます。 安全なサイトとインフラストラクチャは、悪意のある攻撃の対象としての魅力を低くし、ソリューションとお客様の機密情報のセキュリティを確保し、サイトの中断やコストの高い調査を引き起こすセキュリティ関連のインシデントを最小限に抑えます。

>[!NOTE]
>
>クラウドインフラストラクチャ上でAdobe Commerceプロジェクトを保護および保守するための役割と責務について詳しくは、 [共有職責ガイド](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) 」と入力します。Adobeセキュリティセンター

[サポートされているすべてのバージョン](../../../release/versions.md) /:

- Adobe Commerce an cloud infrastructure
- Adobe Commerceオンプレミス

## 優先度の推奨事項

Adobeは、すべての顧客にとって、次のレコメンデーションが最も優先されると考えます。 すべての Commerce デプロイメントで、次の主要なセキュリティのベストプラクティスを実装します。

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **管理者とすべての SSH 接続に対する 2 要素認証の有効化**

- [コマース管理者のセキュリティ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html)

- [セキュアな SSH 接続](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html) （クラウドインフラストラクチャ）

プロジェクトで MFA を有効にした場合、SSH アクセスを使用する Cloud Infrastructure アカウント上のすべてのAdobe Commerceは、認証ワークフローに従う必要があります。 このワークフローで環境にアクセスするには、2 要素認証 (2FA) コードか、API トークンと SSH 証明書が必要です。

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **管理者の保護**

- [デフォルト以外の管理 URL の設定](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html#use-a-custom-admin-url) デフォルトの `admin` または一般的な用語 `backend`. この設定により、サイトへの不正なアクセスを試みるスクリプトの危険性が低下します。

- [セキュリティの詳細設定](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html) — 秘密鍵を URL に追加し、パスワードの大文字と小文字を区別する必要があり、管理者セッションの長さ、パスワードの有効期間、および管理者ユーザーアカウントをロックする前に許可されるログイン試行回数を制限します。 セキュリティを強化するには、現在のセッションが期限切れになるまでのキーボードの操作が実行されない時間を設定し、ユーザー名とパスワードで大文字と小文字を区別する必要があります。

- [ReCAPTCHA を有効にする](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html) 管理者を自動ブルートフォース攻撃から守るために。

- 割り当て時に最小権限の原則に従う [管理者権限](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html) を管理者ユーザーアカウントに追加します。

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Adobe Commerceの最新リリースへのアップグレード**

コードをで更新しておく [コマースプロジェクトを最新リリースにアップグレード中](#upgrade-to-the-latest-release) Adobe Commerce、Commerce Services、拡張機能 ( セキュリティパッチ、ホットフィックス、およびAdobeが提供するその他のパッチを含む )。

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **機密の高い設定値の保護**

用途 [設定管理](../../../configuration/cli/set-configuration-values.md) 重要な設定値をロックします。

The `lock config` および `lock env` CLI コマンドは、環境変数を設定して、管理者からの更新を防ぎます。 このコマンドは、値を `<Commerce base dir>/app/etc/env.php` ファイル。 ( クラウドインフラストラクチャプロジェクトでのコマースについては、 [ストア設定管理](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html#sensitive-data).)

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **セキュリティスキャンを実行する**

以下を使用します。 [Commerce Security Scan サービス](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) すべてのAdobe CommerceおよびMagento Open Sourceサイトで既知のセキュリティリスクとマルウェアを監視し、新規登録してパッチの更新とセキュリティ通知を受け取るには、次の手順に従います。

## 拡張機能とカスタムコードのセキュリティを確保する

Adobe Commerce Marketplace からサードパーティの拡張機能を追加してAdobe Commerceを拡張する場合、またはカスタムコードを追加する場合は、次のベストプラクティスを適用して、これらのカスタマイズのセキュリティを確保してください。

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **セキュリティに精通したパートナーまたはソリューションインテグレータ (SI) を選択** — 安全な開発慣行に従い、セキュリティ上の問題の回避と対処に関する確実な記録を持つ組織を選択することで、安全な統合とカスタムコードの安全な配信を確保します。

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **セキュアな拡張機能を使用** — ソリューションインテグレーターまたは開発者と相談し、次の手順に従って、コマースの導入に最も適した安全な拡張を特定します。 [Adobe拡張機能のベストプラクティス](../planning/extensions.md).

- Adobe Commerce Marketplace またはソリューションインテグレーターを通じて、のソース拡張機能のみ。 拡張機能がインテグレーターを通じて提供されている場合は、インテグレーターが変更された場合に備えて、拡張機能ライセンスの所有権が譲渡可能であることを確認します。

- 拡張機能とベンダーの数を制限することで、リスクを軽減します。

- 可能な場合は、拡張コードを確認してセキュリティを確保してから、コマースアプリケーションとの統合をおこなってください。

- PHP 拡張機能の開発者が、Adobe Commerceの開発ガイドライン、プロセス、セキュリティのベストプラクティスに従っていることを確認します。 特に、開発者は、リモートコードの実行や暗号化の脆弱性を引き起こす可能性のある PHP 機能を使用しないようにする必要があります。 詳しくは、 [セキュリティ](https://developer.adobe.com/commerce/php/best-practices/security/) （内） *拡張機能開発者ガイドのベストプラクティス*.

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **監査コード** — サーバーとソースコードリポジトリで開発の残り物を確認します。 アクセス可能なログファイル、公開されている.git ディレクトリ、SQL 文を実行するトンネル、データベースダンプ、php 情報ファイル、または不要な非保護ファイルがなく、攻撃で使用される可能性があることを確認します。

## 最新リリースへのアップグレード

Adobeは、セキュリティを強化し、妥協の可能性に対するお客様の保護を強化するために、更新されたソリューションコンポーネントを継続的にリリースしています。 最新バージョンのAdobe Commerceアプリケーション、インストール済みのサービス、拡張機能にアップグレードし、現在のパッチを適用することは、セキュリティ上の脅威に対する最も優れた防御方法です。

Commerce は通常、セキュリティの更新を四半期単位でリリースしますが、優先度やその他の要因に基づく主要なセキュリティ上の脅威に対するホットフィックスをリリースする権利を留保します。

使用可能なAdobe Commerceバージョン、リリースサイクル、およびアップグレードとパッチのプロセスについては、次のリソースを参照してください。

- [リリースされたバージョン](../../../release/versions.md)
- [製品の可用性](../../../release/product-availability.md) (Adobe Commerce services およびAdobeが作成した拡張機能 )
- [Adobe Commerceライフサイクルポリシー](../../../release/lifecycle-policy.md)
- [アップグレードガイド](../../../upgrade/overview.md)
- [パッチの適用方法](../../../upgrade/patches/overview.md)

>[!TIP]
>
>最新のセキュリティ情報を取得し、既知のセキュリティの問題に対する対策を行うには、 [Adobeセキュリティ通知サービス](https://www.adobe.com/subscription/adbeSecurityNotifications.html).

## 災害復旧プランの作成

コマースサイトに問題が発生した場合は、包括的な災害復旧プランを策定し、実装することで、損害を抑え、通常の業務を迅速に復元します。

障害が発生したためにコマースインスタンスの復元が必要な場合、Adobeはお客様にバックアップファイルを提供できます。 お客様およびソリューションインテグレーターは、該当する場合は、リストアを実行できます。

災害復旧プランの一環として、Adobeはお客様に強くお勧めします。 [Adobe Commerceアプリケーション設定の書き出し](../../../configuration/cli/export-configuration.md) ビジネス継続性のために必要な場合に、再導入を容易にする。 構成をファイルシステムに書き出す主な理由は、システム構成がデータベース構成よりも優先されるためです。 読み取り専用のファイル・システムでは、アプリケーションを再デプロイして、機密性の高い構成設定を変更し、保護を強化する必要があります。

### 追加情報

**Adobe Commerceをクラウドインフラストラクチャに導入**

- [バックアップと災害復旧](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#backup-and-disaster-recovery)

- [クラウドインフラストラクチャ上のAdobe Commerceの設定管理を保存](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html)

**Adobe Commerceはオンプレミスで導入されました**

- [災害復旧のアイデア](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [バックアップとリカバリ](../../infrastructure/self-hosting/disaster-recovery-ideas.md)

- [書き出し設定](../../../configuration/cli/export-configuration.md)

   - [設定を読み込み](../../../configuration/cli/import-configuration.md)

   - [ファイル・システム、メディア、データベースのバックアップとロールバック](../../../installation/tutorials/backup.md)

## 安全なサイトとインフラストラクチャの維持

この節では、Adobe Commerceのインストールでサイトとインフラストラクチャのセキュリティを維持するためのベストプラクティスについてまとめます。 これらのベストプラクティスの多くは、コンピューターインフラストラクチャの一般的な保護に焦点を当てているので、推奨事項の一部は既に実装されている可能性があります。

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **不正なアクセスをブロックする** — ホスティングパートナーと協力して、コマースサイトおよび顧客データへの不正なアクセスをブロックする VPN トンネルを設定します。 コマースアプリケーションへの不正なアクセスをブロックする SSH トンネルを設定します。

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Web アプリケーションファイアウォールを使用する** — トラフィックを分析し、Web アプリケーションファイアウォールを使用して、不明な IP アドレスにクレジットカード情報が送信されるなど、疑わしいパターンを見つけます。

クラウドインフラストラクチャにデプロイされたAdobe Commerceのインストールでは、 [Fastly サービスの統合](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **詳細なパスワードセキュリティ設定の構成**—8.2.4 節の PCI Data Security Standard で推奨されているように、堅牢なパスワードを設定し、少なくとも 90 日ごとに変更します。詳しくは、 [管理者セキュリティ設定の構成](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html).

![チェックリスト](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **HTTPS を使用** — コマースサイトが新しく実装されている場合は、HTTPS を使用してサイト全体を起動します。 Googleは HTTPS をランキング要因として使用するだけでなく、HTTPS で保護されていない限り、多くのユーザーはサイトからの購入を検討しません。

## Protect — マルウェア

e コマースサイトを対象としたマルウェア攻撃はすべてあまりにも一般的で、脅威の要因は常に新しい方法でクレジットカードと個人情報を取り込むためのトランザクションからの新しい方法を開発しています。

しかし、Adobeは、サイトの侵害の多くは革新的なハッカーによるものではないことを発見しました。 むしろ、脅威要因は、ファイルシステム内の既存の、パッチが適用されていない脆弱性、パスワードの不足、所有権と権限の弱い設定を利用します。

最も一般的な攻撃では、悪意のあるコードがカスタマーストアの絶対ヘッダーまたは絶対フッターに挿入されます。 ここでは、顧客ログイン資格情報やチェックアウトフォームデータなど、顧客がストアフロントに入力したフォームデータを収集します。 その後、このデータは悪意のある目的で Commerce バックエンドではなく別の場所に送信されます。 また、マルウェアは、元の支払いフォームを、支払いプロバイダーが設定した保護を上書きする偽のフォームで置き換えるコードを管理者が実行するように強制する可能性があります。

クライアントサイドクレジットカードのスキマーとは、次の図に示すように、ユーザーのブラウザーで実行できるマーチャント Web サイトコンテンツにコードを埋め込んだマルウェアの一種です。
ユーザーがフォームを送信したり、フィールド値の変更などのアクションが発生すると、スキマーはデータをシリアル化して、サードパーティのエンドポイントに送信します。 これらのエンドポイントは、通常、問題が発生し、データを最終的な宛先に送信するリレーとして機能する、他の Web サイトです。

![e コマースサイトをターゲットにしたマルウェア攻撃のデータフロー](../../../assets/playbooks/malware-data-flow.svg)

ユーザーがフォームを送信したり、フィールド値の変更などのアクションが発生すると、スキマーはデータをシリアル化して、サードパーティのエンドポイントに送信します。 これらのエンドポイントは、通常、問題が発生し、データを最終的な宛先に送信するリレーとして機能する、他の Web サイトです。


コマースサイトが攻撃された場合は、Adobe Commerceのベストプラクティスに従って、 [治安事件への対応](../maintenance/respond-to-security-incident.md).

### 最も一般的な攻撃を把握する

以下に、Commerce のすべてのお客様が認識し、保護対策を講じることをAdobeが推奨する一般的な攻撃カテゴリを示します。

- **サイトの廃止** — 攻撃者は、サイトの外観を変更したり、独自のメッセージを追加したりして、Web サイトに損害を与えます。 サイトおよびユーザーアカウントへのアクセスは侵害されていますが、支払い情報は安全なままです。

- **ボットネット** — 顧客のコマースサーバーが、スパムメールを送信するボットネットの一部になります。 通常、ユーザーデータは侵害されませんが、お客様のドメイン名はスパムフィルターによってさブロックリストに加えるれ、ドメインからの E メールの配信を防ぐことができます。 または、お客様のサイトがボットネットの一部となり、別のサイトで分散型 DoS(DoS) 攻撃が発生します。ボットネットは、コマースサーバーへのインバウンド IP トラフィックをブロックし、顧客が買い物をできなくなる場合があります。

- **ダイレクトサーバー攻撃** — データが漏洩し、バックドアとマルウェアがインストールされ、サイトの操作に影響が及びます。 サーバーに保存されていない支払い情報は、これらの攻撃によって侵害される可能性が低くなります。

- **サイレントカードのキャプチャ** — この最も悲惨な攻撃では、侵入者は隠されたマルウェアやカードキャプチャソフトウェアをインストールするか、さらに悪いことに、クレジットカードデータを収集するためのチェックアウトプロセスを変更します。 次に、データが別のサイトに送信され、ダークウェブで販売されます。 このような攻撃は、長期間にわたって注目を浴びることがなく、お客様のアカウントや財務情報が大幅に侵害される可能性があります。

- **サイレントキーログ** — 脅威アクターは、顧客サーバーにキーログコードをインストールして管理者ユーザーの資格情報を収集し、検出されることなくログインして他の攻撃を開始できます。

### Protect（パスワード推測攻撃に対する）

Brute Force パスワード推測攻撃は、不正な管理者アクセスを引き起こす可能性があります。 次のベストプラクティスに従って、これらの攻撃からサイトをProtectに移行します。

- コマースのインストールが外部からアクセスできるすべてのポイントを特定し、保護します。

  管理者へのアクセスを保護できます。通常は最も保護が必要ですが、Adobeの [優先事項](#priority-recommendations) コマースプロジェクトを設定する際に使用します。

- 指定した IP アドレスまたはネットワークからのユーザーへのアクセスのみを許可するアクセス制御リストを設定して、コマースサイトへのアクセスを制御します。

  カスタム VCL コードスニペットを使用して Fastly Edge ACL を使用し、受信リクエストをフィルタリングし、IP アドレスでアクセスを許可できます。 詳しくは、 [リクエストを許可するカスタム VCL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).


  >[!TIP]
  >
  >リモートワーカーを使用する場合は、リモート従業員の IP アドレスが、コマースサイトへのアクセス権を持つアドレスのリストに含まれていることを確認します。

### クリックジャックの悪用を防ぐ

Adobeは、 `X-Frame-Options` ストアフロントへのリクエストに含めることができる HTTP リクエストヘッダー。 詳しくは、 [クリックジャックの悪用を防ぐ](../../../configuration/security/xframe-options.md) （内） *Adobe Commerce設定ガイド*.
