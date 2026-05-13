---
title: Adobe Commerce 2.4.2 セキュリティパッチリリースノート
description: Adobe Commerce バージョン 2.4.2のセキュリティパッチリリースに含まれているセキュリティバグの修正、セキュリティの強化、およびその他のセキュリティ関連アップデートについて説明します。
exl-id: e6058e96-b810-4a78-8804-15783afef951
source-git-commit: 87302734f3ff91f0403beac283ff21925d89318d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Adobe Commerce 2.4.2 セキュリティパッチのリリースノート

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.2-p2

Adobe Commerce 2.4.2-p2のセキュリティリリースには、以前のリリースの2.4.2で特定された脆弱性に対するセキュリティバグの修正が含まれています。

セキュリティ バグの修正に関する最新情報については、[Adobe セキュリティ情報APSB21-64](https://helpx.adobe.com/security/products/magento/apsb21-64.html)を参照してください。

## 配送業者としてDHLを提供し続けるには、AC-3022.patchを適用します

DHLはスキーマバージョン 6.2を導入しており、近い将来スキーマバージョン 6.0を廃止する予定です。 DHL統合をサポートするAdobe Commerce 2.4.4以前のバージョンは、バージョン 6.0のみをサポートします。 これらのリリースを展開する販売者は、DHLを配送業者として提供し続けるために、最も早い都合で`AC-3022.patch`を適用する必要があります。 パッチのダウンロードとインストールについて詳しくは、[配送業者としてDHLを提供し続けるためのパッチの適用](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) ナレッジベースの記事を参照してください。

<!-- Last updated from includes: 2026-04-08 15:01:38 -->
