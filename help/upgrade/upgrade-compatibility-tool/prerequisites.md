---
title: アップグレード互換性ツールの前提条件
description: 'Adobe Commerceプロジェクトのアップグレード互換性ツールを実行するために必要な要件をシステムが満たしていることを確認します。 '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# アップグレード互換性ツールの前提条件

アップグレード互換性ツールを実行すると、必要な作業を特定できます **前** Adobe Commerceのバージョンをアップグレードしています。

アップグレード互換性ツールを実行するための最小要件は次のとおりです。

| **要件** | **制約** |
|----------------|-----------------|
| PHP バージョン | >= 7.3 |
| コンポーザー | なし |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`または `>=16.0.0`) |
| メモリ制限 | 2GB 以上の RAM |
| Adobe Commerce Access キー | なし |
| Adobe Commerce （Open Source または Enterprise） | なし |

アップグレード互換性ツールは、任意のオペレーティングシステムで実行できます。 Adobe Commerceインスタンスが配置されているアップグレード互換性ツールを実行する必要はありません。

アップグレード互換性ツールでAdobe Commerceインスタンスのソースコードにアクセスできる必要があります。 例えば、あるサーバーにインストールし、別のサーバー上のAdobe Commerceインストール場所を示すことができます。 詳しくは、 [インストール](../upgrade-compatibility-tool/install.md) トピックを参照してください。
