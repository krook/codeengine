---

copyright:
  years: 2021
lastupdated: "2021-03-25"

keywords: applications in code engine, apps in code engine, http requests in code engine, deploy apps in code engine, app workloads in code engine, deploying workloads in code engine

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


# Determining memory and CPU combinations
{: #mem-cpu-combo}

Applications and jobs consume CPU and memory. These amounts can vary, depending on if your app is compute-intensive, memory-intensive, or balanced.
{: shortdesc}

See the following table for valid combinations of vCPU and memory.

| CPU-intensive  | Balanced | Memory-intensive |
|--------|--------|--------|
| 0.125 vCPU 0.25 GB | 0.125 vCPU 0.5 GB | 0.125 vCPU 1 GB |
| 0.25 vCPU 0.5 GB | 0.25 vCPU 1 GB | 0.25 vCPU 2 GB |
| 0.5 vCPU 1 GB | 0.5 vCPU 2 GB | 0.5 vCPU 4 GB |
| 1 vCPU 2 GB | 1 vCPU 4 GB | 1 vCPU 8 GB |
| 2 vCPU 4 GB | 2 vCPU 8 GB | 2 vCPU 16 GB |
| 4 vCPU 8 GB | 4 vCPU 16 GB | 4 vCPU 32 GB |
| 6 vCPU 12 GB | 6 vCPU 24 GB |  |
| 8 vCPU 16 GB | 8 vCPU 32 GB |  |
{: caption="Table 1. Valid vCPU and memory combinations" caption-side="top"}

Your existing apps and jobs might be using other memory and CPU combinations. However, these other combinations are not valid and soon only the valid combinations will be supported.
{: important}