# Environments {: class="guideH1"}

(updated 2023-03-06 using v0.3) 
{: class="guideCreated"}

There are various ways how you can access the OpenStudyBuilder solution as a running application. The following options are documented:

- Sandbox system (no own installation required)
- Lokal docker installation 
- Azure deployment

## Sandbox environment

The OpenStudyBuilder project is progressing with a sandbox environment where people can register to play around with the open-source solution without needing to install anything. This provides an excellent opportunity to get a more detailed impression of the metadata repository (MDR). The sandbox allows for investigations on how standards can be maintained, differences identified, how studies can be created with all protocol information and much more. The API is also accessible to see the capabilities for connecting tools.  And lastly, a database browser allows for check out details of the biomedical concept. 

### Overview

The following tools and URLs are available after registration

Tool | URL | Note
--|--|--
OpenStudyBuilder App | [https://openstudybuilder.northeurope.cloudapp.azure.com/](https://openstudybuilder.northeurope.cloudapp.azure.com/){target=_blank} | main application
Documentation | [https://openstudybuilder.northeurope.cloudapp.azure.com/doc/](https://openstudybuilder.northeurope.cloudapp.azure.com/doc/){target=_blank} | product related documentation
API | [https://openstudybuilder.northeurope.cloudapp.azure.com/api/docs](https://openstudybuilder.northeurope.cloudapp.azure.com/api/docs){target=_blank} | API documentation and running API calls
NeoDash | [https://openstudybuilder.northeurope.cloudapp.azure.com/neodash/](https://openstudybuilder.northeurope.cloudapp.azure.com/neodash/){target=_blank} | Dashboard for underlying database
DB Browser | [https://openstudybuilder.northeurope.cloudapp.azure.com/browser/](https://openstudybuilder.northeurope.cloudapp.azure.com/browser/){target=_blank} | Browser for underlying database
Bloom | [https://openstudybuilder.northeurope.cloudapp.azure.com/bloom/](https://openstudybuilder.northeurope.cloudapp.azure.com/bloom/){target=_blank} | Graph broswer for underlying database

### Getting Access

To get access to the Sandbox environment, you can simply send a mail to openstudybuilder@neotechnology.com with the subject "Request Sandbox Access". Your e-mail will be used together with Microsoft authentication to access the various tools via browser. Please be aware that your mail might be exposed when you perform changes as all changes are tracked for a version history.

### The Application

The core application can easily be started with a browser. The sandbox system has already an example study which can be loaded, browsed and changed. Under the "Define Study" all relevant study protocol and trial domain information can be managed. The "View Specifications" section is available to use the entered information in different formats, e.g. for the protocol.

![Screenshot of the study part from the OpenStudyBuilder](./img/guide_sandbox_01.png)

The general and sponsor standards can be maintained in the "Library" part of the application. Next to the functionality to browse standards like the controlled terminology from CDISC, also sponsored preferred names can be stored alongside. Extensible codelists can be added by elements and additional new sponsor codelists like for different visits can be created. Dictionaries can be maintained and browsed as well.

A core feature of the MDR and the underlying graph data model are the concepts. Standard activities can be grouped and linked. Even unit mapping for UCUM, CT and sponsor units can be maintained. The "Syntax Templates" are a fantastic feature which allows to use generic texts for protocols with semantic meaning.


![Screenshot of the library part from the OpenStudyBuilder](./img/guide_sandbox_02.png)

### The Documentation

The tool documentation is available via the sandbox as well. This even does not need any authentication as it's a simple webpage which can be accessed [here](https://openstudybuilder.northeurope.cloudapp.azure.com/doc/){target=_blank}. Next to a user guide, you also find useful information about the architecture.

### The API

A main advantage of the OpenStudyBuilder is the openness for interfaces. The API is very powerful. Everything what the application does uses APIs which updates the graph database. This means that everything can be automated via scripts. Data can easily be loaded via the API. All the data and standards data is loaded into the solution via import scripts (mdr-standard-imports and data-imports). These can be adopted to import other data.

All information available can also be exported via API and then used by other tools. When you browse the API Swagger documentation, you can see and execute various API endpoints available.

![Screenshot for API usage - get a study](./img/guide_sandbox_03.png)

### The Graph Database / Biomedical Concept

The heart of the application is the graph database which is using Neo4j. It contains a biomedical concept linking all kind of data which allows a high level of connectivity for automations. The NeoDash can be used to browse the concepts.

![Screenshot for NeoDash showing Diastolic Blood Pressure concept](./img/guide_sandbox_04.png)

Next to NeoDash there is also the DB Browser. This can be used to browse the Neo4j database directly using the query language Cypher. After logging in via SSO (in case of issues clear cache or do a hard reload of the page), you can select the sandbox database. You can either use a direct query or get along by selecting a node and follow the connections.

![Screenshot for Neo4J Bloom Browser showing graph data](./img/guide_sandbox_05.png)

Finally, Bloom is also available which allows to create and store Scenes. This is very valuable if you want to come back to a visualization or share this with others. In one of our next newsletters, we are going to have a closer look into the concepts.

### Logins

**Application**

The core application is accessible through https://openstudybuilder.northeurope.cloudapp.azure.com/. You need to register with your Microsoft account which is using the mail you had been used for registration. Click the "Login" button and use your Microsoft credentials and include also the security code which is mailed to you.
 
You can then browse studies or the library by selecting the corresponding icons in the top-bar.

**Documentation Portal**

The documentation is stored here: https://openstudybuilder.northeurope.cloudapp.azure.com/doc/. This contains a lot of documentation and easily browsable. This does not require any authentification.

**Neo Dashboard**

Via https://openstudybuilder.northeurope.cloudapp.azure.com/neodash/, the Dashboard can be used. Use the "SSO" sign in. If this is not available, then there are cookie issues. Please refresh the webpage by using no "cache", for example in Chrome you can use Ctrl + Shift and click R.

**Database Browser**

Via https://openstudybuilder.northeurope.cloudapp.azure.com/browser/, the Neo4j database can be browsed, e.g. by using Cypher for queries. You need to select single sign on (SSO) and then the browser will start. If the SSO is not available, then there are cookie issues. Please refresh the webpage by using no "cache", for example in Chrome you can use Ctrl + Shift and click R.

**Bloom**

Finally, https://openstudybuilder.northeurope.cloudapp.azure.com/bloom/ is available to access the bloom tool. You have to select SSO for login here as well. If the SSO is not available, then there are cookie issues. Please refresh the webpage by using no "cache", for example in Chrome you can use Ctrl + Shift and click R.

## Lokal docker installation

You can install the OpenStudyBuilder with or without test data locally. The easiest way is to use the docker instructions. For this you just need to follow the instructions on the readme files. You can also install the single components by following the instructions in the corresponding readme files within each sub-folder.

The current version 0.4 installation does include already test data and is very convenient to install. For **Windows** for example, make sure that you meet all pre-requisites that docker is running on the command line. Then you just need the following commands to setup, install and startup the OpenStudyBuilder:

```
cd c:\myInstallLocation
git clone https://gitlab.com/Novo-Nordisk/nn-public/openstudybuilder/OpenStudyBuilder-Solution.git OpenStudyBuilder
cd OpenStudyBuilder
docker compose up -d --build
```

You can also checkout the readme files in the subfolders to install individual components. If you also want to load additional CDISC terminology, you can follow along the "mdr-standards-import" [readme](https://gitlab.com/Novo-Nordisk/nn-public/openstudybuilder/OpenStudyBuilder-Solution/-/blob/main/mdr-standards-import/README.md). You might not want to load all CTs at once, but load just those you need.

Please note that Windows is not recommended, but it is working.

### Overview

On the local docker installation, the following tools are available. If you have not changed the port numbers, the tools will be available via the following links:

Tool | URL | Note
--|--|--
OpenStudyBuilder App | [http://localhost:5005/](http://localhost:5005/){target=_blank} | main application
Documentation | [http://localhost:5005/doc/](http://localhost:5005/doc/){target=_blank} | product related documentation
API | [http://localhost:5005/api/docs](http://localhost:5005/api/docs){target=_blank} | API documentation and running API calls
Consumer API | [http://localhost:5005/consumer-api/docs](http://localhost:5005/consumer-api/docs){target=_blank} | API documentation and running API calls for consumer API
Dashboards | [http://localhost:5005/neodash/](http://localhost:5005/neodash/){target=_blank} | Browser available NeoDash dashboards
DB Browser | [http://localhost:5001/browser/](http://localhost:5001/browser/){target=_blank} | Browser for underlying database

### Installation Experiences

If you want to follow along installation experiences on a Windows system, you can checkout the documentation on the separate [OpenStudyBuilder-Scripts](https://github.com/KatjaGlassConsulting/OpenStudyBuilderScripts/blob/main/doc/InstallationExperiences.md){target=_blank} repository from a user.

## Azure Deployment

You can also use the following instructions for an azure deployment. Please note that this setup is not using any security.

```bash
az login
az account set --subscription <name or id>
az group create --name myOpenStudyBuilderResourceGroup --location westeurope
az acr create --resource-group myOpenStudyBuilderResourceGroup --name myuniqueownacrname --sku Basic
az acr login --name myuniqueownacrname
git clone https://gitlab.com/Novo-Nordisk/nn-public/openstudybuilder/OpenStudyBuilder-Solution.git
cd OpenStudyBuilder-Solution
```

Then you have to update some configurations, add the following to docker-compose.yml:

- Line 7 -> image: myuniqueownacrname.azurecr.io/database
- Line 29 -> image: myuniqueownacrname.azurecr.io/api
- Line 56 -> image: myuniqueownacrname.azurecr.io/frontend
- Line 68 -> image: myuniqueownacrname.azurecr.io/documentation

Furhtermore replace in frontendfiles/default.conf:

- proxy_pass http://api:5003/; -> proxy_pass http://localhost:5003/;
- proxy_pass http://documentation:5006/; -> proxy_pass http://localhost:5006/;

Then finally create and deploy the solution:

```bash
docker compose build
docker compose push
az acr repository show --name myuniqueownacrname --repository database
az acr update --resource-group myOpenStudyBuilderResourceGroup --name myuniqueownacrname --admin-enabled true
az deployment group create --resource-group myOpenStudyBuilderResourceGroup --template-file openstudybuilder-template.json --parameters containerImageRegistryServer=myuniqueownacrname.azurecr.io containerImageRegistryUser=myuniqueownacrname
```

When prompted enter you access key to Azure container registry. Now the solution could be started using your Azure URL: http://#URL#:5005/.
