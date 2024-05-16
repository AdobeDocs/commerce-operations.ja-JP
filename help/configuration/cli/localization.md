---
title: 翻訳辞書と言語パッケージ
description: 翻訳辞書を生成し、言語パッケージを作成する方法を説明します。
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---

# 場所

{{file-system-owner}}

Commerce翻訳を使用すると、次の情報を生成することで、複数の地域や市場に合わせてストアをカスタマイズおよびローカライズできます。

- **翻訳辞書**（カスタマイズまたは翻訳する便利な方法） _一部_ 単語およびフレーズ（カスタムモジュールやテーマの単語やフレーズなど）。
- **言語パッケージ** 翻訳できる _いずれか、またはすべて_ Commerce アプリケーション内の単語およびフレーズ。

参照： [翻訳の概要].

## 翻訳辞書の生成

を生成できます [翻訳辞書] 既存の文字列をカスタマイズするには、カスタムモジュールで単語や語句を翻訳するか、テーマをローカライズするか、言語パッケージを作成します。

翻訳を開始するには、コマンドを使用して、既存のすべてのフレーズと単語のリストを収集した辞書 CSV ファイルを生成します。

辞書を生成して翻訳を開始するには：

1. 翻訳コレクションコマンドを使用して、有効なコンポーネントから翻訳可能な単語や語句を抽出する。 コンテンツを CSV ファイルに抽出します。
1. 既存の単語やフレーズを翻訳してください。 必要に応じて、カスタム用語を追加できます。

   翻訳済み辞書を使用するオプションがあります。

1. 翻訳辞書を言語パッケージにまとめ、Commerce ストア管理者に提供することができます。

1. 管理者には、ストア管理者がいます。 [翻訳を設定します].

コマンドオプション：

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

次の表で、パラメーターと値について説明します。

| パラメーター | 値 | 必須？ |
|--- |--- |--- |
| `<path to directory to translate>` | 翻訳可能なコードを持つディレクトリ（つまり、翻訳するフレーズを含む PHP、PHTML または XML ファイル）へのパス。<br><br>入力したパスから検索が開始され、そこに含まれるすべてのファイルとサブディレクトリが検索されます。<br><br>を使用する場合は、このパラメーターを使用しないでください `-m --magento`. | はい（辞書）、いいえ（パッケージ）。 |
| `-m --magento` | この翻訳辞書から言語パッケージを作成するために必要です。 このプロパティを使用すると、bin/magento を含むディレクトリが検索されます。 このオプションを選択すると、辞書の各行にテーマまたはモジュールが追加されます。<br><br>次に例を示します。<br><br>&quot;No Items Found&quot;,&quot;No Items Found&quot;,module,Magento_ウィッシュリスト | 不可 |
| `-o --output="<path>"` | 作成する翻訳ディクショナリ CSV ファイルの絶対ファイルシステムパスとファイル名を指定します。 入力する値は、大文字と小文字が区別されます。 CSV ファイルの名前は、文字の大文字と小文字を含め、ロケール名と完全に一致する必要があります。<br><br>このパラメータを省略すると、出力は stdout に送られます。 | 不可 |

>[!INFO]
>
>翻訳辞書から言語パックを作成するには、次の操作を実行します _が_ を使用する `-m|--magento` オプション。

### 翻訳ガイドライン

単語やフレーズを翻訳する際は、次のガイドラインに従います。

- 2 番目の列の内容のみを変更します。 フレーズを英語から翻訳する（`US`）から目的の言語に変更します。
- ロケール用の辞書を作成する場合、デフォルトのCommerce文字列を使用します。
- 翻訳中は、プレースホルダーに注意を払います。 `%1`, `%2`

Commerceでは、プレースホルダーを使用してコンテキスト値を挿入します。 _ではない_ 翻訳に使用します。 例：

```text
Product '%1' has been added to shopping cart.
```

次の値が入力されます。

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

結果として得られるフレーズには、各プレースホルダーが少なくとも 1 つ含まれている必要があります。 例えば、からプレースホルダーがあるとします `%1` 対象： `%3` 元のフレーズで。 翻訳には、これらのプレースホルダーを任意の順序で含めることができますが、少なくとも 1 つのプレースホルダーが必要です。 `%1`, `%2`、および `%3`. 翻訳には、元の値にプレースホルダーの値が含まれていないことを含めることはできません（例： `%4`, `%5`など）。

フレーズの翻訳例を次に示します。

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 言語パッケージの作成

翻訳辞書とは対照的に、言語パッケージを使用して、Commerce アプリケーションの一部またはすべての単語やフレーズを翻訳できます。 翻訳辞書を使用して、モジュールやテーマなどの特定のコンポーネントを翻訳できます。 [言語パッケージの詳細情報].

この節では、CSV ファイルをモジュールとテーマに書き込む言語パッケージの作成方法について説明します。 言語パッケージを作成するには、次の節で説明するタスクを実行する必要があります。

1. [単語やフレーズの収集と翻訳](#generate-a-translation-dictionary). （ `--magento` パラメーターが必要です。）
1. [言語パッケージコマンドを実行します](#run-the-language-package-command).
1. [ディレクトリとファイルの作成](#create-directories-and-files).
1. （オプション。） [1 つの言語に対して複数のパッケージを設定](#configure-multiple-packages-for-a-language).

### 言語パッケージコマンドを実行します

コマンドの使用法：

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

次の表に、言語パッケージコマンドのパラメーターと値を示します。

| パラメーター | 値 | 必須？ |
|--- |--- |--- |
| `<source>` | 言語パッケージへの分類に必要な翻訳辞書とメタ情報の組み合わせを含む、CSV ファイルの絶対ファイルシステムパスとファイル名。<br><br>使用方法 [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) csv ファイルを作成するには、言語パッケージを作成します（を参照） [ディレクトリとファイルの作成](#m2devgde-xlate-files). | はい |
| `<locale>` | [ISO 639-1] （言語）と [ISO 3166] （国）生成されるすべての CSV ファイルのファイル名として使用される言語の識別子。 例： `de_DE`, `pt_PT`, `pt_BR`. | はい |
| `-m --mode` | ターゲット ファイルが存在する場合、既存の言語パッケージを置き換えるか、新しい言語パックと結合するかを指定します。 結合すると、存在するすべてのフレーズが上書きされ、新しいフレーズが追加されます。<br><br>値：結合または置換（デフォルト）。 | 不可 |
| `-d --allow-duplicates` | 言語パックで重複を許可するには、このオプションを含めます。 そうでない場合、異なる翻訳を持つ複数のエントリで同じフレーズが検出されると、コマンドはエラーで失敗します。 | 不可 |

### ディレクトリとファイルの作成

言語パッケージは、の下のディレクトリにあります `app/i18n/<VendorName>` Commerce ファイルシステムに以下の内容を追加します。

- 必要なライセンスファイル
- `composer.json`
- `registration.php` その [レジスタ] 言語パッケージ
- [`language.xml`](#language-package-languagexml) メタデータ ファイル

>[!INFO]
>
>パス全体を小文字にする必要があります。 例えば、 [`de_de`].

これらのファイルを作成するには：

1. の下にディレクトリを作成します `app/i18n`.

   例えば、Commerce言語パッケージは次の場所にあります。 `app/i18n/magento`

1. 必要なライセンスファイルを追加します。
1. 追加 [`composer.json`] 言語パッケージの依存関係を指定します。
1. 言語パッケージの登録 [`registration.php`]
1. 追加 `language.xml` 次のセクションで説明するメタ情報ファイル。

#### 言語パッケージ language.xml

で言語パッケージを宣言する場合 `language.xml` 設定ファイルです。このパッケージの言語の継承のシーケンスを指定する必要があります。

言語の継承によって、という翻訳を作成できます。 _子_ ～と呼ばれる既存の翻訳に基づく _親_. 子翻訳は親よりも優先されます。 ただし、子翻訳のアップロードや表示に失敗した場合や、フレーズや単語が欠落している場合、Commerceでは親ロケールが使用されます。 [言語パッケージの継承の例](#example-of-language-inheritance).

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

- `code` – 言語パッケージのロケール （必須）
- `vendor`- モジュールのベンダー名（必須）
- `package` – 言語パッケージ名（必須）
- `sort_order`- ストアで使用できる言語パッケージが複数ある場合のパッケージのアップロードの優先度
- `use` – 辞書の継承元となる親言語パッケージのロケール

必要に応じて、複数の親パッケージを指定できます。 親パッケージは、リストに最初に表示され、最初に使用される順序で適用されます。

#### 言語の継承の例

言語パッケージが他の 2 つのパッケージから継承し、それらのパッケージに親パッケージと「grandparent」パッケージも含まれているとします。

言語パッケージが 2 つのパッケージから継承される場合、その `language.xml` 次のようになります。

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

- `language_package_one` 継承元 `en_au_package` および `en_au_package` 継承元 `en_ie_package`
- `language_package_two` 継承元 `en_ca_package` および `en_ca_package` 継承元 `en_us_package`

Commerce アプリケーションがに単語またはフレーズを見つけることができない場合 `en_GB` パッケージは、次の順序で他のパッケージを検索します。

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

言語パッケージ間のすべての継承を指定すると、循環継承チェーンが作成される可能性があります。 使用方法 [Magento\Test\Integrity\App\Language\CircularDependencyTest] このようなチェーンを見つけて修正するテスト。

### 1 つの言語に対して複数のパッケージを設定

ストアの柔軟性を高めるために、同じ言語の複数の言語パッケージをストアにアップロードできます。 したがって、システムは特定の言語で使用可能なすべてのパッケージから 1 つのパッケージをコンパイルするので、ストアの異なる部分に対して異なるカスタムパッケージを使用できます。

既存の言語に対して追加のパッケージを有効にするには、（混乱を避けるために）既存の言語コード名を除く任意の名前を新しいパッケージに付けます。 言語パッケージのに含まれるパッケージの設定を指定します `language.xml` 次のセクションで説明するメタ情報ファイル。

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
   >CSV ファイル名は、 _完全に一致_ 文字の大文字と小文字を含むロケール。

1. を使用して単語やフレーズを翻訳する [このガイドライン](#translation-guidelines).
1. 必要に応じて、をコピーします `xx_YY.csv` 対象： `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` またはモジュールのテーマディレクトリに移動します（翻訳辞書がモジュール用かテーマ用かによって異なります）。

### 例：言語パッケージを作成する

前の例と同様に、CSV ファイルを生成しますが、モジュールまたはテーマディレクトリを指定する代わりに、Commerce アプリケーションのルートディレクトリ全体を指定します。 結果の CSV には、コマンドがコード内で見つけることができたすべてのフレーズが含まれています。

1. モジュールからフレーズを収集します。

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV ファイル名は、 _完全に一致_ 文字の大文字と小文字を含むロケール。

1. を使用して単語やフレーズを翻訳する [このガイドライン](#translation-guidelines).
1. 言語パッケージを作成します。

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 言語パッケージのディレクトリを作成します。

   例：`/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. このディレクトリに、次のすべてを追加します。

   - ライセンス（必要な場合）
   - `composer.json` （次に示す例）
   - `registration.php` （次に示す例）
   - `language.xml` （次に示す例）

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
    * Copyright &copy; Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
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
   /**
   * Copyright &copy; Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[翻訳の概要]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[翻訳辞書]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[翻訳を設定します]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[言語パッケージの詳細情報]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[レジスタ]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[&#39;de_de&#39;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&#39;registration.php&#39;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
