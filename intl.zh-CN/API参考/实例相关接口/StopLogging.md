# StopLogging {#concept_28845_zh .concept}

禁用跟踪。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：`StopLogging`。|
|RegionId|String|是|实例所属的地域 ID。查看最新的阿里云地域列表，请参考：[DescribeRegions](intl.zh-CN/API参考/查询相关接口/DescribeRegions.md#)。|
|Name|String|是|要禁用的跟踪名。|

## 返回参数 { .section}

无。

## 错误码 { .section}

|错误代码|描述|HTTP 状态码|
|:---|:-|:-------|
|InvalidBucketNameException|非法的 bucket 名称。|400|
|TrailNotFoundException|要禁用的跟踪不存在。|404|

## 需要的权限 { .section}

**Action**

`actiontrail:StopLogging`

**Resource**

`acs:actiontrail:${region}:${AccountId}:*`

## 示例 { .section}

**请求示例**

```
http://actiontrail.cn-hangzhou.aliyuncs.com/?
Action=StopLogging
&RegionId=cn-hangzhou
&Name=trail-test
&<公共请求参数>

```

