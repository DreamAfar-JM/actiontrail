# DeleteTrail {#concept_28847_zh .concept}

删除跟踪。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：`DeleteTrail`。|
|RegionId|String|是|实例所属的地域 ID。查看最新的阿里云地域列表，请参考：[DescribeRegions](intl.zh-CN/API参考/查询相关接口/DescribeRegions.md#)。|
|Name|String|是|要删除的跟踪的名称。|

## 返回参数 { .section}

无。

## 需要的权限 { .section}

**Action**

`actiontrail:DeleteTrail`

**Resource**

`acs:actiontrail:${region}:${AccountId}:*`

## 错误码 { .section}

|错误代码|描述|HTTP 状态码|
|:---|:-|:-------|
|InvalidTrailNameException|非法的跟踪名称。|400|
|TrailNotFoundException|指定的跟踪不存在。|404|

## 示例 { .section}

**请求示例**

```
http://actiontrail.cn-hangzhou.aliyuncs.com/?
Action=DeleteTrail
&RegionId=cn-hangzhou
&Name=my-test
&<公共请求参数>

```

