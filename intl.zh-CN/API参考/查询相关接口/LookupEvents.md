# LookupEvents {#concept_28849_zh .concept}

检索事件。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：`LookupEvents`。|
|RegionId|String|是|实例所属的地域 ID。查看最新的阿里云地域列表，请参考：[DescribeRegions](intl.zh-CN/API参考/查询相关接口/DescribeRegions.md#)。|
|Event|String|否|要检索的事件 ID。|
|Request|String|否|要检索的请求 ID。|
|EventType|String|否|要检索的事件类型，比如`ApiCall`。|
|ServiceName|String|否|要检索的云服务名，比如`Ecs`。|
|EventName|String|否|要检索的事件名，比如`CreateInstance` 。|
|User|String|否|要检索的调用者名，RAM 账号。|
|ResourceType|String|否|要检索的资源类型，比如`Database` 。|
|ResourceName|String|否|要检索的资源名，比如 RDS 的`rdsxxxxxx`。|
|NextToken|String|否|用于请求下一页检索结果。请求参数必须保证和上次请求一致。|
|MaxResults|Integer|否|允许返回的最大结果数目。取值范围在 0 到 50 之间。|
|StartTime|String|否|检索事件的开始时间戳。-   支持最多检索最近 7 天的事件。
-   默认值是 7 天。
-   日期格式按照ISO8601 标准表示，并使用 UTC 时间。格式为`YYYY-MM-DDThh:mm:ssZ`。例如，`2014-05-26T12:00:00Z`（北京时间 2014 年 5 月 27 日 00:00:00）。

|
|EndTime|String|否|检索事件的结束时间戳。- 支持最多检索最近 7 天的事件。-   默认值是 7 天。
-   日期格式按照ISO8601 标准表示，并使用 UTC 时间。格式为`YYYY-MM-DDThh:mm:ssZ`。例如，`2014-05-26T12:00:00Z`（北京时间 2014 年 5 月 27 日 00:00:00）。

|

## 返回参数 { .section}

公共返回参数，详见[公共参数](intl.zh-CN/API参考/调用方式/公共参数.md#)。

|名称|类型|描述|
|:-|:-|:-|
|Events|String|检索到的事件列表。|
|NextToken|String|返回下一页的检索结果。无更多结果则不返回此字段。）|
|StartTime|String|检索到的事件的开始时间。|
|EndTime|String|检索到的事件的结束时间。|

## 需要的权限 { .section}

**Action**

actiontrail:LookupEvents

**Resource**

acs:actiontrail:$\{region\}:$\{AccountId\}:\*

## 错误码 { .section}

|错误代码|描述|HTTP 状态码|
|:---|:-|:-------|
|InvalidTimeRangeException|检索结束时间早于开始时间。|400|
|InvalidParameterValue|参数值错误。|400|

## 示例 { .section}

**请求示例**

```
http://actiontrail.cn-hangzhou.aliyuncs.com/?
Action=LookupEvents
&RegionId=cn-hangzhou
&<公共请求参数>

```

**返回示例**

`JSON`示例

```language-json
{
  "EndTime": "2016-01-12T09:11:06Z",
  "Events": [],
  "StartTime": "2016-01-05T09:11:36Z"
}

```

