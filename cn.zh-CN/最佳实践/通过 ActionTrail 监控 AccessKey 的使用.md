# 通过 ActionTrail 监控 AccessKey 的使用 {#concept_zm4_fk2_lfb .concept}

本文将介绍如何通过 ActionTrail 监控 AccessKey 的使用。通过历史事件可以查看近 30 天内 AccessKey 的使用情况。通过配置跟踪，将审计事件投递到日志服务，可以做到对 AccessKey 的监控报警。

## 查询历史事件 {#section_t3x_gk2_lfb .section}

开通 ActionTrail 服务之后，即可查询最近 30 天的审计事件。

1.  登录 [ActionTrail控制台](https://actiontrail.console.aliyun.com)。
2.  在左侧导航栏，单击**历史事件查询**。
3.  在**过滤器**下拉菜单选择 **AccessKeyId**。
4.  输入您的 **AccessKeyId**来检索事件。

    **说明：** 在页面顶端切换区域，可以查询各个区域下 **AccessKeyId**使用的审计事件。


## 使用跟踪 {#section_y3x_gk2_lfb .section}

通过将审计事件投递到日志服务，ActionTrail 还可以实现对 AccessKey 的监控和报警。

1.  在左侧导航栏，选择**跟踪列表**。
2.  单击**创建跟踪**。
3.  选择投递目标为**将审计事件投递到日志服务**。设置**日志服务 Project 区域**与**日志服务 Project 名称**。

    **说明：** 此处设置的 Project 用于存储 ActionTrail 日志。您可以填写已选择的地域下的 Project 名称，也可以输入一个新的 Project 名称。

4.  打开**是否开启日志记录**开关。
5.  单击**提交**，结束配置。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154026127913881_zh-CN.png)


成功新建跟踪任务后，ActionTrail 会将所有地域的审计事件都投递到指定的 logstore 中。

## 配置日志服务 {#section_djx_gk2_lfb .section}

日志服务具有丰富的功能，包括数据分析、报表和报警等。下面举例说明如何设置报警。

1.  登录[日志服务控制台](https://sls.console.aliyun.com/)。
2.  选择所需的项目，单击项目名称。
3.  在**Logstore 列表**页面，选择所需的日志库并单击**查询**。
4.  根据需求指定日志库（Logstore）、主题（Topic）和查询语句后，搜索指定日志。

    **说明：** 单击页面右上角的**另存为快速查询**，将查询参数保存为快速查询。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154026127913882_zh-CN.png)

5.  基于快速查询创建报警。

    其中**检查间隔**设置为 5，即每隔 5 分钟检查最近 10 分钟的数据。如果**LTAIT04MwpKReB7Z**在十分钟内被用过一次，那么就报警。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154026127913884_zh-CN.png)


收到的报警如下所示：

【阿里云】日志服务告警：账号 71887*\*\**@qq.com下项目henshao-test-send-sls-600/触发器use\_ak\_b7z生效2 \> 1，内容AccessKey: LTAIT04MwpKReB7Z 正在被使用，上下文\[use\_ak\_LTAIT04MwpKReB7Z:2\]

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154026127913885_zh-CN.png)

创建的快速查询和报警均可在项目界面进行查看和管理。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154026127913886_zh-CN.png)

日志服务支持通知中心、短信、钉钉机器人和自定义 WebHook 等几种报警方式，您可以根据自身需求，选择合适的报警方式。请参考：[通知方式](../../../../cn.zh-CN/用户指南/告警与通知/通知方式.md#) 。

