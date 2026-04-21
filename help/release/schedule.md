---
title: パッチリリーススケジュール
description: Adobe Commerce の新しいパッチとセキュリティ修正のリリースに関して、アドビが発表を予定している時期について説明します。
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 0f46bdfd0afbca07e0d60e995ee9426f5408671d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 4%

---


# パッチリリーススケジュール

Adobeでは、製品のアップグレードをシンプルにすることと、予測可能にすることの適切なバランスを常に取りながら、アーリーアダプターにより迅速に改善を提供することに努めています（[ バージョンポリシー](versioning-policy.md)を参照）。

このスケジュールの目的は、AdobeがコアのAdobe Commerce PHP アプリケーションの各サポートされているリリースラインに[ パッチ ](versioning-policy.md#patch-release)のリリースを発表する予定の日付を提供することです。 パッチリリースは、プラットフォームを安全で信頼性の高い、パフォーマンスを維持するために、コアコードベースをアップグレードする機会です。

>[!NOTE]
>
>新機能、クラウドインフラストラクチャ、および拡張性リリースについて詳しくは、[Adobe Commerce サービス ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all) リリースドキュメントを参照してください。

このページに記載されている予定されている品質、セキュリティ、ベータ版パッチに加えて、Adobeは[品質パッチツール ](versioning-policy.md#individual-patch)を通じて[個々のパッチ ](../tools/quality-patches-tool/usage.md)へのアクセスを提供します。 このツールを使用すると、インストールされているバージョンのAdobe Commerceで使用できるすべての個々のパッチに関する一般的な情報を適用、取り消し、表示できます。

Adobe Commerce パッチリリースは、次のガイドラインに基づいてリリースされます。

- **個別のセキュリティ パッチ ファイル** – 個別の累積以外の[ セキュリティ パッチ ファイル ](versioning-policy.md#isolated-security-patch-file)は、より迅速な修正を可能にするために個別にリリースされ、次の完全なセキュリティ パッチに組み込まれます。 分離されたセキュリティパッチファイルを適用するには、分離されたセキュリティ修正プログラムはそのバージョンに対してのみテストされるので、お客様はサポートされているリリースラインの最新のセキュリティ専用パッチリリース（最新の – p バージョン）に属している必要があります。

- **セキュリティパッチ** – 最低でも、[ サポートされているすべての](versioning-policy.md#security-patch-release) リリースラインについて、[ セキュリティパッチ ](lifecycle-policy.md)が毎年リリースされます。 これらのパッチには、以前にリリースされたすべてのセキュリティ、コンプライアンス、品質のホットフィックスが含まれます。  Adobeは、必要に応じて追加のセキュリティパッチをリリースする場合がありますが、保証されていません。

- **パッチ** - Adobe Commerce 2.4.x LTS リリースライン （3年間のサポート期間）の[ パッチ ](versioning-policy.md#patch-release)が毎年（5月）リリースされます。

- Adobe Commerce 2.4.x LTS リリースライン用の&#x200B;**Alpha パッチ**-One [ アルファパッチ ](versioning-policy.md#alpha-patch-release)が毎年リリースされます。

- **Beta パッチ** - Adobe Commerce 2.4.x LTS リリースラインの[ ベータパッチ ](versioning-policy.md#beta-patch-release)が毎年1つリリースされます。

詳しくは、次の画像を参照してください。

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![2026 Adobe Commerce リリースカレンダー](../assets/release/release-calendar.png)


## リリース通知チャネル

Adobeは、次のチャネルを通じて、新しいパッチリリースについてお客様に通知します。

- [Adobeのセキュリティ情報とアドバイザリー](https://helpx.adobe.com/security/security-bulletin.html#magento)
- メール
- 製品内アラート

>[!NOTE]
>
> マイナー、パッチ、セキュリティの各リリースのリリース日と、通常のサポートの終了日については、[ リリース済みバージョン ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions)を参照してください。
