---
title: system.xml リファレンス
description: システムの XML ファイルがコマースアプリケーションの設定を管理する方法を説明します。
feature: Configuration, System
badge: label="寄稿：David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="デビッド・ランバウアー"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: e231a27d70e29b01c872b0655168e31f590d4876
workflow-type: tm+mt
source-wordcount: '2663'
ht-degree: 0%

---

# system.xml リファレンス

The `system.xml` ファイルを使用すると、Commerce システムの設定を管理できます。 このトピックを、 `system.xml` ファイル。 The `system.xml` ファイルは、 `etc/adminhtml/system.xml` 特定の Commerce 2 拡張機能内。

次のコードスニペットは、ファイルのベアスケルトンを示しています。

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>IDE で即座に XSD 検証を行う場合は、を実行できます。 `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## タブ//セクション//グループ//フィールド

Adobe Analytics の `system.xml` ファイルを指定する場合、互いに関連する 4 つの異なるタイプのエンティティを定義できます。 次の節では、タブ、セクション、グループ、フィールド間の関係について説明します。 次のスクリーンショットは、Admin バックエンドでの Commerce 2 システム設定を示しています。
赤い正方形は、 `system.xml` ファイル：

![管理画面に設定済みのセクションが表示されたスクリーンショット。](../../assets/configuration/magento2-system-configuration.png)

タブは、様々な設定領域を意味的に分割するために使用されます。 各タブには 1 つ以上のセクションを含めることができます。このセクションはサブメニューとしても参照できます。 1 つのセクションに 1 つ以上のグループが含まれています。
各グループには、1 つ以上のフィールドが一覧表示されます。 グループを使用して、次のフィールドの一般的な説明を追加することもできます。 既に述べたように、各グループには 1 つ以上のフィールドを設定できます。 フィールドは、システム設定コンテキストで最も小さいエンティティです。

## タブ

A `<tab>` — タグは、システム構成の既存のタブまたは新しいタブへの参照です。

### タブ属性リファレンス

A `<tab>`-Tag は次の属性を持つことができます。

| 属性 | 説明 | タイプ | 必須 |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | セクションを参照する際に使用される識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能にするフィールドを定義します。 提供 `label` ラベルを翻訳可能にする。 | `string` | オプション |
| `sortOrder` | セクションの並べ替え順を定義します。 大きい数字はセクションをページの下部に、小さい数字はセクションを上に押します。 | `float` | オプション |
| `class` | 定義済みの CSS クラスを、レンダリングされたタブHTML要素に追加します。 | `string` | オプション |

### タブノードの参照

A `<tab>`-Tag は次の子を持つことができます。

| ノード | 説明 | タイプ |
|---------|------------------------------------------------------|----------|
| `label` | フロントエンドに表示するラベルを定義します。 | `string` |

### 例：タブの作成

次のコードスニペットは、サンプルデータを含む新しいタブの作成方法を示しています。

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

上のスニペットは、識別子を持つ新しいタブを作成します `A_UNIQUE_ID`. を `translate`-attribute が定義され、ラベルを参照する場合、 `label`-node は翻訳可能です。 レンダリングプロセス中に、CSS クラス `a-custom-css-class-to-style-this-tab` が、このタブ用に作成されたHTML要素に適用されます。
The `sortOrder`-attribute に `10` レンダリング時のすべてのタブのリストにおけるタブの位置を定義します。

## セクション

A `<section>` — タグは、システム構成内の既存のセクションまたは新しいセクションへの参照です。

### セクション属性リファレンス

A `<section>`-Tag は次の属性を持つことができます。

| 属性 | 説明 | タイプ | 必須 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | セクションを参照する際に使用される識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能にするフィールドを定義します。 提供 `label` ラベルを翻訳可能にする。 | `string` | オプション |
| `type` | レンダリングされたHTML要素の入力タイプを定義します。 デフォルトはです。 `text`. | `string` | オプション |
| `sortOrder` | セクションの並べ替え順を定義します。 大きい数字はセクションをページの下部に押し出し、小さい数字はセクションを上部に押し出します。 | `float` | オプション |
| `showInDefault` | セクションをデフォルトの設定範囲に表示するかどうかを定義します。 指定 `1` セクションを表示し、 `0` をクリックして、「 」セクションを非表示にします。 | `int` | オプション |
| `showInStore` | セクションをストアレベルで表示するかどうかを定義します。 指定 `1` セクションを表示し、 `0` をクリックして、「 」セクションを非表示にします。 | `int` | オプション |
| `showInWebsite` | セクションを Web サイトレベルで表示するかどうかを定義します。 指定 `1` セクションを表示し、 `0` をクリックして、「 」セクションを非表示にします。 | `int` | オプション |
| `canRestore` | セクションをデフォルトに戻すことができるかどうかを定義します。 | `int` | オプション |
| `advanced` | 100.0.2 以降で非推奨（廃止予定）となりました。 | `bool` | オプション |
| `extends` | 別のセクションの識別子を指定することで、このノードのコンテンツは、参照したセクションを拡張します。 | `string` | オプション |

### セクションノードのリファレンス

A `<section>`-Tag は次の子を持つことができます。

| ノード | 説明 | タイプ |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | フロントエンドに表示するラベルを定義します。 | `string` |
| `class` | 定義済みの CSS クラスをレンダリングされたセクションHTML要素に追加します。 | `string` |
| `tab` | 関連するタブを参照します。 タブの ID が必要です。 | `typeTabId` |
| `header_css` | この記述の時点では使用も評価もされていません。 | `string` |
| `resource` | ACL リソースを参照して、このセクションの権限設定を指定します。 | `typeAclResourceId` |
| `group` | 1 つ以上のサブグループを定義します。 | `typeGroup` |
| `frontend_model` | 別のフロントエンドモデルを指定して、レンダリングを変更し、出力を変更します。 | `typeModel` |
| `include` | 追加の `system_include.xsd` 互換性のあるファイル。 通常、大きな構造に使用されます `system.xml` ファイル。 | `includeType` |

### 例：セクションを作成してタブに割り当てる

次のコードスニペットは、新しいセクションを作成する基本的な使用方法を示しています。

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

上記の節では、ID を定義します `A_UNIQUE_SECTION_ID`は、デフォルトの設定ビューとストアコンテキストに表示されます。 The `label`-node は翻訳可能です。 セクションは、ID を持つタブに関連付けられています `A_UNIQUE_ID`. セクションには、ACL で権限が定義されているユーザーのみがアクセスできます `VENDOR_MODULE::path_to_the_acl_resource`.

## グループ

The `<group>`-Tag は、フィールドをグループ化するために使用します。

### グループ属性のリファレンス

A `<group>`-Tag は次の属性を持つことができます。

| 属性 | 説明 | タイプ | 必須 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | グループを参照する際に使用される識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能にするフィールドを定義します。 提供 `label` ラベルを翻訳可能にする。 複数のフィールドはスペースで区切る必要があります。 | `string` | オプション |
| `type` | レンダリングされたHTML要素の入力タイプを定義します。 デフォルトはです。 `text`. | `string` | オプション |
| `sortOrder` | セクションの並べ替え順を定義します。 大きい数字はセクションをページの下部に押し出し、小さい数字はセクションを上部に押し出します。 | `float` | オプション |
| `showInDefault` | グループをデフォルトの設定範囲に表示するかどうかを定義します。 指定 `1` グループを表示し、 `0` をクリックして、グループを非表示にします。 | `int` | オプション |
| `showInStore` | グループをストアレベルで表示するかどうかを定義します。 指定 `1` グループを表示し、 `0` をクリックして、グループを非表示にします。 | `int` | オプション |
| `showInWebsite` | グループを Web サイトレベルで表示するかどうかを定義します。 指定 `1` グループを表示し、 `0` をクリックして、グループを非表示にします。 | `int` | オプション |
| `canRestore` | グループをデフォルトに復元できるかどうかを定義します。 | `int` | オプション |
| `advanced` | 100.0.2 以降で非推奨（廃止予定）となりました。 | `bool` | オプション |
| `extends` | 別のグループの識別子を指定することで、このノードのコンテンツは、参照したセクションを拡張します。 | `string` | オプション |

### グループノードの参照

A `<group>`-Tag は次の子を持つことができます。

| ノード | 説明 | タイプ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | フロントエンドに表示するラベルを定義します。 | `string` |
| `fieldset_css` | 1 つ以上の CSS クラスをグループフィールドセットに追加します。 | `string` |
| `frontend_model` | 別のフロントエンドモデルを指定して、レンダリングを変更し、出力を変更します。 | `typeModel` |
| `clone_model` | フィールドを複製する特定のモデルを指定します。 | `typeModel` |
| `clone_fields` | フィールドの複製を有効または無効にします。 | `int` |
| `help_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `more_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `demo_link` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `comment` | グループラベルの下にコメントを追加します。 次を使用： `<![CDATA[//]]>` HTMLを適用できます。 | `string` |
| `hide_in_single_store_mode` | グループをシングルストアモードで表示するかどうかを指定します。 `1` グループを非表示にします。 `0` グループを表示します。 | `int` |
| `field` | このグループで使用可能な 1 つ以上のフィールドを定義します。 | `field` |
| `group` | 1 つ以上のサブグループを定義します。 | `unbounded` |
| `depends` | 他のフィールドへの依存関係を宣言するために使用できます。 特定のフィールドの値が `1`. このノードは、 `section/group/field`-string. | `depends` |
| `attribute` | カスタム属性はフロントエンドモデルで使用できます。 通常、特定のフロントエンドモデルをより動的にするために使用します。 | `attribute` |
| `include` | 追加の `system_include.xsd` 互換性のあるファイル。 通常、大きな構造に使用されます `system.xml` ファイル。 | `includeType` |

>[!WARNING]
>
>ノード `more_url`, `demo_url` および `help_url` は、1 回だけ使用される PayPal フロントエンドモデルによって定義されます。 これらのノードは再利用できません。

### 例：特定のセクションのグループを作成する

次のコードスニペットは、新しいグループを作成する基本的な使用方法を示しています。

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

上記のグループは ID を定義します `A_UNIQUE_GROUP_ID`は、デフォルトの設定ビューとストアコンテキストに表示されます。 両方の `label` そして `comment` は翻訳可能としてマークされます。

## フィールド

The `<field>` — タグは `<group>` — 特定の設定値を定義するタグ。

### フィールド属性のリファレンス

A `<field>`-Tag は次の属性を持つことができます。

| 属性 | 説明 | タイプ | 必須 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | フィールドを参照する際に使用される識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能にするフィールドを定義します。 提供 `label` ラベルを翻訳可能にする。 複数のフィールドはスペースで区切る必要があります。 | `string` | オプション |
| `type` | レンダリングされたHTML要素の入力タイプを定義します。 デフォルトはです。 `text`. | `string` | オプション |
| `sortOrder` | セクションの並べ替え順を定義します。 大きい数字はセクションをページの下部に、小さい数字はセクションを上に押します。 | `float` | オプション |
| `showInDefault` | フィールドをデフォルトの設定範囲に表示するかどうかを定義します。 指定 `1` フィールドを表示し、 `0` をクリックして、フィールドを非表示にします。 | `int` | オプション |
| `showInStore` | フィールドをストアレベルで表示するかどうかを定義します。 指定 `1` フィールドを表示し、 `0` をクリックして、フィールドを非表示にします。 | `int` | オプション |
| `showInWebsite` | フィールドを Web サイトレベルで表示するかどうかを定義します。 指定 `1` フィールドを表示し、 `0` をクリックして、フィールドを非表示にします。 | `int` | オプション |
| `canRestore` | フィールドをデフォルトに復元できるかどうかを定義します。 | `int` | オプション |
| `advanced` | 100.0.2 以降で非推奨（廃止予定）となりました。 | `bool` | オプション |
| `extends` | 別のフィールドの識別子を指定すると、このノードのコンテンツは、参照したセクションを拡張します。 | `string` | オプション |

### フィールドタイプの参照

A `<field>`-Tag は、 `type=""` 属性：

| タイプ | 説明 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | 標準の 1 行のテキストフィールド |
| `textarea` | テキストブロック |
| `select` | 通常のドロップダウン ( カスタム `source_model`. また、 `Yes/No` 選択。 詳しくは、 `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` 例を示します。 |
| `multiselect` | 次に類似 `select` ただし、複数のオプションが有効です。 |
| `button` | 即時イベントをトリガーするボタン。 ボタンのテキストとアクションを定義するには、カスタムフロントエンドモデルが必要です。 詳しくは、 `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` 例を示します。 |
| `obscure` | 暗号化され、次のように表示される値を持つテキストフィールド `****`. ブラウザーで「Inspect Element」を使用してタイプを変更しても、値は表示されません。 |
| `password` | 次に類似 `obscure` 非表示の値は暗号化されず、ブラウザーで「Inspect要素」を使用して強制的に型を変更すると、値が表示されます。 |
| `file` | ファイルのアップロードを処理に許可します。 |
| `label` | 編集可能なフィールドの代わりにラベルを表示します。 このタイプは、特定のスコープでのみフィールドを編集できる場合に使用します（例： Store View レベルのみ）。 |
| `time` | 時間、分、秒の 3 つのドロップダウンを使用して時間を設定するコントロール。 |
| `allowspecific` | 特定の国の複数選択リスト。 が必要です `source_model` 例： `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | 画像のアップロードを許可します。 |
| `note` | ページに情報メモを追加できます。 このタイプには、 `frontend_model` ノートをレンダリングします。 |

また、カスタムフィールドタイプを作成することもできます。 これは、多くの場合、アクションを持つ特別なボタンが必要な場合におこなわれます。 これをおこなうには、次の 2 つの主な要素が必要です。

- でのブロックの作成 `adminhtml` 領域
- の設定 `type=""` このブロックのパスに

ブロック自体には、少なくとも `__construct` メソッドおよび `getElementHtml()` メソッド。 The [Magento_オフライン出荷](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) は、カスタム型の簡単な例です。

例えば、OfflineShipping モジュールでは、「書き出し」ボタンは `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` フィールドの定義は次のようになります。

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### フィールドノードの参照

A `<field>`-Tag は次の子を持つことができます。

| ノード | 説明 | タイプ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | フロントエンドに表示するラベルを定義します。 | `string` |
| `comment` | フィールドラベルの下にコメントを追加します。 次を使用： `<![CDATA[//]]>` HTMLを適用できます。 | `string` |
| `tooltip` | このフィールドの意味を説明するために使用できる、別の考えられるフロントエンド要素。 フィールドの横に小さなアイコンとして表示されます。 | `string` |
| `hint` | 追加情報を表示します。 特定の `frontend_model`. | `string` |
| `frontend_class` | 定義済みの CSS クラスをレンダリングされたセクションHTML要素に追加します。 | `string` |
| `frontend_model` | 別のフロントエンドモデルを指定して、レンダリングを変更し、出力を変更します。 | `typeModel` |
| `backend_model` | 設定された値を変更する別のバックエンドモデルを指定します。 | `typeModel` |
| `source_model` | 特定の値のセットを提供する別のソースモデルを指定します。 | `typeModel` |
| `config_path` | フィールドの汎用設定パスを上書きするために使用できます。 | `typeConfigPath` |
| `validate` | 異なる検証ルールを定義します（スペースで区切ります）。 使用可能な検証ルールの完全なリファレンスリストを以下に示します。 | `string` |
| `can_be_empty` | 次の場合に使用 `type` 次に該当 `multiselect` をクリックして、フィールドを空にできるように指定します。 | `int` |
| `if_module_enabled` | 特定のモジュールが有効な場合にのみフィールドを表示するために使用します。 | `typeModule` |
| `base_url` | との組み合わせで使用されます `upload_dir` ファイルのアップロード用。 | `typeUrl` |
| `upload_dir` | アップロード先のディレクトリを指定します。 このノードには、追加の属性とノードが含まれます。 これを使用する前にそれらを調べてください。 | `typeUploadDir` |
| `button_url` | 次の場合にボタンを表示 `button_url` および `button_label` が指定されている。 通常、カスタムフロントエンドモデルと組み合わせて使用されます。 | `typeUrl` |
| `button_label` | 次の場合にボタンを表示 `button_label` および `button_url` が指定されている。 通常、カスタムフロントエンドモデルと組み合わせて使用されます。 | `string` |
| `more_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `demo_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `hide_in_single_store_mode` | グループをシングルストアモードで表示するかどうかを指定します。 `1` グループを非表示にします。 `0` グループを表示します。 | `int` |
| `options` | 未使用。 非推奨（廃止予定）となっている可能性があります。 | `complexType` |
| `depends` | 他のフィールドへの依存関係を宣言するために使用できます。 特定のフィールドの値が `1`. このノードは、 `section/group/field`-string. | `complexType` |
| `attribute` | カスタム属性はフロントエンドモデルで使用できます。 通常、特定のフロントエンドモデルをより動的にするために使用します。 | `complexType` |
| `requires` | 拡張可能ではありません。 以下を参照してください。 | `complexType` |

>[!WARNING]
>
>ノード `more_url`, `demo_url`, `requires` および `options` は、別のコア支払いモデルによって定義され、1 回のみ使用されます。 これらのノードは再利用できません。

### 例：特定のグループに 2 つのフィールドを作成する

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

上記の例では、デフォルトとストア表示の両方で表示/設定可能な 2 つのフィールドを作成します。 両方のフィールドには、ユーザーに対して目的を説明するコメントとツールチップが表示されます。 The `label`-node は翻訳可能です。
識別子を持つフィールド `ANOTHER_UNIQUE_FIELD_ID` は、 `if_module_enabled` はグローバルに有効になっています。 また、フィールドは、ルールに対する値を検証します `required-entry` および `no-whitespace`.
識別子を持つフィールド `A_UNIQUE_FIELD_ID` 値を提供する別のソースモデルを定義します `Yes` および `No`.

### 共通のソースモデル

Commerce 2 Core では、次のソースモデルが提供されています。 一般に、ソースモデルはさらに多数あります。最も一般的なモデルを次に示します。 これらのソースモデルには、field 属性が必要です。 `type` 設定する `select` 正しく動作させるために。

| ソースモデル | 説明 |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | 値を指定します `Yes`, `No` および `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | 値を指定します `Enable`, `Disable`. 値を `0` および `1` をデータベースに追加します。 |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | 値を指定します `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` および `24 Hours`. 値は整数として保存されます。 |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | 時刻の形式 (12 h/24 h) の値を指定します。 |
| `Magento\Cron\Model\Config\Source\Frequency` | 値を指定します `Daily`, `Weekly` および `Monthly`. 値は、 `D`, `W` および `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | 特定の言語の 2 文字コードの値を ISO 639-1 形式（en など）で提供します。 |
| `Magento\Config\Model\Config\Source\Locale` | 上記の値と似た値を提供しますが、ロケールコード（en_US など）に関連します。 |

### フィールドの検証

フィールドに 1 つ以上のバリデータークラスを割り当てて、ユーザーの入力が拡張機能の要件を満たしていることを確認できます。 検証ルールは、 `<validate>` — タグ。
次の使用例は、フィールドを検証し、複数の異なる検証ルールを追加します。

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

次の検証ルールを使用できます。

| ルール | 説明 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | 文字、数字、スペース、アンダースコアのみを使用できます。 |
| `integer` | 10 進数以外の正または負の数を許可します。 |
| `ipv4` | 有効な IP v4 アドレスを許可します。 |
| `ipv6` | 有効な IP v6 アドレスを許可します。 |
| `letters-only` | 文字のみを許可します。 例： `abcABC`. |
| `letters-with-basic-punc` | 文字または句読点のみを使用できます。<br>次の式を渡す必要があります。 `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | (UK) 携帯電話番号を許可します。 |
| `no-marginal-whitespace` | 値の先頭または末尾の空白を無効にします。 |
| `no-whitespace` | 空白を許可しません。 |
| `phoneUK` | (UK) の電話番号を許可します。 |
| `phoneUS` | （米国）の電話番号を許可します。 |
| `required-entry` | 空の値（同等の検証）を無効にする `validate-no-empty`) をクリックします。<br>検証失敗のメッセージ：「これは必須フィールドです。」 |
| `time` | 24 時間形式の有効な時間を 00:00 ～ 23:59 の範囲で許可します。 例： `15`, `15:05` または `15:05:48`. |
| `time12h` | 午前 12:00 ～ 11 の有効な時間を 12 時間形式で許可します:59:午後 59 時。 例： `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | 数字と英字の両方を使用して、7 文字以上を許可します。 |
| `validate-alphanum-with-spaces` | 文字（a ～ z または A ～ Z）、数字 (0 ～ 9)、またはスペースのみを使用できます。 |
| `validate-clean-url` | 有効な URL を許可します。 例： `https://www.example.com` または `www.example.com`. |
| `validate-currency-dollar` | 有効な（ドル）金額を指定できます。 例：$100.00 |
| `validate-data` | 文字（a ～ z または A ～ Z）、数字 (0 ～ 9)、アンダースコア (\_) のみを使用できます。<br>最初の文字は文字にする必要があります。<br>( 式に一致する必要があります： `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>検証エラーメッセージ：「このフィールドでは、文字（a ～ z または A ～ Z）、数字 (0 ～ 9)、アンダースコア (\_) のみを使用し、最初の文字は文字にする必要があります。」 |
| `validate-date-au` | dd/mm/yyyy の日付フォーマットを適用します。 例えば、2006 年 3 月 17 日には17/03/2006と入力します。 |
| `validate-email` | 有効な電子メールアドレスを許可します。 例：johndoe@domain.com |
| `validate-emailSender` | 有効な電子メールアドレスを許可します。 例：johndoe@domain.com |
| `validate-fax` | 有効な FAX 番号を許可します。 例：123-456-7890。 |
| `validate-no-empty` | 空の値（同等の検証）を無効にする `requried-entry`) をクリックします。<br>検証失敗のメッセージ：「空の値」 |
| `validate-no-html-tags` | タグの使用を許可しないHTML。 |
| `validate-password` | 6 文字以上を使用できます。 先頭と末尾の空白文字は無視されます。 |
| `validate-phoneLax` | 有効な電話番号を許可します。 例えば、(123) 456-7890 や123-456-7890などです。 |
| `validate-phoneStrict` | 有効な電話番号を許可します。 例えば、(123) 456-7890 や123-456-7890などです。 |
| `validate-select` | 選択した選択オプションに `null` 値，文字列値 `none` または文字列の長さが 0 の場合。 |
| `validate-ssn` | 有効な（米国）社会保障番号を許可します。 例：123-45-6789。 |
| `validate-street` | 文字（a ～ z または A ～ Z）、数字 (0 ～ 9)、スペース、「#」のみを使用できます。 |
| `validate-url` | 有効な URL を許可します。 プロトコルが必要です (http://、https://、ftp://)。 |
| `validate-xml-identifier` | 有効な XML 識別子を許可します。 例えば、 something_1, block5, id-4 などです。 |
| `validate-zip-us` | 有効な（米国）郵便番号を許可します。 例えば、90602や90602-1234 などです。 |
| `vinUS` | （米国）車両識別番号 (VIN) 値を許可します。 |

### デフォルト値

フィールドのデフォルト値は、モジュールの `etc/config.xml` ファイルを作成する場合は、 `section/group/field_ID` ノード。

#### 例：のデフォルト値の設定 `ANOTHER_UNIQUE_FIELD_ID` （デフォルトの範囲）

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### 例：のデフォルト値の設定 `ANOTHER_UNIQUE_FIELD_ID` （Web サイトの範囲）

の使用 `websites` タグを使用して、特定の web サイトのデフォルト値を指定します。

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
