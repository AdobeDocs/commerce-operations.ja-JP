---
title: umask の設定（オプション）
description: ファイルシステムの権限を制限することで、Adobe CommerceまたはMagento Open Sourceのオンプレミスインストールのセキュリティ姿勢を改善します。
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# umask の設定（オプション）

Web サーバ・グループは、ファイル・システム内の特定のディレクトリに対する書き込み権限を持つ必要があります。ただし、特に実稼動環境では、より厳しいセキュリティが必要になる場合があります。 アドビでは、 [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html).

解決策は、オプションでという名前のファイルを作成できるようにすることです。 `magento_umask` を設定します。

>[!NOTE]
>
>1 人のユーザーまたは共有のホスティングシステム上でのみ umask を変更することをお勧めします。 プライベート・アプリケーション・サーバがある場合、グループはファイル・システムへの書き込みアクセス権を持っている必要があります。umask は書き込みアクセスをグループから削除します。

デフォルトの umask ( `magento_umask` 指定 ) `002`は次の意味を持ちます。

* ディレクトリの場合は 775。つまり、ユーザーによるフルコントロール、グループによるフルコントロールを意味し、全員がディレクトリを経由できるようにします。 これらの権限は、通常、共有ホスティングプロバイダーで必要になります。

* ファイルの場合は 664、ユーザーが書き込み可能、グループが書き込み可能、他の全員が読み取り専用

一般的な提案は、 `022` 内 `magento_umask` ファイルの意味は次のとおりです。

* 755（ディレクトリの場合）:ユーザーと他の全員がディレクトリをトラバースできるように、完全に制御します。
* 644（ファイルの場合）:ユーザーに対する読み取り/書き込み権限と、他の全員に対する読み取り専用権限。

設定するには `magento_umask`:

1. コマンドラインターミナルで、アプリケーションサーバーに [ファイルシステム所有者](../prerequisites/file-system/overview.md).
1. アプリケーションのインストールディレクトリに移動します。

   ```bash
   cd <Application install directory>
   ```

1. 次のコマンドを使用して、という名前のファイルを作成します。 `magento_umask` そして、 `umask` の値を含める必要があります。

   ```bash
   echo <desired umask number> > magento_umask
   ```

   これで、という名前のファイルが作成されました。 `magento_umask` 内 `<Magento install dir>` コンテンツが `umask` 数値。

1. ログアウトし、 [ファイルシステム所有者](../prerequisites/file-system/overview.md) 変更を適用します。
