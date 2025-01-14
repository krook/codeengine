---

copyright:
  years: 2021
lastupdated: "2021-05-07"

keywords: eventing, ping event, cos event, object storage event, event producers, subscribing, subscription, cloudevents

subcollection: codeengine

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Getting started with subscriptions
{: #subscribing-events}

Oftentimes in distributed environments you want your applications or jobs to react to messages (events) that are generated from other components, which are usually called event producers. With {{site.data.keyword.codeengineshort}}, your applications or jobs can receive events of interest by subscribing to event producers. Event information is received as POST HTTP requests for applications and as environment variables for jobs.
{: shortdesc}

{{site.data.keyword.codeengineshort}} supports two types of event producers. 

**Ping (cron)**: The Ping event producer is based on cron and generates an event at regular intervals. Use a Ping event producer when an action needs to be taken at well-defined intervals or at specific times.

**{{site.data.keyword.cos_full_notm}}**: The {{site.data.keyword.cos_short}} event producer generates events as changes are made to the objects in your object storage buckets. For example, as objects are added to a bucket, an application can receive an event and then perform an action based on that change, perhaps consuming that new object.

Apps and jobs can subscribe to multiple event producers, but only one app or job can receive events from each subscription. Note that subscriptions can affect how an application scales. For more information, see [Configuring application scaling](/docs/codeengine?topic=codeengine-app-scale). Subscriptions can also affect how many jobs are started. For example, if your job subscribes to delete changes on an {{site.data.keyword.cos_short}} bucket and that bucket is deleted, a job is run for each object that was in that bucket.
{: shortdesc}

Subscription support for jobs is available as a beta function. Beta functions and services might be unstable or change frequently.	
{: beta}

For more information about subscription APIs, see [{{site.data.keyword.codeengineshort}} API reference - Subscription CRD methods](/docs/codeengine?topic=codeengine-api#api-crd-subscription).

## Can I use other `CloudEvents` specifications?
{: #subscribing-events-cloudevents}

Events that are managed by {{site.data.keyword.codeengineshort}} when you create a subscription are modified so that they adhere to the
[`CloudEvents` specification](https://cloudevents.io){: external}. This specification defines a set of common attributes that can be included with each event to provide a common set of metadata. By looking at the metadata, you can quickly understand key pieces of the message without parsing and understanding the entirety of the event payload. For example, each event that is delivered to an application includes an HTTP header called `ce-type`, which indicates the semantic meaning (or "reason") for the event. An event from a database might include a `ce-type` value of `com.example.row.deleted`, indicating that the event was generated because a row was deleted in the database.

The following table lists some of the key common attributes.

| Header   | Description      | 
|----------|------------------|
| ID | This required attribute is a unique ID for the event. No two events from the same event producer are assigned the same value. | 
| Source | This required attribute specifies the context in which the event occurred. For example, for an object storage system, this value might be the bucket in which the object in question resides. |
| Type | This required attribute describes the type of the event. For example, the type of event might be that a resource was created or deleted. |
| Subject | This optional attribute indicates the resource about which the event is related. For example, in an object storage system, this value might be the object from the bucket that was modified. |
| Time | This optional attribute is the timestamp of when the occurrence happened. |
{: caption="Table 1. Common `CloudEvent` attributes" caption-side="top"}

For more information about the complete list of attributes, see the [`CloudEvents` specification](https://github.com/cloudevents/spec){: external}.

In {{site.data.keyword.codeengineshort}}, when events are delivered to applications, the `CloudEvent` attributes appear as HTTP headers, prefixed with `ce-`. When events are delivered to batch jobs, the attributes appear as environment variables, prefixed with `CE_` and the entire variable name is in upper-case.

## What happens when I create a subscription?
{: #subscribing-events-what-happens}

By default, the [`subscription ping create`](/docs/codeengine?topic=codeengine-cli#cli-subscription-ping-create) and the [`subscription cos create`](/docs/codeengine?topic=codeengine-cli#cli-subscription-cos-create) commands first check to see whether the destination application or job exists. If the destination check fails because the application or job does not exist in your project, the `subscription create` command returns an error. If you want to create a subscription without first creating the application, use the `--force` option. By using the `--force` option, the command bypasses the destination check. Note that the `Ready` field of the subscription shows false until the destination application or job is created. Then, the subscription moves to a `Ready: true` state automatically.

After the subscription is created, the subscription is repeatedly polled for status to verify its readiness. This polling lasts for 15 seconds by default before it times out. You can change the amount of time before the command times out by using the `--wait-timeout` option. You can also bypass the status polling by setting the `--no-wait` option to `false`.

You can display the status of your subscription by using the [`subscription ping get`](/docs/codeengine?topic=codeengine-cli#cli-subscription-ping-get) or the [`subscription cos get`](/docs/codeengine?topic=codeengine-cli#cli-subscription-cos-get) CLI commands.
