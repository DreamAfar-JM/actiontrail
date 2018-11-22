# 操作事件\(Event\)结构定义 {#concept_28819_zh .concept}

## 一个事件记录内容包含的关键字段 {#section_gxs_gbd_lfb .section}

## apiVersion { .section}

-   类型：String
-   必须：是
-   描述：所调用的云服务 API 版本。

## eventId { .section}

-   类型：String
-   必须：是
-   描述：事件 ID，由 ActionTrail 服务为每个操作事件所产生的一个 GUID。

## eventName { .section}

-   类型：String
-   必须：是
-   描述：API 操作名称，可参考各服务的 API 操作列表，比如`Ecs`的`StopInstance`。

## eventSource { .section}

-   类型：String
-   必须：是
-   描述：处理 API 请求的服务端，比如 ram.aliyuncs.com 。

## eventTime { .section}

-   类型：String
-   必须：是
-   描述：API 请求的发生时间（UTC格式）。

## eventType { .section}

-   类型：String
-   必须：是
-   描述：发生的事件类型，如`ApiCall`（控制台或API操作）， `ConsoleSignin`（用户登录）。

## eventVersion { .section}

-   类型：String
-   必须：是
-   描述：ActionTrail 事件格式的版本，当前版本为"1"。

## errorCode { .section}

-   类型：String
-   必须：否
-   描述：如果云服务处理 API 请求时发生了错误，这里记录了相应的错误码，比如 `NoPermission`。·

## errorMessage { .section}

-   类型：String
-   必须：否
-   描述：如果云服务处理API请求时发生了错误，这里记录了相应的错误消息，比如 “You are not authorized.”

## requestId { .section}

-   类型：String
-   必须：是
-   描述：云服务处理 API 请求时所产生的消息请求 ID。

## requestParameters { .section}

-   类型：字典
-   必须：否
-   描述：API 请求的输入参数，具体参数含义需参考相应云服务的 API 文档。

## responseElements {#section_y2s_yrz_qfb .section}

-   类型：字典
-   必须：否
-   描述： API 响应的数据，具体格式需参考相应云服务的 API 文档。

## referencedResources {#section_bkd_dn1_wfb .section}

-   类型：字典
-   必须：否
-   描述： API 操作的资源。

## serviceName { .section}

-   类型：String
-   必须：是
-   描述：云服务名称，如`Ecs`, `Rds`, `Ram`。

## sourceIpAddress { .section}

-   类型：String
-   必须：是
-   描述：发送 API 请求的源 IP 地址。如果 API 请求是由用户通过控制台操作触发，那么这里记录的是用户浏览器端的 IP 地址，而不是控制台 Web 服务器的IP地址。

## userAgent { .section}

-   类型：String
-   必须：是
-   描述：发送 API 请求的客户端代理标识，比如控制台为`AliyunConsole`，SDK 为`aliyuncli/2.0.6`。

## userIdentity { .section}

-   类型：字典
-   必须：是
-   描述：请求者的身份信息。

## userIdentity包含如下属性字段 { .section}

|名称|是否必需|描述|
|:-|:---|:-|
|type|是|身份类型。当前支持的身份类型包括`root-account`（主账号）、`ram-user`（RAM 用户）、`assumed-role`（RAM 角色）。|
|principalId|是|当前请求者的 ID。如果身份类型是`root-account`，则记录主账号 ID；如果是`ram-user`，则记录 RAM 用户名；如果是`assumed-role`，则记录 RoleID:RoleSessionName。|
|accountId|是|主账号 ID。|
|accessKeyId|否|请求者通过 SDK 访问云服务API 时记录该字段。如果通过控制台访问，则该字段不显示。|
|userName|否|如果请求者类型为`ram-user`，则记录 RAM 用户名；如果请求者类型为`assumed-role`，则记录 roleName:roleSessionName。|
|sessionContext|否|如果调用 API 请求时使用的是临时安全凭证 [配置STS Token](../../../../intl.zh-CN/.NET SDK/使用手册/配置STS Token.md#)，则记录该信息；通过控制台执行操作时也会触发session的创建并记录该信息。Session 内容包括：creationDate（Session创建时间）、mfaAuthenticated（用户登录控制台时是否使用多因素认证）|

## userIdentity示例 { .section}

-   RAM 用户通过 SDK 执行操作：

```language-json
"userIdentity": {
    "type": "ram-user",
    "principalId": "288153348682784898",
    "accountId": "1122334455667788",
    "accessKeyId": "55nCtAwmPLkkt5PB",
    "userName": "Bob"
}

```

-   RAM 用户通过控制台执行操作：

```language-json
"userIdentity": {
    "type": "ram-user",
    "principalId": "288153348682784898",
    "accountId": "1122334455667788",
    "userName": "Bob",
    "sessionContext": {
        "attributes": {
            "mfaAuthenticated": "true",
            "creationDate": "2015-12-31T06:33:14Z"
        }
    }
}

```

-   RAM 角色通过 SDK 执行操作：

```language-json
"userIdentity": {
    "type": "assumed-role",
    "principalId": "288153348682784898:alice",
    "accountId": "1122334455667788",
    "accessKeyId": "STS.F24gnHkUE7dER4rsFFQ4n2wCS",
    "userName": "manager:alice"
}

```

