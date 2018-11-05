# DescribeTrails {#concept_28842_zh .concept}

查询当前区域跟踪的设置信息。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：`DescribeTrails` 。|
|RegionId|String|是|实例所属的地域 ID。查看最新的阿里云地域列表，请参考：[DescribeRegions](intl.zh-CN/API参考/查询相关接口/DescribeRegions.md#)。|
|NameList|String|否|需要查询的跟踪名称列表，以逗号分隔。|
|IncludeShadowTrails|String|否|是否显示影子跟踪。取值为`true`或`false`，默认为否。|

## 返回参数 { .section}

返回参数`TrailList`中包含的字段见下表。

|名称|类型|描述|
|:-|:-|:-|
|Name|String|跟踪名称。|
|OssBucketName|String|OSS bucket 名称。|
|OssBucketLocation|String|OSS bucket 所在的区域。|
|OssKeyPrefix|String|OSS bucket 名称前缀。|
|RoleName|String|ActionTrail 的角色名称。|
|SlsProjectArn|String|日志服务项目的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|
|SlsWriteRoleArn|String|日志服务角色的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|

## 需要的权限 { .section}

**Action**

`actiontrail:DescribeTrails`

**Resource**

`acs:actiontrail:${region}:${AccountId}:*`

## 错误码 { .section}

无。

## 示例 { .section}

**请求示例**

```
http://actiontrail.cn-hangzhou.aliyuncs.com/?
Action=DescribeTrails
&RegionId=cn-hangzhou
&NameList=abc%2cdef
&<公共请求参数>

```

**返回示例**

`JSON`示例

```language-json
{
  "TrailList": [
    {
      "Name": "default",
      "OssBucketName": "secloud",
	  "OssBucketLocation": "cn-hangzhou",
      "OssKeyPrefix": "trail1",
      "RoleName": "aliyunactiontraildefaultrole",
      "SlsProjectArn":"acs:log:cn-shanghai::project/***",
      "SlsWriteRoleArn":"acs:ram::***:role/aliyunactiontraildefaultrole"
    }
  ]
}

```

