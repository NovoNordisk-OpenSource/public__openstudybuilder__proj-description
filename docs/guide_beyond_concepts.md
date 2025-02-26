# Beyond concepts {: class="guideH1"}

(created 2025-02-21) 
{: class="guideCreated"}

The activity concepts as explained in the corresponding [guide](./guide_activity_concept.md) goes beyond the usage of the definition for the Schedule of Activities. The concept is a core part of the linking of required information to enable and trace the stream from defining an activity in the protocol, through a data specification which can then be used in a concrete data collection, this will go into a concrete location in the data model(s) and can then later on be linked up to analysis results.

This documentation will go into the details of the current linkage and the concept for synchronization and downstream utilization in a specific EDC system (Veeva EDC).

## Linking vision

The idea is to create and utilize a connecting flow - define once and use many times!

The core elements are to be linked together:

- Protocol definition
- CRF utilization
- EDC specification
- SDTM definition
- ADAM definition

The activities, which are for example any kind of laboratory tests, build the base for the linkage. The following example shows how it could be envisioned in general. 

![Linking All Together - High Level Vision](./img/guide_bc_01.png)
{: class="imageParagraph"}

Figure 1: Linking All Together - High Level Vision
{: class="imageDescription"}

In the first place, there is an activity with a specific meaning, for example "Bilirubin". This activity belongs to a group and subgroup - in the example it is a "Laboratory Assessment" belonging to the "Urinalysis". For the **protocol**, this is the information required. 

For the **data specification**, this information is not sufficient. Even though there is a good understanding on what should be done in the study, there are still different ways how to collect and where it should go into. For the "Urine Bilirubin" activity, we could collect this as concrete numerical values or just collect the category (e.g. "normal", "high", "low"). To be specific, we define an activity instance.

This activity instance is a very concrete item. For this we could store many **connecting information**:

- To which section of M11 does this activity belong
- Concrete CRF location (Form, ItemGroup, Item), sometimes even multiple items, as a test often comes as a parameter value and unit
- Expected mapping to a data model (in this case SDTM) including the various variables and additional depending variables and values
- Associated codelists and only specific codelists values (the "UNIT" codelist contains just very few units which are applicable to the concrete activity)
- Associated official CDISC Biomedical Concepts

When having this definition available - for a concrete study, the protocol activities could be selected and later on decided on the concrete data specification. With just these two selections and all the standard mapping done in the background, it's possible to utilize this downstream to define the corresponding CRF items and see already the mapping to the SDTM variables.


## Current Mapping Implementation

In the end, the mapping is a bit more complex having specific relationships of types. The following visualization shows the current implementation planning and status of the linking of the activities to the concrete data specification and beyond.

![Linking all Together - Current Mapping Implementation Example](./img/guide_bc_02.png)
{: class="imageParagraph"}

Figure 2: Linking all Together - Current Mapping Implementation Example
{: class="imageDescription"}

What is important to notice is the differentiation between an "Activity" and an "Activity Instance". The activity is the general definition and used in the protocol, whereas the instance is the concrete definition of the data specification and the mapping to the data model(s) and beyond.

As an example, we could have a look at the "Bilirubin" activity. This could go into different groups and subgroups - concretely into:

- Group: "Laboratory Assessment" - Sub-group: "Urinalysis"
- Group: "Laboratory Assessment" - Sub-group: "Biochemistry" 
- Group "AE Requiring Additional Data" - Sub-group: "Laboratory Assessment"

![Activities and Activity Instances in OpenStudyBuilder](./img/guide_bc_05.png)
{: class="imageParagraph"}

Figure 3: Activities and Activity Instances in OpenStudyBuilder
{: class="imageDescription"}

Then there are concrete instances which build the data specification. These could be numeric values or categories and have additional specification each.


## Veeva Integration High Level Overview

We are working on integrating the Veeva EDC System with the OpenStudyBuilder. The following high-level overview shows the main idea.

![High Level Overview of Veeva EDC Integration Plans](./img/guide_bc_03.png)
{: class="imageParagraph"}

Figure 4: High Level Overview of Veeva EDC Integration Plans
{: class="imageDescription"}

**In short** - the currently plan is the following:

- Maintain CRF Forms, ItemGroups and Items in Veeva EDC
- Synchronize CRF objects to OpenStudyBuilder (keep linking information)
- Select activity instances in Schedule of Activities for timepoints (which are linked to CRF objects)
- Create JSON file to call Veeva API to setup a Veeva EDC study which copies the corresponding forms and elements from the library
- Use this for VAL and PROD to have the study setup in Veeva EDC

**Explanation** 

In the OpenStudyBuilder the CRF relevant information is defined in the library module in Forms, ItemGroups and Items. The Veeva EDC System contains also a CRF Library module storing the same. The idea is to have a synchronization job to keep both libraries containing the same information, containing linkage information in OpenStudyBuilder. Due to the limitations of the current version of the Veeva API, the current plan is to maintain and update the form information within the Veeva system and create the corresponding objects in OpenStudyBuilder via an automation job.

A futher step is required to update and maintain the data specifications. For activities which are rough concepts, we need to define activity instances - which is a concrete definition of the data specification. This contains next to the final SDTM location for example additionally the form, item and item group links. This is typically done by a standards function.

On study setup, an activity is selected for the schedule of activities which is used in the clinical protocol. Then these activities are further fine tuned with selecting the activity instances. By selecting the activity instance, the linkage of a selected activity and the corresponding required CRF elements is available.

This specification can now be used to generate a very specifig formatted JSON file, when can then be consumed by the Veeva API to setup the study in Veeva EDC. We are working on a process (robot), to setup the Veeva EDC study database:

- Create Study Master
- Create Event Group Definitions
- Create Event Definitions
- Copy Form Definitions from the Veeva CRF Library 
- Create Schedule

This is then checked in the Veeva EDC system and will then be used for the study setup in VAL and PROD.

## Veeva Integration Detailed Plan

Actually, to see the details of the elements and how this is all linked together, a more detailed view is required. The following section describes additional details. A high level overview is shown in the following figure.

![Detailed Overview of Veeva EDC Integration Plans](./img/guide_bc_04.png)
{: class="imageParagraph"}

Figure 4: Detailed Overview of Veeva EDC Integration Plans
{: class="imageDescription"}