---
title: 一般的な開発のベストプラクティス
description: Adobe Commerce プロジェクトを開発するための一般的なベストプラクティスについて説明します。
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 68dc4635df9fc411925fe0d48a578edece8895dc
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Adobe Commerceの一般的な開発のベストプラクティス

ここでは、健全なAdobe Commerce開発プロセスのベースラインについて説明します。 開発者をガイドするための基本的なプロセス、コーディングの原則およびアプリケーション設計の原則について説明します。

>[!NOTE]
>
>Adobeテクニカルアーキテクトは、開発を含むエンゲージメントの際の参考としてこれらのベストプラクティスを使用します。

これらのベストプラクティスは、Commerce プロジェクトの開発および提供に関する長年の経験に基づいて開発されています。 Adobeは、技術的な取り組みがこれらのベストプラクティスに従い、既存のプロセスとコードをそれらに合わせて改善することをお勧めします。

## テキスト規則

このトピックにおける「必須」、「必須」、「必須」、「必須」、「必須」、「必須」、「必須」、「必須」、「推奨」、「MAY」、「オプション」のキーワードは、[RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119) で説明されているように解釈される。

## プロセス

1. プロジェクトアクティビティを開始する前に、定義済みのプロジェクト手法について合意する必要があります。 定義されている限り、スクラム、ウォーターフォール、その他の方法や方法論の組み合わせにすることができます。
1. 開発チームがバージョン管理システムのブランチ戦略を使用できるようになるまで、開発を開始しないでください。
1. 技術仕様の承認、ユーザーストーリーとユースケースの承認、テストケースの承認が開発チームに提供されるまで、開発を開始しないでください。
1. 少なくとも開発環境と QA 環境が使用可能になるまで、開発を開始しないでください。
1. 開発の開始に必須のプロジェクト固有の要件は、_準備完了の定義_ に記載されている場合があります。
1. サインオフは、プロジェクト成果物のサインオフを許可されたクライアント担当者が行う必要があります。
1. アジャイルプロジェクトの方法論では、承認の後に追加の要件が生じる場合があります。 これらの要件は、新しい要件として扱い、それに応じて取得、構築、計画する必要があります。
1. すべての開発は、送信前に開発者によって機能的にテストされる必要があります。
1. すべての開発は、コードレビューのために送信される前に、自動テストに合格する必要があります。 これは、プルリクエスト作成後の自動プロセスとして設定できます。
1. すべての開発は、品質保証のために送信される前に、テクニカルアーキテクトまたはリード開発者による手動のコードレビューに合格する必要があります。
1. すべての開発は、クライアントに配信する前に品質保証を渡す必要があります。
1. 配信に必須のプロジェクト固有の要件は、「完了の定義」に記載されている場合があります。

## 0.5511122

1. すべての開発者は同じ IDE を使用する必要があります。 PhpStorm は、Adobe Commerceの開発に推奨される IDE です。
1. すべての開発者は、（将来の）実稼動サーバーで使用されるのと同じテクノロジースタックを使用して開発およびテストする必要があります。 このテクノロジースタック内のソフトウェアのバージョンは、実稼動サーバーにインストールされているソフトウェアのメジャーバージョンおよびマイナーバージョンと一致する必要があります。 Adobe Commerceの一般的なテクノロジースタックについて詳しくは、[ システム要件 ](../../../installation/system-requirements.md) を参照してください。
1. システム管理者またはテクニカルアーキテクトは、一元管理されたローカル開発環境をチームに提供して、同じ最新のローカル環境を確保および促進できます。
1. 開発者と QA エンジニアは、QA 環境のコマンドライン、データベース、ログファイルにアクセスできる必要があります。 VPN 接続が必要になる場合があります。

## バージョン管理

モジュールバージョンは、[Semantic Versioning 2.0.0 標準 ](https://semver.org/) に準拠する必要があります。
Adobe Commerce コードベースの依存関係は、[ モジュールバージョンの依存関係のガイドライン ](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) に従う必要があります。

## リビジョン管理

コミットには、意味のあるコミットメッセージを付ける必要があります。

## セキュリティ

1. [ セキュアでない関数 ](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) を使用しないでください。
1. [XSS 予防戦略 ](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) を適用すべきである。
1. [ コンテンツセキュリティポリシー ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) を適用する必要があります。
1. 新しいAdobe Commerce インスタンスは、「セキュリティ修正の終了」の日付に達していないバージョンの最新のセキュリティリリースに提供する必要があります。 [Adobe Commerce ソフトウェア ライフサイクル ポリシー ](../../../release/lifecycle-policy.md) を参照してください。
