---
title: '"[!DNL Upgrade Compatibility Tool] 前提条件»'
description: 'システムが、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクト用 '
source-git-commit: c4769b555df49ed2f0b2fffbeaf458c5a64816ba
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 前提条件

{{commerce-only}}

の実行 [!DNL Upgrade Compatibility Tool] が、 **前** Adobe Commerceのバージョンをアップグレードしています。

を実行するための最小要件 [!DNL Upgrade Compatibility Tool] 次の場合：

| **要件** | **制約** |
|----------------|-----------------|
| PHP バージョン | >= 7.3 |
| コンポーザー | なし |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`または `>=16.0.0`) |
| メモリ制限 | 2GB 以上の RAM |
| Adobe Commerce Access キー | なし |
| Adobe Commerce | なし |

次を実行できます。 [!DNL Upgrade Compatibility Tool] （任意のオペレーティングシステム）。 を実行する必要はありません。 [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスの場所

～に必要だ [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスのソースコードにアクセスできるようにする。 例えば、あるサーバーにインストールし、別のサーバー上のAdobe Commerceインストール場所を示すことができます。 詳しくは、 [インストール](../upgrade-compatibility-tool/install.md) トピックを参照してください。

を実行している場合、 [!DNL Upgrade Compatibility Tool] 大きなモジュールやファイルを持つAdobe Commerceインスタンスに対しては、このツールに大量の RAM（2GB 以上の RAM）が必要になる場合があります。
