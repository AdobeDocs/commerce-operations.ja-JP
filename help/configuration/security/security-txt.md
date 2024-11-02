---
title: Security.txt
description: セキュリティ研究者が脆弱性を報告するのに役立つ情報を提供する方法を説明します。
feature: Configuration, Security
badge: label="寄稿：Kalpesh Meta from Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="カルペシュ メッタ"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# セキュリティ TXT ファイル

研究者によってセキュリティの脆弱性が発見された場合、適切なレポートチャネルがないことがよくあります。 その結果、一部の脆弱性は報告されません。 `security.txt` [ ファイル形式 ](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) ファイルの目的は、セキュリティ調査担当者が調査結果を報告するために使用できる情報を提供することです。

マーチャントは、[ セキュリティの問題のレポート ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-issue-reporting) に関する連絡先情報をCommerceから入力できます _管理者_。 開発者向けに、`Magento_Securitytxt` モジュールは次の機能を提供します。

- _Admin_ からセキュリティ設定を保存できるようにします。
- `.well-known/security.txt` ファイルと `.well-known/security.txt.sig` ファイルへの要求に対するアプリケーション アクション クラスに一致するルーターが含まれています。
- `.well-known/security.txt` ファイルと `.well-known/security.txt.sig` ファイルのコンテンツを提供します。

有効な `security.txt` ファイルは次のようになります。

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

`security.txt` signature （`security.txt.sig`）ファイルを作成するには：

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

署名を検証するには：

```bash
gpg --verify security.txt.sig security.txt
```
