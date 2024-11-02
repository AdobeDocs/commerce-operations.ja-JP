---
title: パスワードハッシュ
description: パスワードハッシュ戦略と実装について説明します。
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# パスワードハッシュ

現在、Commerceは、様々な PHP 固有のハッシュアルゴリズムに基づいて、独自の方法でパスワードをハッシュします。 Commerceは、`MD5`、`SHA256`、`Argon 2ID13` など複数のアルゴリズムをサポートしています。 Sodium 拡張モジュールがインストールされている（PHP 7.3 ではデフォルトでインストールされています）場合、`Argon 2ID13` がデフォルトのハッシュアルゴリズムとして選択されます。 それ以外の場合は、`SHA256` がデフォルトです。 Commerceは、Argon 2i アルゴリズムをサポートする PHP `password_hash` 関数を使用できます。

`MD5` などの古いアルゴリズムでハッシュ化された古いパスワードが危険に晒されるのを避けるために、現在の実装では元のパスワードを変更せずにハッシュをアップグレードする方法が提供されています。 一般に、パスワードハッシュの形式は次のようになります。

```text
password_hash:salt:version<n>:version<n>
```

ここで、`version<n>`...`version<n>` は、パスワードで使用されるすべてのハッシュアルゴリズムバージョンを表します。 また、塩は常にパスワードハッシュと一緒に保存されるので、アルゴリズムのチェーン全体を復元できます。 次に例を示します。

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

最初の部分はパスワードハッシュを表します。 2 つ目は塩 `8qnyO4H1OYIfGCUb` す。 最後の 2 つは、異なるハッシュアルゴリズムです。1 は `SHA256`、2 は `Argon 2ID13` です。 つまり、顧客のパスワードは最初に `SHA256` でハッシュ化され、その後、アルゴリズムは `Argon 2ID13` で更新され、ハッシュはアルゴンで再ハッシュ化されたことを意味します。

## ハッシュ戦略のアップグレード

ハッシュアップグレードメカニズムがどのように見えるかを検討します。 最初にパスワードが `MD5` でハッシュ化され、その後アルゴリズムが Argon 2ID13 で複数回更新されたとします。 次の図に、ハッシュのアップグレードフローを示します。

![ ハッシュアップグレードワークフロー ](../../assets/configuration/hash-upgrade-algorithm.png)

各ハッシュアルゴリズムは、前のパスワードハッシュを使用して新しいハッシュを生成します。 Commerceには、元の生のパスワードは保存されません。

![ ハッシュアップグレード方法 ](../../assets/configuration/hash-upgrade-strategy.png)

上記のように、パスワードハッシュには、元のパスワードに適用された複数のハッシュバージョンが含まれる場合があります。
顧客の認証中にパスワード検証メカニズムがどのように機能するかを次に示します。

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

Commerceは、使用されたすべてのパスワードハッシュのバージョンをパスワードハッシュと共に保存するので、パスワードの検証中にハッシュチェーン全体を復元できます。 ハッシュの検証メカニズムは、ハッシュアップグレード戦略に似ています。パスワードハッシュと共に保存されたバージョンに基づいて、アルゴリズムは、指定されたパスワードからハッシュを生成し、ハッシュ化されたパスワードとデータベースに保存されたハッシュの比較結果を返します。

## 実装

`\Magento\Framework\Encryption\Encryptor` クラスは、パスワードハッシュの生成と検証を行います。 [`bin/magento customer:hash:upgrade`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#customerhashupgrade) コマンドは、顧客パスワード ハッシュを最新のハッシュ アルゴリズムにアップグレードします。
