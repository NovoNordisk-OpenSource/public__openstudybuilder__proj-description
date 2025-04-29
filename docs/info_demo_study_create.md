# Study Creation Demonstration {: class="guideH1"}

(created 2025-04-29 using v0.14)  
{: class="guideCreated"}

This demonstration provides a step-by-step guide on how to create a study. For this purpose, we can use the **CDISC Pilot Study** as an example. The corresponding **clinical protocol** is available [here](https://wiki.ihe.net/images/4/47/Lzzt_protocol_redacted.pdf).  Alternatively, we can utilize the **USDM (Unified Study Definitions Model)** representation of the study. An example of the USDM 3.0 representation of this protocol is available. The **Excel USDM** file, created by data4knowledge, can be accessed [here](https://github.com/data4knowledge/study_definitions_workbench/tree/main/docs/examples/Excel) (file dated 12 November 2024).  


## Create Study

To begin, we need to create a new study that will belong to a project specific to a clinical program. The study requires a **study number** and an **acronym**, both of which can be customized. By default, the study number has a maximum length of 4 characters, but this can be adjusted in the **Settings** menu (accessible from the top-right corner).

We will create a new study with the following details:

- **Project**: CDISC DEV
- **Study Number**: 6708
- **Acronym**: LZZT

![Animation - Create a New Study](./img/demo/info_demo_sc_10_create_study.gif)

## Manage Study 

The **Manage Study** view allows you to maintain its versions, subparts, protocol versions (planned for future updates), and applicable data standards. Core attributes such as the study name, acronym, clinical program, and project are displayed to show the study's context.

In the **Study Status** area, you can lock the study to create a new main version or unlock it to enable editing. This feature ensures proper version control and traceability. For complex studies, multiple subparts can be managed through the **Study Subparts** area. As an example, many Phase 1 studies utilize subparts due to the complexity of their schedules of activities.

Although protocol version management is not yet implemented, it is planned for future updates. 

Another aspect of study management is defining the applicable standards. The **Data Standards Versions** section allows you to link controlled terminology and other standards from specific version to the study. Controlled terminology typically involves a combination of a specific CDISC standard version and a corresponding sponsor standard version for packages like SDTM, ADaM, or CDASH. These standards are expected to be managed in the library and can be selected as needed. This linkage impacts on the concrete terminology used as the linked version is fixes the values.

The **Dictionaries** and **Data Exchange** standards are also intended to link to specific versions, but this functionality is still under development. 

![Animation - Manage Study](./img/demo/info_demo_sc_20_manage_study.gif)

## Define Study

The most important section to create the study content is the **Define Study** section. 
