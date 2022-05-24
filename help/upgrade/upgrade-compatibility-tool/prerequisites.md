---
title: '"[!DNL Upgrade Compatibility Tool] 前提条件»'
description: 'システムが、 [!DNL Upgrade Compatibility Tool] Adobe Commerceプロジェクト用 '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] 前提条件

{{commerce-only}}

を実行するための最小要件 [!DNL Upgrade Compatibility Tool] 次の場合：

| **要件** | **制約** |
|----------------|-----------------|
| PHP バージョン | >= 7.3 |
| コンポーザー | なし |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`または `>=16.0.0`) |
| メモリ制限 | 2GB 以上の RAM |
| Adobe Commerce Access キー | なし |
| Adobe Commerce | なし |

次を実行できます。 [!DNL Upgrade Compatibility Tool] （Windows はサポートされていません）。 を実行する必要はありません。 [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスの場所

～に必要だ [!DNL Upgrade Compatibility Tool] Adobe Commerceインスタンスのソースコードにアクセスできるようにする。 例えば、あるサーバーにインストールし、別のサーバー上のAdobe Commerceインストール場所を示すことができます。 詳しくは、 [インストール](../upgrade-compatibility-tool/install.md) トピックを参照してください。

を実行している場合、 [!DNL Upgrade Compatibility Tool] 大きなモジュールやファイルを含むAdobe Commerceインスタンスに対しては、大量の RAM（少なくとも 2GB）が必要になる場合があります。 以下を使用して、 `[=MODULE-PATH]` オプションを使用して、メモリ不足の問題を回避します。

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

引数は次のようになります。

- `<dir>`:Adobe Commerceインストールディレクトリ。
- `[=MODULE-PATH]`:特定のモジュールパスディレクトリ。
