---
title: 管理者アカウントを作成、編集またはロック解除
description: Adobe Commerce Admin アプリケーションの Administrator アカウントを管理するには、次の手順に従います。
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: aaed7dba7d11085eb8e2793cefffb8c8b082e750
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# 管理者アカウントを作成、編集またはロック解除

このコマンドを使用する前に、次の操作を行う必要があります。

- [デプロイメント設定の作成](deployment.md)
- [少なくともMagento_Authorization モジュールとMagento_User モジュールを有効にします](manage-modules.md)
- データベーススキーマの作成

>[!NOTE]
>
>データベースを作成する最も簡単な方法は、コマンド `magento setup:upgrade` を使用することです。

## 管理者の作成または編集

管理者を作成したり、既存の管理者を編集するには、このコマンドを使用します。

>[!NOTE]
>
>管理者を編集している場合は、`first name`、`last name`、`password` のみを編集できます。

コマンドの使用法：

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

次の表に、パラメーターと値を示します。

| 名前 | 値 | 必須？ |
|--- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| `--admin-firstname` | 管理者ユーザーの名。 | はい |
| `--admin-lastname` | 管理者ユーザーの姓。 | はい |
| `--admin-email` | 管理者ユーザーのメールアドレス。 | はい |
| `--admin-user` | 管理者ユーザー名。 | はい |
| `--admin-password` | 管理者ユーザーのパスワード。 パスワードは 12 文字以上で、アルファベットと数字が少なくとも 1 つずつ含まれている必要があります。 <br><br>Adobeでは、より長く、より複雑なパスワードを指定することをお勧めします。 パスワード文字列にリテラル解釈が必要な特殊文字（バックスラッシュやスペースなど）が含まれている場合は、パスワードを単一引用符で囲みます。 | はい |
| `--magento-init-params` | を任意のコマンドに追加して、アプリケーション初期化パラメーターをカスタマイズ <br/><br/> ます。例：`MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | 不可 |

使用例：

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```
Created Magento administrator user named j.doe
```

必要なパラメーターを指定しない場合、アプリケーションは CLI でそれらのパラメーターについて尋ねます。

```bash
bin/magento admin:user:create
```

```
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```
Created Magento administrator user named John
```

次の例では、管理者ユーザーの `first name`、`last name`、`password` `j.doe` 更新します。

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```
Created Magento administrator user named j.doe
```

## 管理者アカウントのロックの解除

ログインの試行が何度も間違っていることが原因で、ロックされた管理者のアカウントをロック解除する場合は、このコマンドを使用します。

```bash
bin/magento admin:user:unlock {username}
```

管理者のユーザー名を指定してください。 例：

```bash
bin/magento admin:user:unlock admin
```

```
The user account "admin" has been unlocked
```

アカウントのロックが解除されていないか、問題があった場合は、次のメッセージが表示されます。

```
The user account "admin" was not locked or could not be unlocked
```

ユーザーが管理者であり、ユーザーがアクティブであり、アカウントがロックされていることを確認します。 管理者でロックされたユーザーのリストを表示するには、管理者としてログインし、**システム**/**権限**/**ロックされたユーザー** をクリックします。

アカウントが存在しない場合は、次のメッセージが表示されます。

```
Couldn't find the user account "bob"
```
