# CreateTrail {#concept_28841_zh .concept}

创建跟踪。您可以根据需要选择合适的投递目标，比如日志服务（推荐）或者 OSS bucket。

## 请求参数 { .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名`CreateTrail`。|
|RegionId|String|是|实例所属的地域 ID。查看最新的阿里云地域列表，请参考：[DescribeRegions](intl.zh-CN/API参考/查询相关接口/DescribeRegions.md#)。|
|Name|String|是|创建的跟踪名称。同一个账户内跟踪名称不可重复。|
|OssBucketName|String|是|跟踪写入的 OSS bucket。创建跟踪时必须保证该 bucket 已经存在。|
|RoleName|String|是|用户允许 ActionTrail服务扮演的 RAM 角色名称。|
|OssKeyPrefix|String|否|写入的 OSS bucket文件名的前缀，可为空。|
|SlsProjectArn|String|否|日志服务项目的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|
|SlsWriteRoleArn|String|否|日志服务角色的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|

## 返回参数 { .section}

公共返回参数，详见[公共参数](intl.zh-CN/API参考/调用方式/公共参数.md#)。

|名称|类型|描述|
|:-|:-|:-|
|Name|String|跟踪名称。|
|HomeRegion|String|跟踪的 home region。|
|OssBucketName|String|用户指定的 OSS bucket。|
|OssKeyPrefix|String|用户指定的 OSS 文件名的前缀。|
|RoleName|String|用户指定的角色名称。|
|SlsProjectArn|String|日志服务项目的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|
|SlsProjectArn|String|日志服务角色的阿里云唯一标识符（ Aliyun Resource Name, ARN）。详情请参考：[相关术语](../../../../intl.zh-CN/产品简介/相关术语.md#)。|

## 需要的权限 { .section}

**Action**

`actiontrail:CreateTrail`

**Resource**

`acs:actiontrail:${region}:${AccountId}:*`

## 错误码 { .section}

|错误代码|描述|HTTP 状态码|
|:---|:-|:-------|
|InvalidBucketNameException|非法的 bucket 名称。|400|
|InvalidPrefixException|非法的前缀。|400|
|InvalidTrailNameException|非法的跟踪名称。|400|
|TrailAlreadyExistsException|该区域已存在指定的跟踪名称。|400|
|InsufficientBucketPolicyException|没有权限访问指定的 OSS bucket。|403|
|MaximumNumberOfTrailsExceededException|超过了在该区域允许创建跟踪的数量。|403|
|BucketDoesNotExistException|bucket 不存在。|404|

## 示例 { .section}

**请求示例**

```
http://actiontrail.cn-hangzhou.aliyuncs.com/?
Action=CreateTrail
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

