---
title: Adobe Commerce 2.4.2 セキュリティパッチのリリースノート
description: Adobe Commerce バージョン 2.4.2 のセキュリティパッチリリースに含まれている、セキュリティバグ修正、セキュリティ機能強化、その他のセキュリティ関連アップデートについて説明します。
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: 2e62c49dd0c338f0913ce5f725f396c2cfa95122
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# Adobe Commerce 2.4.2 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.2-p2

Adobe Commerce 2.4.2-p2 セキュリティリリースは、以前のリリースの 2.4.2 で特定された脆弱性に対するセキュリティバグ修正を提供します。

セキュリティのバグ修正の最新情報については、[Adobe セキュリティ速報 APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html) を参照してください。

## AC-3022.patch を適用して、引き続き配送業者として DHL を提供します

DHL ではスキーマバージョン 6.2 を導入しており、近い将来、スキーマバージョン 6.0 を廃止する予定です。 DHL 統合をサポートするAdobe Commerce 2.4.4 以前のバージョンは、バージョン 6.0 のみをサポートしています。これらのリリースをデプロイするマーチャントは、DHL を配送業者として引き続き提供するために、できるだけ早い時期に `AC-3022.patch` を適用する必要があります。 パッチのダウンロードとインストールについては、ナレッジベースの記事 [DHL を引き続き配送業者として提供するためのパッチを適用する ](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) を参照してください。

<!-- Last updated from includes: 2025-05-28 17:01:56 -->
