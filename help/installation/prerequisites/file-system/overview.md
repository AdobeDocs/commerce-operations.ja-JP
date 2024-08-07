---
title: ファイルの所有権と権限
description: Adobe Commerceのオンプレミスインストールを扱う場合のファイルシステム権限の重要性について説明します。
exl-id: a84784bf-afd6-4dba-9745-3fefc0ecafcb
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ファイルの所有権と権限

許可されていないユーザーやプロセスがシステムにアクセスして、システムに損害を与える可能性に関連する問題を防ぐために、開発環境でAdobe Commerceのインストールを保護することが重要です。 インストールを保護するために、次のファイルシステムの所有権と権限のガイドラインを使用します。

## ファイルシステムの所有者

ファイルシステム所有者は、ファイルシステム内のファイルに対する書き込み権限を所有および保持するユーザーです。

ファイル・システム・オーナーには、次の 2 種類があります。

- **単一ユーザーでの共有ホスティング**

  共有ホスティングプロバイダーを使用すると、1 人のユーザーとしてアプリケーションサーバーにログインできます。 1 人のユーザーとしてログインし、FTP を使用してファイルを転送し、web サーバーを実行できます。 [`umask`](#restrict-access-with-a-umask) を設定して、特に実稼動環境でのアクセスをさらに制限するオプションがあります。

- **2 人のユーザーによるプライベートホスティング**

  プライベートホスティングは、アプリケーションサーバーを管理する場合に役立ちます。 各ユーザーには、次のような特定の責任があります。

   - _Web サーバーユーザー_ は、管理およびストアフロントを実行します。

   - _コマンドラインユーザー_ は、cron ジョブとコマンドラインユーティリティを実行します。

  どちらのユーザーもファイルシステムに対して同じ権限が必要なので、[ 共有グループ ](configure-permissions.md#set-ownership-and-permissions-for-two-users) を使用して [`umask`](#restrict-access-with-a-umask) を設定することをお勧めします。

### umask を使用してアクセスを制限

セキュリティを強化するには、特に共有ホスティングシステム上の実稼動環境で、`umask` を使用してアクセスを制限します。 `umask` （_ファイルシステム作成マスク_ とも呼ばれます）は、新しく作成されたファイルに対するファイル権限の設定方法を制御する一連のビットです。

>[!WARNING]
>
>ファイルシステムのセキュリティは複雑で重要です。 設定する権限のレベルを決定する前に、経験豊富なシステム管理者またはネットワーク管理者に問い合わせることを強くお勧めします。 使用するメカニズムを提供しますが、権限戦略を作成するのはユーザーの責任です。

Adobe Commerceでは、3 ビットのデフォルトマスク `002` が使用されます。 UNIX のデフォルトのファイルの場合は 666、ディレクトリの場合は 777 からデフォルトのマスクを引きます。

例：

- **775 for directories**：ユーザーによるフル・コントロール、グループによるフル・コントロール、すべてのユーザーによるディレクトリのトラバースを可能にします。 これらの権限は、通常、共有ホスティングプロバイダーで必要です。

- **664 for files** - ユーザーが書き込み可能、グループが書き込み可能、その他のすべてのユーザーが読み取り専用です。

`magento_umask` ファイルの作成の詳細については、[umask の設定 ](../../next-steps/set-umask.md) を参照してください。

## 権限、所有権、アプリケーションモード

様々なAdobe Commerce アプリケーションモードを使用する場合は、異なる権限と所有権をお勧めします。

- デフォルト
- 開発者
- 実稼動

_設定ガイド_ の [ モードについて ](../../../configuration/bootstrap/application-modes.md) を参照してください。

さらに、「構成ガイド [ の「ファイル・システムのアクセス権限 ](../../../configuration/deployment/file-system-permissions.md) におけるアクセス権限の推奨事項 _についても説明_ ます。

>[!TIP]
>
>Adobe Commerceをインストールする前に、[ ファイルの所有権と権限の設定 ](configure-permissions.md) を確認してください。
