---
title: 詳細 [!DNL JavaScript] バンドル
description: JavaScript のバンドルによって、サーバーリクエストのサイズと頻度を減らす方法について説明します。
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '2137'
ht-degree: 0%

---


# 詳細 [!DNL JavaScript] 束縛

バンドル [!DNL JavaScript] パフォーマンスを向上させるモジュールは、次の 2 つの点を減らすことです。

1. サーバーリクエストの数。
1. これらのサーバーリクエストのサイズ。

モジュラーアプリケーションでは、サーバーリクエストの数が数百に達する可能性があります。 例えば、次のスクリーンショットは、 [!DNL JavaScript] クリーンインストールのホームページに読み込まれたモジュール。

![バンドルなし](../assets/performance/images/noBundling.png)

## マージとバンドル

すぐに使える [!DNL Commerce] では、次の 2 つの方法でサーバーリクエスト数を削減できます。マージとバンドル。 これらの設定は、デフォルトではオフになっています。 これらは、 **[!UICONTROL Stores]** > **設定** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]**&#x200B;またはをコマンドラインから呼び出します。

![バンドル](../assets/performance/images/bundlingImage.png)

### 基本的なバンドル

コマンドラインから組み込みのバンドルを有効にするには：

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

これはネイティブの [!DNL Commerce] システム内に存在するすべてのアセットを組み合わせて、同じサイズのバンドル (bundle_0.js、bundle_1.js .. bundle_x.js) に配布するメカニズム

![[!DNL Commerce] 束縛](../assets/performance/images/magentoBundling.png)

より良い。ただし、ブラウザーは、 [!DNL JavaScript] 必要なものだけではなく、バンドル。

[!DNL Commerce] バンドルは、1 ページあたりの接続数を減らしますが、各ページリクエストでは、要求されたページが 1 つまたは 2 つのバンドル内のファイルに依存している場合でも、すべてのバンドルが読み込まれます。 ブラウザーがバンドルをキャッシュすると、パフォーマンスが向上します。 ただし、ブラウザーがこれらのバンドルを同期的に読み込むので、ユーザーが最初に [!DNL Commerce] ストアフロントは、レンダリングがおこなわれ、ユーザーエクスペリエンスが損なわれるまでに時間がかかる場合があります。

### 基本的な結合

コマンドラインから組み込みマージを有効にするには：

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

このコマンドは、すべての同期を結合します [!DNL JavaScript] ファイルを 1 つのファイルに格納します。 バンドルを有効にせずにマージを有効にすることは、 [!DNL Commerce] は RequireJS を使用します。 バンドルを有効にしない場合、 [!DNL Commerce] は、RequireJS とその設定を結合するだけです。 バンドルとマージの両方を有効にする場合、 [!DNL Commerce] は単一の [!DNL JavaScript] ファイル：

![実世界のマージ](../assets/performance/images/magentoMergingDevWorld.png)

## 実世界のレンダリング時間

以前のバンドルおよびマージされた読み込み時間は、開発環境では非常に良く見えます。 しかし、現実世界では、多くのことがレンダリングの速度を落とす可能性があります。低速な接続、大きな接続しきい値、限られたネットワーク。 また、モバイルデバイスはデスクトップほど高速にレンダリングされません。

実世界向けのストアフロントデプロイメントをテストして準備するには、Chrome のネイティブスロットルプロファイル「Slow 3G」を使用してテストすることをお勧めします。 Slow 3G を使用すると、以前にバンドルされた出力時間は、多くのユーザーの接続の現実を反映するようになりました。

![実世界でのバンドル](../assets/performance/images/magentoBundlingRealWorld.png)

Slow 3G 接続では、クリーンなホームページのすべてのバンドルを読み込むのに約 44 秒かかります [!DNL Commerce] インストール。

バンドルを単一のファイルにマージする場合も同じことが言えます。 次に示すように、ユーザーは、最初のページ読み込みが約 42 秒待つことができます。

![実世界のマージ](../assets/performance/images/magentoMergingRealWorld.png)

より高度なアプローチで [!DNL JavaScript] バンドルすると、これらの読み込み時間を改善できます。

## 高度なバンドル

次の目標を忘れないでください： [!DNL JavaScript] バンドルは、ブラウザーに読み込まれる各ページに対して要求されるアセットの数とサイズを減らすためのものです。 そのためには、ストア内の各ページがアクセスした各ページに共通のバンドルとページ固有のバンドルをダウンロードするだけで済むように、バンドルを構築します。

これを実現する 1 つの方法は、ページタイプ別にバンドルを定義することです。 分類可能 [!DNL Commerce]のページを複数のページタイプ（カテゴリ、製品、CMS、顧客、買い物かご、チェックアウトなど）に分割します。 これらのページタイプの 1 つに分類される各ページは、異なる RequireJS モジュール依存関係のセットを持ちます。 ページタイプ別に RequireJS モジュールをバンドルする場合、最終的にはストア内のページの依存関係をカバーする一部のバンドルのみが表示されます。

例えば、すべてのページに共通する依存関係のバンドル、CMS のみのページのバンドル、カタログのみのページのバンドル、検索のみのページの別のバンドル、チェックアウトページのバンドルが作成される場合があります。

また、目的別にバンドルを作成することもできます。一般的な機能、製品関連の機能、発送機能、チェックアウト機能、税金、フォーム検証について説明します。 バンドルの定義方法は、ユーザーおよびストアの構造次第です。 一部のバンドル戦略は他のバンドル戦略よりも効果が高くなる場合があります。

きれい [!DNL Commerce] をインストールすると、ページのタイプ別にバンドルを分割することで十分なパフォーマンスを得ることができますが、一部のカスタマイズでは、より深い分析や他のアセットの配布が必要になる場合があります。

### 必要なツール

以下の手順では、をインストールし、次のツールに関する知識が必要です。

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](https://phantomjs.org/) （オプション）

### サンプルコード

この記事で使用されるサンプルコードの完全なバージョンは、次の場所で入手できます。

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### パート 1:バンドル設定の作成

#### 1\. build.js ファイルの追加

の作成 `build.js` ファイルを [!DNL Commerce] ルートディレクトリ。 このファイルには、バンドルのビルド設定全体が含まれます。

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

後で、 `optimize:` 設定：_ `none` から `uglify2` バンドル出力を縮小する ただし、現時点では、開発時に、をに設定しておくことができます。 `none` を使用して、より迅速なビルドを実現します。

#### 2\. RequireJS 依存関係、shim、パス、およびマップを追加します。

以下の RequireJS ビルド設定ノードを追加します。 `deps`, `shim`, `paths`、および `map`をビルドファイルに追加します。

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },
})
```

#### 3\. requirejs-config.js インスタンスの値を集計します。

この手順では、 `deps`, `shim`, `paths`、および `map` ストアの設定ノード `requirejs-config.js` を `build.js` ファイル。 これをおこなうには、 **[!UICONTROL Network]** 」タブをクリックし、ストア内の任意のページ（ホームページなど）に移動します。 「ネットワーク」タブに、ストアのインスタンスが `requirejs-config.js` 上部付近のファイル（ここでハイライト表示）:

![RequireJS 設定](../assets/performance/images/RequireJSConfig.png)

このファイル内には、各設定ノード (`deps`, `shim`, `paths`, `map`) をクリックします。 これらの複数のノード値を、build.js ファイルの単一の設定ノードに集計する必要があります。 例えば、ストアの `requirejs-config.js` インスタンスには 15 個の別のエントリがあります `map` ノードを使用する場合、15 個のノードのエントリをすべて 1 つのノードに結合する必要があります `map` ノード内の `build.js` ファイル。 同じことが人にも当てはまる `deps`, `shim`、および `paths` ノード。 この処理を自動化するスクリプトがない場合は、時間がかかる場合があります。

パスを変更する必要があります `mage/requirejs/text` から `requirejs/text` in `paths` 設定ノードを次のように指定します。

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4\. モジュールノードの追加

の最後 `build.js` ファイルを開き、モジュールを追加する[] 配列は、後でストアフロントに定義するバンドルのプレースホルダーとして使用します。

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },

    modules: [],
})
```

#### 5\. RequireJS の依存関係の取得

次の [!DNL RequireJS] 次を使用して、ストアのページタイプからモジュールの依存関係を取得します。

1. [!DNL PhantomJS] コマンドラインから ( [!DNL PhantomJS] インストール済み )。
1. ブラウザーのコンソールで、RequireJS コマンドを使用します。

#### 使用する [!DNL PhantomJS]:

内 [!DNL Commerce] ルートディレクトリ、新しいファイルを作成します。 `deps.js` 以下のコードのをコピーします。 このコードは [!DNL [!DNL PhantomJS]] をクリックしてページを開き、ブラウザーがすべてのページアセットを読み込むのを待ちます。 次に、すべての [!DNL RequireJS] 特定のページの依存関係。

```javascript
"use strict";
var page = require('webpage').create(),
    system = require('system'),
    address;

if (system.args.length === 1) {
    console.log('Usage: $phantomjs deps.js url');
    phantom.exit(1);
} else {
    address = system.args[1];
    page.open(address, function (status) {
        if (status !== 'success') {
            console.log('FAIL to load the address');
        } else {
            setTimeout(function () {
                console.log(page.evaluate(function () {
                    return Object.keys(window.require.s.contexts._.defined);
                }));
                phantom.exit();
            }, 5000);
        }
    });
}
```

内でターミナルを開きます。 [!DNL Commerce] ルートディレクトリに移動し、特定のページタイプを表すストア内の各ページに対してスクリプトを実行します。

<pre>
phantomjs deps.js <i>URL から特定のページへ</i> &gt; <i>text-file-representing-pagetype-dependencies</i>
</pre>

例えば、Luma をテーマにしたサンプルストアの 4 つのページで、4 つのバンドル（ホームページ、カテゴリ、製品、買い物かご）の作成に使用する 4 つのページタイプを表します。

```terminal
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### ブラウザーコンソールを使用するには：

を使用しない場合、 [!DNL PhantomJS]を使用すると、ストアフロントで各ページタイプを表示しているときに、ブラウザーのコンソールから次のコマンドを実行できます。

```shell
Object.keys(window.require.s.contexts._.defined)
```

このコマンド ( [!DNL PhantomJS] スクリプト ) は、 [!DNL RequireJS] 依存関係を参照し、ブラウザーのコンソール内に表示します。 この方法の欠点は、独自のバンドル/ページタイプのテキストファイルを作成する必要があることです。

#### 6\. 出力のフォーマットとフィルター

結合後、 [!DNL RequireJS] ページタイプのテキストファイルへの依存関係は、各ページタイプの依存関係ファイルで次のコマンドを使用して、ファイル内のコンマを改行に置き換えることができます。

```terminal
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

Mixin は重複する依存関係を持つので、各ファイルのすべての Mixin を削除する必要もあります。 各依存ファイルで次のコマンドを使用します。

```terminal
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\. 一意のバンドルおよび共通のバンドルの識別

目的は、 [!DNL JavaScript] すべてのページで必要なファイル。 これにより、ブラウザーは、1 つ以上の特定のページタイプと共に、共通のバンドルを読み込むだけで済みます。

でターミナルを開きます。 [!DNL Commerce] ルートディレクトリに移動し、次のコマンドを使用して、別々のバンドルに分割できる依存関係があることを確認します。

```bash
sort bundle/*.txt |uniq -c |sort -n
```

このコマンドは、 `bundle/*.txt` ファイル。  出力には、各依存関係を含むファイルの数も表示されます。

```terminal
1 buildTools,
1 jquery/jquery.parsequery,
1 jsbuild,
2 jquery/jquery.metadata,
2 jquery/validate,
2 mage/bootstrap,
3 jquery
3 jquery/ui
3 knockoutjs/knockout
...
```

この出力は、を示しています。 `buildTools` は、bundle/*.txt ファイルの 1 つにのみ依存関係です。 この `jquery/jquery.metadata` 依存関係は 2 つの (2) ファイルで、 `es6-collections` は 3 つ (3) のファイルに含まれています。

出力には、3 つのページタイプ（ホームページ、カテゴリ、製品）のみが表示され、次のことがわかります。

- 3 つの依存関係は、1 つのページタイプ（数値 1 で表示）に対してのみ一意です。
- 2 つのページタイプ（数値 2 で表示）に対して、さらに 3 つの依存関係が発生します。
- 最後の 3 つの依存関係は、3 つのページタイプすべてに共通です（3 番目で示されます）。

これにより、どのページタイプがどの依存関係を必要とするかを把握したら、依存関係を別々のバンドルに分割することで、ストアのページ読み込み速度を向上できる可能性が高くなります。

#### 8\. 依存関係配布ファイルを作成する

どのページタイプにどの依存関係が必要かを調べるには、 [!DNL Commerce] ルートディレクトリ： `deps-map.sh` をコピーして、次のコードに格納します。

```shell
awk 'END {
 for (R in rec) {
   n = split(rec[R], t, "/")
   if (n > 1)
     dup[n] = dup[n] ? dup[n] RS sprintf("\t%-20s -->\t%s", rec[R], R) : \
       sprintf("\t%-20s -->\t%s", rec[R], R)
   }
 for (D in dup) {
   printf "records found in %d files:\n\n", D
   printf "%s\n\n", dup[D]
   }
 }
{
 rec[$0] = rec[$0] ? rec[$0] "/" FILENAME : FILENAME
}' bundle/*.txt
```

スクリプトは、 [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

でターミナルを開きます。 [!DNL Commerce] ルートディレクトリに移動し、次のファイルを実行します。

```bash
bash deps-map.sh
```

このスクリプトの出力は、3 つのページタイプの例では次のようになります（ただし、はるかに長くなります）。

```terminal
bundle/product.txt   -->   buildTools,
bundle/category.txt  -->   jquery/jquery.parsequery,
bundle/product.txt   -->   jsbuild,

bundle/category.txt/bundle/homepage.txt -->    jquery/jquery.metadata,
bundle/category.txt/bundle/homepage.txt -->    jquery/validate,
bundle/category.txt/bundle/homepage.txt -->    mage/bootstrap,

bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery/ui,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> knockoutjs/knockout,
```

これは、バンドル設定を構築するのに十分な情報です。

#### 9\. build.js ファイルにバンドルを作成します。

を開きます。 `build.js` 設定ファイルを開き、バンドルを `modules` ノード。 各バンドルでは、次のプロパティを定義する必要があります。

- `name` — バンドルの名前。 例： `bundles/cart` を生成します。 `cart.js` 包む `bundles` サブディレクトリ。

- `create` — バンドルを作成するブール型フラグ ( 値： `true` または `false`) をクリックします。

- `include` — ページの依存関係として含まれるアセット（文字列）の配列。 RequireJS は、すべての依存関係をトレースし、除外されない限り、バンドルに含めます。

- `exclude` — バンドルから除外するバンドルまたはアセットの配列。

```javascript
{
    name: 'bundles/catalog',
    create: true,
    include: [
        'addToWishlist',
        'priceBundle',
        'priceUtils',
        'priceOptions',
        'sticky',
        'productSummary',
        'slide'
    ],
    exclude: [
        'requirejs/require',
        'bundles/default',
        'mage/bootstrap'
    ],
}
```

この例は再利用します `mage/bootstrap` および `requirejs/require` アセットを使用する場合は、同期的に読み込む必要がある最も重要なコンポーネントとコンポーネントの優先度を高くします。 存在するバンドルは次のとおりです。

- `requirejs/require` — 同期的に読み込まれたバンドルのみ
- `mage/bootstrap`— UI コンポーネントを含むブートストラップバンドル
- `bundles/default` — すべてのページにデフォルトのバンドルが必要です
- `bundles/cart` — 買い物かごページに必要なバンドル
- `bundles/shipping` — 買い物かごとチェックアウトページ用の共通バンドル（以前に買い物かごページが開かれ、出荷バンドルが既に読み込まれていた場合でも、チェックアウトページが直接開かれないと仮定）
- `bundles/checkout` — チェックアウトのすべて
- `bundles/catalog` — 商品ページとカテゴリページのすべて

### パート 2:バンドルを生成

次の手順では、より効率的なを生成するための基本的なプロセスについて説明します [!DNL Commerce] バンドル。 このプロセスは好きなように自動化できますが、 `nodejs` および `r.js` 実際にバンドルを生成する。 テーマに [!DNL JavaScript]関連するカスタマイズと再利用はできません `build.js` ファイルを作成する場合、 `build.js` テーマごとの設定

#### 1.静的ストアサイトを生成する

バンドルを生成する前に、静的デプロイメントコマンドを実行します。

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

このコマンドは、設定したテーマとロケールごとに静的ストアの配置を生成します。 例えば、Luma テーマと、英語とフランス語のロケールを使用したカスタムテーマを使用する場合、次の 4 つの静的デプロイメントが生成されます。

- ...luma/en_US
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

すべてのストアテーマとロケールのバンドルを生成するには、各ストアテーマとロケールに対して以下の手順を繰り返します。

#### 2.静的ストアコンテンツを一時ディレクトリに移動します

まず、静的コンテンツをターゲットディレクトリ内のすべてのコンテンツを RequireJS で置き換えるので、静的コンテンツをターゲットディレクトリ内の一時ディレクトリに移動する必要があります。

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

例：

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3. r.js オプティマイザーを実行する

次に、 `build.js` ファイルから [!DNL Commerce]&#39;s ルートディレクトリ。 すべてのディレクトリとファイルへのパスは、作業ディレクトリを基準とした相対パスです。

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

このコマンドは、 `bundles` ターゲットディレクトリのサブディレクトリ ( この場合は `pub/static/frontend/Magento/luma/en_US/bundles`.

新しいバンドルディレクトリの内容のリストは、次のようになります。

```bash
ll pub/static/frontend/Magento/luma/en_US/bundles
```

```terminal
total 1900
drwxr-xr-x  2 root root    4096 Mar 28 11:24 ./
drwxr-xr-x 70 root root    4096 Mar 28 11:24 ../
-rw-r--r--  1 root root  116417 Mar 28 11:24 cart.js
-rw-r--r--  1 root root  187090 Mar 28 11:24 catalog.js
-rw-r--r--  1 root root  307619 Mar 28 11:24 checkout.js
-rw-r--r--  1 root root 1240608 Mar 28 11:24 default.js
-rw-r--r--  1 root root   74233 Mar 28 11:24 shipping.js
```

#### 4.バンドルを使用するように RequireJS を設定する

RequireJS でバンドルを使用するには、 `onModuleBundleComplete` の後のコールバック `modules` ノードを `build.js` ファイル：

```javascript
[
    {
       //...
       exclude: [
           'requirejs/require',
           'bundles/default',
           'bundles/checkout',
           'bundles/cart',
           'bundles/shipping',
           'mage/bootstrap'
       ],
   },
],
bundlesConfigOutFile: `${config.dir}/requirejs-config.js`,
onModuleBundleComplete: function(data) {
    if (this.bundleConfigAppended) {
        return;
    }
    this.bundleConfigAppended = true;

    // bundlesConfigOutFile requires a simple require.config call in order to modify the configuration
    const bundleConfigPlaceholder = `
(function (require) {
require.config({});
})(require);
    `;

    fs.appendFileSync(this.bundlesConfigOutFile, bundleConfigPlaceholder);
}
```

#### 5.デプロイコマンドの再実行

次のコマンドを実行してデプロイします。

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

開く `requirejs-config.js` 内 `pub/static/frontend/Magento/luma/en_US` ディレクトリに、RequireJS がバンドル設定の呼び出しでファイルに追加されていることを確認します。

```javascript
require.config({
    bundles: {
        "bundles/default": ["mage/template", "mage/apply/scripts", "mage/apply/main", "mage/mage", "mage/translate", "mage/loader"],
        "bundles/cart": ["Magento_Ui/js/lib/validation/utils", "Magento_Ui/js/lib/validation/rules", "Magento_Ui/js/lib/validation/validation"]
    }
}
```

>[!NOTE]
>
>バンドルを設定する場合、 `requirejs.config()` の呼び出しは、実行したい順序で実行されます。呼び出しは、表示される順序で実行されます。

#### 6.結果をテストする

ページが読み込まれた後、ブラウザーが様々な依存関係とバンドルを読み込んでいることに注意してください。 例えば、「Slow 3G」プロファイルの結果は次のようになります。

![2 倍の速さ](../assets/performance/images/TwiceAsFast.png)

空のホームページのページ読み込み時間が、ネイティブのホームページを使用する場合の 2 倍の速さになりました。 [!DNL Commerce] バンドル。 でももっと良いことができます

#### 7.バンドルを最適化します。

gzip 圧縮された場合でも、 [!DNL JavaScript] ファイルは大きいままです。 縮小用の RequireJS を使用して縮小します。 [!DNL JavaScript] 良い結果に。

オプティマイザーを `build.js` ファイル、追加 `uglify2` を、 `build.js` ファイル：

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

結果は次のように重要になります。
![3 倍の速さ](../assets/performance/images/ThreeTimesFaster.png)

ロード時間がネイティブの場合と比べて 3 倍も高速になりました。 [!DNL Commerce] バンドル。
