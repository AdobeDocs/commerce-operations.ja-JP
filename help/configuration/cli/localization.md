---
title: 翻訳辞書と言語パッケージ
description: Adobe Commerceの翻訳辞書を生成し、言語パッケージを構築する方法について説明します。 ローカライゼーションと多言語ストアの設定。
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '1513'
ht-degree: 0%

---

# ローカライズ

{{file-system-owner}}

Commerceの翻訳機能を利用すれば、次の機能を生み出すことで、複数の地域や市場向けにストアをカスタマイズし、ローカライズできます。

- **翻訳辞書**。カスタムモジュールやテーマ用など、_一部_&#x200B;の単語やフレーズをカスタマイズまたは翻訳するのに便利な方法です。
- Commerce アプリケーションの&#x200B;_すべてまたはすべての_&#x200B;単語とフレーズを翻訳できる&#x200B;**言語パッケージ**。

[翻訳の概要](https://developer.adobe.com/commerce/frontend-core/guide/translations/)を参照してください。

## 翻訳辞書の生成

[翻訳辞書](https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries)を生成して、既存の文字列のカスタマイズ、カスタムモジュールでの単語やフレーズの翻訳、テーマのローカライズ、言語パッケージの作成を行うことができます。

翻訳を開始するには、コマンドを使用して、既存のすべてのフレーズと単語のリストを含む辞書CSV ファイルを生成します。

辞書を生成して翻訳を開始するには：

1. 翻訳収集コマンドを使用して、有効なコンポーネントから翻訳可能な単語やフレーズを抽出します。 コンテンツはCSV ファイルに抽出されます。
1. 既存の単語とフレーズを翻訳します。 必要に応じてカスタム用語を追加することができます。

   翻訳された辞書を使用するためのオプションがあります。

1. 翻訳ディクショナリを言語パッケージにパッケージ化し、そのパッケージをCommerce ストア管理者に提供できます。

1. 管理画面で、ストア管理者[が翻訳を設定します](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-localize)。

コマンドオプション：

```shell
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

次の表では、パラメーターと値について説明します。

| パラメーター | 値 | 必要ですか？ |
|--- |--- |--- |
| `<path to directory to translate>` | 翻訳可能なコードを持つディレクトリへのパス。つまり、翻訳するフレーズを持つPHP、PHTML、またはXML ファイルです。<br><br> ツールは、入力したパスで検索を開始し、そのパスに含まれるすべてのファイルとサブディレクトリを検索します。<br><br>`-m --magento`を使用する場合は、このパラメーターを使用しないでください。 | はい（辞書）、いいえ（パッケージ）。 |
| `-m --magento` | この翻訳ディクショナリから言語パッケージを作成する必要があります。 使用する場合は、bin/magentoを含むディレクトリを検索します。 このオプションを選択すると、ディクショナリの各行にテーマまたはモジュールが追加されます。<br><br> サンプルは<br><br>&quot;No Items Found&quot;,&quot;No Items Found&quot;,module,Magento_Wishlist | いいえ |
| `-o --output="<path>"` | 作成する翻訳辞書CSV ファイルの絶対ファイルシステムパスとファイル名を指定します。 入力する値では、大文字と小文字が区別されます。 CSV ファイルの名前は、文字の大文字と小文字を含むロケール名と完全に一致している必要があります。<br><br>このパラメーターを省略すると、出力はstdoutに送信されます。 | いいえ |

>[!INFO]
>
>翻訳ディクショナリから言語パックを作成するには、_必ず_&#x200B;を`-m|--magento` オプションを使用してください。

### 翻訳ガイドライン

単語やフレーズを翻訳する際には、次のガイドラインを使用します。

- 2列目の内容のみを変更します。 フレーズを英語（`US`）から目的の言語に翻訳します。
- ロケール用の辞書を作成する場合は、デフォルトのCommerce文字列を使用します。
- 翻訳中は、プレースホルダーに注意してください：`%1`、`%2`

Commerceでは、プレースホルダーを使用してコンテキスト値を挿入します。これらは&#x200B;_not_&#x200B;翻訳に使用されます。 例：

```text
Product '%1' has been added to shopping cart.
```

値を設定します。

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

結果のフレーズには、各プレースホルダーの少なくとも1つが含まれている必要があります。 例えば、元のフレーズに`%1`から`%3`までのプレースホルダーがあるとします。 翻訳は、これらのプレースホルダーを任意の順序で複数持つことができますが、`%1`、`%2`、`%3`の中に少なくとも1つのプレースホルダーが存在する必要があります。 翻訳に、元の値に存在しないプレースホルダー値を含めることはできません（例：`%4`、`%5`など）。

フレーズの翻訳の例：

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 言語パッケージの作成

翻訳ディクショナリとは異なり、Commerce アプリケーションでは、言語パッケージを使用して、すべての単語やフレーズを翻訳できます。 モジュールやテーマなど、特定のコンポーネントを翻訳辞書を使用して翻訳できます。 [言語パッケージの詳細](https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages)。

この節では、CSV ファイルをモジュールやテーマに書き込む言語パッケージの作成方法について説明します。 言語パッケージを作成するには、次の節で説明するタスクを実行する必要があります。

1. [単語やフレーズを収集して翻訳する](#generate-a-translation-dictionary)。 （`--magento` パラメーターが必要です）。
1. [言語パッケージコマンドを実行します](#run-the-language-package-command)。
1. [&#x200B; ディレクトリとファイルを作成](#create-directories-and-files)。
1. （オプション） [1つの言語に対して複数のパッケージを設定](#configure-multiple-packages-for-a-language)。

### 言語パッケージコマンドの実行

コマンドの使用状況：

```shell
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

次の表に、言語パッケージコマンドのパラメーターと値を示します。

| パラメーター | 値 | 必要ですか？ |
|--- |--- |--- |
| `<source>` | 言語パッケージへの分類に必要な翻訳辞書とメタ情報を組み合わせたCSV ファイルの絶対ファイルシステムパスとファイル名。<br><br>[`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict)を使用してCSV ファイルを作成し、[&#x200B; ディレクトリとファイルの作成](#m2devgde-xlate-files)で説明したように言語パッケージを作成します。 | はい |
| `<locale>` | [ISO 639-1](https://www.iso.org/iso-639-language-codes.html) （言語）および[ISO 3166](https://www.iso.org/iso-3166-country-codes.html) （国）の言語の識別子は、結果のすべてのCSV ファイルのファイル名として使用されます。 例：`de_DE`、`pt_PT`、`pt_BR`。 | はい |
| `-m --mode` | ターゲットファイルが存在する場合は、既存の言語パッケージを置き換えるか、新しい言語パックと結合するかを指定します。 結合すると、既存のフレーズが上書きされ、新しいフレーズが追加されます。<br><br>値：結合または置換（デフォルト）。 | いいえ |
| `-d --allow-duplicates` | 言語パックで重複を許可するには、このオプションを含めます。 そうでなければ、異なる翻訳を持つ複数のエントリで同じフレーズが発生した場合、コマンドはエラーで失敗します。 | いいえ |

### ディレクトリとファイルの作成

言語パッケージは、次の内容を含むCommerce ファイルシステムの`app/i18n/<VendorName>`の下のディレクトリにあります。

- 必要なライセンスファイル
- `composer.json`
- [が言語パッケージを](https://developer.adobe.com/commerce/php/development/build/component-registration/)登録する`registration.php`
- [`language.xml`](#language-package-languagexml) メタ情報ファイル

>[!INFO]
>
>パス全体を小文字にする必要があります。 例えば、[`de_de`](https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php)を参照してください。

これらのファイルを作成するには：

1. `app/i18n`の下にディレクトリを作成します。

   例えば、Commerceの言語パッケージは`app/i18n/magento`にあります

1. 必要なライセンスファイルを追加します。
1. 言語パッケージの依存関係を指定する[`composer.json`](https://developer.adobe.com/commerce/php/development/build/composer-integration/)を追加します。
1. 言語パッケージを[`registration.php`](https://developer.adobe.com/commerce/php/development/build/component-registration/)に登録します
1. 次の節で説明するように、`language.xml`のメタ情報ファイルを追加します。

#### 言語パッケージ language.xml

`language.xml`設定ファイルで言語パッケージを宣言する場合は、このパッケージの言語継承の順序を指定する必要があります。

言語の継承を使用すると、_parent_&#x200B;という既存の翻訳に基づいて、_child_&#x200B;という翻訳を作成できます。 子翻訳は親を上書きします。 ただし、子翻訳がアップロードまたは表示に失敗した場合、またはフレーズや単語が見つからない場合は、Commerceで親ロケールが使用されます。 [言語パッケージ継承の例](#example-of-language-inheritance)。

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

どこで：

- `code` – 言語パッケージのロケール （必須）
- `vendor` - モジュールのベンダー名（必須）
- `package` – 言語パッケージ名（必須）
- `sort_order` - ストアで使用可能な複数の言語パッケージがある場合のパッケージのアップロードの優先度
- `use` – 辞書を継承する親言語パッケージのロケール

必要に応じて、複数の親パッケージを指定できます。 親パッケージは、最初にリストされ、最初に使用されたベースで適用されます。

#### 言語継承の例

言語パッケージが他の2つのパッケージから継承し、それらのパッケージにも親パッケージと「祖父母」パッケージがあるとします。

言語パッケージが2つのパッケージから継承する場合、その`language.xml`は次のようになります。

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

前の例では、

- `language_package_one`は`en_au_package`から継承し、`en_au_package`は`en_ie_package`から継承します
- `language_package_two`は`en_ca_package`から継承し、`en_ca_package`は`en_us_package`から継承します

Commerce アプリケーションが`en_GB` パッケージ内の単語または語句を見つけられない場合、次の順序で他のパッケージを検索します。

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

言語パッケージ間のすべての継承を指定すると、循環する継承チェーンが作成される場合があります。 [Magento\Test\Integrity\App\Language\CircularDependencyTest](https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php) テストを使用して、そのようなチェーンを見つけ、修正します。

### 1つの言語用に複数のパッケージを設定する

ストアの柔軟性を高めるために、ストアに同じ言語の言語パッケージを複数アップロードできます。 したがって、システムは言語で使用可能なすべてのパッケージから1つのパッケージをコンパイルするため、ストアの異なる部分に対して異なるカスタムパッケージを使用できます。

既存の言語の追加パッケージを有効にするには、新しいパッケージに既存の言語コード名を除く任意の名前を付けます（混乱を避けるために）。 次の節で説明するように、言語パッケージの`language.xml` メタ情報ファイルでパッケージの設定を指定します。

## 翻訳コマンドの使用例

次の節では、このトピックで説明するコマンドを使用して翻訳辞書と翻訳パッケージを作成するエンドツーエンドの例を示します。

### 例：モジュールまたはテーマの翻訳辞書の作成

他の販売者に配布するモジュールまたはテーマにドイツ語翻訳を追加するには：

1. モジュールからフレーズを収集します。

   ```shell
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV ファイル名は、文字の大文字と小文字を含め、ロケールが&#x200B;_完全に_&#x200B;一致している必要があります。

1. [これらのガイドライン &#x200B;](#translation-guidelines)を使用して、単語やフレーズを翻訳します。
1. 必要に応じて、`xx_YY.csv`を`/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n`またはモジュールのテーマディレクトリにコピーします（翻訳ディクショナリがモジュール用かテーマ用かによって異なります）。

### 例：言語パッケージの作成

前述の例と同様に、CSV ファイルを生成しますが、モジュールまたはテーマディレクトリを指定する代わりに、Commerce アプリケーションルートディレクトリ全体を指定します。 結果のCSVには、コマンドがコード内で検索できるフレーズが含まれています。

1. モジュールからフレーズを収集します。

   ```shell
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV ファイル名は、文字の大文字と小文字を含め、ロケールが&#x200B;_完全に_&#x200B;一致している必要があります。

1. [これらのガイドライン &#x200B;](#translation-guidelines)を使用して、単語やフレーズを翻訳します。
1. 言語パッケージを作成します。

   ```shell
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 言語パッケージのディレクトリを作成します。

   例：`/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. そのディレクトリに、次のすべてを追加します。

   - ライセンス（必要な場合）
   - `composer.json` （次のサンプル）
   - `registration.php` （次のサンプル）
   - `language.xml` （次のサンプル）

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

