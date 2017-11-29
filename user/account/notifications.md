---
layout: wmt/docs
side-navigation: user-navigation.html
title: Notifications
---

# Notification

A number of events in an organization in OneOps can trigger notifications. These events include deployments,
monitors, scale and repair actions.

Notifications can be sent to a number of receiving _notification sinks_ including simple URLs, Jabber, Amazon SNS
and Slack.

To set up and configure notifications, follow these steps:

1. Access the settings for the desired organization
   1. Click _Settings_ under the specific organization in the left hand navigation
   2. Alternative click on the settings icon in the header
2. Select the _notifications_ tab.
3. Press the _Add_ button on top of the list of notifications to create a new notification sink.
4. Or click on the name of a specific notification sink in the list to access its configuration in the _Details_
section on the right. Pressing the _Edit_ button allows you to change the configuration.
5. Provide all desired values and press _Save_.

Each notification sink includes a number of generic as well as type-specific configuration settings.
The type is selected as a first action when creating a new notification sink.

The generic settings are:

<dl>
<dt>Name:</dt>
<dd>The required name of the notification sink.</dd>

<dt>Global - Description:</dt>
<dd>Optional description for the notification sink</dd>

<dt>Filtering:</dt> <dd>Fine-grained control over which messages are sent is possible with filtering enabled. You
can configure filters with criteria such as _Event Type_, _Severity Level_, _Environment Profile Pattern_, _NS
Paths_, _Monitoring Clouds_ and _Message Pattern_. Typically filtering should be enabled so that specific the
notification sync is not flooded by all events for the organization. Instead it can be filtered to e.g. only
receive specific events for a specific assembly with a combination of the available criteria.</dd>

<dt>Transformation:</dt><dd>Message can be transformed before they are sent </dd> <dt>Dispatching - Message
Dispatching:</dt><dd>Configure to use synchronous or asynchronous mechanism for dispatching event messages.</dd>

</dl>

You can select multiple notification sinks to similar targets with different filters to achieve the desired
verbosity and message frequence.

Type-specific configuration and usage is explained in the the sink specific sections:

* [Notifications to URL](/user/account/notifications-to-url.html)
* [Notifications to Amazon SNS](/user/account/notifications-to-amazon-sns.html)
* [Notifications to Jabber](/user/account/notifications-to-jabber.html)
* [Notifications to Slack](/user/account/notifications-to-slack.html)

![SNS](/assets/docs/local/images/sns.png)
