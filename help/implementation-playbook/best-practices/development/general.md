---
title: 一般的な開発のベストプラクティス
description: Adobe Commerceプロジェクトの開発に関する一般的なベストプラクティスについて説明します。
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Adobe Commerceの一般的な開発のベストプラクティス

ここでは、健全なAdobe Commerce開発プロセスのベースラインについて説明します。 開発者を導くための基本的なプロセス、コーディング原則およびアプリケーション設計原則について説明します。

>[!NOTE]
>
>Adobeの技術アーキテクトは、開発に関するエンゲージメントの際に、これらのベストプラクティスを参考にします。

これらのベストプラクティスは、長年にわたるコマースプロジェクトの開発と提供の経験に基づいて開発されています。 Adobeでは、技術的な取り組みについて、次のベストプラクティスに従い、既存のプロセスやコードを改善してそれに合わせることをお勧めします。

## テキストの規則

このトピックのキーワード「MUST」、「MUST NOT」、「REQUIRED」、「SHALL」、「SHOULD NOT」、「SHOULD NOT」、「RECOMMENDED」、「MAY」、「OPTIONAL」は、 [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## プロセス

1. プロジェクト活動を開始する前に、定義されたプロジェクト手法について合意が必要です。 スクラム、ウォーターフォール、その他の方法論や組み合わせが定義されている限り、その方法論を使用できます。
1. 開発チームがバージョン管理システムの分岐戦略を利用できるようになるまで、開発を開始しないでください。
1. 開発は、技術仕様、ユーザー事例、ユースケースに対するサインオフ、およびテストケースに対するサインオフが開発チームに提供されるまで、開発を開始しないでください。
1. 開発と QA 環境が利用可能になるまで、開発を開始しないでください。
1. 開発を開始するために必須のプロジェクト固有の要件は、 _準備完了の定義_.
1. 承認プロジェクトの成果物に対する承認を受けたクライアント担当者が、承認を受ける必要があります。
1. アジャイルプロジェクトの手法では、サインオフに従って追加の要件が必要になる場合があります。 これらの要件は新しい要件として扱われ、それに応じて取得、設計、計画される必要があります。
1. すべての開発は、提出前に開発者が機能的にテストする必要があります。
1. すべての開発は、コードレビュー用に送信される前に、自動化されたテストに合格する必要があります。 この設定は、プルリクエスト作成後の自動プロセスとして設定できます。
1. すべての開発は、品質保証のために提出される前に、テクニカルアーキテクトまたはリード開発者による手動でのコードレビューに合格する必要があります。
1. すべての開発は、クライアントに配信する前に品質保証に合格する必要があります。
1. 配信に必須のプロジェクト固有の要件については、「完了の定義」に記載されている場合があります。

## 環境

1. すべての開発者は同じ IDE を使用する必要があります。 PhpStorm は、Adobe Commerce開発に推奨される IDE です。
1. すべての開発者は、（将来の）実稼動サーバで使用されるのと同じテクノロジースタックを使用して開発およびテストを行う必要があります。 このテクノロジースタック内のソフトウェアのバージョンは、本番サーバーにインストールされているソフトウェアのメジャーバージョンとマイナーバージョンと一致する必要があります。 詳しくは、 [システム要件](../../../installation/system-requirements.md) Adobe Commerceの典型的なテクノロジースタックの詳細。
1. システム管理者またはテクニカルアーキテクトは、同じ最新のローカル環境を保証し、促進するために、一元的に管理されたローカル開発環境をチームに提供できます。
1. 開発者と QA エンジニアは、QA 環境のコマンドライン、データベース、ログファイルにアクセスできる必要があります。 この場合、VPN 接続が必要になる可能性があります。

## コーディング規格

1. すべてのコードは、アーキテクチャ、手法、コーディング規格の規則に従う必要があります。 創造性は形ではなく、機能で求められる。
1. すべてのコードは、 [Adobe Commerce Architecture ガイド](https://developer.adobe.com/commerce/php/architecture/){target="_blank}.
1. すべてのコードは、 [Adobe Commerce Coding Standards](https://developer.adobe.com/commerce/php/coding-standards/).
1. すべてのコードは、 [Adobe Commerce Technical Guidelines](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).
1. すべてのコードで、 [Adobe Commerce Best Practices](../phases.md)（該当する場合）
1. すべてのコードは、 [PHP-Framework Interoperability Group(FIG) 規格](https://www.php-fig.org/).
1. 可能な限り、次の操作をおこなうことをお勧めします。 [Adobe Commerce Technical Visions](https://developer.adobe.com/commerce/php/architecture/technical-vision/) を考慮に入れます。
1. 外部システムとの統合には、ビジネスプロセスを検証する統合テストが必要です。
1. すべてのモジュールは、テスト対象になるはずです。 正確にテストすべきものは、テクニカルアーキテクトまたはリード開発者と協力して開発チームが決定する必要があります。 この決定は、定量的な測定ではなく定性的な測定に基づくべきです。コードカバレッジの割合が高いとは、成功の指標ではなく、また、コードの質が高いことを意味するものでもありません。 むしろ、プログラムのその部分でのリグレッションの確率と重大度を評価することで、コードの一部をカバーしないリスクを判断します。

## バージョン管理

モジュールのバージョンは、 [セマンティックバージョン管理 2.0.0 標準](https://semver.org/).
Adobe Commerceコードベースへの依存関係は、 [モジュールバージョンの依存関係のガイドライン](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## リビジョン管理

コミットには、意味のあるコミットメッセージが付随する必要があります。

## セキュリティ

1. [非セキュア関数](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) 使用しないでください。
1. [XSS 防止戦略](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) 適用する必要があります。
1. [コンテンツセキュリティポリシー](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) 適用する必要があります。
1. 新しいAdobe Commerceインスタンスは、「セキュリティの修正終了」の日付に達していないバージョンの最新のセキュリティリリースに配信される必要があります。 詳しくは、 [Adobe Commerce Software Lifecycle Policy](../../../release/lifecycle-policy.md).
