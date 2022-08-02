---
title: パスワードのハッシュ
description: パスワードのハッシュ化戦略と実装についてお読みください。
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# パスワードのハッシュ

現在、Commerce は、異なるネイティブ PHP ハッシュアルゴリズムに基づく、パスワードハッシュに独自の方法を使用しています。 Commerce は、 `MD5`, `SHA256`または `Argon 2ID13`. Sodium 拡張機能がインストールされている場合（PHP 7.3 ではデフォルトでインストールされている）、 `Argon 2ID13` は、デフォルトのハッシュアルゴリズムとして選択されます。 それ以外の場合は、 `SHA256` がデフォルトです。 Commerce ではネイティブの PHP を使用できます `password_hash` 関数は、Argon 2i アルゴリズムをサポートしています。

次のような古いアルゴリズムでハッシュ化された古いパスワードを妥協するのを防ぐため `MD5`を使用すると、現在の実装では、元のパスワードを変更せずにハッシュをアップグレードする方法が提供されます。 一般に、パスワードハッシュの形式は次のとおりです。

```text
password_hash:salt:version<n>:version<n>
```

ここで、 `version<n>`...`version<n>` は、パスワードで使用されるすべてのハッシュアルゴリズムのバージョンを表します。 また、この塩は常にパスワードハッシュと共に保存されるので、アルゴリズムのチェーン全体を復元できます。 次に例を示します。

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

最初の部分は、パスワードのハッシュを表します。 二人目の男は `8qnyO4H1OYIfGCUb` 塩です。 最後の 2 つは異なるハッシュアルゴリズムです。1 は `SHA256` および 2 は `Argon 2ID13`. つまり、顧客のパスワードは元々 `SHA256` その後、アルゴリズムは `Argon 2ID13` ハッシュはアルゴンで再ハッシュ化された。

## ハッシュ戦略をアップグレード

ハッシュアップグレードメカニズムの外観を考慮します。 最初に、パスワードが `MD5` その後、アルゴリズムは Argon 2ID 13 で複数回更新されました。 次の図に、ハッシュアップグレードフローを示します。

![ハッシュアップグレードワークフロー](../../assets/configuration/hash-upgrade-algorithm.png)

各ハッシュアルゴリズムは、以前のパスワードハッシュを使用して新しいハッシュを生成します。 Commerce は、元の生のパスワードを保存しません。

![ハッシュアップグレード方法](../../assets/configuration/hash-upgrade-strategy.png)

上で説明したように、パスワードハッシュは、元のパスワードに複数のハッシュバージョンが適用される場合があります。
次に、顧客認証中のパスワード検証メカニズムの仕組みを示します。

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

Commerce は、使用されたすべてのパスワードハッシュバージョンをパスワードハッシュと共に保存するので、パスワードの検証中にハッシュチェーン全体を復元できます。 ハッシュ検証メカニズムは、次に示すハッシュアップグレード戦略と似ています。アルゴリズムは、パスワードハッシュと共に保存されたバージョンに基づいて、指定されたパスワードからハッシュを生成し、ハッシュ化されたパスワードとデータベースに保存されたハッシュの比較結果を返します。

## 実装

この `\Magento\Framework\Encryption\Encryptor` クラスは、パスワードハッシュの生成と検証を担当します。 この [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) コマンドを実行すると、顧客のパスワードハッシュが最新のハッシュアルゴリズムにアップグレードされます。
