---
title: system.xml リファレンス
description: system.xml ファイルでAdobe Commerce アプリケーション設定を管理する方法を説明します。 システム設定管理、XML 構造、実装技術について説明します。
feature: Configuration, System
badge: label="執筆：David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '2717'
ht-degree: 0%

---

# system.xml リファレンス

`system.xml` ファイルを使用すると、Commerce システム設定を管理できます。 このトピックは、`system.xml` ファイルの一般的なリファレンスとして使用します。 `system.xml` ファイルは、特定のCommerce 2 拡張子の `etc/adminhtml/system.xml` の下にあります。

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
>IDE で即時*XSD 検証が必要な場合は、`bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>` を実行できます。

## タブ // セクション // グループ // フィールド

`system.xml` ファイルでは、互いに関連する 4 つの異なるタイプのエンティティを定義できます。 次の節では、タブ、セクション、グループ、フィールドの関係について説明します。 次のスクリーンショットは、Admin バックエンドのCommerce 2 システム設定を示しています。
赤い四角形は、`system.xml` ファイルで定義されている様々なタイプを示しています。

![ 管理者に設定済みセクションを表示するスクリーンショット。](../../assets/configuration/magento2-system-configuration.png)

タブは、様々な設定領域を意味的に分割するために使用されます。 各タブには 1 つ以上のセクションを含めることができ、サブメニューとして参照することもできます。 セクションには 1 つ以上のグループが含まれます。
各グループには、1 つ以上のフィールドが一覧表示されます。 グループを使用して、次のフィールドの一般的な説明を追加することもできます。 前述のように、各グループには 1 つ以上のフィールドを含めることができます。 フィールドは最小のエンティティです
システム設定コンテキストで上書きできます。

## タブ

`<tab>` タグは、システム設定の既存または新しいタブを参照します。

### タブ属性リファレンス

`<tab>` タグには、次の属性を含めることができます。

| 属性 | 説明 | タイプ | 必須 |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | セクションを参照するために使用する識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能にするフィールドを定義します。 ラベルを翻訳可能にする `label` を指定します。 | `string` | optional |
| `sortOrder` | セクションの並べ替え順を定義します。 数値が大きい場合はセクションがページの下部にプッシュされ、数値が小さい場合はセクションが上部にプッシュされます。 | `float` | optional |
| `class` | は、定義済みの CSS クラスを、レンダリングされたタブのHTML要素に追加します。 | `string` | optional |

### タブノードのリファレンス

`<tab>`-Tag は次の子を持つことができます。

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

上記のスニペットは、識別子が `A_UNIQUE_ID` の新しいタブを作成します。 `translate` 属性が定義され、ラベルを参照すると、`label` ノードが翻訳可能になります。 レンダリングプロセス中に、このタブ用に作成されたHTML要素に CSS クラス `a-custom-css-class-to-style-this-tab` が適用されます。
値が `sortOrder` の `10` 属性は、レンダリング時のすべてのタブのリスト内のタブの位置を定義します。

## セクション

`<section>` タグは、システム設定の既存または新しいセクションを参照します。

### セクション属性リファレンス

`<section>` タグには、次の属性を含めることができます。

| 属性 | 説明 | タイプ | 必須 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | セクションを参照するために使用する識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能にするフィールドを定義します。 ラベルを翻訳可能にする `label` を指定します。 | `string` | optional |
| `type` | レンダリングされるHTML要素の入力タイプを定義します。 デフォルトは `text` です。 | `string` | optional |
| `sortOrder` | セクションの並べ替え順を定義します。 数値が大きい場合はセクションがページの下部に移動し、数値が小さい場合はセクションが上部に移動します。 | `float` | optional |
| `showInDefault` | セクションを既定の構成範囲に表示するかどうかを定義します。 `1` を指定してセクションを表示し、`0` を指定してセクションを非表示にします。 | `int` | optional |
| `showInStore` | セクションをストアレベルで表示するかどうかを定義します。 `1` を指定してセクションを表示し、`0` を指定してセクションを非表示にします。 | `int` | optional |
| `showInWebsite` | セクションを web サイトレベルで表示するかどうかを定義します。 `1` を指定してセクションを表示し、`0` を指定してセクションを非表示にします。 | `int` | optional |
| `canRestore` | セクションをデフォルトに復元できるかどうかを定義します。 | `int` | optional |
| `advanced` | 100.0.2 以降で非推奨。 | `bool` | optional |
| `extends` | 別のセクションの識別子を指定すると、このノードのコンテンツによって、参照したセクションが拡張されます。 | `string` | optional |

### 断面ノード リファレンス

`<section>` タグには、次の子を含めることができます。

| ノード | 説明 | タイプ |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | フロントエンドに表示されるラベルを定義します。 | `string` |
| `class` | 定義された CSS クラスを、レンダリングされたセクションのHTML要素に追加します。 | `string` |
| `tab` | 関連付けられたタブを参照します。 では、タブの ID が想定されます。 | `typeTabId` |
| `header_css` | このドキュメントの作成時には使用も評価もされません。 | `string` |
| `resource` | このセクションの権限設定を提供する ACL リソースを参照します。 | `typeAclResourceId` |
| `group` | 1 つ以上のサブグループを定義します。 | `typeGroup` |
| `frontend_model` | レンダリングを変更し、出力を変更する別のフロントエンドモデルを指定します。 | `typeModel` |
| `include` | 追加の `system_include.xsd` 互換ファイルを含めるために使用されます。 通常、大きな `system.xml` ファイルを構造化するために使用します。 | `includeType` |

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

上記の節では、ID `A_UNIQUE_SECTION_ID` を定義します。この ID は、デフォルトの設定表示およびストアコンテキストに表示されます。 `label` ノードは翻訳可能です。 セクションは、ID が `A_UNIQUE_ID` のタブに関連付けられています。 セクションは、ACL `VENDOR_MODULE::path_to_the_acl_resource` で権限が定義されているユーザーのみがアクセスできます。

## グループ

`<group>`-Tag は、フィールドをグループ化するために使用されます。

### グループ属性参照

`<group>` タグには、次の属性を含めることができます。

| 属性 | 説明 | タイプ | 必須 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | グループを参照するために使用する識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能なフィールドを定義します。 ラベルを翻訳可能にする `label` を指定します。 複数のフィールドはスペースで区切る必要があります。 | `string` | optional |
| `type` | レンダリングされるHTML要素の入力タイプを定義します。 デフォルトは `text` です。 | `string` | optional |
| `sortOrder` | セクションの並べ替え順を定義します。 数値が大きい場合はセクションがページの下部に移動し、数値が小さい場合はセクションが上部に移動します。 | `float` | optional |
| `showInDefault` | グループを既定の構成範囲に表示するかどうかを定義します。 グループを表示する場合は `1` を指定し、グループを非表示にする場合は `0` を指定します。 | `int` | optional |
| `showInStore` | グループをストアレベルで表示するかどうかを定義します。 グループを表示する場合は `1` を指定し、グループを非表示にする場合は `0` を指定します。 | `int` | optional |
| `showInWebsite` | グループを web サイトレベルで表示するかどうかを定義します。 グループを表示する場合は `1` を指定し、グループを非表示にする場合は `0` を指定します。 | `int` | optional |
| `canRestore` | グループをデフォルトに復元できるかどうかを定義します。 | `int` | optional |
| `advanced` | 100.0.2 以降で非推奨。 | `bool` | optional |
| `extends` | 別のグループの識別子を指定すると、このノードのコンテンツによって、参照したセクションが拡張されます。 | `string` | optional |

### グループノード参照

`<group>` タグには、次の子を含めることができます。

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
| `comment` | グループラベルの下にコメントを追加します。 HTMLを使用 `<![CDATA[//]]>` ると適用できます。 | `string` |
| `hide_in_single_store_mode` | グループを単一ストアモードで表示するかどうかを指定します。 `1` はグループを非表示にし、`0` はグループを表示します。 | `int` |
| `field` | このグループで使用できるフィールドを 1 つ以上定義します。 | `field` |
| `group` | 1 つ以上のサブグループを定義します。 | `unbounded` |
| `depends` | 他のフィールドへの依存関係を宣言するために使用できます。 特定のフィールドの値が `1` の場合にのみ特定のフィールドやグループを表示するために使用されます。 このノードには `section/group/field` 文字列が必要です。 | `depends` |
| `attribute` | カスタム属性は、フロントエンドモデルで使用できます。 通常、特定のフロントエンドモデルをより動的にするために使用されます。 | `attribute` |
| `include` | 追加の `system_include.xsd` 互換ファイルを含めるために使用されます。 通常、大きな `system.xml` ファイルを構造化するために使用します。 | `includeType` |

>[!WARNING]
>
>ノード `more_url`、`demo_url`、`help_url` は、1 回だけ使用される PayPal フロントエンドモデルによって定義されます。 これらのノードは再利用できません。

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

上記のグループは ID `A_UNIQUE_GROUP_ID` を定義し、デフォルトの設定ビューおよびストアコンテキストに表示されます。 `label` と `comment` の両方が翻訳可能としてマークされます。

## フィールド

`<field>`-Tag は、特定の設定値を定義するために `<group>`-Tags 内で使用されます。

### フィールド属性リファレンス

`<field>` タグには、次の属性を含めることができます。

| 属性 | 説明 | タイプ | 必須 |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | フィールドを参照するために使用する識別子を定義します。 | `typeId` | 必須 |
| `translate` | 翻訳可能なフィールドを定義します。 ラベルを翻訳可能にする `label` を指定します。 複数のフィールドはスペースで区切る必要があります。 | `string` | optional |
| `type` | レンダリングされるHTML要素の入力タイプを定義します。 デフォルトは `text` です。 | `string` | optional |
| `sortOrder` | セクションの並べ替え順を定義します。 数値が大きい場合はセクションがページの下部にプッシュされ、数値が小さい場合はセクションが上部にプッシュされます。 | `float` | optional |
| `showInDefault` | デフォルトの設定範囲にフィールドを表示するかどうかを定義します。 `1` を指定してフィールドを表示し、`0` を指定してフィールドを非表示にします。 | `int` | optional |
| `showInStore` | フィールドをストアレベルで表示するかどうかを定義します。 `1` を指定してフィールドを表示し、`0` を指定してフィールドを非表示にします。 | `int` | optional |
| `showInWebsite` | Web サイトレベルでフィールドを表示するかどうかを定義します。 `1` を指定してフィールドを表示し、`0` を指定してフィールドを非表示にします。 | `int` | optional |
| `canRestore` | フィールドをデフォルトに復元できるかどうかを定義します。 | `int` | optional |
| `advanced` | 100.0.2 以降で非推奨。 | `bool` | optional |
| `extends` | 別のフィールドの識別子を指定すると、このノードのコンテンツは、参照したセクションを拡張します。 | `string` | optional |

### フィールドタイプの参照

`<field>`-Tag は、`type=""` 属性に対して次の値を持つことができます。

| タイプ | 説明 |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | 標準、1 行のテキストフィールド |
| `textarea` | テキストブロック |
| `select` | 通常のドロップダウン。カスタム `source_model` が必要になる場合があります。 `Yes/No` 選択にも使用されます。 例については、`Magento\Search\Model\Adminhtml\System\Config\Source\Engine` を参照してください。 |
| `multiselect` | `select` に似ていますが、複数のオプションが有効です。 |
| `button` | 即時イベントをトリガーにするボタン。 ボタンのテキストとアクションを定義するには、カスタムフロントエンドモデルが必要です。 例については、`Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` を参照してください。 |
| `obscure` | 値が暗号化され、`****` として表示されるテキストフィールド。 ブラウザーで「要素を検査」を使用してタイプを変更しても、値は表示されません。 |
| `password` | `obscure` と同様に、非表示の値は暗号化されず、ブラウザーで「要素を検査」を使用してタイプを強制的に変更すると、値が表示される点が異なります。 |
| `file` | ファイルをアップロードして処理できるようにします。 |
| `label` | 編集可能なフィールドの代わりにラベルを表示します。 フィールドが特定の範囲でのみ編集できる場合に、このタイプを使用します（例：ストア表示レベルのみ）。 |
| `time` | 時、分、秒の 3 つのドロップダウンを使用して時間を設定するコントロール。 |
| `allowspecific` | 特定の国の複数選択リスト。 `source_model` などの `Magento\Shipping\Model\Config\Source\Allspecificcountries` が必要です |
| `image` | 画像のアップロードを許可します。 |
| `note` | 情報メモをページに追加することを許可します。 このタイプでは、メモをレンダリングする `frontend_model` が必要です。 |

カスタムフィールドタイプを作成することもできます。 これは、アクションを含む特別なボタンが必要な場合によく行われます。 それには、次の 2 つの主な要素が必要です。

- `adminhtml` 領域にブロックを作成する
- `type=""` をこのブロックへのパスに設定しています

ブロック自体には、少なくとも `__construct` メソッドと `getElementHtml()` メソッドが必要です。 [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) は、カスタムタイプの簡単な例です。

例えば、OfflineShipping モジュールでは、「書き出し」ボタンは `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` で定義され、フィールドは次のように定義されます。

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### フィールドノードの参照

`<field>` タグには、次の子を含めることができます。

| ノード | 説明 | タイプ |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | フロントエンドに表示されるラベルを定義します。 | `string` |
| `comment` | フィールドラベルの下にコメントを追加します。 HTMLを使用 `<![CDATA[//]]>` ると適用できます。 | `string` |
| `tooltip` | このフィールドの意味を説明するために使用できるもう 1 つのフロントエンド要素。 フィールドの横に小さなアイコンとして表示されます。 | `string` |
| `hint` | 追加情報を表示します。 特定の `frontend_model` でのみ使用可能です。 | `string` |
| `frontend_class` | 定義された CSS クラスを、レンダリングされたセクションのHTML要素に追加します。 | `string` |
| `frontend_model` | レンダリングを変更し、出力を変更する別のフロントエンドモデルを指定します。 | `typeModel` |
| `backend_model` | 設定された値を変更する別のバックエンドモデルを指定します。 | `typeModel` |
| `source_model` | 特定の値のセットを提供する別のソースモデルを指定します。 | `typeModel` |
| `config_path` | フィールドの汎用設定パスを上書きするために使用できます。 | `typeConfigPath` |
| `validate` | 別の検証ルールを定義します（スペース区切り）。 使用可能な検証ルールの完全な参照リストを以下に示します。 | `string` |
| `can_be_empty` | `type` が `multiselect` の場合、フィールドを空にできるように指定するために使用します。 | `int` |
| `if_module_enabled` | 特定のモジュールが有効な場合にのみフィールドを表示するために使用されます。 | `typeModule` |
| `base_url` | ファイルのアップロードに `upload_dir` と組み合わせて使用します。 | `typeUrl` |
| `upload_dir` | アップロードターゲットディレクトリを指定します。 このノードには、追加のアトリビュートとノードがあります。 これを使用する前に調べてください。 | `typeUploadDir` |
| `button_url` | `button_url` と `button_label` が指定されている場合にボタンを表示します。 通常、カスタムフロントエンドモデルと組み合わせて使用します。 | `typeUrl` |
| `button_label` | `button_label` と `button_url` が指定されている場合にボタンを表示します。 通常、カスタムフロントエンドモデルと組み合わせて使用します。 | `string` |
| `more_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `demo_url` | 拡張可能ではありません。 以下を参照してください。 | `typeUrl` |
| `hide_in_single_store_mode` | グループを単一ストアモードで表示するかどうかを指定します。 `1` はグループを非表示にし、`0` はグループを表示します。 | `int` |
| `options` | 未使用。 非推奨になる可能性があります。 | `complexType` |
| `depends` | 他のフィールドへの依存関係を宣言するために使用できます。 特定のフィールドの値が `1` の場合に、特定のフィールドやグループのみを表示するために使用されます。 このノードには `section/group/field` 文字列が必要です。 | `complexType` |
| `attribute` | カスタム属性は、フロントエンドモデルで使用できます。 通常、特定のフロントエンドモデルをより動的にするために使用されます。 | `complexType` |
| `requires` | 拡張可能ではありません。 以下を参照してください。 | `complexType` |

>[!WARNING]
>
>ノード `more_url`、`demo_url`、`requires`、`options` は、別のコア支払いモデルで定義されており、1 回のみ使用されます。 これらのノードは再利用できません。

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

上記の例では、デフォルト表示とストア表示の両方で表示可能/設定可能な 2 つのフィールドを作成します。 両方のフィールドには、ユーザーに目的を説明するためのコメントとツールチップがあります。 `label` ノードは翻訳可能です。
識別子が `ANOTHER_UNIQUE_FIELD_ID` のフィールドは、フ `if_module_enabled` ールド内の特定のモジュールがグローバルに有効になっている場合に表示されます。 また、このフィールドでは、ルール `required-entry` および `no-whitespace` に対して値を検証します。
識別子 `A_UNIQUE_FIELD_ID` のフィールドは、`Yes` と `No` の値を提供する別のソースモデルを定義します。

### 共通ソースモデル

次のソースモデルは、Commerce 2 コアが提供します。 一般に、さらに多くのソースモデルがあります。以下に、最も一般的なソースモデルを示します。 これらのソースモデルが正しく機能するには、フィールド属性 `type` を `select` に設定する必要があります。

| Source モデル | 説明 |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | 値 `Yes`、`No`、`Specified` を指定します。 |
| `Magento\Config\Model\Config\Source\Enabledisable` | 値 `Enable`、`Disable` を指定します。 値を `0` および `1` としてデータベースに保存します。 |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | 値 `1 Hour`、`2 Hours`、`6 Hours`、`12 Hours` および `24 Hours` を指定します。 値は整数として保存されます。 |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | 時間形式の値を示します（12 時間/24 時間）。 |
| `Magento\Cron\Model\Config\Source\Frequency` | 値 `Daily`、`Weekly`、`Monthly` を指定します。 値は、`D`、`W`、`M` としてデータベースに保存されます。 |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | ISO 639-1 形式（例：en）の指定言語の 2 文字コードの値を提供します。 |
| `Magento\Config\Model\Config\Source\Locale` | 上記の値に類似した値を提供しますが、ロケールコードに関連しています（例：en_US）。 |

### フィールドの検証

フィールドには 1 つ以上のバリデータクラスを割り当てて、ユーザーの入力が拡張機能の要件を満たしていることを確認できます。 検証ルールは `<validate>`-Tag で適用できます。
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
| `letters-only` | レターのみを使用できます。 例：`abcABC`。 |
| `letters-with-basic-punc` | 文字または句読点のみを使用できます。<br> 次の式を渡す必要があります：`/^[a-z\-.,()\u0027\u0022\s]+$/i`。 |
| `mobileUK` | （英国）の携帯電話番号を使用できます。 |
| `no-marginal-whitespace` | 値の先頭または末尾に空白を使用できないようにします。 |
| `no-whitespace` | 空白を許可しません。 |
| `phoneUK` | （英国）の電話番号を使用できます。 |
| `phoneUS` | （米国）の電話番号を使用できます。 |
| `required-entry` | 空の値を許可しません（`validate-no-empty` と同等の検証）。<br> 検証エラーメッセージ：「これは必須フィールドです。」 |
| `time` | 24 時間形式（00 ～ 23:00）で有効 :59 時間を指定できます。 例えば、`15`、`15:05` または `15:05:48` です。 |
| `time12h` | 12 時間形式（午前 12 時～午後 11:0059:59:）で有効な時間を指定できます。 例えば、`3 am`、`11:30 pm`、`02:15:00 pm` です。 |
| `validate-admin-password` | 数字とアルファベットの両方を使用して、7 文字以上の文字を許可します。 |
| `validate-alphanum-with-spaces` | 文字（a ～ z または A ～ Z）、数字（0 ～ 9）、スペースのみを使用できます。 |
| `validate-clean-url` | 有効な URL を使用できます。 例えば、`https://www.example.com` や `www.example.com` です。 |
| `validate-currency-dollar` | 有効な（ドル）金額を許可します。 例えば、$100.00 です。 |
| `validate-data` | 文字（a ～ z または A ～ Z）、数字（0 ～ 9）、アンダースコア（\_）のみを使用できます。<br> 最初の文字は文字である必要があります。<br> （Must match expression: `/^[A-Za-z]+[A-Za-z0-9_]+$/`） <br> 検証エラーメッセージ：「このフィールドでは文字（a ～ z または A ～ Z）、数字（0 ～ 9）またはアンダースコア（\_）のみを使用してください。最初の文字は文字にする必要があります。」 |
| `validate-date-au` | では、dd/mm/yyyy の日付形式が適用されます。 2006 年 3 月 17 日の場合は、17/03/2006 となります。 |
| `validate-email` | 有効なメールアドレスを指定できます。 例えば、johndoe@domain.comです。 |
| `validate-emailSender` | 有効なメールアドレスを指定できます。 例えば、johndoe@domain.comです。 |
| `validate-fax` | 有効な FAX 番号を許可します。 例：123-456-7890 |
| `validate-no-empty` | 空の値を許可しません（`requried-entry` と同等の検証）。<br> 検証エラーメッセージ：「空の値。」 |
| `validate-no-html-tags` | HTML タグの使用を許可しません。 |
| `validate-password` | 6 文字以上を使用できます。 先頭と末尾のスペースは無視されます。 |
| `validate-phoneLax` | 有効な電話番号を許可します。 例えば、（123） 456-7890 や 123-456-7890 などです。 |
| `validate-phoneStrict` | 有効な電話番号を許可します。 例えば、（123） 456-7890 や 123-456-7890 などです。 |
| `validate-select` | 選択した選択オプションに `null` 値、文字列値 `none`、または文字列長 0 が含まれていないことを強制します。 |
| `validate-ssn` | 有効な（米国）社会保障番号を許可します。 例：123-45-6789 |
| `validate-street` | 文字（a ～ z または A ～ Z）、数字（0 ～ 9）、スペース、「#」のみを使用できます。 |
| `validate-url` | 有効な URL を使用できます。 プロトコルが必要です（http://、https://、ftp://）。 |
| `validate-xml-identifier` | 有効な XML 識別子を許可します。 例えば、something_1、block5、id-4 などです。 |
| `validate-zip-us` | 有効な（米国）郵便番号を指定できます。 例えば、90602 や 90602-1234 です。 |
| `vinUS` | 車両識別番号（VIN）値を許可します。 |

### デフォルト値

フィールドのデフォルト値は、`etc/config.xml` ノードでデフォルト値を指定することで、モジュールの `section/group/field_ID` ファイルで設定することができます。

#### 例：`ANOTHER_UNIQUE_FIELD_ID` のデフォルト値の設定（デフォルトの範囲）

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

#### 例：`ANOTHER_UNIQUE_FIELD_ID` のデフォルト値の設定（Web サイトの範囲）

`websites` タグを使用して、特定の web サイトのデフォルト値を指定します。

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
