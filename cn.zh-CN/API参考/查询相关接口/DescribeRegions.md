# DescribeRegions {#concept_a2f_ykt_qfb .concept}

查询您可以使用的阿里云地域。更多详情，请参阅 [地域与可用区](https://www.alibabacloud.com/help/doc-detail/40654.htm)。

## 请求参数 {#section_iyv_zlt_qfb .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeRegions|
|RegionId|String|是|实例所属的地域 ID。|

## 返回参数 {#section_kqz_jpt_qfb .section}

返回参数 Region 列表包含字段见下表：

|名称|类型|描述|
|:-|:-|:-|
|RegionId|String|地域 ID|

## 示例 {#section_hqr_lpt_qfb .section}

**请求示例**

```
https://ecs.cn-hangzhou.aliyuncs.com/?
Action=DescribeRegions
&RegionId=cn-hangzhou
&<公共请求参数>
```

**返回示例**

`XML`格式

```
<DescribeRegionsResponse>
    <RequestId>38EC7366-F5A9-46B1-BDB1-0FDC2E296397</RequestId>
    <Regions>
        <Region>
            <RegionId>cn-shanghai</RegionId>
        </Region>
        <Region>
            <RegionId>cn-qingdao</RegionId>
        </Region>
    </Regions>
</DescribeRegionsResponse>
```

`JSON`格式

```
{
    "RequestId":"38EC7366-F5A9-46B1-BDB1-0FDC2E296397",
    "Regions":{
        "Region":[
            {
                "RegionId":"cn-shanghai",
            },
            {
                "RegionId":"cn-qingdao",
            }
        ]
    }
}
```

## 错误码 {#section_pnk_tpt_qfb .section}

无。

