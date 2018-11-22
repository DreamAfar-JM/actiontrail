# Monitor the use of an AccessKey through ActionTrail {#concept_zm4_fk2_lfb .concept}

This topic describes how to monitor the use of an AccessKey through ActionTrail. You can view the use of an AccessKey in the last 30 days by checking historical events and monitor the AccessKey by configuring a trail and delivering the trail events to the Log Service.

## Query historical events {#section_t3x_gk2_lfb .section}

You can view the trail events that occurred in the last 30 days after activating the ActionTrail service.

1.  Log on to the [ActionTrail console](https://partners-intl.console.aliyun.com/#/actiontrail).
2.  In the left-side navigation pane, click **History Search**.
3.  From the **Filter** drop-down list, select **AccessKeyId**.
4.  Enter your **AccessKeyId** to search for a trail event.

    **Note:** By switching the region in the upper-left corner, you can view the trail events used by the **AccessKeyId** of different regions.


## Use a trail {#section_y3x_gk2_lfb .section}

ActionTrail allows you to monitor an AccessKey by delivering a trail event to the Log Service.

1.  In the left-side navigation pane, click **Trail List**.
2.  Click **Create Trail**.
3.  If you select **Delivery to Log Service**, set the **Log Service Region** and **Log Service Project**.

    **Note:** The project is used to store ActionTrail logs. You can enter a project name under the region you selected, or enter a new project name.

4.  Select **Enable logging**.
5.  Click **Submit**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154285130313881_en-US.png)


ActionTrail automatically delivers the trail events of all regions to the specified Logstore after you successfully create a trail.

## Configure Log Service {#section_djx_gk2_lfb .section}

Log Service has multiple features, including data analysis, reporting, and alarming. The following is an example of how to set an alarm.

1.  Log on the [Log Service console](https://partners-intl.console.aliyun.com/#/sls).
2.  Click a project.
3.  On the **Logstores** page, select a Logstore and click **Search**.
4.  Specify the Logstore, topic, and query SQL statement as required, and search for the specified logs.

    **Note:** You can click **Save Search** in the upper-right corner of the page to save the parameters for quick search.

    Query SQL statement example:

    ```
    event.userIdentity.accessKeyId: "LTAIDC4unc8R2qPu" | select count(1) as use_ak_LTAIDC4unc8R2qPu
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154285130313882_en-US.png)

5.  Create an alarm according to the saved search and click **Saved as Alarm** in the upper-right corner of the page.

    **Note:** If you set **Check Interval** to 5, data in the last 10 minutes is checked at an interval of 5 minutes. If the `accessKeyId` \(such as LTAIDC4unc8R2qPu\) is used once in 10 minutes, an alarm is generated.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154285130313884_en-US.png)


The following is an alarm example:

\[Alibaba Cloud\] Log Service alarm: The project henshao-test-send-sls-600/trigger use\_ak\_b7z of 71887*\*\**@qq.com takes effect 2 \> 1; content: AccessKey: LTAIDC4unc8R2qPu is in use. Context: \[use\_ak\_LTAIDC4unc8R2qPu:2\]

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154285130313885_en-US.png)

You can view and manage the saved search and alarms on the project page.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23638/154285130413886_en-US.png)

Log Service supports various alarm types, for example, notifications, SMS, WebHook-DingTalk Bot, and WebHook-Custom. You can select an appropriate type as needed.

