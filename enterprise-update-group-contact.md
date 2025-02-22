---

copyright:
  years: 2021
lastupdated: "2021-03-04"

keywords: enterprise, organize accounts, account group, change contact, account group contact 

subcollection: account

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:important: .important}
{:tip: .tip}
{:note: .note}
{:ui: .ph data-hd-interface='ui'}
{:cli: .ph data-hd-interface='cli'}
{:api: .ph data-hd-interface='api'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}

# Updating the account group contact
{: #update-account-group-contact}

You can update the contact for any account group within your enterprise. The contact is different from an account owner in that they don't have any additional access within the account group or its accounts. The user that you select as a contact acts as a focal point for any account group issues. For example, if a financial officer notices that the account group's usage costs are unexpectedly high, they might notify the account group contact.
{: shortdesc}

To update an account group contact, you need the Administrator or Editor role on the Enterprise service in the enterprise account. For more information, see [Assigning enterprise access](/docs/account?topic=account-assign-access-enterprise).

## Updating the account group contact in the console
{: #update-account-group-contact-ui}
{: ui}

To update the contact for an account group, complete the following steps. If a user that you want to assign as the contact isn't in the enterprise, first invite the user to the enterprise account. See [Inviting users](/docs/account?topic=account-iamuserinv) for more information.

1. Click **Manage** > **Enterprise** > **Accounts**.
1. In the **Account groups** section, click the Actions icon ![Actions icon](../icons/actions-icon-vertical.svg) in the row for the account group, and select **Edit**.
1. Select the new contact for the account group, and click **Save**. 

## Updating the account group contact using the CLI
{: #update-account-group-contact-cli}
{: cli}

This action can be done only through the UI, API, or SDKs. To see the steps, switch to the UI or API instructions. 


## Updating the account group contact using the API
{: #update-account-group-contact-api}
{: api}

To update the primary contact for the account group, call the [Enterprise Management API](https://{DomainName}/apidocs/enterprise-apis/enterprise#import-an-account-into-an-enterprise){: external} as shown in the following sample request. Replace the IAM token and ID variables with the values from your enterprise.

1. If a user that you want to assign as the contact isn't in the enterprise, first invite the user to the enterprise account. See [Inviting users](/docs/account?topic=account-iamuserinv) for more information.

1. To find the IAM ID for the new contact, see [List accounts](https://cloud.ibm.com/apidocs/enterprise-apis/enterprise#list-accounts) in the Enterprise Management API. 

```
  curl -X PATCH \
  "https://enterprise.cloud.ibm.com/v1/account-groups/$ACCOUNT_GROUP_ID" \
  -H "Authorization: Bearer <IAM_Token>" \
  -H 'Content-Type: application/json' \
  -d '{
    "primary_contact_iam_id": "iam_id"
  }'
  ```
{: codeblock}
{: curl}

```
UpdateAccountGroupOptions options = new UpdateAccountGroupOptions.Builder()
        .accountGroupId("ent-id-123")
        .name("IBM")
        .build();
Response<Void> response = service.updateAccountGroup(options).execute();
```
{: codeblock}
{: java}

```
const params = {
        accountGroupId: 'account-group-id-12',
        name: 'IBM'
};
service.updateAccountGroup(params).then(response => {
        console.log(response)
}).catch(err => {});
```
{: codeblock}
{: javascript}

```
response = service.update_account_group ( 
        account_group_id = 'account-group-id-12',
        name = 'IBM'
)
```
{: codeblock}
{: python}

```
updateAccountGroupOptionsModel := service.NewUpdateAccountGroupOptions()
updateAccountGroupOptionsModel.SetAccountGroupID("account-group-id-123")
updateAccountGroupOptionsModel.SetName("IBM")
result, detailedResponse, err := service.UpdateAccountGroup(updateAccountGroupOptionsModel)
```
{: codeblock}
{: go}
