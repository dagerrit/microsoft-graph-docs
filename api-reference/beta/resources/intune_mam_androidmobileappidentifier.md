﻿# androidMobileAppIdentifier resource type

> **Important:** APIs under the /beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

> **Note:** Using the Microsoft Graph APIs to configure Intune controls and policies still requires that the Intune service is [correctly licensed](https://go.microsoft.com/fwlink/?linkid=839381) by the customer.

The identifier for an Android app.

Inherits from [mobileAppIdentifier](../resources/intune_mam_mobileappidentifier.md)

## Properties
|Property|Type|Description|
|---|---|---|
|packageId|String|The identifier for an app, as specified in the play store.|

## Relationships
None
## JSON Representation
Here is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.androidMobileAppIdentifier"
}
-->
```json
{
  "@odata.type": "#microsoft.graph.androidMobileAppIdentifier",
  "packageId": "String"
}
```



