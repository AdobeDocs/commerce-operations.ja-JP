---
title: 管理者アカウントの作成、編集、ロック解除
description: Adobe CommerceまたはMagento Open Source管理アプリケーションの管理者アカウントを管理するには、次の手順に従います。
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# 管理者アカウントの作成、編集、ロック解除

このコマンドを使用する前に、次の操作を行う必要があります。

- [デプロイメント設定の作成](deployment.md)
- [少なくともMagento_Authorization モジュールとMagento_User モジュールを有効にする](manage-modules.md)
- を作成します。 [データベーススキーマ](https://glossary.magento.com/database-schema)

>[!NOTE]
>
>データベースを作成する最も簡単な方法は、コマンドを使用することです `magento setup:upgrade`.

## 管理者の作成または編集

このコマンドを使用して、管理者を作成するか、既存の管理者を編集します。

>[!NOTE]
>
>管理者を編集している場合は、 `first name`, `last name`、および `password` 編集可能です。

コマンドの使用：

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

次の表に、パラメータと値の定義を示します。

| 名前 | 値 | 必須？ |
|--- |--- |--- |
| `--admin-firstname` | 管理者ユーザーの名。 | はい |
| `--admin-lastname` | 管理者ユーザーの姓。 | はい |
| `--admin-email` | 管理者ユーザーの電子メールアドレス。 | はい |
| `--admin-user` | 管理者ユーザー名。 | はい |
| `--admin-password` | 管理者ユーザーのパスワード。 パスワードは 7 文字以上で、英字および数字を少なくとも 1 文字含める必要があります。 <br><br>より長く、より複雑なパスワードを使用することをお勧めします。 パスワード文字列にリテラル解釈を必要とする特殊文字（バックスラッシュやスペースなど）が含まれている場合は、パスワードを一重引用符で囲みます。 | はい |
| `--magento-init-params` | 任意のコマンドに追加して、アプリケーション初期化パラメータをカスタマイズ<br/><br/>例： `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | いいえ |

使用例：

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```terminal
Created Magento administrator user named j.doe
```

必要なパラメータを指定しない場合は、CLI で次のように要求されます。

```bash
bin/magento admin:user:create
```

```terminal
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```terminal
Created Magento administrator user named John
```

以下の例は更新されます `first name`, `last name`、および `password` / `j.doe` 管理者ユーザー：

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```terminal
Created Magento administrator user named j.doe
```

## 管理者アカウントのロック解除

ロックされた管理者のアカウントのロックを解除するには、このコマンドを使用します。通常、ログインの試行が複数回行われたためです。

```bash
bin/magento admin:user:unlock {username}
```

管理者のユーザー名を指定する必要があります。 例：

```bash
bin/magento admin:user:unlock admin
```

```terminal
The user account "admin" has been unlocked
```

アカウントのロックが解除されていない場合、または問題が発生した場合は、次のメッセージが表示されます。

```terminal
The user account "admin" was not locked or could not be unlocked
```

ユーザーが管理者であり、ユーザーがアクティブであり、アカウントがロックされていることを確認します。 ロックされたユーザーのリストを管理者として表示するには、管理者としてログインし、 **システム** > **権限** > **ロックされたユーザー**.

アカウントが存在しない場合は、次のメッセージが表示されます。

```terminal
Couldn't find the user account "bob"
```
