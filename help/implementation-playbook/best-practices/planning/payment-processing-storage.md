---
title: 支払い処理と保存のベストプラクティス
description: 支払いの詳細を安全に処理および保存する方法を説明します
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# 支払い処理と保存のベストプラクティス

維持に関する主要な原則の 1 つ [PCI コンプライアンス](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) は、クレジットカードの支払いを適切に処理および保存するための戦略を持っています。

Adobe Commerceへのカード所有者データの格納は **厳禁** これは、支払いカード業界のデータセキュリティ標準 (PCI-DSS) に基づく商人としての義務を侵害する可能性があります。 当社の共有責任モデルと商業債務のガイドラインの詳細は、 [Adobe Commerceの共有責任ガイド](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) Adobeセキュリティセンター

e コマースサイトで支払い情報を適切に処理するのに役立つよう、以下のベストプラクティスに従うことをお勧めします。 全体的なセキュリティのベストプラクティスに関する追加のガイダンスについては、 [Adobe Commerceのセキュリティベストプラクティスガイド](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) Adobe・トラスト・センター

## 影響を受ける製品およびバージョン

[サポートされているすべてのバージョン](../../../release/versions.md) /:

* Adobe Commerce an cloud infrastructure
* Adobe Commerceオンプレミス

## カード所有者データの保護

カード所有者のデータの保存が必要な場合は、カード所有者のデータを保管保護機能を備えたAdobe Commerceの外に保存する必要があります。 クレジットカード所有者データなど、支払いの詳細に対してストレージ保護を適用することで、詐欺や他の潜在的なセキュリティ問題を防ぐことができます。 他の PCI 標準に従って、保護を適用することは、防御の第 1 ラインです。 保存データの保護を強化する推奨される方法には、暗号化、切り捨て、トークン化、一方向ハッシュ、マスキングなどがあります。

暗号鍵の保護は、データ保護戦略にとって不可欠です。 これらのキーを監視するのは、熟練した信頼できる顧客が重要です。

最後に、ストレージ中にプライマリアカウント番号 (PAN) を読み取れなくする必要があります（例：XXX などのマスク）。 これには、フラッシュドライブ、USB、外付けハードドライブなどのポータブルストレージとバックアップメディア、監査ログも含まれます。

## カード所有者データの送信を暗号化する

送信中のデータの保護は、カード所有者のデータなど、支払い情報を保護するための鍵となります。 この情報がオープンネットワーク経由で送信されると、セキュリティ上の問題に対する脆弱性が高まる可能性があります。

### セキュアな送信プロトコルを使用

安全な送信プロトコルと次のような慣行を使用して、カード所有者データを送信します。

* 信頼されたキーと証明書
* セキュアな送信プロトコル（TLS、SSH、VPN など）
* 暗号化の非対称アルゴリズム
* PAN の送信と表示を使用したトークン化、マスキング、侵入テスト
* カード所有者データへのアクセスを制限する
* 機密情報へのアクセスは、ニーズ・トゥ・ナウジングで制限され、ビジネス・ニーズを持つ権限を持つ担当者のみに提供される必要があります。

カード所有者のデータを処理する方法としては、プライマリアカウント番号 (PAN) を保存せず、特定の支払い処理プロバイダーでカードをトークン化し、トークン、カードタイプ、暗号化された有効期限を保存することが推奨されます。 トークンはマーチャントごとにのみ一意なので、将来の使用のために、ファイルの資格情報として使用できます。 トークンは一意なので、セキュリティの問題がある場合、トークンは無効化され、不正なアクティビティを防ぐのに役立ちます

## 追加情報

Adobe別の推奨支払い方法をお探しの場合は、 [Adobe支払サービス](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
