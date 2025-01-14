---

copyright:
  years: 2021
lastupdated: "2021-05-11"

keywords: faq for code engine, project faq for code engine, feedback for code engine, code samples for code engine, terms of service for code engine, faq, feedback, terms, code samples, project, code engine, limits

subcollection: codeengine

content-type: faq

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


# FAQs 
{: #faqs}

Answers to common questions about the {{site.data.keyword.codeenginefull}} service. 
{:shortdesc}

## What is {{site.data.keyword.codeenginefull_notm}}? 
{: #what-is-codeengine}
{: faq}
{: support}

{{site.data.keyword.codeengineshort}} is an open source platform that was developed by IBM. The goal is to extend the capabilities of Kubernetes to help you create modern, source-centric containerized, and serverless apps that run on your Kubernetes cluster. The platform is designed to address the needs of developers who today must decide what type of app they want to run in the cloud: 12-factor apps, containers, or functions. For more information, see [About {{site.data.keyword.codeengineshort}}](/docs/codeengine?topic=codeengine-about).

With {{site.data.keyword.codeengineshort}}, you can deploy applications, run jobs, and even build source code from a single dashboard.

## What is a project? 
{: #what-is-project}
{: faq}
{: support}

A project is a grouping of {{site.data.keyword.codeengineshort}} entities such as applications, jobs, and builds. A project is based on a Kubernetes namespace. The name of your project must be unique within your {{site.data.keyword.cloud}} resource group, user account, and region. Projects are used to manage resources and provide access to its entities. A project provides the following items:<ul><li>Provides a unique namespace for entity names.</li><li> Manages access to project resources (inbound access).</li><li> Manages access to backing services, registries, and repositories (outbound access).</li><li> Has an automatically generated certificate for Transport Layer Service (TLS).</li></ul>

For more information about projects, see [Manage projects](/docs/codeengine?topic=codeengine-manage-project).

## Where can I find code samples?   
{: #find-code-samples}
{: faq}
{: support}

You can find code samples to help you explore the capabilities of {{site.data.keyword.codeengineshort}}. Visit our [{{site.data.keyword.codeengineshort}} code samples repository on GitHub](https://github.com/IBM/CodeEngine){: external}. 

## I need more memory! Can I increase my limits?
{: #increase-ce-limits}
{: faq}
{: support}

Yes, you can increase your {{site.data.keyword.codeengineshort}} [limits](/docs/codeengine?topic=codeengine-limits) by contacting [IBM support](/docs/codeengine?topic=codeengine-get-support). 

## What is the difference between a Docker build on my system and a build in {{site.data.keyword.codeengineshort}}? 
{: #dockerbld-cebuild}
{: faq}
{: support}

The result of a Docker build that you run on your local system is the same container image that you get if you run a build with the same Dockerfile in {{site.data.keyword.codeengineshort}}. However, the build in {{site.data.keyword.codeengineshort}} is not running on your local system, but instead in the {{site.data.keyword.codeengineshort}} system. This build in {{site.data.keyword.codeengineshort}} gives you several advantages.

1. You are not required to install software, such as Docker Desktop, locally.
2. You can use the resources that are provided by {{site.data.keyword.codeengineshort}}. For example, you can take advantage of the speed of {{site.data.keyword.Bluemix_notm}} to push and pull container registry images for you.
3. You can build your container image by using the [Buildpack build strategy](/docs/codeengine?topic=codeengine-plan-build#build-strategy) instead of Dockerfile, which detects your sources for various languages and automatically builds a container out of it.
  
## Do {{site.data.keyword.codeengineshort}} apps support WebSockets? 
{: #app-websockets}
{: faq}
{: support}

Yes! You can find a [sample app that uses WebSockets](https://github.com/IBM/CodeEngine/tree/main/websocket){: external} by visiting our {{site.data.keyword.codeengineshort}} samples repository on GitHub.

## How can I review the {{site.data.keyword.codeengineshort}} service terms?  
{: #review-service-terms}
{: faq}
{: support}

For the latest service level agreement terms, see the [terms of service](/docs/overview/terms-of-use?topic=overview-terms).

## How can I give feedback? 
{: #give-feedback}
{: faq}
{: support}

Your feedback on {{site.data.keyword.codeengineshort}} is important to us and helps us improve. You can provide feedback in multiple ways:
  * Click **Feedback** from any page on the [{{site.data.keyword.codeengineshort}} console](https://cloud.ibm.com/codeengine/overview){: external} or in the product documentation to provide your comments.  
  * Share feedback through Slack. You can [register](https://cloud.ibm.com/kubernetes/slack){: external} and join the discussion in the [#code-engine channel](https://ibm-cloud-success.slack.com){: external}. 
