# Get YammerDeviceUsage report

> **Important:** APIs under the /beta version in Microsoft Graph are in preview and are subject to change. Use of these APIs in production applications is not supported.

Retrieve the reports of Yammer Client Activity. The response will be a CSV file in a binary stream.

> Note: You can go to [Office 365 Reports - Yammer device usage](https://support.office.com/client/Yammer-device-usage-b793ffdd-effa-43d0-849a-b1ca2e899f38) to check the meaning of different views.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](../../../concepts/permissions_reference.md).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Not supported.    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Reports.Read.All |

## HTTP request

<!-- { "blockType": "ignored" } -->

```http
GET /reports/YammerDeviceUsage(view=view-value, period=period-value, date=date-value)/content
```

## Request headers

| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {token}. Required. |

## Request body

In the request URL, provide following query parameters with values.

| Parameter   | Type|Description|
|:---------------|:--------|:----------|
|view|ViewType|View is an enumeration type, used to determine which type of information that current report should return. Can not be null.|
|period|PeriodType|Period is an enumeration type, used to specify the aggregate type.|
|date|String|Specifies the day to a view of the users that performed an activity on that day. Must have a format of YYYY-MM-DD. Only available for the last 30 days and is ignored unless view type is **Detail**|

> Note: When view type is **Detail**, the period parameter will be ignored. For other view types, date parameter will be ignored.
> If you call with **Detail** view along with **PeriodType**, the return data is a list of all users that are licensed for the product with their respective last activity date.

The following **ViewType** are available in this report:

- Detail
- Distribution
- Users

The following **PeriodType** are available in this report:

- D7
- D30
- D90
- D180

## Response

If successful, this method returns `302 Found` response redirecting to a pre-authenticated download URL for the report.

To download the contents of the file your application will need to follow the `Location` header in the response.
Many HTTP client libraries will automatically follow the 302 redirection and start downloading the file immedately.

Pre-authenticated download URLs are only valid for a short period of time (a few minutes) and do not require an `Authorization` header to download.

## Example

Here is an example of how to call this API.

##### Request

Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "reportroot_yammerdeviceusage"
}-->

```http
GET https://graph.microsoft.com/beta/reports/YammerDeviceUsage(view='Detail',period='D7')/content
```

##### Response

Here is an example of the response.
<!-- {
  "blockType": "response",
  "@odata.type": "stream"
} -->

```http
HTTP/1.1 302 Found
Content-Type: text/plain
Location: https://reports.office.com/data/download/odffer_eYRg4sXTiKqggV6eXU0t__XDezYGO-NQw
```

Follow the 302 redirection and the downloading CSV file will have the schema as follows.

<!-- { "blockType": "ignored" } -->

```http
HTTP/1.1 200 OK
Data as of,User name,Display name,User state,State change date (UTC),Last activity date (UTC),Web,Windows Phone,Android Phone,iPhone,iPad,Other,Reporting period in days
```

### Other valid requests

<!-- { "blockType": "ignored" } -->

```http
GET https://graph.microsoft.com/beta/reports/YammerDeviceUsage(view='Detail',date='2017-02-02')/content
GET https://graph.microsoft.com/beta/reports/YammerDeviceUsage(view='Distribution',period='D7')/content
GET https://graph.microsoft.com/beta/reports/YammerDeviceUsage(view='Users',period='D7')/content
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "ReportRoot: YammerDeviceUsage",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->