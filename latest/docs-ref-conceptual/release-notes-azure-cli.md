---
title: "Azure CLI 2.0 リリース ノート"
description: "Azure CLI 2.0 の最新情報について説明します"
keywords: "Azure CLI 2.0, リリース ノート"
author: sptramer
ms.author: sttramer
manager: douge
ms.date: 04/03/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ms.assetid: ce0428f7-0a59-4e72-9237-d907b171af51
ms.openlocfilehash: ad30efeb7efafcc5816160ee130665d37adb62c6
ms.sourcegitcommit: e866977985ba0286fa05f41729dd7e7d9ce86f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2017
---
# <a name="azure-cli-20-release-notes"></a>Azure CLI 2.0 リリース ノート

## <a name="september-11-2017"></a>2017 年 9 月 11 日

バージョン 2.0.17

### <a name="core"></a>コア

* テレメトリで独自の関連付け ID を設定するコマンド モジュールを有効にしました
* テレメトリが診断モードに設定された際に発生する JSON ダンプの問題を修正しました

### <a name="acs"></a>ACS

* `acs list-locations` コマンドを追加しました
* `ssh-key-file` を予想される既定値と共に使用されるようにしました

### <a name="appservice"></a>Appservice

* アクティブなサービス プラン以外のリソース グループで Web アプリを作成する機能を追加しました

### <a name="cdn"></a>CDN

* `cdn custom-domain create` の "CustomDomain is not interable" バグを修正しました。

### <a name="extension"></a>内線番号

* 最初のリリース。

### <a name="keyvault"></a>KeyVault

* `keyvault set-policy` について、アクセス許可の大文字と小文字が区別される問題を修正しました。

### <a name="network"></a>ネットワーク

* `vnet list-private-access-services` の名前を `vnet list-endpoint-services` に変更しました
* `vnet subnet create/update` の `--private-access-services` 引数の名前を `--service-endpoints` に変更しました
* `nsg rule create/update` に対する複数の IP 範囲およびポート範囲のサポートを追加しました
* `lb create` に対する SKU のサポートを追加しました
* `public-ip create` に対する SKU のサポートを追加しました

### <a name="resource"></a>リソース

* `policy definition create` と `policy definition update` でリソース ポリシーのパラメーター定義を渡せるようにします
* `policy assignment create` でパラメーター値を渡せるようにします
* すべてのパラメーターについて JSON またはファイルを渡せるようにします
* API バージョンを増やしました

### <a name="sql"></a>SQL

* `sql server vnet-rule` コマンドを追加しました

### <a name="vm"></a>VM

* 修正済み: `--scope` が指定されないとアクセス権が割り当てられない
* 修正済み: ポータルと同じ拡張機能の名前付けが行われる
* `[vm|vmss] create` 出力から `subscription` を削除しました
* 修正済み: `[vm|vmss] create` ストレージ SKU がイメージ付きのデータ ディスクに適用されない
* 修正済み: `vm format-secret --secrets` で、改行によって分かれた ID を使用できない

## <a name="august-31-2017"></a>2017 年 8 月 31 日

バージョン 2.0.16

### <a name="keyvault"></a>KeyVault

* `secret download` でシークレット エンコードを自動的に解決しようとする際に発生するバグを修正しました

### <a name="sf"></a>SF

* すべてのコマンドが非推奨とされ、Service Fabric CLI (sfctl) が優先されます

### <a name="storage"></a>Storage

* ネットワーク ACL 機能がサポートされていないリージョンでストレージ アカウントを作成できない問題を修正しました
* コンテンツの種類とエンコードがどちらも指定されていない場合、BLOB とファイルのアップロード中にコンテンツの種類とエンコードを決定します

## <a name="august-28-2017"></a>2017 年 8 月 28 日

バージョン 2.0.15

### <a name="cli"></a>CLI

* `--version` に法的事項を追加しました。

### <a name="acs"></a>ACS

* プレビュー リージョンを修正しました。
* 既定の `dns_name_prefix` を正しい形式にしました。
* ACS コマンド出力を最適化しました。

### <a name="appservice"></a>Appservice

* [重大な変更] `az webapp config appsettings [delete|set]` の出力の不整合を修正しました
* `az webapp config container set --docker-custom-image-name` の `-i` の新しいエイリアスを追加しました
* `az webapp log show` を公開しました
* App Service プラン、メトリック、または DNS 登録を保持するために、`az webapp delete` の新しい引数を公開しました
* 修正済み: スロット設定の正常な検出

### <a name="iot"></a>IoT

* 修正済み #3934: ポリシーの作成で既存のポリシーが消去されなくなりました

### <a name="network"></a>ネットワーク

* [重大な変更] 名前を `vnet list-private-access-services` から `vnet list-endpoint-services` に変更しました
* [重大な変更] `vnet subnet [create|update]` のオプション `--private-access-services` の名前を `--service-endpoints` に変更しました
* `nsg rule [create|update]` に対する複数 IP およびポート範囲のサポートを追加しました
* `lb create` に対する SKU のサポートを追加しました
* `public-ip create` に対する SKU のサポートを追加しました

### <a name="profile"></a>プロファイル

* 仮想マシンの ID を使用してログインするために、`--msi` と `--msi-port` を公開しました

### <a name="service-fabric"></a>Service Fabric

* プレビュー リリース
* コマンドに対するレジストリのユーザー/パスワード規則を簡略化しました
* パラメーターを渡した後でもユーザーにパスワードの入力が求められる問題を修正しました
* 空の `registry_cred` のサポートを追加しました

### <a name="storage"></a>Storage

* BLOB 層の設定を有効にしました
* サービス トンネリングをサポートするために、`--bypass` 引数と `--default-action` 引数を `storage account [create|update]` に追加しました
* VNET ルールと IP ベースのルールを `storage account network-rule` に追加するためのコマンドを追加しました  
* 顧客管理キーによるサービスの暗号化を有効にしました
* [重大な変更] `az storage account create and az storage account update` コマンドの `--encryption` オプションの名前を `--encryption-services` に変更しました
* 修正済み #4220: `az storage account update encryption` - 構文の不一致

### <a name="vm"></a>VM

* `vmss get-instance-view` で `--instance-id *` を使用した場合に、余分な間違えた情報が表示される問題を修正しました
* `vmss create` に `--lb-sku` のサポートを追加しました。 
* `[vm|vmss] create` の管理者名ブラックリストから人物名を削除しました 
* イメージからプラン情報を抽出できない場合に `[vm|vmss] create` がエラーをスローする問題を修正しました
* 内部 LB で vmms scaleset を作成するときのクラッシュを修正しました
* `vm availability-set create` で `--no-wait` 引数が機能しない問題を修正しました


## <a name="august-15-2017"></a>2017 年 8 月 15 日

バージョン 2.0.14

### <a name="acs"></a>ACS

* kubernetes の sshMaster0 ポート番号を修正しました

### <a name="appservice"></a>Appservice

* 新しい Git ベースの Linux Web アプリを作成するときの例外を修正しました

### <a name="event-grid"></a>Event Grid

* SDK 依存関係を追加しました

## <a name="august-11-2017"></a>2017 年 8 月 11 日

バージョン 2.0.13

### <a name="acs"></a>ACS

* プレビュー リージョンを追加しました

### <a name="batch"></a>Batch


* Batch SDK 3.1.0 と Batch Management SDK 4.1.0 に更新しました
* ジョブのタスク数を表示する新しいコマンドを追加しました
* リソース ファイルの SAS URL 処理のバグを修正しました
* Batch アカウントのエンドポイントで、オプションの "https://" プレフィックスがサポートされるようになりました
* ジョブに対する 100 を超えるタスクのリストの追加をサポートします
* 拡張機能コマンド モジュールの読み込みのデバッグ ログを追加しました

### <a name="component"></a>コンポーネント

* "az component" コマンドに非推奨警告を追加しました

### <a name="container"></a>コンテナー

* `create`: 環境変数内で等号を使用できない問題を修正しました


### <a name="data-lake-store"></a>Data Lake Store

* プログレス コントロールを有効にしました

### <a name="event-grid"></a>Event Grid

* 最初のリリース

### <a name="network"></a>ネットワーク

* `lb`: 特定の子リソース名が省略された場合に正しく解決されない問題を修正しました
* `application-gateway {subresource} delete`: `--no-wait` が受け入れられない問題を修正しました
* `application-gateway http-settings update`: `--connection-draining-timeout` を無効にできない問題を修正しました
* `az network vpn-connection ipsec-policy add` での予期しないキーワード引数 `sa_data_size_kilobyes` のエラーを修正しました

### <a name="profile"></a>プロファイル

* `account list`: サーバーの最新のサブスクリプションを同期する `--refresh` を追加しました

### <a name="storage"></a>Storage

* システムによって割り当てられた ID によるストレージ アカウントの更新を有効にします

### <a name="vm"></a>VM

* `availability-set`: 変換時の障害ドメイン数を公開しました
* `list-skus` コマンドを公開しました
* ロールの割り当てを作成しない ID の割り当てをサポートします
* データ ディスクのアタッチ時にストレージ SKU を適用します
* 管理ディスクを使用する場合の既定の os-disk 名とストレージ SKU を削除しました


## <a name="july-28-2017"></a>2017 年 7 月 28 日

バージョン 2.0.12

* コンテナー コマンドを追加しました
* 請求および使用量モジュールを追加しました

```
azure-cli (2.0.12)  

acr (2.0.9)  
acs (2.0.11)  
appservice (0.1.11)  
batch (3.0.3)  
billing (0.1.3)  
cdn (0.0.6)  
cloud (2.0.7)  
cognitiveservices (0.1.6)  
command-modules-nspkg (2.0.1)  
component (2.0.6)  
configure (2.0.10)  
consumption (0.1.3)  
container (0.1.7)  
core (2.0.12)  
cosmosdb (0.1.11)  
dla (0.0.10)  
dls (0.0.11)  
feedback (2.0.6)  
find (0.2.6)  
interactive (0.3.7)  
iot (0.1.10)  
keyvault (2.0.8)  
lab (0.0.9)  
monitor (0.0.8)  
network (2.0.11)  
nspkg (3.0.1)  
profile (2.0.9)  
rdbms (0.0.5)  
redis (0.2.7)  
resource (2.0.11)  
role (2.0.9)  
sf (1.0.5)  
sql (2.0.8)  
storage (2.0.11)  
vm (2.0.11) 
```

### <a name="core"></a>コア

* サービス プリンシパルの SDK 認証情報と証明書を出力します
* デプロイの進行状況の例外を修正しました
* サブスクリプション クライアントを作成するために、現在のクラウドの ARM エンドポイントを使用します
* clouds.config ファイルの同時処理機能が向上しました (#3636)
* コマンド実行のたびにクライアント要求 ID を更新します
* 正しい SDK プロファイルでサブスクリプション クライアントを作成します (#3635)
* テンプレート デプロイの進行状況レポート (#3510)
* jmespath クエリを通じてテーブル出力フィールドを選択するサポートを追加しました (#3581)
* 解析引数のミュートを改善し、ジェスチャによる履歴を追加しました (#3434)
* 正しい SDK プロファイルでサブスクリプション クライアントを作成します
* すべての既存のレコーディング ファイルを最新のフォルダーに移動します
* VM/VMSS 作成のべき等を修正しました (#3586)
* コマンド パスで大文字と小文字が区別されなくなりました
* 特定のブール型パラメーターで大文字と小文字が区別されなくなりました
* Azure Stack のような ADFS オンプレミス サーバーへのログインをサポートします
* clouds.config への同時書き込みを修正しました (#3255)

### <a name="acr"></a>ACR

* 管理対象レジストリ用の `show-usage` コマンドを追加しました
* 管理対象レジストリの SKU 更新をサポートします
* 管理対象レジストリと管理 SKU を追加しました
* 管理対象レジストリの webhook と acr webhook コマンド モジュールを追加しました
* AAD 認証と acr login コマンドを追加しました
* Docker リポジトリ、マニフェスト、タグ用の delete コマンドを追加しました

### <a name="acs"></a>ACS

* API バージョン 2017-07-01 をサポートします

### <a name="appservice"></a>Appservice

* Linux Web アプリの一覧表示で何も返されないバグを修正しました
* acr からの資格情報の取得をサポートします
* `appservice web` のすべてのコマンドを削除します
* コマンド出力で Docker レジストリのパスワードをマスクします (#3656)
* macOS でエラーにならずに既定のブラウザーが使用されます (#3623)
* `webapp log tail` と `webapp log download` のヘルプを改善します (#3624)
* 静的ルーティングを構成するための `traffic-routing` コマンドを公開しました (#3566)
* ソース管理の構成で信頼性のための修正が追加されました (#3245)
* Windows Web アプリ用の `webapp config update` から、サポートされていない `--node-version` 引数を削除しました。 代わりに `webapp config appsettings set --settings WEBSITE_NODE_DEFAULT_VERSION=...` を使用してください

### <a name="batch"></a>Batch


* Batch SDK 3.0.0 に更新して、プール内の優先度が低い VM がサポートされるようにしました
* `pool create` のオプション `--target-dedicated` の名前を `--target-dedicated-nodes` に変更しました
* `pool create` のオプションの `--target-low-priority-nodes` と `--application-licenses` を追加しました

### <a name="cdn"></a>CDN

* `--profile-name` によって指定されたプロファイルが存在しない場合に表示される `cdn endpoint list` のエラー メッセージを、より適切な内容に変更しました。

### <a name="cloud"></a>クラウド

* クラウド メタデータ エンドポイントの API バージョンを YYYY-MM-DD 形式に変更しました
* ギャラリー エンドポイントは必須ではありません
* ARM リソース マネージャー エンドポイントだけでのクラウドの登録をサポートします
* `cloud set` で現在のクラウドを選択するときにプロファイルを選択できるオプションを提供しました
* `endpoint_vm_image_alias_doc` を公開しました

### <a name="cosmosdb"></a>Cosmos DB

* カスタム パーティション キーでコレクションを作成できるように修正しました
* 既定のコレクション TTL のサポートを追加しました。

### <a name="data-lake-analytics"></a>Data Lake Analytics

* コンピューティング ポリシー管理用のコマンドを `dla account compute-policy` 見出しの下に追加しました
* `dla job pipeline show` を追加しました
* `dla job recurrence list` を追加しました

### <a name="data-lake-store"></a>Data Lake Store

* ユーザー管理のキー コンテナーのキー ローテーションのサポートを `dls account update` に追加しました
* 基になる Data Lake Store ファイル システム SDK のバージョンを更新して、パフォーマンスの問題に対応しました
* コマンド `dls enable-key-vault` を追加しました。 このコマンドでは、Data Lake Store アカウント内でデータの暗号化を使用するために、ユーザー指定のキー コンテナーの有効化が試行されます

### <a name="interactive"></a>対話

* キャッシュされたコマンドを使用することで、起動時間が向上しました
* テスト カバレッジが増えました
* "?" ジェスチャが次のコマンドにも挿入されるよう強化しました
* プロファイル 2017-03-09-profile-preview との対話エラーを修正しました (#3587)
* `--version` を対話モードのパラメーターとして使用できるようにしました (#3645)
* 対話モードで検証の完了時にエラーがスローされないようにします (#3570)
* テンプレート デプロイの進行状況レポート (#3510)
* `--progress` フラグを追加しました
* 入力候補から `--debug` と `--verbose` を削除しました
* 入力候補から `interactive` を削除しました (#3324)

### <a name="iot"></a>IoT

* ポリシーの作成で既存のポリシーが消去されないように修正しました。 (#3934)

### <a name="key-vault"></a>Key Vault

* キー コンテナーの回復機能のために、以下のコマンドを追加しました。
  * `keyvault` サブコマンドの `purge`、`recover`、`keyvault list-deleted`
  * `keyvault secret` サブコマンドの `backup`、`restore`、`purge`、`recover`、`list-deleted`
  * `keyvault certificate` サブコマンドの `purge`、`recover`、`list-deleted`
  * `keyvault key` サブコマンドの `purge`、`recover`、`list-deleted`
* サービス プリンシパルのキー コンテナーの統合を追加しました (#3133)
* キー コンテナー データプレーンを 0.3.2 に更新しました。 (#3307)

### <a name="lab"></a>ラボ

* `az lab vm claim` を通じてラボ内の任意の VM を要求するためのサポートを追加しました
* `az lab vm list` と `az lab vm show` のテーブル出力フォーマッタを追加しました

### <a name="monitor"></a>監視

* `monitor autoscale-settings get-parameters-template` コマンドのテンプレート ファイルを修正しました (#3349)
* `monitor alert-rule-incidents list` の名前を `monitor alert list-incidents` に変更しました
* `monitor alert-rule-incidents show` の名前を `monitor alert show-incident` に変更しました
* `monitor metric-defintions list` の名前を `monitor metrics list-definitions` に変更しました
* `monitor alert-rules` の名前を `monitor alert` に変更しました
* `monitor alert create` を次のように変更しました。
  * `condition` および `action` サブコマンドが JSON を受け入れなくなりました
  * ルール作成プロセスを簡略化するために多数のパラメーターを追加します
  * `location` が必須ではなくなりました
  * ターゲットの名前と ID のサポートを追加します
  * `--alert-rule-resource-name` を削除します
  * `is-enabled` の名前を `enabled` に変更し、省略可能にしました
  * `description` の既定値が、指定された条件に基づいて設定されるようになりました
  *  新しい形式をわかりやすく示すための例を追加します
* `monitor metric` コマンドの名前または ID をサポートします
* `monitor alert rule update` に便利な引数と例を追加しました

### <a name="network"></a>ネットワーク

* `list-private-access-services` コマンドを追加しました
* `--private-access-services` 引数を `vnet subnet create` と `vnet subnet update` に追加しました
* `application-gateway redirect-config create` が失敗する問題を修正しました
* `application-gateway redirect-config update` で `--no-wait` を指定しても機能しない問題を修正しました
* `application-gateway address-pool create` と `application-gateway address-pool update` で `--servers` 引数を使用する場合のバグを修正しました
* `application-gateway redirect-config` コマンドを追加しました
* `list-options`、`predefined list`、`predefined show` の各コマンドを `application-gateway ssl-policy` に追加しました
* `--name`、`--cipher-suites`、`--min-protocol-version` の各引数を `application-gateway ssl-policy set` に追加しました
* `--host-name-from-backend-pool`、`--affinity-cookie-name`、`--enable-probe`、`--path` の各引数を `application-gateway http-settings create` と `application-gateway http-settings update` に追加しました
* `--default-redirect-config` 引数と `--redirect-config` 引数を `application-gateway url-path-map create` と `application-gateway url-path-map update` に追加しました
* `--redirect-config` 引数を `application-gateway url-path-map rule create` に追加しました
* `--no-wait` のサポートを `application-gateway url-path-map rule delete` に追加しました
* `--host-name-from-http-settings`、`--min-servers`、`--match-body`、`--match-status-codes` の各引数を `application-gateway probe create` と `application-gateway probe update` に追加しました
* `--redirect-config` 引数を `application-gateway rule create` と `application-gateway rule update` に追加しました
* `--accelerated-networking` のサポートを `nic create` と `nic update` に追加しました
* `nic create` から `--internal-dns-name-suffix` 引数を削除しました
* `--dns-servers` のサポートを `nic update` と `nic create` に追加しました: --dns-servers のサポートを追加しました
* `local-gateway create` で `--local-address-prefixes` が無視されるバグを修正しました
* `--dns-servers` のサポートを `vnet update` に追加しました
* `express-route peering create` でルート フィルター処理をせずにピアリングを作成するときのバグを修正しました
* `express-route update` で `--provider` および `--bandwidth` 引数が機能しないバグを修正しました
* `network watcher show-topology` の既定値設定ロジックのバグを修正しました
* `network list-usages` の出力書式設定を改善しました
* `application-gateway http-listener create` に既定のフロントエンド IP を使用します (1 つしかない場合)
* `application-gateway rule create` に既定のアドレス プール、HTTP 設定、および HTTP リスナーを使用します (1 つしかない場合)
* `lb rule create` に既定のフロントエンド IP およびバックエンド プールを使用します (1 つしかない場合)
* `lb inbound-nat-rule create` に既定のフロントエンド IP を使用します (1 つしかない場合)

### <a name="profile"></a>プロファイル

* 管理対象 ID での VM 内のログインをサポートします
* `account show` で SDK 認証ファイル形式での出力をサポートします
* "--expanded-view" を使用した場合に非推奨警告を表示します
* 生の AAD トークンを提供するための `get-access-token` コマンドを追加しました
* サブスクリプションが関連付けられていないユーザー アカウントでのログインをサポートします

### <a name="rdbms"></a>RDBMS

* サブスクリプション全体のサーバーの一覧表示をサポートします (#3417)
* `% server_type` が見つからないために `%s` が処理されない問題を修正しました (#3393)
* ドキュメント ソース マップを修正し、検証するための CI タスクを追加しました (#3361)
* MySQL および PostgreSQL のヘルプを修正しました (#3369)

### <a name="resource"></a>リソース

* `group deployment create` の不足しているパラメーターの指定を求めるメッセージを改善しました
* `--parameters KEY=VALUE` 構文の解析を改善しました
* `group deployment create` のパラメーター ファイルが `@<file>` 構文で認識されなくなった問題を修正しました
* `resource` および `managedapp` コマンドで `--ids` 引数をサポートします
* いくつかの解析およびエラー メッセージを修正しました (#3584)
* `<resource-namespace>` と `<resource-type>` を受け入れるよう、`lock` コマンドの `--resource-type` の解析を修正しました
* テンプレート リンク テンプレートのパラメーター チェックを追加しました (#3629)
* `KEY=VALUE` 構文でデプロイ パラメーターを指定するためのサポートを追加しました

### <a name="role"></a>役割

* `create-for-rbac` で SDK 認証ファイル形式での出力をサポートします
* サービス プリンシパルを削除するときに、ロールの割り当てと、関連する AAD アプリケーションがクリーンアップされるようになりました (#3610)
* `app create` の引数 `--start-date` および `--end-date` の説明に時刻形式を含めます
* `--expanded-view` を使用した場合に非推奨警告を表示します
* キー コンテナーの統合を `create-for-rbac` および `reset-credentials` コマンドに追加しました

### <a name="service-fabric"></a>Service Fabric
* アプリケーション内の大きなファイルがアップロード時に切り詰められる問題を修正しました (#3666)
* Service Fabric コマンドのテストを追加しました (#3424)
* 多数の Service Fabric コマンドを修正しました (#3234)

### <a name="sql"></a>SQL

* 壊れた `sql server create` `--identity` パラメーターを削除しました
* `sql server create` および `sql server update` コマンドの出力からパスワード値を削除しました
* `sql db list-editions` および `sql elastic-pool list-editions` コマンドを追加しました

### <a name="storage"></a>Storage

* `storage blob list`、`storage container list`、`storage share list` の各コマンドから `--marker` オプションを削除しました (#3745)
* https 専用ストレージ アカウントの作成を有効にしました
* storage metrics、logging、cors の各コマンドを更新しました (#3495)
* CORS add からの例外メッセージを言い換えました (#3638) (#3362)  
* ジェネレーターをドライ ラン モードのダウンロード バッチ コマンド内の一覧に変換しました (#3592) 
* BLOB ダウンロード バッチのドライ ランの問題を修正しました (#3640) (#3592)

### <a name="vm"></a>VM

* nsg の構成をサポートします
* DNS サーバーが正しく構成されないバグを修正しました
* 管理対象のサービス ID をサポートします
* 既存のロード バランサーを使用する `cmss create` で `--backend-pool-name` が必要だった問題を修正しました。
* `vm image create` で作成された datadisks の lun を 0 から開始します


## <a name="may-10-2017"></a>2017 年 5 月 10 日

バージョン 2.0.6

* documentdb から cosmosdb に名前が変更されました
* rdbms (mysql、postgres) が追加されました
* Data Lake Analytics モジュールと Data Lake Store モジュールが追加されました。
* Cognitive Services モジュールが追加されました。
* Service Fabric モジュールが追加されました。
* 対話型モジュールが追加されました (az-shell の名前変更)。
* CDN コマンドに対応するようになりました。
* コンテナー モジュールが削除されました。
* "az --version" のショートカットとして "az -v" が追加されました ([#2926](https://github.com/Azure/azure-cli/issues/2926))
* パッケージ読み込みとコマンド実行のパフォーマンスが向上しています ([#2819](https://github.com/Azure/azure-cli/issues/2819))

```
azure-cli (2.0.6)

acr (2.0.4)
acs (2.0.6)
appservice (0.1.6)
batch (2.0.4)
cdn (0.0.2)
cloud (2.0.2)
cognitiveservices (0.1.2)
command-modules-nspkg (2.0.0)
component (2.0.4)
configure (2.0.6)
core (2.0.6)
cosmosdb (0.1.6)
dla (0.0.6)
dls (0.0.6)
feedback (2.0.2)
find (0.2.2)
interactive (0.3.1)
iot (0.1.5)
keyvault (2.0.4)
lab (0.0.4)
monitor (0.0.4)
network (2.0.6)
nspkg (3.0.0)
profile (2.0.4)
rdbms (0.0.1)
redis (0.2.3)
resource (2.0.6)
role (2.0.4)
sf (1.0.1)
sql (2.0.3)
storage (2.0.6)
vm (2.0.6)
```

### <a name="core"></a>コア

* コア: 登録されていないプロバイダーによる例外がキャプチャされ、自動登録されます   
* パフォーマンス: プロセスが終了するまで ADAL トークン キャッシュがメモリに保持されます ([#2603](https://github.com/Azure/azure-cli/issues/2603))
* 16 進フィンガープリント -o tsv から返されるバイトが修正されました ([#3053](https://github.com/Azure/azure-cli/issues/3053))
* Key Vault 証明書ダウンロードの強化と AAD SP 統合 ([#3003](https://github.com/Azure/azure-cli/issues/3003))
* Python の場所が "az —version" に追加されました ([#2986](https://github.com/Azure/azure-cli/issues/2986))
* ログイン: サブスクリプションがないときのログインに対応するようになりました ([#2929](https://github.com/Azure/azure-cli/issues/2929))
* コア: サービス プリンシパルを 2 回使用してログインするときのエラーが修正されました ([#2800](https://github.com/Azure/azure-cli/issues/2800))
* コア: accessTokens.json のファイル パスを環境変数で構成できます ([#2605](https://github.com/Azure/azure-cli/issues/2605))
* コア: 構成済み既定値を省略可能な引数に適用できます ([#2703](https://github.com/Azure/azure-cli/issues/2703))
* コア: パフォーマンスの向上
* コア: カスタム CA 証明書 - REQUESTS_CA_BUNDLE 環境変数の設定を利用できます
* コア: クラウド構成 - "管理" エンドポイントが設定されていない場合に、"リソース マネージャー" エンドポイントが使用されます

### <a name="acs"></a>ACS

* マスター数とエージェント数が文字列から整数に修正されました
* 非同期作成用に "az acs create --no-wait" と "az acs wait" が公開されました
* ドライラン検証用に "az acs create --validate" が公開されました
* スケール コマンドの PUT 呼び出しの前の Windows プロファイルが削除されます ([#2755](https://github.com/Azure/azure-cli/issues/2755))

### <a name="appservice"></a>AppService

* 関数アプリ: 作成、表示、リスト、削除、ホスト名、SSL など、関数アプリに完全に対応するようになりました
* Team Services (VSTS) が継続的な配信オプションとして "appservice web source-control config" に追加されました
* "az webapp" が作成され "az app service web" が置き換えられています (下位互換性のために "az app service web" は 2 リリースだけ保持されます)
* WebApp 作成時にデプロイと "ランタイム スタック" を構成するための引数が公開されました
* "webapp list-runtimes" が公開されました
* 接続文字列の構成がサポートされています ([#2647](https://github.com/Azure/azure-cli/issues/2647))
* プレビューでのスロット スワップがサポートされています
* appservice コマンドからのポーランド語のエラー ([#2948](https://github.com/Azure/azure-cli/issues/2948))
* 証明書の操作に App Service プランのリソース グループが使用されます ([#2750](https://github.com/Azure/azure-cli/issues/2750))

### <a name="cosmosdb"></a>CosmosDB

* documentdb モジュールから cosmosdb に名前が変更されました。
* DocumentDB データプレーン API: データベースとコレクション管理に対応するようになりました
* データベース アカウントにおける自動フェールオーバーの有効化に対応するようになりました
* 新しい一貫性ポリシー ConsistentPrefix に対応するようになりました

### <a name="data-lake-analytics"></a>Data Lake Analytics

* ジョブ リストの結果と状態に対するフィルター処理でエラーがスローされるバグが修正されました。
* 新しいカタログ項目の種類: パッケージに対応するようになりました。 `az dla catalog package` を介してアクセスされます
* 次のカタログ項目の一覧をデータベース内から表示できます (スキーマ仕様は不要です)。

  * テーブル
  * テーブル値関数
  * 表示
  * テーブルの統計。 スキーマと一緒に表示することもできますが、テーブル名を指定する必要はありません。

### <a name="data-lake-store"></a>Data Lake Store

* 基になるファイルシステム SDK のバージョンが更新され、サーバー側スロットル処理への対応が強化されました。
* パッケージ読み込みとコマンド実行のパフォーマンスが向上しています ([#2819](https://github.com/Azure/azure-cli/issues/2819))
* access show のヘルプがなかったため、 追加しました  ([#2743](https://github.com/Azure/azure-cli/issues/2743))

### <a name="find"></a>検索

* 検索結果を改善し、検索インデックスのバージョン管理を可能にしました

### <a name="keyvault"></a>KeyVault

* BC: `az keyvault certificate download` によって -e が文字列またはバイナリから PEM または DER に変更され、オプションの表現が向上しました
* BC: --expires パラメーターと --not-before パラメーターはサービスでサポートされていないため、`keyvault certificate create` から削除されました。
* --validity パラメーターが `keyvault certificate create` に追加され、--policy の値が選択的に上書きされます
* "expires" と "not_before" が公開され、"validity_in_months" が公開されなかった場合に `keyvault certificate get-default-policy` で発生する問題が修正されました。
* KeyVault における pem と pfx のインポートが修正されました ([#2754](https://github.com/Azure/azure-cli/issues/2754))

### <a name="lab"></a>ラボ

* ラボ環境用の作成、表示、削除、およびリスト コマンドが追加されました。
* ラボで ARM テンプレートを表示するための表示およびリスト コマンドが追加されました。
* ラボ環境で VM をフィルター処理するための --environment フラグが `az lab vm list` に追加されました。
* ラボの数式内でアーティファクト スキャフォールディングをエクスポートするための便利なコマンド `az lab formula export-artifacts` が追加されました。
* ラボ内でシークレットを管理するためのコマンドが追加されました。

### <a name="monitor"></a>監視

* バグの修正: JSON 文字列を使用するため `az alert-rules create` の `--actions` がモデル化されています ([#3009](https://github.com/Azure/azure-cli/issues/3009))
* バグの修正: diagnostic settings create が、表示コマンドからのログ/メトリックを受け付けません ([#2913](https://github.com/Azure/azure-cli/issues/2913))

### <a name="network"></a>ネットワーク

* `network watcher test-connectivity` コマンドが追加されました。
* `network watcher packet-capture create` の `--filters` パラメーターに対応するようになりました。
* Application Gateway 接続のドレインに対応するようになりました。
* Application Gateway WAF 規則セットの構成に対応するようになりました。
* ExpressRoute ルート フィルターとルールに対応するようになりました。
* TrafficManager の地理的なルーティングに対応するようになりました。
* VPN 接続ポリシー ベースのトラフィック セレクターに対応するようになりました。
* VPN 接続 IPSec ポリシーに対応するようになりました。
* `--no-wait` パラメーターまたは `--validate` パラメーターを使用するときの `vpn-connection create` のバグが修正されました。
* アクティブ/アクティブ VNet ゲートウェイに対応するようになりました
* `network vpn-connection list/show` コマンドの出力から null 値が削除されました。
* BC: `vpn-connection create` の出力のバグが修正されました 
* "vpn-connection create" の "--key-length" 引数が適切に解析されないバグが修正されました。
* `dns zone import` でレコードが適切にインポートされないバグが修正されました。
* `traffic-manager endpoint update` が動作しないバグを修正しました。
* "Network Watcher" プレビューのコマンドが追加されました。

### <a name="profile"></a>プロファイル

* サブスクリプションが見つからないときのログインに対応するようになりました ([#2560](https://github.com/Azure/azure-cli/issues/2560))
* az account set --subscription で短いパラメーター名に対応するようになりました ([#2980](https://github.com/Azure/azure-cli/issues/2980))

### <a name="redis"></a>Redis

* Redis Cache のスケール機能も追加する更新コマンドが追加されました
* "update-settings" コマンドが廃止されました。

### <a name="resource"></a>リソース

* managedapp と managedapp の定義コマンドが追加されました ([#2985](https://github.com/Azure/azure-cli/issues/2985))
* "provider operation" コマンドに対応するようになりました ([#2908](https://github.com/Azure/azure-cli/issues/2908))
* 汎用リソースの作成に対応するようになりました ([#2606](https://github.com/Azure/azure-cli/issues/2606))
* リソース解析および API バージョンの検索が修正されました  ([#2781](https://github.com/Azure/azure-cli/issues/2781))
* az lock update のドキュメントが追加されました  ([#2702](https://github.com/Azure/azure-cli/issues/2702))
* 存在しないグループのリソースの一覧を表示しようとするとエラーが出力されます  ([#2769](https://github.com/Azure/azure-cli/issues/2769))
* [コンピューティング] VMSS と VM の可用性セットの更新に関する問題が修正されました。 ([#2773](https://github.com/Azure/azure-cli/issues/2773))
* parent-resource-path が None の場合のロックの作成と削除が修正されました ([#2742](https://github.com/Azure/azure-cli/issues/2742))

### <a name="role"></a>役割

* create-for-rbac: SP の終了日が、確実に証明書の有効期限の前に設定されます ([#2989](https://github.com/Azure/azure-cli/issues/2989))
* RBAC: "ad group" が完全にサポートされるようになりました ([#2016](https://github.com/Azure/azure-cli/issues/2016))
* ロール: ロール定義の更新に関する問題が修正されました ([#2745](https://github.com/Azure/azure-cli/issues/2745))
* create-for-rbac: ユーザーによって指定されたパスワードが確実に取得されます

### <a name="sql"></a>SQL

* az sql server list-usages コマンドと az sql db list-usages コマンドが追加されました。
* SQL - リソース プロバイダーに直接接続できます ([#2832](https://github.com/Azure/azure-cli/issues/2832))

### <a name="storage"></a>Storage

* `storage account create` のリソース グループの場所に対する既定の場所。
* 増分 BLOB コピーに対応するようになりました
* 大きなブロック BLOB アップロードに対応するようになりました
* アップロードするファイルが 200 GB を超える場合にブロック サイズが 100 MB に変更されます

### <a name="vm"></a>VM

* avail-set: UD&FD ドメイン数が省略可能になりました

  注: 独立したクラウドの VM コマンド。次の管理対象ディスク関連機能は避けるようにしてください。
  1. az disk/snapshot/image
  2. az vm/vmss disk
  3. "az vm/vmss create" 内では、"—use-unmanaged-disk" を使用して管理対象ディスクを回避します。他のコマンドは機能します
* vm/vmss: SSH キー ペアを生成するときの警告テキストが向上します
* vm/vmss: プラン情報を必要とするマーケットプレイス イメージからの作成をサポートします ([#1209](https://github.com/Azure/azure-cli/issues/1209))


## <a name="april-3-2017"></a>2017 年 4 月 3 日

バージョン 2.0.2

このリリースでは、ACR、Batch、KeyVault、SQL コンポーネントをリリースしました。

```
azure-cli (2.0.2)
 
acr (2.0.0)
acs (2.0.2)
appservice (0.1.2)
batch (2.0.0)
cloud (2.0.0)
component (2.0.0)
configure (2.0.2)
container (0.1.2)
core (2.0.2)
documentdb (0.1.2)
feedback (2.0.0)
find (0.0.1b1)
iot (0.1.2)
keyvault (2.0.0)
lab (0.0.1)
monitor (0.0.1)
network (2.0.2)
nspkg (2.0.0)
profile (2.0.2)
redis (0.1.1b3)
resource (2.0.2)
role (2.0.1)
sql (2.0.0)
storage (2.0.2)
vm (2.0.2)
```

### <a name="core"></a>コア

* 既定の一覧に acr、lab、monitor、find モジュールを追加。
* ログイン: 誤ったテナントをスキップ ([#2634](https://github.com/Azure/azure-cli/pull/2634))
* ログイン: 既定のサブスクリプションを "Enabled" の状態のサブスクリプションに設定 ([#2575](https://github.com/Azure/azure-cli/pull/2575))
* wait コマンドと --no-wait のサポートをより多くのコマンドに追加 ([#2524](https://github.com/Azure/azure-cli/pull/2524))
* コア: 証明書を持つサービス プリンシパルを使用したログインをサポート ([#2457](https://github.com/Azure/azure-cli/pull/2457))
* 不足しているテンプレート パラメーターの指定を求めるメッセージを追加  ([#2364](https://github.com/Azure/azure-cli/pull/2364))
* 既定のリソース グループ、既定の Web、既定の VM など、一般的な引数の既定値の設定をサポート
* 特定のテナントへのログインをサポート
 
### <a name="acs"></a>ACS

* [ACS] 既定の ACS クラスターを構成するためのサポートを追加 ([#2554](https://github.com/Azure/azure-cli/pull/2554))
* ssh キー パスワードの入力要求のサポートを追加  ([#2044](https://github.com/Azure/azure-cli/pull/2044))
* Windows クラスターのためのサポートを追加  ([#2211](https://github.com/Azure/azure-cli/pull/2211))
* 所有者から共同作成者へのロールの切り替え  ([#2321](https://github.com/Azure/azure-cli/pull/2321))
 
### <a name="appservice"></a>AppService

* appservice: DNS A レコードで使用される外部 IP アドレスの取得をサポート ([#2627](https://github.com/Azure/azure-cli/pull/2627))
* appservice: ワイルドカード証明書のバインドをサポート ([#2625](https://github.com/Azure/azure-cli/pull/2625))
* appservice: 発行プロファイルの一覧表示をサポート ([#2504](https://github.com/Azure/azure-cli/pull/2504))
* AppService - 構成後にソース管理の同期をトリガー ([#2326](https://github.com/Azure/azure-cli/pull/2326))
 
### <a name="datalake"></a>DataLake

* Data Lake Analytics モジュールの最初のリリース。
* Data Lake Store モジュールの最初のリリース。
 
### <a name="docuemntdb"></a>DocuemntDB

* DocumentDB: 接続文字列を一覧表示するためのサポートを追加 ([#2580](https://github.com/Azure/azure-cli/pull/2580))

### <a name="vm"></a>VM

* [コンピューティング] 仮想マシン スケール セットを作成するための AppGateway サポートを追加 ([#2570](https://github.com/Azure/azure-cli/pull/2570))
* [VM/VMSS] ディスク キャッシュのサポートを改善しました ([#2522](https://github.com/Azure/azure-cli/pull/2522))
* VM/VMSS: ポータルで使用される資格情報検証ロジックを組み込む ([#2537](https://github.com/Azure/azure-cli/pull/2537))
* wait コマンドと --no-wait のサポートを追加 ([#2524](https://github.com/Azure/azure-cli/pull/2524))
* 仮想マシン スケール セット: VM 間にわたるインスタンス ビューの一覧表示をサポート * ([#2467](https://github.com/Azure/azure-cli/pull/2467))
* VM と仮想マシン スケール セット用の --secrets を追加 ([#2212](https://github.com/Azure/azure-cli/pull/2212))
* 特殊化した VHD による VM 作成を許可 ([#2256](https://github.com/Azure/azure-cli/pull/2256))

## <a name="february-27-2017"></a>2017 年 2 月 27 日

バージョン 2.0.0

Azure CLI 2.0 のこのリリースは、最初の "一般公開" リリースです。
一般公開に該当するのは、以下のコマンド モジュールです。
- コンテナー サービス (acs)
- コンピューティング (Resource Manager、VM、仮想マシン スケール セット、Managed Disks など)
- ネットワーク
- Storage

これらのコマンド モジュールは、運用環境で使用することができ、標準の Microsoft SLA でサポートされています。
問題は、Microsoft サポートで直接開くことも、[github の問題一覧](https://github.com/azure/azure-cli/issues/)で開くこともできます。
[azure-cli タグを使用して StackOverflow](http://stackoverflow.com/questions/tagged/azure-cli) で質問したり、製品チーム ([azfeedback@microsoft.com](mailto:azfeedback@microsoft.com)) に問い合わせたりすることもできます。`az feedback` コマンドを使用すると、コマンド ラインからフィードバックを送ることができます。

これらのモジュールのコマンドは安定しており、Azure CLI のこのバージョンの今後のリリースで構文が変更されることは想定されていません。

CLI のバージョンを確認するには、`az --version` を使用します。
出力では、CLI 自体のバージョン (このリリースでは 2.0.0)、個々のコマンド モジュール、および使用している Python と GCC のバージョンが示されます。

```
azure-cli (2.0.0)

acs (2.0.0)
appservice (0.1.1b5)
batch (0.1.1b4)
cloud (2.0.0)
component (2.0.0)
configure (2.0.0)
container (0.1.1b4)
core (2.0.0)
documentdb (0.1.1b2)
feedback (2.0.0)
iot (0.1.1b3)
keyvault (0.1.1b5)
network (2.0.0)
nspkg (2.0.0)
profile (2.0.0)
redis (0.1.1b3)
resource (2.0.0)
role (2.0.0)
sql (0.1.1b5)
storage (2.0.0)
vm (2.0.0)
 
Python (Darwin) 2.7.10 (default, Jul 30 2016, 19:40:32) 
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.34)]
```

> [!Note]
> コマンド モジュールには、"b*n*" または "rc*n*" という接尾辞が付いているものがあります。
> これらのコマンド モジュールはまだプレビュー段階であり、今後一般公開される予定です。

CLI のナイトリー プレビュー ビルドもあります。
詳細については、[ナイトリー ビルドの入手](https://github.com/Azure/azure-cli#nightly-builds)に関する手順と、[開発者向けセットアップおよび共同作成コード](https://github.com/Azure/azure-cli#developer-setup)に関する手順を参照してください。

ナイトリー プレビュー ビルドの問題は、次の方法で報告することができます。
- [github の問題一覧](https://github.com/azure/azure-cli/issues/)で問題を報告する。
- 製品チーム ([azfeedback@microsoft.com](mailto:azfeedback@microsoft.com)) に問い合わせる。
- `az feedback` コマンドを使用してコマンド ラインからフィードバックを送る。
