---

copyright:
  years: 2021
lastupdated: "2021-05-11"

keywords: getting started with ibm cloud code engine, code engine, ibm cloud code engine, jobs in code engine, apps in code engine, builds with code engine, {{site.data.keyword.codeenginefull_notm}}, building container image

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



<style>
    <!--
        #tutorials { /* hide the page header */
            display: none !important;
        }
        .allCategories {
            display: flex !important;
            flex-direction: row !important;
            flex-wrap: wrap !important;
        }
        .categoryBox {
            flex-grow: 1 !important;
            width: calc(33% - 20px) !important;
            text-decoration: none !important;
            margin: 0 10px 20px 0 !important;
            padding: 16px !important;
            border: 1px #dfe6eb solid !important;
            box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.2) !important;
            text-align: center !important;
            text-overflow: ellipsis !important;
            overflow: hidden !important;
        }
        .solutionBoxContainer {}
        .solutionBoxContainer a {
            text-decoration: none !important;
            border: none !important;
        }
        .solutionBox {
            display: inline-block !important;
            width: 100% !important;
            margin: 0 10px 20px 0 !important;
            padding: 16px !important;
            background-color: #f4f4f4 !important;
        }
        @media screen and (min-width: 960px) {
            .solutionBox {
            width: calc(50% - 3%) !important;
            }
            .solutionBox.solutionBoxFeatured {
            width: calc(50% - 3%) !important;
            }
            .solutionBoxContent {
            height: 350px !important;
            }
        }
        @media screen and (min-width: 1298px) {
            .solutionBox {
            width: calc(33% - 2%) !important;
            }
            .solutionBoxContent {
            min-height: 350px !important;
            }
        }
        .solutionBox:hover {
            border: 1px rgb(136, 151, 162)solid !important;
            box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.2) !important;
        }
        .solutionBoxContent {
            display: flex !important;
            flex-direction: column !important;
        }
        .solutionBoxTitle {
            margin: 0rem !important;
            margin-bottom: 5px !important;
            font-size: 14px !important;
            font-weight: 900 !important;
            line-height: 16px !important;
            height: 37px !important;
            text-overflow: ellipsis !important;
            overflow: hidden !important;
            display: -webkit-box !important;
            -webkit-line-clamp: 2 !important;
            -webkit-box-orient: vertical !important;
            -webkit-box-align: inherit !important;
        }
        .solutionBoxDescription {
            flex-grow: 1 !important;
            display: flex !important;
            flex-direction: column !important;
        }
        .descriptionContainer {
        }
        .descriptionContainer p {
            margin: 0 !important;
            overflow: hidden !important;
            display: -webkit-box !important;
            -webkit-line-clamp: 4 !important;
            -webkit-box-orient: vertical !important;
            font-size: 14px !important;
            font-weight: 400 !important;
            line-height: 1.5 !important;
            letter-spacing: 0 !important;
            max-height: 70px !important;
        }
        .architectureDiagramContainer {
            flex-grow: 1 !important;
            min-width: calc(33% - 2%) !important;
            padding: 0 16px !important;
            text-align: center !important;
            display: flex !important;
            flex-direction: column !important;
            justify-content: center !important;
            background-color: #f4f4f4;
        }
        .architectureDiagram {
            max-height: 175px !important;
            padding: 5px !important;
            margin: 0 auto !important;
        }
    -->
    </style>

# Getting started with {{site.data.keyword.codeenginefull_notm}}
{: #getting-started}

{{site.data.keyword.codeenginefull}} is a fully managed, serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs. {{site.data.keyword.codeengineshort}} even builds container images for you from your source code. Because these workloads are all hosted within the same Kubernetes infrastructure, all of them can seamlessly work together. The {{site.data.keyword.codeengineshort}} experience is designed so that you can focus on writing code and not on the infrastructure that is needed to host it. 
{: shortdesc}



<div class=solutionBoxContainer>
  <div class="solutionBox">
    <a href = "#app-hello">
      <div>
        <p><strong><img src="images/application.svg" alt="Application icon." width="15" style="width:15px; border-style: none"/> Create an application</p></strong>
        <p class="bx--type-caption">Applications run your code to serve HTTP requests.</p>
      </div>
    </a>
  </div>
  <div class="solutionBox">
    <a href = "#first-job">
      <div>
         <p><strong><img src="images/job.svg" alt="Job icon." width="15" style="width:15px; border-style: none"/> Create a job</p></strong>
         <p class="bx--type-caption">Jobs run your code in order to complete tasks.</p>
      </div>
    </a>
  </div>
  <div class="solutionBox">
    <a href = "#build-image-gs">
      <div>
         <p><strong>Build a container image</p></strong>
         <p class="bx--type-caption">Build a container image from your source code and run it.</p>
      </div>
    </a>
  </div>
</div>

## What are {{site.data.keyword.codeengineshort}} projects, applications, jobs, and builds?
{: #term-summary}

Before you get started, become familiar with some key terms for {{site.data.keyword.codeengineshort}}. Afterward, you can test your knowledge and [take a quiz!](https://ibm.biz/BdfFxR){: external}

| Term | Description |
| --------- | ------------------- |
| Project | A project is a grouping of {{site.data.keyword.codeengineshort}} entities such as applications, jobs, and builds. Projects are used to manage resources and provide access to its entities.|
| Application | An application, or app, runs your code to serve HTTP requests. An application has a URL for incoming requests. The number of running instances of an application are automatically scaled up or down (to zero) based on incoming workload. |
| Build | A build, or image build, is a mechanism that you can use to create a container image from your source code. {{site.data.keyword.codeengineshort}} supports building from a Dockerfile or Cloud Native Buildpacks. |
| Job | A job runs one or more instances of your executable code. Unlike applications, which include an HTTP Server to handle incoming requests, jobs are designed to run one time and exit. |
{: caption="Table 1. {{site.data.keyword.codeengineshort}} Terms" caption-side="bottom"}

For more information about terms, see [{{site.data.keyword.codeengineshort}} terminology](/docs/codeengine?topic=codeengine-about#terminology).

## Creating your first {{site.data.keyword.codeengineshort}} app
{: #app-hello}

Create your first {{site.data.keyword.codeengineshort}} app by using the [`helloworld`](https://hub.docker.com/r/ibmcom/helloworld){: external} image from the public Docker Hub. 
{: shortdesc}

1. Open the [{{site.data.keyword.codeengineshort}}](https://cloud.ibm.com/codeengine/overview){: external} console.
2. Select **Start creating** from **Run a container image**.
3. Select **Application**.
4. Enter a name for the application. Use a name for your application that is unique within the project. 
5. Select a project from the list of available projects. You can also [create a new one](/docs/codeengine?topic=codeengine-manage-project#create-a-project). Note that you must have a selected project to deploy an app.
6. Select to run a **Container image** and specify `docker.io/ibmcom/helloworld` for the image reference. For this example, you do not need to modify the default values for environment variables or runtime settings.
7. Click **Create**. 
8. After the application status changes to **Ready**, you can test the application by clicking **Send request** in the Test pane. To open the application in a web page, click **Open application URL**.  

**Output**

```
Hello World from:
  ___  __  ____  ____             
 / __)/  \(    \(  __)            
( (__(  O )) D ( ) _)             
 \___)\__/(____/(____)            
 ____  __ _   ___  __  __ _  ____ 
(  __)(  ( \ / __)(  )(  ( \(  __)
 ) _) /    /( (_ \ )( /    / ) _) 
(____)\_)__) \___/(__)\_)__)(____)
Some Env Vars:
--------------
HOME=/root
HOSTNAME=myhelloworldapp-00001-deployment-59cff67d65-zxdhr
KUBERNETES_PORT=tcp://172.21.0.1:443
KUBERNETES_PORT_443_TCP=tcp://172.21.0.1:443
KUBERNETES_PORT_443_TCP_ADDR=172.21.0.1
KUBERNETES_PORT_443_TCP_PORT=443
KUBERNETES_PORT_443_TCP_PROTO=tcp
KUBERNETES_SERVICE_HOST=172.21.0.1
KUBERNETES_SERVICE_PORT=443
KUBERNETES_SERVICE_PORT_HTTPS=443
K_CONFIGURATION=myhelloworldapp
K_REVISION=myhelloworldapp-00001
K_SERVICE=myhelloworldapp
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PORT=8080
PWD=/
SHLVL=1
```
{: screen}

You deployed your first application to {{site.data.keyword.codeengineshort}} and tested it out. Go to the [Tutorial: Deploying applications](/docs/codeengine?topic=codeengine-deploy-app-tutorial) to try out more options for applications.

## Running your first {{site.data.keyword.codeengineshort}} job
{: #first-job}

Create and run your first {{site.data.keyword.codeengineshort}} job by using the [`ibmcom/firstjob`](https://hub.docker.com/r/ibmcom/firstjob){: external} image. This job prints `Hi from a batch job! My index is: <index>`. 
{: shortdesc}

1. Open the [{{site.data.keyword.codeengineshort}}](https://cloud.ibm.com/codeengine/overview){: external} console.
2. Select **Start creating** from **Run a container image**.
3. Select **Job**.
4. Enter a name for the job. Use a name for your job that is unique within the project.
5. Select a project from the list of available projects. You can also [create a new one](/docs/codeengine?topic=codeengine-manage-project#create-a-project). Note that you must have a selected project to create a job.
6. Specify `docker.io/ibmcom/firstjob` for the image reference.  For this example, you do not need to modify the default values for environment variables or runtime settings.
7. Click **Create**.
8. From your job page, in the Job runs pane, click **Submit job**. 
9. From the Submit job pane, accept all of the default values, and click **Submit job** again to run your job.

When logging is enabled, the expected output of `Hi from a batch job! My index is: 0` is displayed in the logs. To learn about running jobs with logging enabled, see [Viewing logs](/docs/codeengine?topic=codeengine-view-logs). 
{: tip}

You created and ran your job from the console. Go to the [Tutorial: Running jobs](/docs/codeengine?topic=codeengine-deploy-job-tutorial) or [Running jobs in Code Engine](/docs/codeengine?topic=codeengine-job-deploy) to try out more options for jobs.

## Building your first container image from source code
{: #build-image-gs}

Create and run your first {{site.data.keyword.codeengineshort}} build and then deploy the container image in an application.
{: shortdesc}

{{site.data.keyword.codeengineshort}} can automatically push images to a {{site.data.keyword.registryshort}} namespaces in your account. It can even create a namespace for you. To push images to a different {{site.data.keyword.registryshort}} account or to a private DockerHub account, see [Adding access to a private container registry](/docs/codeengine?topic=codeengine-add-registry).

1. Open the [{{site.data.keyword.codeengineshort}}](https://cloud.ibm.com/codeengine/overview){: external} console.
2. Select **Start creating** from **Start from source code**.
3. Select **Application**.
5. Enter a name for the application. Use a name for your application that is unique within the project. 
4. Select a project from the list of available projects. You can also [create a new one](/docs/codeengine?topic=codeengine-manage-project#create-a-project). Note that you must have a selected project to deploy an app.
6. Select **Source code**.
7. Click **Specify build details**.
9. Select `https://github.com/IBM/CodeEngine` for Source repository and `main` for Branch name.  Click **Next**.
10. Select `Dockerfile` for Strategy, `CEDockerfile` for Dockerfile, `10m` for Timeout, and `Medium` for Build resources. Click **Next**.
11. Select a container registry location, such as `IBM Registry, Dallas`.
12. Select `Automatic` for **Registry access**.
13. Select an existing namespace or enter a name for a new one, for example, `newnamespace`.
14. Enter a name for your image and optionally a tag.
15. Click **Done**. 
16. Click **Create**.

After your build run is submitted, the built container image is sent to {{site.data.keyword.registryshort}} and then your application pulls the image and deploys for you. After the application status changes to **Ready**, you can try it out by clicking **Send request**. To open the application in a web page, click **Open application URL**. 

**Output**

```
Hello World from:
  ___  __  ____  ____             
 / __)/  \(    \(  __)            
( (__(  O )) D ( ) _)             
 \___)\__/(____/(____)            
 ____  __ _   ___  __  __ _  ____ 
(  __)(  ( \ / __)(  )(  ( \(  __)
 ) _) /    /( (_ \ )( /    / ) _) 
(____)\_)__) \___/(__)\_)__)(____)
Some Env Vars:
--------------
HOME=/root
HOSTNAME=myhelloworldapp-00001-deployment-59cff67d65-zxdhr
KUBERNETES_PORT=tcp://172.21.0.1:443
KUBERNETES_PORT_443_TCP=tcp://172.21.0.1:443
KUBERNETES_PORT_443_TCP_ADDR=172.21.0.1
KUBERNETES_PORT_443_TCP_PORT=443
KUBERNETES_PORT_443_TCP_PROTO=tcp
KUBERNETES_SERVICE_HOST=172.21.0.1
KUBERNETES_SERVICE_PORT=443
KUBERNETES_SERVICE_PORT_HTTPS=443
K_CONFIGURATION=myhelloworldapp
K_REVISION=myhelloworldapp-00001
K_SERVICE=myhelloworldapp
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
PORT=8080
PWD=/
SHLVL=1
```
{: screen}

You submitted source code to {{site.data.keyword.codeengineshort}} and created a container image that you then deployed in an application - all from one interface.

Go to the [Building a container image](/docs/codeengine?topic=codeengine-plan-build) to explore and try out more options for builds.

## Next steps for {{site.data.keyword.codeengineshort}}
{: #nextsteps-getstart}

Learn more about performing these {{site.data.keyword.codeengineshort}} tasks from the console or with the [{{site.data.keyword.codeengineshort}} CLI](/docs/codeengine?topic=codeengine-install-cli).
- [Managing projects](/docs/codeengine?topic=codeengine-manage-project)
- [Deploying applications](/docs/codeengine?topic=codeengine-application-workloads)
- [Running jobs](/docs/codeengine?topic=codeengine-job-deploy)
- [Building container images](/docs/codeengine?topic=codeengine-build-image)

Looking for more code examples? Check out the [Samples for {{site.data.keyword.codeenginefull_notm}} GitHub repo](https://github.com/IBM/CodeEngine){: external}.
{: tip}
