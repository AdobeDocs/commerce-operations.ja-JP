---
title: Security.txt
description: セキュリティ研究者が脆弱性を報告する際に役立つ情報を提供する方法を説明します。
feature: Configuration, Security
badge: label="Corra から Kalpesh Mehta に寄稿" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# セキュリティ TXT ファイル

研究者がセキュリティの脆弱性を発見した場合、適切なレポートチャネルが不足することがよくあります。 その結果、一部の脆弱性は報告されません。 の目的 `security.txt` [ファイル形式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) ファイルは、セキュリティ研究者がその発見を報告する際に使用できる情報を提供するためのものです。

商人は次の連絡先情報を入力できます： [セキュリティ問題の報告](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) コマースから _管理者_. 開発者の場合、 `Magento_Securitytxt` モジュールは、次の機能を提供します。

- セキュリティ設定を _管理者_.
- に対する要求のアプリケーションアクションクラスを照合するルータが含まれます `.well-known/security.txt` および `.well-known/security.txt.sig` ファイル。
- のコンテンツを提供 `.well-known/security.txt` および `.well-known/security.txt.sig` ファイル。

有効な `security.txt` ファイルは次のようになります。

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

次の手順で `security.txt` 署名 (`security.txt.sig`) ファイル：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

署名を検証するには：

```bash
gpg --verify security.txt.sig security.txt
```
