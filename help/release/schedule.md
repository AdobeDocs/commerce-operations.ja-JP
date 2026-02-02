---
title: パッチリリーススケジュール
description: AdobeがAdobe Commerceの新しいパッチとセキュリティ修正のリリースを発表する予定の時期について説明します。
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 1c32f1e506cd3caefacbb250821da087e34c34ea
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# パッチリリーススケジュール

Adobeは、製品のアップグレードをシンプルで予測可能なものにすると同時に、早期導入者に対して改善をより迅速に提供することの間で、適切なバランスを継続的に見つけ出そうと努めています（[ バージョンポリシー ](versioning-policy.md) を参照）。

このスケジュールの目的は、Adobeがコア Adobe Commerce PHP アプリケーションのサポート対象の各リリースラインに対して [ パッチ ](versioning-policy.md#patch-release) のリリースを発表する予定の日付を指定することです。 パッチリリースは、プラットフォームの安全性、信頼性、パフォーマンスを維持するために、コアコードベースをアップグレードする機会です。

>[!NOTE]
>
>新機能、クラウドインフラストラクチャ、拡張機能リリースについて詳しくは、[Adobe Commerce サービス ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all) リリースドキュメントを参照してください。

このページにリストされているスケジュールされた品質、セキュリティ、ベータ版のパッチに加えて、Adobeでは [Quality Patches Tool](versioning-policy.md#individual-patch) を通じて [ 個別パッチ ](../tools/quality-patches-tool/usage.md) にアクセスできます。 このツールを使用すると、インストールされているバージョンのAdobe Commerceで使用可能な個々のパッチに関する一般情報を適用、元に戻して表示できます。

Adobe Commerceは、次の方法で、毎月のパッチリリーススケジュールに従います。

- **個別のセキュリティ修正** – 累積的でない個別の [ セキュリティ修正 ](versioning-policy.md#isolated-patch) が毎月リリースされる場合があり、すべての [ サポートされている ](lifecycle-policy.md) リリース行のセキュリティ修正が含まれます（通常サポートおよび拡張サポートを含む）。

- **セキュリティパッチ** – 最低限、[ セキュリティパッチ ](versioning-policy.md#security-patch-release) は、すべての [ サポート対象 ](lifecycle-policy.md) リリースラインに対して毎年（5 月）リリースされます。 これらのパッチには、以前にリリースされた独立したセキュリティ修正がすべて含まれています。 Adobeは、必要に応じて 11 月に追加のセキュリティパッチをリリースする可能性がありますが、保証されません。

- **パッチ** - Adobe Commerce 2.4.x LTS リリースラインの完全な [ パッチ ](versioning-policy.md#patch-release) は、毎年（5 月）にリリースされます。

- **Beta パッチ** - Adobe Commerce 2.4.x LTS リリースラインの 2 つの [ ベータ版パッチ ](versioning-policy.md#beta-patch-release) は、年 2 回（3 月と 11 月）リリースされます。

詳しくは、次の画像を参照してください。

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![2026 Adobe Commerceのリリースカレンダー ](../assets/release/release-calendar.png)


## リリース通知チャネル

Adobeは、次のチャネルを通じて、新しいパッチリリースについてお客様に通知します。

- [Adobeのセキュリティ速報および情報 ](https://helpx.adobe.com/security/security-bulletin.html#magento)
- 電子メール
- 製品内アラート

>[!NOTE]
>
> すべてのマイナー、パッチ、セキュリティのリリースのリリース日と通常のサポートが終了する日付については、[ リリース済みバージョン ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions) を参照してください。
