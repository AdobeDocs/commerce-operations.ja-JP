---
title: Cloud バージョン アップグレードの適用ポリシー
description: Adobe Commerce on Cloudのバージョンのアップグレードの適用について説明します。アップグレード、適用日、廃止、必要なアクションをAdobeで適用する理由を説明します。 移行プロビジョニングと移行パスについては、ライフサイクルポリシーを参照してください。
nudge: false
source-git-commit: 797f067de451c8b1b4d735e82de66a3fd9b56563
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Adobe Commerce on Cloudのバージョンアップグレードポリシー

Adobe Commerce版の定期的なサポートと拡張サポートが終了した場合、Adobeは、そのサポート対象外の版を実行しているクラウド環境でAdobe Commerceを使用停止する権利を留保します。 バージョンアップグレードの適用は、Adobe Commerce on Cloud環境にのみ適用されます。オンプレミスのお客様は、独自のインフラストラクチャを管理します。

サポートされているAdobe Commerce バージョンに移行するか、リリースラインの延長サポートの公開日[終了](lifecycle-policy.md#end-of-support-dates)までに[!DNL Adobe Commerce as a Cloud Service]に移行する必要があります。

次の節では、Adobeがアップグレードを適用する理由、適用日の計算方法、および適用日に何が発生するかを説明します。 バージョン固有の適用日については、ライフサイクルポリシーの「[ サポート終了日](lifecycle-policy.md#end-of-support-dates)」テーブルを参照してください。

>[!NOTE]
>
>このトピックでは、クラウド アップグレードの適用についてのみ説明します。 サポート層の定義については、[ サポート終了日](lifecycle-policy.md#end-of-support-dates) テーブル、[ セキュリティのみの移行規定](lifecycle-policy.md#security-only-transitional-period)、[ サードパーティ製ソフトウェアの依存関係](lifecycle-policy.md#platform-dependencies)、[PHPの提供終了およびPCI コンプライアンス ](lifecycle-policy.md#php-end-of-life-and-pci-compliance)および[ アップグレードと移行のオプション ](lifecycle-policy.md#upgrade-and-migration-options)については、[ ライフサイクルポリシー](lifecycle-policy.md)を参照してください。 サポート対象のAdobe Commerce バージョンにアップグレードするだけでなく、Adobeでは、サポート対象のバージョンにサードパーティ製ソフトウェアの依存関係を維持する必要があります。

## Adobeがこのポリシーを導入する理由

Adobeは、Adobe Commerce on Cloudのお客様が実行するホスト型プラットフォームインフラストラクチャのセキュリティとコンプライアンスを担当します。 これには、ソフトウェアのあらゆる依存関係を最新の状態に保つことや、セキュリティパッチを適用すること、顧客が依拠するPCIなどのコンプライアンス標準を満たすことが含まれます。

基盤となるソフトウェアの依存関係に対するセキュリティサポートがベンダーによって正式に終了すると、Adobeは必要なレベルのセキュリティカバレッジとプラットフォームサポートを提供できなくなります。 サポートされていないインフラストラクチャで店舗を運営し続けることで、顧客、買い物客、Adobeに受け入れがたいリスクを与えます。 そのため、Adobeでは、サポートされていないCommerce版を実行しているAdobe Commerce on Cloud環境を廃止するタイミングを定義する正式なバージョンアップアップポリシーを導入しています。

## アップグレード実施日の計算方法

Adobe Commerceの各リリース行について、アップグレード実施日は次のように計算されます。

**アップグレード実施日** =一般公開日+ 3年間の定期的なサポート +最大1年間の延長サポート

拡張サポートは、各リリースラインの定期的なサポートの終了に近いタイミングで発表されます。

## バージョンのアップグレード実施日の処理

公開されたアップグレード適用日に、Adobeは、影響を受けるリリースバージョンを実行しているすべてのAdobe Commerce on Cloud環境のメンテナンスを停止し、それらを廃止する権利を留保します。 バージョンのアップグレードの適用日までの主要なマイルストーンに事前通知が届きます。 Adobeでは、環境をディアクティベートする前にデータ書き出しウィンドウが提供されるので、データを取得できます。

このポリシーの最初の実施日は&#x200B;**2027年6月1日**&#x200B;です。この日までに延長サポートが終了するリリースラインの場合は、この日より前です。 バージョン固有の適用日については、[ サポート終了日](lifecycle-policy.md#end-of-support-dates)の表を参照してください。
