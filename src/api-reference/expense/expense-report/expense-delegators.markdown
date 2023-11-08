---
title: Expense Delegators
layout: reference
---

# Expense Delegators

Users that have granted delegate permissions to the another Expense user.

Retrieves the list of users that have granted delegate permissions to the user specified in the OAuth access token.

### Version
1.1

## Limitations

Access to this documentation does not provide access to the API. 

### URI
`https://www.concursolutions.com/api/expense/expensereport/v1.1/delegators`

### Operations
[GET](#get)  

## Request <a name="request"></a>

#### Request Parameters
|Name|Type|Format|Description|
|---|---|---|---|
|`includeInactive`|`string`|`query`|Allows to include inactive delegators in the response for the delegate. Accepted values: `Y|N`. Default: `N`|

Example: `https://{datacenterURI}/api/expense/expensereport/v1.1/delegators?includeInactive=Y`

### Headers

#### Authorization Header
Authorization header with OAuth token for valid SAP Concur user. Required.

### Accept Header
application/xml

## Response <a name="response"></a>

#### Content Types
application/xml

#### <a name="schema"></a>Schema

This request will return a **DelegatorsList** parent element with a **Delegator** parent element for each user that has granted delegate rights to the OAuth consumer.
By default only active delegators are returned. Use `includeInactive` query parameter to include incative delegators.

#### Delegator Elements

|  Element |  Description |
| -------- | ------------ |
|  CanApprove |  Whether the delegate is granted the right to approve expense reports on behalf of the delegator. |
|  CanPrepare |  Whether the delegate is granted the right to create expense reports on behalf of the delegator. |
|  CanSubmit |  Whether the delegate is granted the right to submit expense reports on behalf of the delegator. |
|  CanTemporaryApprove |  Whether the delegate is granted the same temporary approval rights as the delegator. |
|  CanViewReceipts |  Whether the delegate is granted the right to view receipts on behalf of the delegator. |
|  ReceiveApprovalEmails |  Whether the delegate also receives the approval emails sent to the delegator. |
|  ReceivesEmails |  Whether the delegate also receives the SAP Concur emails sent to the delegator. |
|  DelegatorXUserID |  The user ID of the delegator. |

## Examples <a name="examples"></a>

#### XML Example Request

```http
GET https://www.concursolutions.com/api/expense/expensereport/v1.1/Delegators HTTP/1.1
Authorization: OAuth {access token}
...
```

#### XML Example of Successful Response

```http
HTTP/1.1 200 OK
Content-Type: application/xml

<DelegatorsList xmlns="http://www.concursolutions.com/api/expense/expensereport/2011/03" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
    <Delegator>
        <CanApprove>N</CanApprove>
        <CanPrepare>Y</CanPrepare>
        <CanSubmit>Y</CanSubmit>
        <CanTemporaryApprove>N</CanTemporaryApprove>
        <CanViewReceipts>Y</CanViewReceipts>
        <ReceiveApprovalEmails>N</ReceiveApprovalEmails>
        <ReceivesEmails>N</ReceivesEmails>
        <DelegatorXUserID>terryb@example.com</DelegatorXUserID>
    </Delegator>
    <Delegator>
        <CanApprove>N</CanApprove>
        <CanPrepare>Y</CanPrepare>
        <CanSubmit>Y</CanSubmit>
        <CanTemporaryApprove>N</CanTemporaryApprove>
        <CanViewReceipts>N</CanViewReceipts>
        <ReceiveApprovalEmails>N</ReceiveApprovalEmails>
        <ReceivesEmails>N</ReceivesEmails>
        <DelegatorXUserID>patd@example.com</DelegatorXUserID>
    </Delegator>
</DelegatorsList>
```
