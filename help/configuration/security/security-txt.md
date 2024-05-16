---
title: Security.txt
description: セキュリティ研究者が脆弱性を報告するのに役立つ情報を提供する方法を説明します。
feature: Configuration, Security
badge: label="寄稿：Kalpesh Meta from Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="カルペシュ メッタ"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# セキュリティ TXT ファイル

研究者によってセキュリティの脆弱性が発見された場合、適切なレポートチャネルがないことがよくあります。 その結果、一部の脆弱性は報告されません。 の目的 `security.txt` [ファイル形式](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) ファイルは、セキュリティ研究者が調査結果を報告するために使用できる情報を提供することです。

マーチャントは、次の連絡先情報を入力できます [セキュリティ問題レポート](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) Commerceから _Admin_. 開発者の場合、 `Magento_Securitytxt` モジュールは次の機能を提供します。

- からセキュリティ設定を保存できるようにします _Admin_.
- に対する要求のアプリケーション アクション クラスに一致するルーターが含まれています `.well-known/security.txt` および `.well-known/security.txt.sig` ファイル。
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

を作成するには `security.txt` 署名（`security.txt.sig`） ファイル：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

署名を検証するには：

```bash
gpg --verify security.txt.sig security.txt
```
