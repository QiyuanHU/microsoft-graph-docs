# Update privilegedRoleSettings

> **Important:** APIs under the /beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

Update the role settings for the given role setting. A [privilegedRoleSettings](../resources/privilegedrolesettings.md) object will be returned.
## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](../../../concepts/permissions_reference.md).

The requester must have one of the following roles: Privileged Role Administrator, Global Administrator, Security Administrator, or Security Reader. 

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | PrivilegedAccess.ReadWrite.AzureAD, Directory.AccessAsUser.All    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Not supported. |

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
PUT /privilegedRoles/{id}/settings
```

## Request headers
| Name      |Description|
|:----------|:----------|
| Authorization  | Bearer {token}. Required. |

## Request body
In the request body, supply a JSON representation of a [privilegedRoleSettings](../resources/privilegedrolesettings.md) object.

The following table shows the properties that can be supplied when you update a role setting.

|Property|Type|Required|Description|
|:---------------|:--------|:--------|:----------|
|elevationDuration|duration|Yes|The duration when the role is activated.|
|id|string|Yes| The unique identifier for the role settings. Read-only.|
|isMfaOnElevationConfigurable|boolean|Yes|**true** if mfaOnElevation is configurable. **false** if mfaOnElevation is not configurable.|
|lastGlobalAdmin|boolean|No|Internal used only.|
|maxElavationDuration|duration|Yes|Maximal duration for the activated role.|
|mfaOnElevation|boolean|Yes|**true** if MFA is required to activate the role. **false** if MFA is not required to activate the role.|
|minElevationDuration|duration|Yes|Minimal duration for the activated role.|
|notificationToUserOnElevation|boolean|Yes|**true** if send notification to the end user when the role is activated. **false** if do not send notification when the role is activated.|
|ticketingInfoOnElevation|boolean|Yes|**true** if the ticketing information is required when activate the role. **false** if the ticketing information is not required when activate the role.|
|approvalOnElevation|boolean|Yes|**true** if the approval is required when activate the role. **false** if the approval is not required when activate the role.|
|approverIds|array|No|List of Approval ids, if approval is required for activation.|

## Response

If successful, this method returns a `204 No Content` response code.

Note that the tenant needs to be registered to PIM. Otherwise, the HTTP 403 Forbidden status code will be returned.
## Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "put_privilegedrolesettings"
}-->
```http
PUT https://graph.microsoft.com/beta/privilegedRoles/{id}/settings
Content-type: application/json

{
    "id": "9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
    "elevationDuration": "PT8H",
    "notificationToUserOnElevation": false,
    "ticketingInfoOnElevation": true,
    "mfaOnElevation": false,
    "maxElavationDuration": "PT0S",
    "minElevationDuration": "PT0S",
    "lastGlobalAdmin": false,
    "isMfaOnElevationConfigurable": true,
    "approvalOnElevation": false,
    "approverIds": ["e2b2a2fb-13d7-495c-adc9-941fe966793f", "22770e3f-b9b4-418e-9dea-d0e3d2f275dd"]
}
```
##### Response
Here is an example of the response.

```http
HTTP/1.1 204 No Content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update privilegedRoleSettings",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->