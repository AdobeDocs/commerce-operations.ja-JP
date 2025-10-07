---
title: 翻訳辞書と言語パッケージ
description: Adobe Commerceの翻訳辞書を生成し、言語パッケージを作成する方法を説明します。 ローカライゼーションと多言語ストアの設定について説明します。
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1441'
ht-degree: 0%

---

# 場所

{{file-system-owner}}

Commerce翻訳を使用すると、次の情報を生成することで、複数の地域や市場に合わせてストアをカスタマイズおよびローカライズできます。

- **翻訳辞書**：カスタムモジュールやテーマなどの _一部_ の単語やフレーズをカスタマイズまたは翻訳する便利な方法です。
- **言語パッケージ**:Commerce アプリケーションですべて _またはすべて_ の単語やフレーズを翻訳できます。

[ 翻訳の概要 ] を参照してください。

## 翻訳辞書の生成

[ 翻訳辞書 ] を生成して、既存の文字列のカスタマイズ、カスタムモジュールでの単語やフレーズの翻訳、テーマのローカライズ、言語パッケージの作成を行うことができます。

翻訳を開始するには、コマンドを使用して、既存のすべてのフレーズと単語のリストを収集した辞書 CSV ファイルを生成します。

辞書を生成して翻訳を開始するには：

1. 翻訳コレクションコマンドを使用して、有効なコンポーネントから翻訳可能な単語や語句を抽出する。 コンテンツを CSV ファイルに抽出します。
1. 既存の単語やフレーズを翻訳してください。 必要に応じて、カスタム用語を追加できます。

   翻訳済み辞書を使用するオプションがあります。

1. 翻訳辞書を言語パッケージにまとめ、Commerce ストア管理者に提供することができます。

1. 管理者は、ストア管理者が [ 翻訳を設定 ] します。

コマンドオプション：

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

次の表で、パラメーターと値について説明します。

| パラメーター | 値 | 必須？ |
|--- |--- |--- |
| `<path to directory to translate>` | 翻訳可能なコードを持つディレクトリ（つまり、翻訳するフレーズを含む PHP、PHTML または XML ファイル）へのパス。<br><br> 入力したパスから検索が開始され、そこに含まれるすべてのファイルとサブディレクトリが検索されます。<br><br>`-m --magento` を使用する場合は、このパラメーターを使用しないでください。 | はい（辞書）、いいえ（パッケージ）。 |
| `-m --magento` | この翻訳辞書から言語パッケージを作成するために必要です。 このプロパティを使用すると、bin/magento を含むディレクトリが検索されます。 このオプションを選択すると、辞書の各行にテーマまたはモジュールが追加されます。<br><br> 次に例を示します。<br><br>&quot;No Items Found&quot;,&quot;No Items Found&quot;,module,Magento_Wishlist | 不可 |
| `-o --output="<path>"` | 作成する翻訳ディクショナリ CSV ファイルの絶対ファイルシステムパスとファイル名を指定します。 入力する値は、大文字と小文字が区別されます。 CSV ファイルの名前は、文字の大文字と小文字を含め、ロケール名と完全に一致する必要があります。<br><br> このパラメータを省略すると、出力は stdout に送られます。 | 不可 |

>[!INFO]
>
>翻訳辞書から言語パックを作成するには、_オプションを使用する_ 必ず `-m|--magento` 必要です。

### 翻訳ガイドライン

単語やフレーズを翻訳する際は、次のガイドラインに従います。

- 2 番目の列の内容のみを変更します。 フレーズを英語（`US`）から目的の言語に翻訳します。
- ロケール用の辞書を作成する場合、デフォルトのCommerce文字列を使用します。
- 翻訳中は、プレースホルダー `%1`、`%2` に注意します。

Commerceではプレースホルダーを使用してコンテキスト値を挿入します。これらは翻訳には使用 _れません_。 例：

```text
Product '%1' has been added to shopping cart.
```

次の値が入力されます。

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

結果として得られるフレーズには、各プレースホルダーが少なくとも 1 つ含まれている必要があります。 例えば、元のフレーズに `%1`～`%3` のプレースホルダーがあるとします。 翻訳では、これらのプレースホルダーを任意の順序で何個も使用できますが、`%1`、`%2` および `%3` のプレースホルダーは少なくとも 1 つ必要です。 翻訳には、元の値に存在しないプレースホルダー値（`%4`、`%5` など）を含めることはできません。

フレーズの翻訳例を次に示します。

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 言語パッケージの作成

翻訳辞書とは対照的に、言語パッケージを使用して、Commerce アプリケーションの一部またはすべての単語やフレーズを翻訳できます。 翻訳辞書を使用して、モジュールやテーマなどの特定のコンポーネントを翻訳できます。 [ 言語パッケージの詳細情報 ]。

この節では、CSV ファイルをモジュールとテーマに書き込む言語パッケージの作成方法について説明します。 言語パッケージを作成するには、次の節で説明するタスクを実行する必要があります。

1. [&#x200B; 単語やフレーズの収集と翻訳 &#x200B;](#generate-a-translation-dictionary)。 （`--magento` パラメーターは必須です。）
1. [&#x200B; 言語パッケージコマンドを実行します &#x200B;](#run-the-language-package-command)。
1. [&#x200B; ディレクトリとファイルの作成 &#x200B;](#create-directories-and-files)。
1. （任意） [1 つの言語に対して複数のパッケージを設定 &#x200B;](#configure-multiple-packages-for-a-language)。

### 言語パッケージコマンドを実行します

コマンドの使用法：

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

次の表に、言語パッケージコマンドのパラメーターと値を示します。

| パラメーター | 値 | 必須？ |
|--- |--- |--- |
| `<source>` | 言語パッケージへの分類に必要な翻訳辞書とメタ情報の組み合わせを含む、CSV ファイルの絶対ファイルシステムパスとファイル名。<br><br>[`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) を使用して CSV ファイルを作成し、「ディレクトリとファイルの作成 [&#x200B; の説明に従って言語パッケージを作成します &#x200B;](#m2devgde-xlate-files)。 | はい |
| `<locale>` | [ISO 639-1] （言語）および [ISO 3166] （国）生成されるすべての CSV ファイルのファイル名として使用される言語の識別子。 例：`de_DE`、`pt_PT`、`pt_BR`。 | はい |
| `-m --mode` | ターゲット ファイルが存在する場合、既存の言語パッケージを置き換えるか、新しい言語パックと結合するかを指定します。 結合すると、存在するすべてのフレーズが上書きされ、新しいフレーズが追加されます。<br><br> 値：結合または置換（デフォルト）。 | 不可 |
| `-d --allow-duplicates` | 言語パックで重複を許可するには、このオプションを含めます。 そうでない場合、異なる翻訳を持つ複数のエントリで同じフレーズが検出されると、コマンドはエラーで失敗します。 | 不可 |

### ディレクトリとファイルの作成

言語パッケージは、Commerce ファイルシステムの `app/i18n/<VendorName>` の下のディレクトリにあり、次の内容が含まれています。

- 必要なライセンスファイル
- `composer.json`
- 言語パッケージを `registration.php` レジスタ [ する ]
- メ [`language.xml`](#language-package-languagexml) タ情報ファイル

>[!INFO]
>
>パス全体を小文字にする必要があります。 例えば、[`de_de`] を参照してください。

これらのファイルを作成するには：

1. `app/i18n` の下にディレクトリを作成します。

   例えば、Commerce言語パッケージは `app/i18n/magento` にあります

1. 必要なライセンスファイルを追加します。
1. 言語パッケージの依存関係を指定する [`composer.json`] を追加します。
1. [`registration.php`] への言語パッケージの登録
1. 次 `language.xml` 節で説明するように、メタ情報ファイルを追加します。

#### 言語パッケージ language.xml

`language.xml` 設定ファイルで言語パッケージを宣言する場合、このパッケージの言語の継承のシーケンスを指定する必要があります。

言語の継承により、_parent_ と呼ばれる既存の翻訳に基づいて _child_ と呼ばれる翻訳を作成できます。 子翻訳は親よりも優先されます。 ただし、子翻訳のアップロードや表示に失敗した場合や、フレーズや単語が欠落している場合、Commerceでは親ロケールが使用されます。 [&#x200B; 言語パッケージの継承の例 &#x200B;](#example-of-language-inheritance)

パッケージを宣言するには、次の情報を指定します。

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

ここで、

- `code` – 言語パッケージ・ロケール（必須）
- `vendor` - モジュールのベンダー名（必須）
- `package` – 言語パッケージ名（必須）
- `sort_order` - ストアで使用できる言語パッケージが複数ある場合のパッケージのアップロードの優先度
- `use` – 辞書の継承元の親言語パッケージ・ロケール

必要に応じて、複数の親パッケージを指定できます。 親パッケージは、リストに最初に表示され、最初に使用される順序で適用されます。

#### 言語の継承の例

言語パッケージが他の 2 つのパッケージから継承し、それらのパッケージに親パッケージと「grandparent」パッケージも含まれているとします。

言語パッケージが 2 つのパッケージから継承される場合、`language.xml` は次のようになります。

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

前述の例では、次のようになります。

- `language_package_one` は `en_au_package` から、`en_au_package` は `en_ie_package` から継承します
- `language_package_two` は `en_ca_package` から、`en_ca_package` は `en_us_package` から継承します

Commerce アプリケーションが `en_GB` パッケージ内の単語や語句を見つけることができない場合は、次の順序で他のパッケージを検索します。

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

言語パッケージ間のすべての継承を指定すると、循環継承チェーンが作成される可能性があります。 [Magento\Test\Integrity\App\Language\CircularDependencyTest] テストを使用して、このようなチェーンを見つけて修正します。

### 1 つの言語に対して複数のパッケージを設定

ストアの柔軟性を高めるために、同じ言語の複数の言語パッケージをストアにアップロードできます。 したがって、システムは特定の言語で使用可能なすべてのパッケージから 1 つのパッケージをコンパイルするので、ストアの異なる部分に対して異なるカスタムパッケージを使用できます。

既存の言語に対して追加のパッケージを有効にするには、（混乱を避けるために）既存の言語コード名を除く任意の名前を新しいパッケージに付けます。 次の節で説明するように、言語パッケージの `language.xml` メタ情報ファイル内のパッケージの設定を指定します。

## 翻訳コマンドの使用例

次の節では、このトピックで説明したコマンドを使用して翻訳辞書と翻訳パッケージを作成する例についてエンドツーエンドで説明します。

### 例：モジュールまたはテーマの翻訳辞書の作成

他のマーチャントに配布するモジュールまたはテーマにドイツ語翻訳を追加するには：

1. モジュールからフレーズを収集します。

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV ファイル名は、文字の大文字と小文字を含め、ロケールに _完全に一致_ する」必要があります。

1. [&#x200B; これらのガイドライン &#x200B;](#translation-guidelines) を使って単語や語句を翻訳します。
1. 必要に応じて、`xx_YY.csv` を `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` またはモジュールのテーマディレクトリにコピーします（翻訳辞書がモジュール用かテーマ用かによって異なります）。

### 例：言語パッケージを作成する

前の例と同様に、CSV ファイルを生成しますが、モジュールまたはテーマディレクトリを指定する代わりに、Commerce アプリケーションのルートディレクトリ全体を指定します。 結果の CSV には、コマンドがコード内で見つけることができたすべてのフレーズが含まれています。

1. モジュールからフレーズを収集します。

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV ファイル名は、文字の大文字と小文字を含め、ロケールに _完全に一致_ する」必要があります。

1. [&#x200B; これらのガイドライン &#x200B;](#translation-guidelines) を使って単語や語句を翻訳します。
1. 言語パッケージを作成します。

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 言語パッケージのディレクトリを作成します。

   例：`/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. このディレクトリに、次のすべてを追加します。

   - ライセンス（必要な場合）
   - `composer.json` （サンプル提供）
   - `registration.php` （サンプル提供）
   - `language.xml` （サンプル提供）

   **サンプル`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **サンプル`registration.php`**:

   ```php
   <?php
   /**
    * Copyright [first year code created] Adobe
    * All Rights Reserved.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **サンプル`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   <!--
   Copyright [first year code created] Adobe
   All Rights Reserved.
   -->
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[翻訳の概要]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[翻訳辞書]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[翻訳を設定します]: https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-localize
[言語パッケージの詳細情報]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[レジスタ]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[&#39;de_de&#39;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&#39;registration.php&#39;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
