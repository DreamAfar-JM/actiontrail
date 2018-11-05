# GetTrailStatus {#concept_28843_zh .concept}

查询跟踪的工作状态。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：`GetTrailStatus`。|
|RegionId|String|是|实例所属的地域 ID。查看最新的阿里云地域列表，请参考：[DescribeRegions](intl.zh-CN/API参考/查询相关接口/DescribeRegions.md#)。|
|Name|String|是|跟踪名称，同一账户内名称不可重复。|

## 返回参数 { .section}

公共返回参数，详见[公共参数](intl.zh-CN/API参考/调用方式/公共参数.md#)。

|名称|类型|描述|
|:-|:-|:-|
|IsLogging|Boolean|服务是否打开。|
|LatestDeliveryError|String|最后一次行为追踪异常的日志信息。|
|LatestDeliveryTime|String|最后一次成功记录行为的时间。|
|StartLoggingTime|String|用户上一次开启该跟踪的时间。|
|StopLoggingTime|String|用户上一次停止该跟踪的时间。|

## 需要的权限 { .section}

**Action**

`actiontrail:GetTrailStatus`

**Resource**

`acs:actiontrail:${region}:${AccountId}:*`

## 错误码 { .section}

|错误代码|描述|HTTP 状态码|
|:---|:-|:-------|
|InvalidTrailNameException|指定的跟踪名称不存在。|400|
|TrailNotFoundException|找不到指定的跟踪。|404|

## 示例 { .section}

**请求示例**

```
http://actiontrail.cn-hangzhou.aliyuncs.com/?
Action=GetTrailStatus
&RegionId=cn-hangzhou
&Name=trail-test
&<公共请求参数>

```

**返回示例**

`JSON`示例

```language-json
{
  "IsLogging": true,
  "StartLoggingTime": "Wed Dec 02 15:41:06 CST 2015"
}

```

