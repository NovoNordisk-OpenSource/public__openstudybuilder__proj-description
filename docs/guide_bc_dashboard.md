# Guide for Activity Dashboard {: class="guideH1"}

(created 2024-01-29 using v0.7.3 and dashboard as available in 0.8) 
{: class="guideCreated"}

## Activity Introduction

Additionally to the Application, a Neo4j Dashboard is available to browse and understand biomedical concepts which are the activities in the OpenStudyBuilder. Please check out the [guide for Biomedical Concepts](./guide_activity_concept.md) to get an understanding of the definition and usage of biomedical concepts for activities.

Within the OpenStudyBuilder application, you can define and see the activities in the "Library" -> "Concepts" -> "Activities" part.

![OpenStudyBuilder view of activities](./img/guide_bc_dash_06.png)

The activities are managed in groups and subgroups. Whereas the "Activity" defines all general attributes, the "ActivityInstance"  is the specific identification of the logical observation. This includes reference to context and qualifier values. For example, this includes references to ADaM BDS PARAM/PARAMCD or column name in ADSL, it also includes internal unique identification as well as internal topic code. This will enable unique identification of source data, representation in SDTM by several qualifiers, and representation in ADaM BDS by PARAMCD value.

The underlying data model documentation is available in GitLab and can be found [here](https://github.com/NovoNordisk-OpenSource/openstudybuilder-solution/tree/main/neo4j-mdr-db/model){target=_blank}. To understand the activities better you might want to look at the following visualizations from the OpenStudyBuilder data model. Please be aware that the models might be enhanced and evolve.

File | Description
-- | --
logical-model-high-level-activity-concept.graphml | High level Logical Model for Activity Concept Class
logical-model-activity-bc-new.graphml | Logical Model for Activities and Assessments (Concepts)
logical-model-activity-bc-new-nested.graphml | Logical Model for Activities and Assessments with nested information

## Activity Dashboard

The activity dashboard is an option to view the activities from a different perspective. Especially when working with biomedical concepts from the OpenStudyBuilder and others like the CoSMOS, it might be valuable to have a database closer access as the dashboard provides. When you have access to the OpenStudyBuilder sandbox environment, you can simply browse the dashboard online: [https://openstudybuilder.northeurope.cloudapp.azure.com/neodash/?](https://openstudybuilder.northeurope.cloudapp.azure.com/neodash/?){target=_blank}. You can also install the dashboard locally - instructions are available [below](#dashboard-in-local-environment).

The dashboard is organized in different tabs supporting different purposes. The first tab provides a quick overview. The next two tabs are designed to navigate the "Activity Lib" either via a top-down or bottom-up search. Then there is the option to get Activities to SDTM using a specifig implementation guide. As the CDISC collaboration with the CoSMOS initiative is very important, there is also a mapping of activities in the OpenStudyBuilder to the CoSMOS format and finally there is an overview of the activity usage in studies.

### Introduction / ReadMe

The first dashboard page gives an overview of activities, their grouping and the types including counting statistics.

![Screenshot of "ReadMe" tab from dashboard](./img/guide_bc_dash_05.png)

The first graphic (A) shows the "Groupings of Activities", which shows the available types and sub-types. Next to this, there are the numbers of activities and instances (B). An instance is the concrete form which is used in studies to observe something. The table for "Number of Activities and Instances by group and subgroup" (C) can be used to get an overview of the groups and subgroups whereas the table "Number of Activities and Instances by type and subtype" shows the overview with type and sub type (D).

### Activity Lib (search top-down)

The second tab allows you to look at activities from the top-down perspective. You can browse the class and sub-class followed by the group and subgroup. 

![Screenshot of second tab from dashboard](./img/guide_bc_dash_08.png)

After the description, there is a selection area where the activities can be filtered until the level of a subgroup (A). The "Number of activities" graph updates with the concrete numbers when you filter all activities (B). Depending on your selection, the "List of activities" shows then the actual activities matching your filter (C). When clicking one concrete activity, the details of this activity are displayed (D).

![Screenshot for selecting an activity](./img/guide_bc_dash_09.png)

We can see that the `PULSE RATE` has an associated domain, a test_name_code which consists of a code and a name, a unit_dimension and a standard_unit.

Below we can see the representation of that activity as in the graph database in the logical view or physical view (E). The complex model enables us to link all information. The following screenshot shows the logical view for `PULSE RATE`. 

![Screenshot for logical view for pulse rate](./img/guide_bc_dash_10.png)

The last part displays information about concrete activities instances. There is the selection part (F) and the display as logical view part (G). 

When we select for example `ALBUMIN` as activity, it could have three different instances depending on the purpose of activity collection. 

![Screenshot for ALBUMIN instances](./img/guide_bc_dash_11.png)

There is an instance for "Albumin Urine", where the specimen is "Urine", the second instance is for the specimen "Serum" and the third one is collected differently with the purpose for "AE Requiring Additional Data".

### Activity Lib (search bottom-up)

The search bottom-up tab enables you to search for a concrete activity or multiple activities in the search field (A). For the concrete activity the groups (B) and sub-groups (C) are displayed. Out of these groups you can select one (D) where the details are displayes in a list (E).

![Screenshot for bottom-up content](./img/guide_bc_dash_12.png)

### Activity to SDTM

The "Activity to SDTM" tab provides a detailed view of how activities are linked to specific SDTM items within a particular implementation guide. This feature allows you to visualize the relationship between activities and SDTM items, enhancing your understanding of the data structure.

![Screenshot for Activity to SDTM](./img/guide_bc_dash_13.png)

In this section, you can select the activity sub-group and the corresponding activity instance (A). Given that SDTM standards evolve over time, item definitions and structures may change. Therefore, you have the option to select a specific implementation version (B). Once selected, the mapping as defined in the implementation guide is displayed (C). Please note that for some activities, the mapping may not yet be available in the database. In such cases, the mapping will not be displayed until it is added.

### Activitiy in COSMoS format

In an effort to standardize and streamline the representation of Biomedical Concepts, CDISC initiated the Conceptual and Operational Standards Metadata Services (COSMoS) project in 2022. More details about this project can be found on their [homepage](https://www.cdisc.org/cdisc-biomedical-concepts){target=_blank}. As part of this initiative, CDISC has adopted the YAML format for displaying biomedical concepts.

Our dashboard has been designed to align with this standard. It can map the activities defined in OpenStudyBuilder into a valid COSMoS format, ensuring compatibility and interoperability with other systems that adhere to the same standard.

The following section presents an example of how the activity instance "TEMPERATURE" is represented in the COSMoS format.

```yaml
category:
  - Vital Signs
dataElementConcepts:
  - dataType: string
    conceptId: C44276
    exampleSet:
      - TEMPERATURE
    shortName: unit_dimension
    href: https://ncithesaurus.nci.nih.gov/ncitbrowser/ConceptReport.jsp?dictionary=NCI_Thesaurus&ns=ncit&code=C44276
  - dataType: string
    conceptId: C82587
    exampleSet:
      - C
    shortName: standard_unit
    href: https://ncithesaurus.nci.nih.gov/ncitbrowser/ConceptReport.jsp?dictionary=NCI_Thesaurus&ns=ncit&code=C82587
  - dataType: string
    conceptId: C25341
    exampleSet:
      - SKIN
    shortName: location
    href: https://ncithesaurus.nci.nih.gov/ncitbrowser/ConceptReport.jsp?dictionary=NCI_Thesaurus&ns=ncit&code=C25341
packageType: bc
definition: A measurement of the temperature of the body.
synonym:
  - TEMP
  - Temperature
resultScale:
  - Quantitative
conceptId: C174446
domain: VS
parentConceptId: C25206
shortName: Body Temperature
href: https://ncithesaurus.nci.nih.gov/ncitbrowser/ConceptReport.jsp?dictionary=NCI_Thesaurus&ns=ncit&code=C174446
packageDate: 2023-04-30
```

### Activities used in Studies

The last tab on the dashboard, 'Activities used in Studies', provides a view of where specific activities are utilized across different studies. This feature allows you to track the usage of activities.

In the selection box (A), you can choose one or more activities. Upon selection, the dashboard dynamically displays the studies in which these activities are used (B). 

![Screenshot for Activities used in Studies](./img/guide_bc_dash_14.png)

## Setup

### Dashboard in Sandbox

When you have access to the OpenStudyBuilder sandbox environment, you can simply browse the dashboard online: [https://openstudybuilder.northeurope.cloudapp.azure.com/neodash/?](https://openstudybuilder.northeurope.cloudapp.azure.com/neodash/?){target=_blank}.

### Dashboard in local environment

With version 0.8 of the OpenStudyBuilder, the dashboard will be deployed within the docker container and is accessible through [http://localhost:5007/](http://localhost:5007/){target=_blank}. With the OpenStudyBuilder version 0.9 we plan additionally to have a direct link from the web application to the dashboard.

The dashboard content is available as JSON file located in `\neo4j-mdr-db\neodash_reports`. For the released version 0.7.3 and earlier, this is not the latest version as deployed in the sandbox, but you can use this to check some cyper queries. 

### Create own dashboards (neodash.graphapp.io)

You can also design your own dashboard. 

**Investigate database name**: We need the name of the actual database. We can open the Neo4j database browser with this URL: [http://localhost:5001/browser/](http://localhost:5001/browser/){target=_blank}. By clicking the database symbol at the right, we can select different databases. There should be a database named `mdrdb-2024.01.05-08.52` or similar. This is the database name we need.

**Create new dashboars**: Now we can visit [http://neodash.graphapp.io/](http://neodash.graphapp.io/){target=_blank} and create a new dashboard. Here we can connect to our local database. If you have not changed the default settings for the docker setup, your port will be `5002`, the username `neo4j` and the password `changeme1234`. Make also sure to enter the correct default database which could be `mdrdb-2024.01.05-08.52`. If you want to connect to your local database, make sure to use `http://` prefix, as `https://` is likely not working.

![Screenshot for connecting to local database](./img/guide_bc_dash_01.png)

**Include content**: By clicking on the grey box, you can add additional elements to the dashboard. For example, you could create a "markdown" box to start with a simple description. Click the "settings" on the box to edit the type - for markdown you can simple edit the content and apply it by pressing "play". 

You can also create a table output. For this you can select the type "Table". Make sure to choose the correct database, which could be for example `mdrdb-2024.01.05-08.52`. Then in the coding box you can put the cypher query in. For example the following to get a simple table with all your compounds:

```cypher
MATCH (n:CompoundValue)
RETURN n.name AS `Compound name`
```

By pressing "play", the query is executed and the result (or the error message) is displayed. You can also resize the boxes and position them in any order. In this way, various dashboards can be designed.

**Tips**

To investigate which types of nodes are available, which connections are available and to work on complex cypher queries, you might want to access the neo4j database browser - in your local installation it's available via [http://localhost:5001/browser/](http://localhost:5001/browser/){target=_blank}. Make sure you select the correct database. You could click on a node label to see which nodes are available. By clicking on "CompoundValue", you would see different compounds. When you click on one node, you see the different attributes. Additionally, you can click on the "tree" to show all connections from this node to somewhere else.

![Screenshot of node propoerties](./img/guide_bc_dash_04.png)

If you're new to Cypher, don't worry! There are several tools available that can assist you in navigating this language. Tools like ChatGPT and Copilot are designed to provide guidance and suggestions, making it easier for you to construct and understand Cypher queries.

To gain a deeper understanding of the database structure, we recommend exploring the model documentation available in GitLab. You can find this under [`/neo4j-mdr-db/model`](https://github.com/NovoNordisk-OpenSource/openstudybuilder-solution/tree/main/neo4j-mdr-db/model){target=_blank}. This resource provides a detailed overview of the database model, helping you to understand how the data is organized and interconnected.

### Create own dashboards (neodash docker)

To install the neoDash tool locally, you can download for example this tool and start this within a container. You might want to use the port 5060 as below (the default 5005 is already used by the OpenStudyBuilder frontend):

```
docker pull nielsdejong/neodash:latest
docker run -it --rm -p 5060:5060 nielsdejong/neodash
```