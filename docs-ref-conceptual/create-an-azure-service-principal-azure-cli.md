---
title: "Azure CLI 2.0 で Azure サービス プリンシパルを使用する"
description: "Azure CLI 2.0 でサービス プリンシパルを作成および使用する方法について説明します。"
author: sptramer
ms.author: sttramer
manager: carmonm
ms.date: 02/12/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: azurecli
ms.service: multiple
ms.openlocfilehash: b46c735a14240bddd07659475ada1c33c75a1e67
ms.sourcegitcommit: b93a19222e116d5880bbe64c03507c64e190331e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="create-an-azure-service-principal-with-azure-cli-20"></a>Azure CLI 2.0 で Azure サービス プリンシパルを作成する

アクセス制限を使用して個別のログインを作成するには、サービス プリンシパルを使用します。 サービス プリンシパルは、アカウントに関連付けることができる個別の ID です。 サービス プリンシパルは、自動化する必要があるアプリケーションとタスクを操作するうえで役に立ちます。 この記事では、サービス プリンシパルを作成する手順について説明します。

## <a name="create-the-service-principal"></a>サービス プリンシパルを作成する

サービス プリンシパルを作成するには、[az ad sp create-for-rbac](/cli/azure/ad/sp#create-for-rbac) コマンドを使用します。 サービス プリンシパル名は、既存のアプリケーションまたはユーザー名には関連付けられていません。 任意の認証の種類を使用して、サービス プリンシパルを作成できます。

* パスワード ベースの認証には `--password` が使用されます。 [Azure Active Directory のパスワードの規則と制約事項](/azure/active-directory/active-directory-passwords-policy)に従って、必ず強力なパスワードを作成してください。 自分でパスワードを指定しなかった場合、任意のパスワードが自動的に生成されます。

  ```azurecli
  az ad sp create-for-rbac --name ServicePrincipalName --password PASSWORD
  ```

* 既存の証明書に対する証明書ベースの認証には、`--cert` が、PEM または DER パブリック文字列、あるいは `@{file}` として使用され、ファイルが読み込まれます。

  ```azurecli
  az ad sp create-for-rbac --name ServicePrincipalName --cert {CertStringOrFile} 
  ```

  `--keyvault` 引数を追加すると、証明書が Azure Key Vault に格納されていることを指定できます。 ここでは、`--cert` 値は Key Vault 内の証明書の名前を表します。

* `--create-cert` は、認証用の "_自己署名_" 証明書を作成します。 `--keyvault` 引数を追加すると、証明書を Azure Key Vault に格納できます。

  ```azurecli
  az ad sp create-for-rbac --name ServicePrincipalName --create-cert
  ```

認証の種類を示す引数が含まれていない場合は、`--password` が既定で使用されます。

`create-for-rbac` コマンドの出力の形式は次のとおりです。

```json
{
  "appId": "APP_ID",
  "displayName": "ServicePrincipalName",
  "name": "http://ServicePrincipalName",
  "password": ...,
  "tenant": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
}
```

認証の値として、`appId`、`tenant`、および `password` が使用されています。 `displayName` は、既存のサービス プリンシパルを検索するときに使用されます。

> [!NOTE]
> ご利用のアカウントにサービス プリンシパルを作成するための十分なアクセス許可がない場合は、"この操作を完了するのに十分な特権がありません" というエラー メッセージが表示されます。 サービス プリンシパルを作成するには、Azure Active Directory 管理者にお問い合わせください。

## <a name="manage-service-principal-roles"></a>サービス プリンシパル ロールを管理する 

Azure CLI 2.0 には、ロールの割り当てを管理するために、次のコマンドが用意されています。

* [az role assignment list](/cli/azure/role/assignment#list)
* [az role assignment create](/cli/azure/role/assignment#create)
* [az role assignment delete](/cli/azure/role/assignment#delete)

サービス プリンシパルの既定のロールは**共同作成者**です。 このロールは、Azure アカウントの読み取りと書き込みを行うための完全なアクセス許可が付与され、通常、アプリケーションには適していません。 **閲覧者**ロールは制限が厳しく、読み取り専用アクセスを提供します。  ロールベースのアクセス制御 (RBAC) とロールの詳細については、[RBAC: 組み込みロール](/azure/active-directory/role-based-access-built-in-roles)に関するページをご覧ください。

この例では、**閲覧者**ロールを追加し、**共同作成者**ロールを削除します。

```azurecli
az role assignment create --assignee APP_ID --role Reader
az role assignment delete --assignee APP_ID --role Contributor
```

ロールを追加しても、以前に割り当てられたアクセス許可は変更され "_ません_"。 サービス プリンシパルのアクセス許可を制限するときは、__共同作成者__ロールを必ず削除する必要があります。

変更を確認するには、割り当てられているロールの一覧を表示します。

```azurecli
az role assignment list --assignee APP_ID
```

> [!NOTE] 
> ロールを割り当てるためのアクセス許可がアカウントにない場合は、アカウントに "'Microsoft.Authorization/roleAssignments/write' over scope '/subscriptions/{guid}' のアクションを実行するためのアクセス権限がありません" というエラー メッセージが表示されます。ロールを管理するには、Azure Active Directory 管理者にお問い合わせください。

## <a name="log-in-using-the-service-principal"></a>サービス プリンシパルを使ってログインする

新しいサービス プリンシパルのログインとアクセス許可をテストするには、Azure CLI 内でそのサービス プリンシパルとしてログインします。 新しいサービス プリンシパルには、`appId`、`tenant`、および資格情報の値を使用してログインします。 指定する認証情報は、サービス プリンシパルの作成にパスワードまたは証明書のどちらを使用したかに基づいて異なります。

パスワードでログインをするには、そのパスワードを引数パラメーターとして指定します。

```azurecli
az login --service-principal --username APP_ID --password PASSWORD --tenant TENANT_ID
```

証明書でログインする場合、その証明書は、PEM または DER ファイルとしてローカルで使用できる必要があります。

```azurecli
az login --service-principal --username APP_ID --tenant TENANT_ID --password PATH_TO_CERT
```
## <a name="reset-credentials"></a>資格情報をリセットする

サービス プリンシパルの資格情報を忘れた場合、その情報は、[az ad sp reset-credentials](https://docs.microsoft.com/en-us/cli/azure/ad/sp?view=azure-cli-latest#az_ad_sp_reset_credentials) コマンドでリセットできます。 新しいサービス プリンシパルを作成するときの制限事項とオプションと同じものが、ここでも適用されます。

```azurecli
az ad sp reset-credentials --name APP_ID --password NEW_PASSWORD
```