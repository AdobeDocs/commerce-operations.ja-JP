---
title: system.xml リファレンス
description: システム XML ファイルでCommerce アプリケーション設定を管理する方法を説明します。
feature: Configuration, System
badge: label="執筆：David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: e231a27d70e29b01c872b0655168e31f590d4876
workflow-type: tm+mt
source-wordcount: '2708'
ht-degree: 0%

---

# system.xml リファレンス

この `system.xml` ファイルを使用すると、Commerce システム設定を管理できます。 このトピックは、の一般的なリファレンスとして使用します `system.xml` ファイル。 この `system.xml` ファイルはの下に配置されます。 `etc/adminhtml/system.xml` 特定のCommerce 2 拡張機能で使用できます。

次のコードスニペットは、ファイルのむき出しのスケルトンを示しています。

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
>IDE で即時に*XSD 検証を行う場合は、次を実行できます `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## タブ // セクション // グループ // フィールド

が含まれる `system.xml` ファイルの場合は、互いに関連する 4 つの異なるタイプのエンティティを定義できます。 次の節では、タブ、セクション、グループ、フィールドの関係について説明します。 次のスクリーンショットは、Admin バックエンドのCommerce 2 システム設定を示しています。
赤い四角は、で定義されている様々なタイプを示しています。 `system.xml` ファイル：

![管理者に設定済みのセクションを表示するスクリーンショット。](../../assets/configuration/magento2-system-configuration.png)

タブは、様々な設定領域を意味的に分割するために使用されます。 各タブには 1 つ以上のセクションを含めることができ、サブメニューとして参照することもできます。 セクションには 1 つ以上のグループが含まれます。
各グループには、1 つ以上のフィールドが一覧表示されます。 グループを使用して、次のフィールドの一般的な説明を追加することもできます。 前述のように、各グループには 1 つ以上のフィールドを含めることができます。 フィールドは、システム設定コンテキストの最小エンティティです。

## タブ

A `<tab>` – システム設定の既存または新しいタブへのタグ参照。

### タブ属性リファレンス

A `<tab>`-Tag は次の属性を持つことができます。

| 属性 | 説明 | タイプ | 必須 |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | セクションを参照するために使用する識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能にするフィールドを定義します。 提供する `label` ラベルを変換可能にします。 | `string` | optional |
| `sortOrder` | セクションの並べ替え順を定義します。 数値が大きい場合はセクションがページの下部にプッシュされ、数値が小さい場合はセクションが上部にプッシュされます。 | `float` | optional |
| `class` | 定義済みの CSS クラスを、レンダリングされたタブHTML要素に追加します。 | `string` | optional |

### タブノードのリファレンス

A `<tab>`-Tag は次の子を持つことができます：

| ノード | 説明 | タイプ |
|---------|------------------------------------------------------|----------|
| `label` | フロントエンドに表示されるラベルを定義します。 | `string` |

### 例：タブの作成

次のコードスニペットは、サンプルデータを使用して新しいタブを作成する方法を示しています。

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

上記のスニペットは、識別子で新しいタブを作成します `A_UNIQUE_ID`. として `translate`-attribute が定義され、ラベル、 `label`-node は変換可能です。 レンダリングプロセス中、CSS クラス。 `a-custom-css-class-to-style-this-tab` このタブ用に作成されたHTML要素に適用されます。
この `sortOrder`-attribute に値 `10` レンダリング時にすべてのタブのリストでタブの位置を定義します。

## セクション

A `<section>` – システム設定の既存のセクションまたは新しいセクションへのタグ参照。

### セクション属性リファレンス

A `<section>`-Tag は次の属性を持つことができます。

| 属性 | 説明 | タイプ | 必須 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | セクションを参照するために使用する識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能にするフィールドを定義します。 提供する `label` ラベルを変換可能にします。 | `string` | optional |
| `type` | レンダリングされるHTML要素の入力タイプを定義します。 デフォルトは `text`. | `string` | optional |
| `sortOrder` | セクションの並べ替え順を定義します。 数値が大きい場合はセクションがページの下部に移動し、数値が小さい場合はセクションが上部に移動します。 | `float` | optional |
| `showInDefault` | セクションを既定の構成範囲に表示するかどうかを定義します。 を指定 `1` セクションを表示するには、および `0` セクションを非表示にします。 | `int` | optional |
| `showInStore` | セクションをストアレベルで表示するかどうかを定義します。 を指定 `1` セクションを表示するには、および `0` セクションを非表示にします。 | `int` | optional |
| `showInWebsite` | セクションを web サイトレベルで表示するかどうかを定義します。 を指定 `1` セクションを表示するには、および `0` セクションを非表示にします。 | `int` | optional |
| `canRestore` | セクションをデフォルトに復元できるかどうかを定義します。 | `int` | optional |
| `advanced` | 100.0.2 以降で非推奨。 | `bool` | optional |
| `extends` | 別のセクションの識別子を指定すると、このノードのコンテンツによって、参照したセクションが拡張されます。 | `string` | optional |

### 断面ノード リファレンス

A `<section>`-Tag は次の子を持つことができます：

| ノード | 説明 | タイプ |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | フロントエンドに表示されるラベルを定義します。 | `string` |
| `class` | 定義された CSS クラスを、レンダリングされたセクションHTML要素に追加します。 | `string` |
| `tab` | 関連付けられたタブを参照します。 では、タブの ID が想定されます。 | `typeTabId` |
| `header_css` | このドキュメントの作成時には使用も評価もされません。 | `string` |
| `resource` | このセクションの権限設定を提供する ACL リソースを参照します。 | `typeAclResourceId` |
| `group` | 1 つ以上のサブグループを定義します。 | `typeGroup` |
| `frontend_model` | レンダリングを変更し、出力を変更する別のフロントエンドモデルを指定します。 | `typeModel` |
| `include` | 追加を含めるために使用されます `system_include.xsd` 互換性のあるファイル 通常、大きな構造を作るために使用される `system.xml` ファイル。 | `includeType` |

### 例：セクションを作成してタブに割り当てる

次のコードスニペットは、新しいセクションを作成する際の基本的な使用方法を示しています。

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

上記の節では、ID を定義しています `A_UNIQUE_SECTION_ID`、デフォルトの config ビューおよびストアコンテキストに表示されます。 この `label`-node は変換可能です。 セクションは、ID とタブに関連付けられています `A_UNIQUE_ID`. セクションは、ACL で権限が定義されているユーザーのみがアクセスできます `VENDOR_MODULE::path_to_the_acl_resource`.

## グループ

この `<group>` – タグはフィールドをグループ化するために使用されます。

### グループ属性参照

A `<group>`-Tag は次の属性を持つことができます。

| 属性 | 説明 | タイプ | 必須 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | グループを参照するために使用する識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能なフィールドを定義します。 提供する `label` ラベルを変換可能にします。 複数のフィールドはスペースで区切る必要があります。 | `string` | optional |
| `type` | レンダリングされるHTML要素の入力タイプを定義します。 デフォルトは `text`. | `string` | optional |
| `sortOrder` | セクションの並べ替え順を定義します。 数値が大きい場合はセクションがページの下部に移動し、数値が小さい場合はセクションが上部に移動します。 | `float` | optional |
| `showInDefault` | グループを既定の構成範囲に表示するかどうかを定義します。 を指定 `1` グループを表示するには、および `0` グループを非表示にします。 | `int` | optional |
| `showInStore` | グループをストアレベルで表示するかどうかを定義します。 を指定 `1` グループを表示するには、および `0` グループを非表示にします。 | `int` | optional |
| `showInWebsite` | グループを web サイトレベルで表示するかどうかを定義します。 を指定 `1` グループを表示するには、および `0` グループを非表示にします。 | `int` | optional |
| `canRestore` | グループをデフォルトに復元できるかどうかを定義します。 | `int` | optional |
| `advanced` | 100.0.2 以降で非推奨。 | `bool` | optional |
| `extends` | 別のグループの識別子を指定すると、このノードのコンテンツによって、参照したセクションが拡張されます。 | `string` | optional |

### グループノード参照

A `<group>`-Tag は次の子を持つことができます：

| ノード | 説明 | タイプ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | フロントエンドに表示されるラベルを定義します。 | `string` |
| `fieldset_css` | 1 つ以上の CSS クラスをグループフィールドセットに追加します。 | `string` |
| `frontend_model` | レンダリングを変更し、出力を変更する別のフロントエンドモデルを指定します。 | `typeModel` |
| `clone_model` | フィールドを複製する特定のモデルを指定します。 | `typeModel` |
| `clone_fields` | フィールドのクローン作成を有効または無効にしました。 | `int` |
| `help_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `more_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `demo_link` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `comment` | グループラベルの下にコメントを追加します。 使用 `<![CDATA[//]]>` HTMLを適用できます。 | `string` |
| `hide_in_single_store_mode` | グループを単一ストアモードで表示するかどうかを指定します。 `1` グループを非表示にします。 `0` グループを表示します。 | `int` |
| `field` | このグループで使用できるフィールドを 1 つ以上定義します。 | `field` |
| `group` | 1 つ以上のサブグループを定義します。 | `unbounded` |
| `depends` | 他のフィールドへの依存関係を宣言するために使用できます。 特定のフィールドの値がの場合にのみ特定のフィールド/グループを表示するために使用されます。 `1`. このノードは `section/group/field`-string を指定します。 | `depends` |
| `attribute` | カスタム属性は、フロントエンドモデルで使用できます。 通常、特定のフロントエンドモデルをより動的にするために使用されます。 | `attribute` |
| `include` | 追加を含めるために使用されます `system_include.xsd` 互換性のあるファイル 通常、大きな構造を作るために使用される `system.xml` ファイル。 | `includeType` |

>[!WARNING]
>
>ノード `more_url`, `demo_url` および `help_url` は、1 回だけ使用される PayPal フロントエンドモデルによって定義されます。 これらのノードは再利用できません。

### 例：特定のセクションのグループを作成する

次のコードスニペットは、新しいグループを作成する際の基本的な使用方法を示しています。

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

上記のグループは、ID を定義します `A_UNIQUE_GROUP_ID`、デフォルトの config ビューおよびストアコンテキストに表示されます。 両方、 `label` および `comment` は翻訳可能としてマークされます。

## フィールド

この `<field>` – タグは内で使用されます `<group>` – 特定の設定値を定義するためのタグ。

### フィールド属性リファレンス

A `<field>`-Tag は次の属性を持つことができます。

| 属性 | 説明 | タイプ | 必須 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | フィールドを参照するために使用する識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能なフィールドを定義します。 提供する `label` ラベルを変換可能にします。 複数のフィールドはスペースで区切る必要があります。 | `string` | optional |
| `type` | レンダリングされるHTML要素の入力タイプを定義します。 デフォルトは `text`. | `string` | optional |
| `sortOrder` | セクションの並べ替え順を定義します。 数値が大きい場合はセクションがページの下部にプッシュされ、数値が小さい場合はセクションが上部にプッシュされます。 | `float` | optional |
| `showInDefault` | デフォルトの設定範囲にフィールドを表示するかどうかを定義します。 を指定 `1` フィールドを表示し、 `0` でフィールドを非表示にします。 | `int` | optional |
| `showInStore` | フィールドをストアレベルで表示するかどうかを定義します。 を指定 `1` フィールドを表示し、 `0` でフィールドを非表示にします。 | `int` | optional |
| `showInWebsite` | Web サイトレベルでフィールドを表示するかどうかを定義します。 を指定 `1` フィールドを表示し、 `0` でフィールドを非表示にします。 | `int` | optional |
| `canRestore` | フィールドをデフォルトに復元できるかどうかを定義します。 | `int` | optional |
| `advanced` | 100.0.2 以降で非推奨。 | `bool` | optional |
| `extends` | 別のフィールドの識別子を指定すると、このノードのコンテンツは、参照したセクションを拡張します。 | `string` | optional |

### フィールドタイプの参照

A `<field>`-Tag は、以下の値を持つことができます。 `type=""` 属性：

| タイプ | 説明 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | 標準、1 行のテキストフィールド |
| `textarea` | テキストブロック |
| `select` | 通常のドロップダウン、カスタムが必要な場合あり `source_model`. 以下にも使用： `Yes/No` 選択。 参照： `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` 例： |
| `multiselect` | 類似 `select` ただし、複数のオプションが有効です。 |
| `button` | 即時イベントをトリガーにするボタン。 ボタンのテキストとアクションを定義するには、カスタムフロントエンドモデルが必要です。 参照： `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` 例： |
| `obscure` | 値が暗号化され、次のように表示されているテキストフィールド `****`. ブラウザーで「Inspect Element」を使用してタイプを変更しても、値は表示されません。 |
| `password` | 類似 `obscure` ただし、hidden 値は暗号化されず、ブラウザーで「Inspect Element」を使用して強制的に型を変更すると、値が表示されます。 |
| `file` | ファイルをアップロードして処理できるようにします。 |
| `label` | 編集可能なフィールドの代わりにラベルを表示します。 フィールドが特定の範囲でのみ編集できる場合に、このタイプを使用します（例：ストア表示レベルのみ）。 |
| `time` | 時、分、秒の 3 つのドロップダウンを使用して時間を設定するコントロール。 |
| `allowspecific` | 特定の国の複数選択リスト。 が必要 `source_model` 例： `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | 画像のアップロードを許可します。 |
| `note` | 情報メモをページに追加することを許可します。 このタイプにはが必要です `frontend_model` をクリックしてノートをレンダリングします。 |

カスタムフィールドタイプを作成することもできます。 これは、アクションを含む特別なボタンが必要な場合によく行われます。 それには、次の 2 つの主な要素が必要です。

- でのブロックの作成 `adminhtml` 面グラフ
- の設定 `type=""` このブロックへのパス

ブロック自体には、少なくとも `__construct` メソッドと `getElementHtml()` メソッド。 この [Magento_オフライン配送](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) は、カスタムタイプの簡単な例です。

例えば、OfflineShipping モジュールでは、「書き出し」ボタンは次の場所で定義されます。 `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` フィールド定義は次のようになります。

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### フィールドノードの参照

A `<field>`-Tag は次の子を持つことができます：

| ノード | 説明 | タイプ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | フロントエンドに表示されるラベルを定義します。 | `string` |
| `comment` | フィールドラベルの下にコメントを追加します。 使用 `<![CDATA[//]]>` HTMLを適用できます。 | `string` |
| `tooltip` | このフィールドの意味を説明するために使用できるもう 1 つのフロントエンド要素。 フィールドの横に小さなアイコンとして表示されます。 | `string` |
| `hint` | 追加情報を表示します。 特定ので利用できる `frontend_model`. | `string` |
| `frontend_class` | 定義された CSS クラスを、レンダリングされたセクションHTML要素に追加します。 | `string` |
| `frontend_model` | レンダリングを変更し、出力を変更する別のフロントエンドモデルを指定します。 | `typeModel` |
| `backend_model` | 設定された値を変更する別のバックエンドモデルを指定します。 | `typeModel` |
| `source_model` | 特定の値のセットを提供する別のソースモデルを指定します。 | `typeModel` |
| `config_path` | フィールドの汎用設定パスを上書きするために使用できます。 | `typeConfigPath` |
| `validate` | 別の検証ルールを定義します（スペース区切り）。 使用可能な検証ルールの完全な参照リストを以下に示します。 | `string` |
| `can_be_empty` | 次の場合に使用されます `type` 等しい `multiselect` フィールドを空にできるように指定します。 | `int` |
| `if_module_enabled` | 特定のモジュールが有効な場合にのみフィールドを表示するために使用されます。 | `typeModule` |
| `base_url` | と組み合わせて使用されます `upload_dir` （ファイルのアップロード用）。 | `typeUrl` |
| `upload_dir` | アップロードターゲットディレクトリを指定します。 このノードには、追加のアトリビュートとノードがあります。 これを使用する前に調べてください。 | `typeUploadDir` |
| `button_url` | 次の場合にボタンを表示 `button_url` および `button_label` が指定されている。 通常、カスタムフロントエンドモデルと組み合わせて使用します。 | `typeUrl` |
| `button_label` | 次の場合にボタンを表示 `button_label` および `button_url` が指定されている。 通常、カスタムフロントエンドモデルと組み合わせて使用します。 | `string` |
| `more_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `demo_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `hide_in_single_store_mode` | グループを単一ストアモードで表示するかどうかを指定します。 `1` グループを非表示にします。 `0` グループを表示します。 | `int` |
| `options` | 未使用。 非推奨になる可能性があります。 | `complexType` |
| `depends` | 他のフィールドへの依存関係を宣言するために使用できます。 特定のフィールドの値がの場合に、特定のフィールドやグループのみを表示するために使用されます。 `1`. このノードは `section/group/field`-string を指定します。 | `complexType` |
| `attribute` | カスタム属性は、フロントエンドモデルで使用できます。 通常、特定のフロントエンドモデルをより動的にするために使用されます。 | `complexType` |
| `requires` | 拡張可能ではありません。 以下を参照してください。 | `complexType` |

>[!WARNING]
>
>ノード `more_url`, `demo_url`, `requires` および `options` 異なるコア支払いモデルによって定義されており、1 回のみ使用されます。 これらのノードは再利用できません。

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

上記の例では、デフォルト表示とストア表示の両方で表示可能/設定可能な 2 つのフィールドを作成します。 両方のフィールドには、ユーザーに目的を説明するためのコメントとツールチップがあります。 この `label`-node は変換可能です。
識別子がのフィールド `ANOTHER_UNIQUE_FIELD_ID` に指定されたモジュールの場合、 `if_module_enabled` はグローバルに有効になっています。 また、フィールドでは、ルールに対して値を検証します `required-entry` および `no-whitespace`.
識別子がのフィールド `A_UNIQUE_FIELD_ID` これらの値を提供する別のソースモデルを定義します `Yes` および `No`.

### 共通ソースモデル

次のソースモデルは、Commerce 2 コアが提供します。 一般に、さらに多くのソースモデルがあります。以下に、最も一般的なソースモデルを示します。 これらのソースモデルには、フィールド属性が必要であることに注意してください `type` に設定されています `select` 正しく機能させるために。

| ソースモデル | 説明 |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | 値を指定します `Yes`, `No` および `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | 値を指定します `Enable`, `Disable`. 値を次の形式で保存 `0` および `1` データベース内にあります。 |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | 値を指定します `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` および `24 Hours`. 値は整数として保存されます。 |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | 時間形式の値を示します（12 時間/24 時間）。 |
| `Magento\Cron\Model\Config\Source\Frequency` | 値を指定します `Daily`, `Weekly` および `Monthly`. 値は、データベースに次のように保存されます `D`, `W` および `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | ISO 639-1 形式（例：en）の指定言語の 2 文字コードの値を提供します。 |
| `Magento\Config\Model\Config\Source\Locale` | 上記の値に類似した値を提供しますが、ロケールコードに関連しています（例：en_US）。 |

### フィールドの検証

フィールドには 1 つ以上のバリデータクラスを割り当てて、ユーザーの入力が拡張機能の要件を満たしていることを確認できます。 検証ルールは、 `<validate>`-Tag。
次の例では、フィールドを検証し、いくつかの異なる検証ルールを追加します。

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

次の検証ルールを使用できます。

| ルール | 説明 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | 文字、数字、スペースまたはアンダースコアのみを使用できます。 |
| `integer` | 正または負の整数を使用できます。 |
| `ipv4` | 有効な IP v4 アドレスを許可します。 |
| `ipv6` | 有効な IP v6 アドレスを許可します。 |
| `letters-only` | レターのみを使用できます。 例： `abcABC`. |
| `letters-with-basic-punc` | 文字または句読点のみを使用できます。<br>次の式を渡す必要があります。 `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | （英国）の携帯電話番号を使用できます。 |
| `no-marginal-whitespace` | 値の先頭または末尾に空白を使用できないようにします。 |
| `no-whitespace` | 空白を許可しません。 |
| `phoneUK` | （英国）の電話番号を使用できます。 |
| `phoneUS` | （米国）の電話番号を使用できます。 |
| `required-entry` | 空の値を許可しない（と同等の検証） `validate-no-empty`）に設定します。<br>検証エラーメッセージ：「これは必須フィールドです。」 |
| `time` | 24 時間形式（00:00 ～ 23:59）で有効な時間を指定できます。 例： `15`, `15:05` または `15:05:48`. |
| `time12h` | 12 時間形式（午前 12:00 ～ 11 の間）で有効な時間を許可します:59:午後 59:00 例： `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | 数字とアルファベットの両方を使用して、7 文字以上の文字を許可します。 |
| `validate-alphanum-with-spaces` | 文字（a ～ z または A ～ Z）、数字（0 ～ 9）、スペースのみを使用できます。 |
| `validate-clean-url` | 有効な URL を使用できます。 例： `https://www.example.com` または `www.example.com`. |
| `validate-currency-dollar` | 有効な（ドル）金額を許可します。 例えば、$100.00 です。 |
| `validate-data` | 文字（a ～ z または A ～ Z）、数字（0 ～ 9）、アンダースコア（\_）のみを使用できます。<br>最初の文字は文字である必要があります。<br>（式に一致する必要があります。 `/^[A-Za-z]+[A-Za-z0-9_]+$/`）<br>検証エラーメッセージ：「このフィールドでは文字（a ～ z または A ～ Z）、数字（0 ～ 9）またはアンダースコア（\_）のみを使用してください。最初の文字は文字にする必要があります。」 |
| `validate-date-au` | では、dd/mm/yyyy の日付形式が適用されます。 2006 年 3 月 17 日の場合は、17/03/2006 となります。 |
| `validate-email` | 有効なメールアドレスを指定できます。 例えば、johndoe@domain.comです。 |
| `validate-emailSender` | 有効なメールアドレスを指定できます。 例えば、johndoe@domain.comです。 |
| `validate-fax` | 有効な FAX 番号を許可します。 例：123-456-7890 |
| `validate-no-empty` | 空の値を許可しない（と同等の検証） `requried-entry`）に設定します。<br>検証エラーメッセージ：「空の値。」 |
| `validate-no-html-tags` | HTMLタグの使用を許可しません。 |
| `validate-password` | 6 文字以上を使用できます。 先頭と末尾のスペースは無視されます。 |
| `validate-phoneLax` | 有効な電話番号を許可します。 例えば、（123） 456-7890 や 123-456-7890 などです。 |
| `validate-phoneStrict` | 有効な電話番号を許可します。 例えば、（123） 456-7890 や 123-456-7890 などです。 |
| `validate-select` | 選択した選択オプションに `null` 値、文字列値 `none` または文字列の長さが 0 である。 |
| `validate-ssn` | 有効な（米国）社会保障番号を許可します。 例：123-45-6789 |
| `validate-street` | 文字（a ～ z または A ～ Z）、数字（0 ～ 9）、スペース、「#」のみを使用できます。 |
| `validate-url` | 有効な URL を使用できます。 プロトコルが必要です（http://、https://、ftp://）。 |
| `validate-xml-identifier` | 有効な XML 識別子を許可します。 例えば、something_1、block5、id-4 などです。 |
| `validate-zip-us` | 有効な（米国）郵便番号を指定できます。 例えば、90602 や 90602-1234 です。 |
| `vinUS` | 車両識別番号（VIN）値を許可します。 |

### デフォルト値

フィールドのデフォルト値は、モジュールの `etc/config.xml` でデフォルト値を指定することにより、ファイルを `section/group/field_ID` ノード。

#### 例：のデフォルト値の設定 `ANOTHER_UNIQUE_FIELD_ID` （既定のスコープ）

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

使用， `websites` タグを使用する場合は、特定の web サイトのデフォルト値を指定します。

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
