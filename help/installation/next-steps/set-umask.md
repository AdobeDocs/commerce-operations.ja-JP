---
title: umaskの設定（オプション）
description: Adobe Commerce オンプレミス インストールのセキュリティ対策を強化するには、ファイルシステム権限を制限します。
feature: Install, Configuration
exl-id: 18d65d75-7be0-4488-bf35-4b058e4ae5ea
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# umaskの設定（オプション）

Web サーバーグループには、ファイルシステム内の特定のディレクトリに対する書き込み権限が必要です。ただし、特に実稼動環境では、より厳しいセキュリティが必要になる場合があります。 [umask](https://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)を使用して、これらの権限をさらに制限する柔軟性を提供します。

アドビのソリューションでは、オプションで`magento_umask`という名前のファイルをアプリケーションルートディレクトリに作成し、web サーバーグループとその他のすべてのユーザーの権限を制限することができます。

>[!NOTE]
>
>1 ユーザーまたは共有ホスティングシステムでのみumaskを変更することをお勧めします。 プライベートアプリケーションサーバーがある場合は、グループにファイルシステムへの書き込みアクセス権が必要です。umaskはグループから書き込みアクセス権を削除します。

デフォルトのumask （`magento_umask`が指定されていない）は`002`です。つまり、次のようになります。

* 775 ディレクトリの場合、ユーザーによる完全な制御、グループによる完全な制御を意味し、すべてのユーザーがディレクトリをトラバースできるようにします。 これらの権限は、通常、共有ホスティングプロバイダーが必要とします。

* 664 （ユーザーによる書き込み可能、グループによる書き込み可能、および他のすべてのユーザーに対する読み取り専用）

一般的な推奨事項は、`magento_umask` ファイルで`022`の値を使用することです。つまり、

* 755 ディレクトリの場合：ユーザーの完全な制御、および他のすべてのユーザーがディレクトリをトラバースできます。
* 644 ファイルの場合：ユーザーの読み取り/書き込み権限、および他のユーザーの読み取り専用。

`magento_umask`を設定するには：

1. コマンドラインターミナルで、[&#x200B; ファイルシステム所有者](../prerequisites/file-system/overview.md)としてアプリケーションサーバーにログインします。
1. アプリケーションのインストールディレクトリに移動します。

   ```shell
   cd <Application install directory>
   ```

1. 次のコマンドを使用して、`magento_umask`という名前のファイルを作成し、`umask`値を書き込みます。

   ```shell
   echo <desired umask number> > magento_umask
   ```

   これで、`<Magento install dir>`に`magento_umask`という名前のファイルがあり、コンテンツは`umask`番号のみです。

1. ログアウトし、[&#x200B; ファイルシステム所有者](../prerequisites/file-system/overview.md)として再度ログインして、変更を適用します。
