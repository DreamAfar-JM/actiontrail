# UpdateTrail {#concept_28846_zh .concept}

更新跟踪可以写入日志服务logstore或者 OSS bucket，该操作必须调用跟踪的 Home Region 的 API 服务器。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：`UpdateTrail`。|
|RegionId|String|是|实例所属的地域 ID。查看最新的阿里云地域列表，请参考：[DescribeRegions](intl.zh-CN/API参考/查询相关接口/DescribeRegions.md#)。|
|Name|String|是|要更新的跟踪的名字。|
|OssBucketName|String|否|写入的 OSS bucket 名称。该 bucket 必须已经存在。|
|RoleName|String|否|用户允许 ActionTrail 服务扮演的 RAM 角色名称。|
|OssKeyPrefix|String|否|写入的 OSS bucket 文件名的前缀，可为空。|
|SlsProjectArn|String|否|日志服务项目的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|
|SlsWriteRoleArn|String|否|日志服务角色的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|

## 返回参数 { .section}

公共返回参数，详见[公共参数](intl.zh-CN/API参考/调用方式/公共参数.md#)。

|名称|类型|描述|
|:-|:-|:-|
|Name|String|跟踪名称。|
|HomeRegion|String|跟踪的 home region。|
|OssBucketName|String|OSS bucket 名称。|
|OssKeyPrefix|String|OSS bucket 文件名的前缀。|
|RoleName|String|角色名称。|
|SlsProjectArn|String|日志服务项目的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|
|SlsWriteRoleArn|String|日志服务角色的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|

## 需要的权限 { .section}

**Action**

`actiontrail:UpdateTrail`

**Resource**

`acs:actiontrail:${region}:${AccountId}:*`

## 错误码 { .section}

|错误代码|描述|HTTP 状态码|
|:---|:-|:-------|
|InvalidBucketNameException|非法的 bucket 名称。|400|
|InvalidPrefixException|非法的前缀。|400|
|InvalidTrailNameException|非法的跟踪名称。|400|
|InsufficientBucketPolicyException|没有权限访问指定的 OSS bucket。|403|
|BucketDoesNotExistException|指定的 bucket 不存在。|404|
|TrailNotFoundException|指定的跟踪不存在。|404|

## 示例 { .section}

**请求示例**

```
http://actiontrail.cn-hangzhou.aliyuncs.com/?
Action=UpdateTrail
&RegionId=cn-hangzhou
&Name=trail-test
&OssBucketName=yuanchuang
&RoleName=aliyunactiontraildefaultrole
&OssKeyPrefix=
&<公共请求参数>

```

**返回示例**

`JSON`示例

```language-json
{
  "Name": "trail-test",
  "OssBucketName": "yuanchuang",
  "OssKeyPrefix": "",
  "RoleName": "aliyunactiontraildefaultrole",
  "SlsProjectArn":"acs:log:cn-shanghai::project/***",
  "SlsWriteRoleArn":"acs:ram::***:role/aliyunactiontraildefaultrole"
}

```

