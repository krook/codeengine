---

copyright:
  years: 2021
lastupdated: "2021-05-11"

keywords: application scaling in code engine, scaling http requests in code engine, concurrency in code engine applications, latency in code engine applications, throughput in code engine applications, scaling, latency, concurrency

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


# Configuring application scaling
{: #app-scale}

With {{site.data.keyword.codeenginefull}}, you don't need to think about scaling because the number of running instances of an application is automatically scaled up or down (to zero) based on incoming workloads. With automatic scaling, you don't pay for resources that are not used. 
{: shortdesc}

{{site.data.keyword.codeengineshort}} monitors the number of requests in the system and scales the application instances up and down in order to meet the load of incoming requests, including any HTTP connections to your application. These HTTP connections can be requests that come from outside of your project, from other workloads that are running in your project, or from event producers that you might be subscribed to, regardless of where those producers are located. {{site.data.keyword.codeengineshort}} automatically replicates application instances and configures the network infrastructure to load balance the requests across all instances.

To observe application scaling from the [{{site.data.keyword.codeengineshort}} console](https://cloud.ibm.com/codeengine/overview), navigate to your specific application page. While the application is running, the number of running instances is `1` or greater based on the maximum number of instances that you specified. When the application is finished running, the number of running instances scales down to the minimum number of instances setting. If the minimum number of instances is set to `0`, the application scales to zero and the number of instances for the app reflects `0` instances. If the application is scaled to zero and a request is routed to the application, {{site.data.keyword.codeengineshort}} scales the application up from zero and routes the request to the newly created application instance.

## How scaling works
{: #app-how-scale}

{{site.data.keyword.codeengineshort}} monitors the number of requests in the system and scales the application instances, within the constraints of the application's concurrency settings.
{: shortdesc} 

Use the following two configuration settings to control application scaling:

- `concurrency` - When creating or updating an application with {{site.data.keyword.codeengineshort}} from the console, set the concurrency value in the Runtime section. With the CLI, specify the `--concurrency` option on the `app create` and `app update` commands. This value indicates how many requests each instance of your app can process at one time.  For example, a `concurrency` value of 100 means that your code can handle 100 concurrent requests at the same time. This value is a "hard limit", meaning that {{site.data.keyword.codeengineshort}} will not allow more than the number of requests (as specified with the concurrency setting) to reach any one instance of your application. Therefore, if your code is single threaded and can process only one request at a time, then consider setting `concurrency` to `1`. Once the specified number of requests are sent to all running instances of your application, {{site.data.keyword.codeengineshort}} then increases the number of instances in preparation for additional requests.

- `concurrency-target` -  When creating or updating an application with the {{site.data.keyword.codeengineshort}} CLI, you can also specify the `--concurrency-target` option on the `app create` and `app update` commands.  This option acts as a "soft limit" or  number of requests per instance that you want in a loaded system. For example, if you specify `concurrency` as `100`, and you specify `--concurrency-target` as `70`, then {{site.data.keyword.codeengineshort}} tries to limit the number of requests per instance to 70.  Specifying this option isn’t a guarantee that requests per instance won't go above 70, because it most likely will during an increase in traffic. However, the buffer between 70 and 100 enables the system to create new instances to bring the load per instance back down to 70 (or below) per instance. This value is available only with the CLI.  If `--concurrency-target` option  is not specified, the default is the value of `--concurrency`.

For more information about how {{site.data.keyword.codeengineshort}} works, see [IBM Cloud Code Engine: Optimising Application Scaling, Latency, and Throughput](https://www.ibm.com/cloud/blog/ibm-cloud-code-engine-optimising-application-scaling-latency-and-throughput){: external}.

## Scaling boundaries
{: #app-scale-boundaries}

You can configure scaling boundaries for {{site.data.keyword.codeengineshort}}, by using `--min-scale` and `--max-scale` options when you create or update applications.
{: shortdesc} 

- `--min-scale`: The minimum number of application instances to keep running. When set to `0` (default) {{site.data.keyword.codeengineshort}} removes all instances when no traffic is reaching the application. 
- `--max-scale`: The maximum number of application instances that can run. {{site.data.keyword.codeengineshort}} does not scale up beyond that value.

When you connect your applications to event producers, remember to account for the frequency and volume of the events from those producers when you set your scale boundaries. For example, if you expect to receive a large number of events at the same time and the processing of each event can take several minutes, then you might need a higher maximum scale value than if each event can be quickly processed. If you set the value too low, you might experience delays in receiving events, or even dropped events due to timeouts while you wait for processing resources to be free.

For example, if you keep the default maximum scale value to `10` and the concurrency to `100`, then by default, an application can process 1000 concurrent events before potential buffering issues might arise. If you expect more than 1000 requests (or events) concurrently, then you might consider increasing your maximum scale value.

## Optimize latency and throughput
{: #app-optimize-latency}

In order to optimize your application latency and throughput, understand the pros and cons of some common models and best practices to configure the container concurrency. Use the `--concurrency` option  (alias `--cn`) with the `app create` or `app update` commands to specify the maximum number of requests that can be processed concurrently per instance.
{: shortdesc} 

| Model | Pros | Cons |
| --------- | -------- | -------- |	
| Single-concurrency, `--cn=1` | Choose the single concurrency configuration when the application serves a memory-intensive or CPU-intensive workload because only one request enters the application instance at a time and therefore gets the full amount of CPU and memory configured for the instance. | Applications that use the single-concurrency model scale-out quickly. The scale-out might introduce additional latency and lower throughput because it's more expensive to create a new application instance than to reuse an existing one. Do not choose this model if requests can be processed concurrently and latency is a critical aspect of the application. |
| High-concurrency, `--cn=100` (default) or higher | Choose this configuration if your application serves a high volume of HTTP request or response workloads that are not CPU-intensive or memory-intensive and can wait for resources. You might choose this concurrency configuration for an API back end that reads and writes data on CRUD operations to a remote database. While some requests wait on I/O, other requests can be processed without impacting overall latency and throughput. | This setting is not optimal when concurrent requests compete for CPU, memory, or I/O because competition for resources can delay execution and impact latency and throughput negatively. |
| Optimal concurrency, `--cn=N` | Choose the optimal concurrency configuration if you know the amount of resources that are required for a single request to meet the response time that you want for your application. You might choose this configuration if your app is a natural language translation application, where the machine learning model for the language translation is `32` GB, and a single translation computation needs about `0.7` vCPU per request. You can choose a configuration of `9` vCPUs and `32` GB of memory per instance. The optimal container concurrency is about `13` (`9 vCPU/0.7 vCPU`). | Do not choose the optimal concurrency configuration if you do not know the resource requirements for your application. Setting the wrong container concurrency can lead to either too aggressive or too lazy scaling, which might impact the latency, error rate, and costs of your application. For more information, see [Determine concurrency for your application container](#app-determine-concurrency). |
| Infinite concurrency, `--cn=0` (disabled) | Disabled | The infinite concurrency configuration is not supported in {{site.data.keyword.codeengineshort}}. The infinite concurrency configuration forwards as many requests as possible to a single application instance, which can delay the scaling of additional application instances. |
{: caption="Examples concurrency in {{site.data.keyword.codeengineshort}} applications" caption-side="top"}

### Determining concurrency of your application container
{: #app-determine-concurrency}

The optimal container concurrency value is determined by the maximum number of concurrent requests the application can handle with an acceptable request latency.
{: shortdesc} 

The container concurrency (cc) has a direct impact on the success rate, latency, and throughput of the application. When the container concurrency value is too high for the application to handle, the latency and throughput is impacted negatively and you might observe `502` and `503` error responses. 

When the container concurrency value is too low for the application, the system scales out the application more quickly and spreads the request across many application instances, introducing additional costs and latency. During a burst of load, a low concurrency value can also lead to temporary `502` responses when the internal buffers of the system run over.

To determine the container concurrency configuration for your application, examine requests and latency.

1. Create an application and set its concurrency to `1000` (max) and both `minScale` and `maxScale` to `1`.

   ```sh
   ibmcloud ce application create -name APPNAME --image APPIMAGE --min-scale=1 --max-scale=1 --concurrency=1000
   ```
   {: pre}
   
2. Start by sending a high rate of requests. If `502` errors occur, then decrease the rate until the result shows a 100% success rate.
3. Find the request latency of the output of Step 2. If the request latency is not acceptable, further decrease the request rate until the request latency looks acceptable. Note that the request duration is also important as it makes a difference if the computation of the request takes `2` seconds or `100` milliseconds. 

   Your acceptable request rate and latency varies according to your application characteristics and your scaling configuration. For example, if the computation within your application takes about 100 ms and your concurrency setting is 10 one application instance is able to process around 100 requests per second with a latency of about 100 ms (ignoring network latency).
4. To calculate the container concurrency value for your application, take the *rate* from Step 2 (in `req/s`) and divide by the *latency* of Step 3 (in seconds): `CC = RATE/LATENCY`. For example, if the rate is `80` requests per second and the latency is `2` seconds, the resulting concurrency is concurrency = `80 req/s / 2 s = 40`.
5. Update the application to set the container concurrency to the value that you found in the previous step and rerun the workload to check whether the success rate and latency are acceptable.
6. Experiment with the application by increasing the container concurrency value and observing the success rate and latency.
7. Update your application with the optimal container concurrency value and remove the `minScale` and `maxScale` boundaries to allow the application to scale automatically.
  
## Scaling your application with the CLI
{: #scale-app-cli}

You can control the maximum and minimum number of running instances of your app by changing the values of the `--min-scale` and `--max-scale` options by using the `application create` or `application update` command.
{: shortdesc} 

To observe application scaling from the {{site.data.keyword.codeengineshort}} CLI,

1. Create an application with the `app create` command.

   ```sh
   ibmcloud ce application create -name myapp --image docker.io/ibmcom/helloworld
   ```
   {: pre}

2. Call the application. You can obtain the URL of your app from the output of the `app create` command, or you can run `ibmcloud ce app get --name myapp --output url`.

   ```sh
   curl https://myapp.4svg40kna19.us-south.codeengine.appdomain.cloud
   ```
   {: pre}

3. Run the `application get` command to display the status of your application. Look for the value for `Running instances`. In this example, the app has `1` running instance. For example,

    ```sh
    ibmcloud ce application get -name myapp
    ```
    {: pre}

   **Example output**
   
   ```
   OK

   Name:          myapp
   [...]

   URL:           https://myapp.4svg40kna19.us-south.codeengine.appdomain.cloud
   Console URL:   https://cloud.ibm.com/codeengine/project/us-south/01234567-abcd-abcd-abcd-abcdabcd1111/application/myapp/configuration

   Status Summary:  Application deployed successfully

   Image:                docker.io/ibmcom/helloworld
   Resource Allocation:
      CPU:                1
      Ephemeral Storage:  500Mi
      Memory:             4G

   Revisions:
    myapp-ds8fn-1:
      Age:                6m25s
      Traffic:            100%
      Image:              docker.io/ibmcom/helloworld (pinned to fe0446)
      Running Instances:  1

   Runtime:
      Concurrency:    100
      Maximum Scale:  10
      Minimum Scale:  0
      Timeout:        300

   Conditions:
      Type                 OK    Age    Reason
      ConfigurationsReady  true  6m10s
      Ready                true  5m56s
      RoutesReady          true  5m56s

   Events:
      Type    Reason   Age    Source              Messages
      Normal  Created  6m28s  service-controller  Created Configuration "myapp"
      Normal  Created  6m28s  service-controller  Created Route "myapp"

   Instances:
      Name                                       Revision       Running  Status   Restarts  Age
      myapp-ds8fn-1-deployment-79bdd76749-khtmw  myapp-ds8fn-1  2/2      Running  0         32s
   ```
   {: screen}

  Wait a few minutes, as it can take a few minutes for your app to scale to zero. 
  {: note}

4. Run the `application get` command again and notice that the value for `Running instances` scaled to zero. When the application is finished running, the number of running instances automatically scales to zero, if the `--min-scale` option is set to `0`, which is the default value. 

   Wait a few minutes, as it can take a few minutes for your app to scale to zero. 
   {: note}

    ```sh
    ibmcloud ce application get -n myapp
    ```
    {: pre}

   **Example output**
   
   ```
   OK

   Name:          myapp
   [...]

   URL:           https://myapp.4svg40kna19.us-south.codeengine.appdomain.cloud
   Console URL:   https://cloud.ibm.com/codeengine/project/us-south/01234567-abcd-abcd-abcd-abcdabcd1111/application/myapp/configuration

   Image:                docker.io/ibmcom/helloworld
   Resource Allocation:
      CPU:                1
      Ephemeral Storage:  500Mi
      Memory:             4G

   Revisions:
    myapp-ds8fn-1:
      Age:                12m
      Traffic:            100%
      Image:              ibmcom/hello (pinned to 548d5c)
      Running Instances:  0

   Runtime:
      Concurrency:         100
      Maximum Scale:       10
      Minimum Scale:       0
      Timeout:             300

   Conditions:
      Type                 OK    Age    Reason
      ConfigurationsReady  true  3m7s
      Ready                true  2m54s
      RoutesReady          true  2m54s

   Events:
      Type    Reason   Age    Source              Messages
      Normal  Created  3m21s  service-controller  Created Configuration "myapp"
      Normal  Created  3m20s  service-controller  Created Route "myapp"
   ```
   {: screen}

5. Call the application again to scale from zero.

   ```sh
   curl https://myapp.4svg40kna19.us-south.codeengine.appdomain.cloud
   ```
   {: pre}

6. Run the `application get` command again and notice that the value for `Running instances` scaled up from zero. For example,

    ```sh
    ibmcloud ce application get -n myapp
    ```
    {: pre}

   **Example output**
   
   ```
   OK

   Name:          myapp
   [...]
 
   URL:           https://myapp.4svg40kna19.us-south.codeengine.appdomain.cloud
   Console URL:   https://cloud.ibm.com/codeengine/project/us-south/01234567-abcd-abcd-abcd-abcdabcd1111/application/myapp/configuration

   Status Summary:  Application deployed successfully

   Image:                docker.io/ibmcom/helloworld
   Resource Allocation:
   CPU:                1
   Ephemeral Storage:  500Mi
   Memory:             4G

   Revisions:
   myapp-ds8fn-1:
      Age:                13m
      Traffic:            100%
      Image:              docker.io/ibmcom/helloworld (pinned to fe0446)
      Running Instances:  1

   Runtime:
   Concurrency:    100
   Maximum Scale:  10
   Minimum Scale:  0
   Timeout:        300

   Conditions:
   Type                 OK    Age  Reason
   ConfigurationsReady  true  16m
   Ready                true  16m
   RoutesReady          true  16m

   Events:
   Type    Reason   Age  Source              Messages
   Normal  Created  17m  service-controller  Created Configuration "myapp"
   Normal  Created  17m  service-controller  Created Route "myapp"

   Instances:
   Name                                       Revision       Running  Status   Restarts  Age
   myapp-ds8fn-1-deployment-79bdd76749-76l4w  myapp-ds8fn-1  1/2      Running  0         16s
   ```
   {: screen}
