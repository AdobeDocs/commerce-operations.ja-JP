---
title: リリースポリシー
description: マイナー、パッチ、セキュリティパッチ、機能、ホットフィックス、個別パッチ、カスタムパッチなど、様々なタイプのAdobe Commerce リリースについて説明します。
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: b5d120893668f4315e289a204649270db4f7a6bc
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Adobe Commerce リリースポリシー

Adobe Commerceでは、個々のモジュールレベル（`magento/framework 101.1.1` など）で [ セマンティックバージョニング ](https://semver.org/) を使用しますが、マーケティングバージョン番号には使用しません。 例：

- **メジャーリリース**-2
- **マイナーリリース**-2.4
- **PATCHリリース**—2.4.5
   - **セキュリティパッチリリース**—2.4.5-p1
      - セキュリティバグ修正
      - セキュリティの強化
- **BETA パッチリリース**—2.4.7-beta2
- **拡張性、インフラストラクチャ、サービスのリリース**
- **ホットフィックス**
- **個別パッチ**
- **カスタムパッチ**

## マイナーリリース

マイナーリリースには、次のガイドラインが適用されます。

- 重大な変更が行われる可能性があります。Adobe Commerce 2.2.x 用に記述されたコードは、Adobe Commerce 2.3.x では動作しなくなる場合があります。例えば、マイナーリリースでは、PHP のような主要なシステム要件や依存関係のサポートが導入される可能性があります。
- モジュールのバージョンは異なる場合があります。 例えば、新しいパッチで導入されるモジュール変更もあれば、マイナーリリースで導入されるモジュール変更もあります。
- マイナーリリースには、互換性を確保するために、アップグレード中にユーザーまたはソリューションパートナーによる追加作業が必要になる可能性のある新機能が含まれる場合があります。
- マイナーリリースには、セキュリティと品質の問題に対する修正が含まれている場合があります。

## PATCHリリース

パッチリリースは、主に、セキュリティ、パフォーマンス、コンプライアンス、優先度の高い品質修正を提供し、サイトのパフォーマンスをピーク時に維持するのに役立ちます。

パッチリリースには、次のガイドラインが適用されます。

- 最新のサポート対象のマイナーリリースでは、機能品質の完全な修正と機能強化が行われています。
- 拡張機能やコードの互換性を損なう可能性のある変更は避けます。 例えば、バージョン 2.2.0 用に記述されたコードは、バージョン 2.2.7 でも機能します。
- 例外的に、セキュリティやコンプライアンスの問題、および影響の大きい品質の問題に対処するために、重大な変更や追加のパッチまたはホットフィックスがリリースされる場合があります。 モジュールレベルでは、これらのほとんどはPATCHレベルの変更です。時にはマイナーレベルの変更もあります。

### セキュリティパッチリリース

{{$include /help/_includes/security-patch-release-overview.md}}

## BETA パッチリリース

Adobe Commerce機能の一般提供より前のリリースは、すべてのAdobe Commerceのお客様およびAdobeパートナーが公開しています。 これにより、一般公開まで、コードと影響を受けるコンポーネントのレビューに時間がかかります。

Beta リリースには不具合が含まれる場合があり、いかなる保証もなく「現状のまま」提供されます。 Adobeは、（Adobeサポートサービスまたはその他の方法を通じて）Beta リリースを保守、修正、更新、変更、変更、その他の方法でサポートする義務を負いません。 お客様は、Beta リリース、およびそれに付随するドキュメントや資料の正しい機能やパフォーマンスに対して、注意を払い、いかなる形でも依存しないことをお勧めします。 したがって、Beta リリースの使用は、すべて顧客自身の責任で行うものとします。

## 機能、クラウドインフラストラクチャおよび拡張リリース

クラウドインフラストラクチャと機能リリースには、パッチリリースとは別に、独立したサービスとして提供される新機能と機能アップデートが含まれています。 例えば、クラウドホスティングサービスとインフラストラクチャ、B2B、SaaS 製品（カタログサービス、データ接続、製品Recommendations、ライブ検索）、拡張機能テクノロジー（API メッシュ、Integration Starter Kit、イベント）の更新などがあります。

## ホットフィックス

ホットフィックスは、多くのマーチャントに影響を与えるゼロデイ脆弱性の修正など、影響の大きいセキュリティ修正や品質修正を含むパッチです。 Adobeリリース必要に応じて、Adobe Commerce バージョンのホットフィックスが引き続きサポートされ、セキュリティや品質に関する重大な問題の影響を受けます。 ホットフィックスは、ナレッジベースの [ 既知の問題 ](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) セクションに公開されています。 これらの修正は、次回の予定パッチリリースに含まれています。

>[!NOTE]
>
>ホットフィックスには、後方互換性のない変更が含まれている場合があります。

## 個々のパッチ

個々のパッチには、特定の問題に対する影響の低い品質修正が含まれています。 これらの修正は、サポートされているAdobe Commerceのマイナーバージョンに適用されます。 Adobeでは、アドビの [ ソフトウェアライフサイクルポリシー ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf) に従って、Adobe Commerceで必要になる個々のパッチをリリースしています。

>[!NOTE]
>
>個々のパッチには、後方互換性のない変更は含まれません。

## 分離パッチ

最新のセキュリティ専用パッチまたは今後リリースされるセキュリティ専用パッチに含まれるスタンドアロン修正が含まれています。このパッチは迅速な実装のために個別にリリースされます。

## カスタムパッチ

Adobe以外の担当者が、様々な理由で問題を修正したり、Adobe Commerce コードを変更したりするために作成します。 カスタムパッチは、[Quality Patches Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) を通じて提供されます。
