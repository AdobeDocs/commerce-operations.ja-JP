---
title: パッチリリーススケジュール
description: Adobe Commerce の新しいパッチとセキュリティ修正のリリースに関して、アドビが発表を予定している時期について説明します。
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: a423b2a2f4938f81db0da3706ba6fa240e53b1b3
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 5%

---


# パッチリリーススケジュール

Adobeは、製品のアップグレードをシンプルで予測可能なものにすると同時に、早期導入者に対して改善をより迅速に提供することの間で、適切なバランスを継続的に見つけ出そうと努めています（[&#x200B; バージョンポリシー &#x200B;](versioning-policy.md) を参照）。

このスケジュールの目的は、Adobeがコア Adobe Commerce PHP アプリケーションのサポート対象の各リリースラインに対して [&#x200B; パッチ &#x200B;](versioning-policy.md#patch-release) のリリースを発表する予定の日付を指定することです。 パッチリリースは、プラットフォームの安全性、信頼性、パフォーマンスを維持するために、コアコードベースをアップグレードする機会です。

>[!NOTE]
>
>新機能、クラウドインフラストラクチャ、拡張機能リリースについて詳しくは、[Adobe Commerce サービス &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all) リリースドキュメントを参照してください。

このページにリストされているスケジュールされた品質、セキュリティ、ベータ版のパッチに加えて、Adobeでは [Quality Patches Tool](versioning-policy.md#individual-patch) を通じて [&#x200B; 個別パッチ &#x200B;](../tools/quality-patches-tool/usage.md) にアクセスできます。 このツールを使用すると、インストールされているバージョンのAdobe Commerceで使用可能な個々のパッチに関する一般情報を適用、元に戻して表示できます。

Adobe Commerce パッチリリースは、次のガイドラインに基づいてリリースされています。

- **分離されたセキュリティ修正** – 累積的でない個々の [&#x200B; セキュリティ修正 &#x200B;](versioning-policy.md#isolated-patch) が必要に応じてリリースされ、すべての [&#x200B; サポートされている &#x200B;](lifecycle-policy.md) リリース行のセキュリティ修正が含まれています（通常のサポートと拡張サポートを含む）。

- **セキュリティパッチ** – 最小限の場合、[&#x200B; セキュリティパッチ &#x200B;](versioning-policy.md#security-patch-release) は、すべての [&#x200B; サポート &#x200B;](lifecycle-policy.md) リリースラインに対して毎年リリースされます。 これらのパッチには、以前にリリースされた独立したセキュリティ修正がすべて含まれています。 Adobeは、必要に応じて追加のセキュリティパッチをリリースする可能性がありますが、保証されません。

- **パッチ** - Adobe Commerce 2.4.x LTS リリースラインの完全な [&#x200B; パッチ &#x200B;](versioning-policy.md#patch-release) は、毎年（5 月）にリリースされます。

- **Beta パッチ** - Adobe Commerce 2.4.x LTS リリースライン用の 2 つの [&#x200B; ベータ版パッチ &#x200B;](versioning-policy.md#beta-patch-release) は、年に 2 回リリースされます。

詳しくは、次の画像を参照してください。

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![2026 Adobe Commerceのリリースカレンダー &#x200B;](../assets/release/release-calendar.png)


## リリース通知チャネル

Adobeは、次のチャネルを通じて、新しいパッチリリースについてお客様に通知します。

- [Adobeのセキュリティ速報および情報 &#x200B;](https://helpx.adobe.com/security/security-bulletin.html#magento)
- 電子メール
- 製品内アラート

>[!NOTE]
>
> すべてのマイナー、パッチ、セキュリティのリリースのリリース日と通常のサポートが終了する日付については、[&#x200B; リリース済みバージョン &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions) を参照してください。
