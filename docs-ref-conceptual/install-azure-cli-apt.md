---
title: "apt を使用して Linux に Azure CLI 2.0 をインストールする"
description: "apt パッケージ マネージャーで Azure CLI 2.0 をインストールする方法"
author: sptramer
ms.author: sttramer
manager: routlaw
ms.date: 02/06/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ms.openlocfilehash: 840e5e7d6531fe92d30235f621e381589266d1d3
ms.sourcegitcommit: f82774a6f92598c41da9956284f563757f402774
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="install-azure-cli-20-with-apt"></a>apt での Azure CLI 2.0 のインストール

Ubuntu や Debian など、`apt` が付属するディストリビューションを実行している場合は、Azure CLI 用の利用可能な 64 ビット パッケージがあります。 このパッケージは、以下でテストされています。

* Ubuntu trusty、xenial、および artful
* Debian wheezy、jessie、および stretch

## <a name="install"></a>Install

1. ソース リストを変更します。

     ```bash
     AZ_REPO=$(lsb_release -cs)
     echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | \
          sudo tee /etc/apt/sources.list.d/azure-cli.list
     ```

2. 次の sudo コマンドを実行します。

   ```bash
   sudo apt-key adv --keyserver packages.microsoft.com --recv-keys 52E16F86FEE04B979B07E28DB02C46DF417A0893
   sudo apt-get install apt-transport-https
   sudo apt-get update && sudo apt-get install azure-cli
   ```

Azure CLI は `az` コマンドで実行できます。

## <a name="troubleshooting"></a>トラブルシューティング

ここでは、`apt` でのインストール時に発生する一般的な問題をいくつか示します。 問題がここに示されていない場合は、[GitHub で問題を報告](https://github.com/Azure/azure-cli/issues)してください。

### <a name="apt-key-fails-with-no-dirmngr"></a>"No dirmngr" で apt-key が失敗する

`apt-key` コマンドの実行時に、次のようなエラーが出力されることがあります。

```output
gpg: failed to start the dirmngr '/usr/bin/dirmngr': No such file or directory
gpg: connecting dirmngr at '/tmp/apt-key-gpghome.kt5zo27tp1/S.dirmngr' failed: No such file or directory
gpg: keyserver receive failed: No dirmngr
```

このエラーは、`apt-key` に必要なコンポーネントがないためです。 これを解決するには、`dirmngr` パッケージをインストールします。

```bash
sudo apt-get install dirmngr
```

## <a name="update"></a>プライマリの

CLI パッケージを更新するには、`apt-get upgrade` を使用します。

   ```bash
   sudo apt-get update && sudo apt-get upgrade
   ```

> [!NOTE]
> このコマンドにより、システムにインストールされている、依存関係が変更されていないすべてのパッケージがアップグレードされます。
> CLI だけをアップグレードするには、`apt-get install` を使用します。
> ```bash
> sudo apt-get update && sudo apt-get install --only-upgrade -y azure-cli
> ```

## <a name="uninstall"></a>アンインストール

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

1. `apt-get remove` を使用してアンインストールします。

    ```bash
    sudo apt-get remove -y azure-cli
    ```

2. CLI を再インストールする予定がない場合は、Azure CLI リポジトリ情報を削除します。

   ```bash
   sudo rm /etc/apt/sources.list.d/azure-cli.list
   ```

3. 不要なパッケージを削除します。

   ```bash
   sudo apt autoremove
   ```