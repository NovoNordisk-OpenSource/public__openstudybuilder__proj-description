# Biomedical Concepts & OSB Activity Concept {: class="guideH1"}

(created 2023-02-17) 
{: class="guideCreated"}

In the library part of the OpenStudyBuilder various kinds of concept definitions are available:

![OpenStudyBuilder Screenshot of the library part](./img/guide_ac_01.png)
{: class="imageParagraph"}

Figure 1: The OpenStudyBuilder Library Part
{: class="imageDescription"}
 
These standard concepts are used when specifying study metadata which allows a high degree of reusability and conformance checks. This article focusses on the "Activities" (Activity Concepts) which are like Biomedical Concepts (BCs).

First, we will give a brief overview of what a Biomedical Concept is and how OpenStudyBuilder Activity Concepts fit into the definition. Then we will focus on describing the use of the Activity Concepts in a study definition. Finally, we will share the conceptual model used for the Activity Concepts in the OpenStudyBuilder.

## Biomedical Concept (BC)

### Definition

One definition is provided by Sam Hume (CDISC)^[1]^:

> BCs address metadata gaps in the current CDISC standards. They provide the conceptual definitions supporting the existing CDISC Foundational Standards metadata. This conceptual metadata is necessary to generate operationally ready Data Elements (DE). These operational DEs represent the detail needed to create the dataset variable, and to get definitions and value level metadata needed to generate a Define-XML document.<br/><br/>A BC is a unit of knowledge created by a unique combination of characteristics. As noted above, BCs complement the existing standards, but omit the operationalization of the standards. That is, BCs exist independent of any given standards implementation, such as SDTMIG v3.2 or CDASHIG v2.0. A BC specifies an observation concept, or what should be observed for a specific subject assessment in a clinical study, but not how to capture the data or how to group observations together

Another definition has been provided by Dave Iberson-Hurst (data4knowledge)^[2]^:

> A Biomedical Concept is the recording, in data, of a single activity within a clinical study.

Armando Olivia provides the following definition  using the term Activities^[3]^:

> Study Activities may be observations, assessments, or administrative activities (informed consent, randomization).<br/><br/>Study Activity, defined as any activity associated with the planning, conduct, analysis, and interpretation of a study. We recognize different sub-types, such as study design activities (Arms, Epochs, Visits, etc.), administrative activities (informed consent, randomization), intervention activities (clinical observations, therapeutic interventions), analysis activities. One highly important type of study activity is Assessments, and they need to be added to the model.

This then requires a definition of an Activity within a clinical study, here we can use the definition from the CDISC Glossary^[4]^:

> An action, undertaking, or event, which is anticipated to be performed or observed, or was performed or observed, according to the study protocol during the execution of the study. 

In the OpenStudyBuillder, the activity concept is defined closer to the definition by Armando Olivia and broader than the above definitions by Sam Hume and Dave Iberson-Hurst. An activity concept in OpenStudyBuillder is made to support both the protocol specification (electronically) as well as the down-stream data flow (Forms, SDTM). An activity in the OpenStudyBuillder can be a clinical recording (like the definition by Dave Iberson-Hurst), but it can also be an activity performed during the study that is not leading to collection of data, for example the administration of study drug (like definition by Armando Olivia).

### Example

To get a better understanding of what a biomedical concept is, let's look at an example. We observe a clinical recording as:

```
Subject 101 had a weight of 76 kg on 01 JAN 2020 which is study day 1.
```

This information belongs to Vital Signs. The Vital Signs test (VS test code) is "WEIGHT" and the result is "76" with the needed unit "kg". In addition, we have the timing information with the date and a reference to the study starting day.

This full set of metadata constitute a Biomedical Concept.

![Biomedical Concept display for example information](./img/guide_ac_02.png)
{: class="imageParagraph"}

Figure 2: Biomedical Concept for Information
{: class="imageDescription"}

Or represented in a tabular format:

Item | property | value |type
-- | -- | -- | --
BC | identifier | Weight | Identifier
Topic | TEST | Weight | TOPIC
Result | value | 76 | Result Qualifier
Unit | value | kg | Variable Qualifier
Data of Collection | collection_date |  01 JAN 2020 | Timing

The value 76 is meaningful when it is defined in a Biomedical Concept together with its qualifiers. In the following we will use the term "a logical observation" for the above combined elements of information.  

In OpenStudyBuilder we use the term ActivityConcept for the implementation of a Biomedical Concept with the following definition (see also section: High-level Logical Activity Concepts Model):

!!! warning  

    TODO

> If the Activity Concepts relate to data collection, then the activity at the level resulting in a semantic logical observation, this can be depending on context and qualifiers having different identifications. If not related to data collection, then to a semantic specific activity. 
To get a detailed understanding of Biomedical Concepts, we recommend reading the detailed paper about “Biomedical Concepts” from Dave Iberson-Hurst.

> We differentiate two different activity concepts: a sematic logical observation and a semantic specific activity. If the activity is related to data collection, it belongs to the logical observation group, otherwise it’s a semantic specific activity. **please include two examples** 

## Usage of Activity Concepts

The OpenStudyBuilder has functionality to create an electronic "protocol". As a user you can define the study design, the visits and what is to be performed/collected at each visit (called Flowchart in OpenStudyBuilder, others may call it Schedule of Activities (SoA)). The Activity Concepts are the activities in the protocol flowchart (or SoA).

On a high-level, a study flowchart can be illustrated as in Figure 3. At a series of timepoint (within an arm, epoch and visit) as set of planned activities is scheduled to occur (the blue dots). Each of the blue dots, when expanding them (illustrated by the 'c'-dot) will have further details as we saw in weight the example above (result, unit).  
 
![Study Flowchart for Scheduled Activities](./img/guide_ac_03.png)
{: class="imageParagraph"}

Figure 3: Study Flowchart for Scheduled Activities
{: class="imageDescription"}

(Source: &#169; Dave Iberson-Hurst, Biomedical Concepts, A Treatise, 18-May-2022, version 0.3)
{: class="imageDescription"}

At protocol level the details of unit and other qualifiers are not needed, but it is important for the down-stream data processing like CRF and SDTM creation. At protocol level we will just display and refer to the identifier of the Activity Concepts.

### Define Activities for a Study

In the OpenStudyBuilder the Activity Concepts can be accessed via the Study Activities in the left menu. The first tab shows the list of activities. You can add the activities or collections to be performed on this view.

![Screenshot of Study Activities in OpenStudyBuilder](./img/guide_ac_04.png)
{: class="imageParagraph"}

Figure 4: Screenshot of Study Activities in OpenStudyBuilder
{: class="imageDescription"}
 
There are three different levels for activity concepts the user can select from: Activity Group, Activity Subgroup and Activity. In a later version it will also be possible to select on the Activity Instance level which is more detailed level. For example, an Activity=Glucose, you can have more detailed version depending on specimen (Activity Instance = Glucose Urine, Activity Instance = Glucose Serum, Activity Instance = Glucose Plasma). They are all grouped in/linked to the same Activity: Activity=Glucose.

Also, later version will allow for study level configurations such as disable parts of the activity definition that is not needed for a particular study (for example leaving out a unit that is not used or a whole qualifier, e.g., position if that is not important for the blood pressure measurement).

On the "Detailed Flowchart" tab, you can control what level of activity to be displayed in the protocol schedule of activities as well as when collections are to be scheduled.

![Screenshot to Manage Study Activities Display in OpenStudyBuilder](./img/guide_ac_05.png)
{: class="imageParagraph"}

Figure 5: Manage Study Activities Display in OpenStudyBuilder
{: class="imageDescription"}

### Visualize Activities (Protocol Flowchart)

On the "Protocol Flowcharts" tab, you can preview how the schedule of activities will be displayed in the protocol. When an activity concept is selected in the schedule of activities in a study it is possible to either select the exact activity instance if all details are known or just the activity itself if some details are still unclear (unit, specimen etc). Once the details of the activity have been clarified it will be possible to select the activity instance. The activity will often be the level of detail needed for the protocol schedule of activities. 
 
![Screenshot of Protocol Flowchart Display](./img/guide_ac_06.png)
{: class="imageParagraph"}

Figure 6: Protocol Flowchart Display
{: class="imageDescription"}


## References

- [1] CDISC 360: Using Biomedical Concept Metadata to Generate Case Report Forms and Dataset Definitions, PHUSE US Connect 2020, Paper TT06 by Sam Hume (CDISC), https://[www.lexjansen.com/phuse-us/2020/tt/TT06.pdf](www.lexjansen.com/phuse-us/2020/tt/TT06.pdf), accessed on 06.02.2023

- [2] Biomedical Concepts - A Treatise by Dave Iberson-Hurst (data4knowledge), Draft 0.3, 18th May 2022, [https://github.com/data4knowledge/biomedical_concepts/blob/main/docs/bc treatise/Biomedical Concepts Treatise.pdf](https://github.com/data4knowledge/biomedical_concepts/blob/main/docs/bc treatise/Biomedical Concepts Treatise.pdf), accessed on 06.02.2023

- [3] Thoughts on Medical Informatics, Blog by Armando Oliva, [https://aolivamd.blogspot.com/](https://aolivamd.blogspot.com/), accessed on 10.02.2023

- [4] CDISC Protocol Controlled Terminology, CDISC CT "C71473" for "Study Activitiy" [https://evs.nci.nih.gov/ftp1/CDISC/Protocol/Archive/Protocol%20Terminology%202017-12-22.html](https://evs.nci.nih.gov/ftp1/CDISC/Protocol/Archive/Protocol%20Terminology%202017-12-22.html), accessed on 10.02.2023