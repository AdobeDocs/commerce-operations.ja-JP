---
title: 翻訳辞書と言語パッケージ
description: 翻訳辞書を生成し、言語パッケージを構築する方法を説明します。
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 0%

---


# ローカリゼーション

{{file-system-owner}}

コマース翻訳を使用すると、次の情報を生成することで、複数の地域や市場向けにストアをカスタマイズし、ローカライズすることができます。

- **翻訳辞書**（カスタマイズや翻訳に便利な方法） _some_ カスタムのモジュールやテーマの単語やフレーズなど。
- **言語パッケージ** 翻訳を可能にする _いずれかまたはすべて_ コマースアプリケーションの単語とフレーズ。

詳しくは、 [翻訳の概要].

## 翻訳辞書を生成

次の項目を生成できます。 [翻訳辞書] 既存の文字列のカスタマイズ、カスタムモジュール内の単語や語句の翻訳、テーマのローカライズ、作成を行うには [言語パッケージ](https://glossary.magento.com/language-package).

翻訳を開始するには、コマンドを使用して、既存のすべての語句を収集したリストで辞書の CSV ファイルを生成します。

辞書を生成して翻訳を開始するには：

1. 翻訳コレクションコマンドを使用して、有効なコンポーネントから翻訳可能な単語やフレーズを抽出します。 コンテンツが CSV ファイルに抽出されます。
1. 既存の単語やフレーズを翻訳します。 必要に応じて、追加のカスタムキーワードを追加できます。

   翻訳済みの辞書を使用するオプションがあります。

1. 翻訳辞書を言語パッケージにパッケージ化し、そのパッケージをコマースストア管理者に提供することができます。

1. 管理者で、ストア管理者 [翻訳を設定します].

コマンドオプション：

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

次の表に、パラメータと値を示します。

| パラメータ | 値 | 必須？ |
|--- |--- |--- |
| `<path to directory to translate>` | 翻訳可能なコードを含むディレクトリへのパス。つまり、翻訳するフレーズを持つ PHP、PHTML、XML ファイルです。<br><br>入力したパスで検索が開始され、そのパスに含まれるすべてのファイルとサブディレクトリが検索されます。<br><br>次を使用する場合は、このパラメーターを使用しないでください： `-m --magento`. | はい（辞書）、いいえ（パッケージ）。 |
| `-m --magento` | この翻訳辞書から言語パッケージを作成するために必要です。 使用した場合、bin/magento を含むディレクトリを検索します。 このオプションは、辞書の各行にテーマまたはモジュールを追加します。<br><br>次に例を示します。<br><br>&quot;項目が見つかりません&quot;,&quot;項目が見つかりません&quot;,module,Magento_Wishlist | いいえ |
| `-o --output="<path>"` | 作成する翻訳辞書の CSV ファイルの絶対ファイルシステムパスとファイル名を指定します。 入力した値は、大文字と小文字が区別されます。 CSV ファイルの名前は、大文字と小文字を含むロケール名と完全に一致する必要があります。<br><br>このパラメータを省略した場合、出力は stdout に送られます。 | いいえ |

>[!INFO]
>
>翻訳辞書から言語パックを作成するには、次の手順を実行します。 _必須_ を使用します。 `-m|--magento` オプション。

### 翻訳のガイドライン

単語や語句を翻訳する際は、次のガイドラインに従います。

- 2 番目の列のコンテンツのみを変更します。 英語 (`US`) を目的の言語に追加します。
- ロケールの辞書を作成する場合は、デフォルトのコマース文字列を使用します。
- 翻訳時に、プレースホルダーに注意を払います。 `%1`, `%2`

Commerce は、プレースホルダーを使用してコンテキスト値を挿入します。これらは _not_ 翻訳に使用されます。 例：

```text
Product '%1' has been added to shopping cart.
```

値を入力：

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

生成されるフレーズには、各プレースホルダーの少なくとも 1 つを含める必要があります。 例えば、 `%1` から `%3` 元のフレーズで 翻訳には、任意の順序でこれらのプレースホルダーをいくつでも含めることができますが、少なくとも 1 つは `%1`, `%2`、および `%3`. 翻訳に、元の値に存在しないプレースホルダー値 ( 例えば、 `%4`, `%5`など )。

フレーズの翻訳例：

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## 言語パッケージの作成

翻訳辞書とは異なり、言語パッケージを使用して、コマースアプリケーションの任意の単語またはすべての語句を翻訳できます。 翻訳辞書を使用して、モジュールやテーマなどの特定のコンポーネントを翻訳できます。 [言語パッケージの詳細を表示].

この節では、CSV ファイルをモジュールやテーマに書き込む言語パッケージの作成方法について説明します。 言語パッケージを作成するには、次の節で説明するタスクを実行する必要があります。

1. [語句の収集と翻訳](#generate-a-translation-dictionary). ( `--magento` パラメーターが必要です。)
1. [言語パッケージコマンドを実行します。](#run-the-language-package-command).
1. [ディレクトリとファイルの作成](#create-directories-and-files).
1. （オプション） [1 つの言語に対する複数のパッケージの設定](#configure-multiple-packages-for-a-language).

### 言語パッケージコマンドを実行します。

コマンドの使用：

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

次の表に、言語パッケージコマンドのパラメータと値を示します。

| パラメータ | 値 | 必須？ |
|--- |--- |--- |
| `<source>` | 言語パッケージへの分類に必要な、組み合わされた翻訳辞書とメタ情報を含む CSV ファイルの絶対ファイルシステムパスとファイル名。<br><br>用途 [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) CSV ファイルを作成するには、 [ディレクトリとファイルの作成](#m2devgde-xlate-files). | はい |
| `<locale>` | [ISO 639-1] （言語）および [ISO 3166] （国）生成されるすべての CSV ファイルのファイル名として使用される言語の識別子。 例： `de_DE`, `pt_PT`, `pt_BR`. | はい |
| `-m --mode` | ターゲットファイルが存在する場合は、既存の言語パッケージを置き換えるか、新しい言語パックとマージするかを指定します。 マージは、既存のフレーズを上書きし、新しいフレーズを追加します。<br><br>値：結合または置換（デフォルト）。 | いいえ |
| `-d --allow-duplicates` | 言語パックでの重複を許可するには、このオプションを含めます。 そうしないと、異なる翻訳を持つ複数のエントリで同じフレーズが検出された場合、コマンドはエラーで失敗します。 | いいえ |

### ディレクトリとファイルの作成

言語パッケージは、 `app/i18n/<VendorName>` 次の内容を含む Commerce ファイルシステム内：

- 必要なライセンスファイル
- `composer.json`
- `registration.php` その [登録者] 言語パッケージ
- [`language.xml`](#language-package-languagexml) メタ情報ファイル

>[!INFO]
>
>パス全体を小文字にする必要があります。 例えば、 [`de_de`].

これらのファイルを作成するには：

1. の下にディレクトリを作成します。 `app/i18n`.

   例えば、コマース言語パッケージは、 `app/i18n/magento`

1. 必要なライセンスファイルを追加します。
1. 追加 [`composer.json`] 言語パッケージの依存関係を指定します。
1. 言語パッケージの登録先 [`registration.php`]
1. 追加 `language.xml` 次の節で説明するメタ情報ファイル。

#### 言語パッケージ language.xml

で言語パッケージを宣言する場合 `language.xml` 設定ファイルを使用する場合は、このパッケージの言語継承のシーケンスを指定する必要があります。

言語の継承により、 _子_ 既存の翻訳に基づく _親_. 子の翻訳は親を上書きします。 ただし、子翻訳のアップロードや表示に失敗した場合や、フレーズや単語が欠落している場合は、親が使用されます [ロケール](https://glossary.magento.com/locale). [言語パッケージの継承の例](#example-of-language-inheritance).

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

- `code` — 言語パッケージのロケール（必須）
- `vendor` — モジュールのベンダー名（必須）
- `package` — 言語パッケージ名（必須）
- `sort_order`—1 つのストアに複数の言語パッケージが使用可能な場合の、パッケージのアップロードの優先順位
- `use` — 辞書の継承元となる親言語パッケージロケール

必要に応じて、複数の親パッケージを指定できます。 親パッケージは、最初にリストされ、最初に使用されたベースで適用されます。

#### 言語継承の例

言語パッケージが他の 2 つのパッケージを継承し、それらのパッケージにも親パッケージと祖父母パッケージがあるとします。

言語パッケージが 2 つのパッケージを継承する場合は、 `language.xml` 次のようになります。

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

前述の例では、

- `language_package_one` から継承 `en_au_package` および `en_au_package` から継承 `en_ie_package`
- `language_package_two` から継承 `en_ca_package` および `en_ca_package` から継承 `en_us_package`

Commerce アプリケーションが `en_GB` パッケージの場合、次の順番で他のパッケージを参照します。

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

言語パッケージ間のすべての継承を指定すると、循環継承チェーンが作成される場合があります。 用途 [Magento\Test\Integrity\App\Language\CircularDependencyTest] このようなチェーンを見つけて修正するためのテスト。

### 1 つの言語に対する複数のパッケージの設定

ストアの柔軟性を高めるために、同じ言語の複数の言語パッケージをストアにアップロードできます。 したがって、1 つの言語で使用可能なすべてのパッケージから 1 つのパッケージをコンパイルするので、ストアの各部分に異なるカスタムパッケージを使用できます。

既存の言語に対して追加のパッケージを有効にするには、新しいパッケージに既存の言語コード名を除く任意の名前を付けます（混乱を避けるため）。 言語パッケージの `language.xml` 次の節で説明するメタ情報ファイル。

## 翻訳コマンドの使用例

以下の節では、このトピックで説明するコマンドを使用して翻訳辞書と翻訳パッケージを作成するエンドツーエンドの例を示します。

### 例：モジュールまたはテーマの翻訳辞書を作成する

他のマーチャントに配布するモジュールまたはテーマにドイツ語の翻訳を追加するには：

1. モジュールからフレーズを収集します。

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV ファイル名を指定する必要があります _完全に一致_ ロケール（文字の大文字と小文字を含む）。

1. 次を使用して語句を翻訳： [これらのガイドライン](#translation-guidelines).
1. 必要に応じて、 `xx_YY.csv` から `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` またはモジュールの theme ディレクトリ（翻訳辞書がモジュール用かテーマ用かに応じて）に書き込まれます。

### 例：言語パッケージの作成

前の例と同様に、CSV ファイルを生成しますが、モジュールやテーマディレクトリを指定する代わりに、Commerce アプリケーションのルートディレクトリ全体を指定します。 結果の CSV には、コード内でコマンドで見つかったフレーズが含まれます。

1. モジュールからフレーズを収集します。

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV ファイル名を指定する必要があります _完全に一致_ ロケール（文字の大文字と小文字を含む）。

1. 次を使用して語句を翻訳： [これらのガイドライン](#translation-guidelines).
1. 言語パッケージを作成します。

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. 言語パッケージ用のディレクトリを作成します。

   例：`/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. このディレクトリに、以下のすべてを追加します。

   - ライセンス（必要な場合）
   - `composer.json` （以下のサンプル）
   - `registration.php` （以下のサンプル）
   - `language.xml` （以下のサンプル）

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
    * Copyright © Magento, Inc. All rights reserved.
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
   * Copyright © Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Translate theme strings]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/translate_theory.html
[翻訳の概要]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html
[Community Engineering contributions]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#translations-project
[翻訳辞書]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-dictionaries
[翻訳を設定します]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[言語パッケージの詳細を表示]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-languagepack
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[登録者]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[&#39;de_de&#39;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&#39;composer.json&#39;]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/composer-integration.html
[&#39;registration.php&#39;]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
