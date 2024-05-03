# DDF Context

(updated 2024-04-29) 
{: class="guideCreated"}

The TransCelerate Digital Data Flow project [(DDF)](https://www.transceleratebiopharmainc.com/initiatives/digital-data-flow/){target=_blank} aims to a future state of fully automated, dynamic, study start-up readiness. This automated end-to-end process is also the goal of the OpenStudyBuilder. In the context of the DDF, the OpenStudyBuilder can be seen as an SDR (Study Definition Repository), but with more capabilities than what DDF is containing in its first version.

The main advantage of DDF is the standard API which allows the connection of very different up- and downstream systems. All tools which support the DDF project through their standard APIs should also be usable with the OpenStudyBuilder, which supports the same APIs.

## DDF API Endpoint

Beginning with the OpenStudyBuilder version 0.9 which is expected to be released in Q2 2024 - the DDF API v3 endpoint is available which is implementing the USDM version 2.7.1. As of now (Mai 2024) it is already released in the sandbox environment and can be checked out [here](https://openstudybuilder.northeurope.cloudapp.azure.com/api/docs#/DDF%20endpoints){target=_blank}.

As the OpenStudyBuilder started before the DDF initiative and contains more metadata than the USDM model, it is currently only possible to export an OpenStudyBuilder study to the USDM format using the endpoint. 

![Screenshot of the DDF export of an OSB study](./img/info_ddf_01.png)


## 2022 Connectathon Content

During the DDF Connectathon in 2022, the OpenStudyBuilder team covered various aspects of the SDR and connections. We covered managing the Study Definition set-up with reference to data standards and showed a DDF API Adapter utilising SDR/USDM for integrations. Additionally, we demonstrated standards management, integration into Common Protocol Template (CPT) using a Word add-in tool and EDC integrations via various methods.

### OpenStudyBuilder as a DDF Compatible SDR

The first focus area demonstrated how the OpenStudyBuilder can be seen as DDF compatible SDR.

<iframe
  title="DDF-1 OpenStudyBuilder as SDR Solution"
  width=720
  height=405
  src="https://www.youtube-nocookie.com/embed/SB3AFJJQj-c"
  frameBorder="0"
  allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
  allowFullScreen
></iframe>

### Integration to Protocol and SDTM Study Design data

The second focus shows how protocol automation could work by using content directly from the OpenStudyBuilder.

<iframe
  title="DDF-2 OpenStudyBuilder for Standards and Protocol"
  width=720
  height=405
  src="https://www.youtube-nocookie.com/embed/rUOIwqVWGII"
  frameBorder="0"
  allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
  allowFullScreen
></iframe>

### ODM Study Definition solution

The last video shows the ODM export which enables EDC vendors to read this in to setup the study within the corresponding EDC system.

<iframe
  title="DDF-3 OpenStudyBuilder with EDC Integrations"
  width=720
  height=405
  src="https://www.youtube-nocookie.com/embed/gGYkZGjWprs"
  frameBorder="0"
  allow="accelerometer; encrypted-media; gyroscope; picture-in-picture"
  allowFullScreen
></iframe>