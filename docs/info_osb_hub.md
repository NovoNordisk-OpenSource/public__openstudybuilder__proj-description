# OpenStudyBuilder Hub (OSB-Hub)

The OpenStudyBuilder Hub (OSB-Hub) is a collaboration team under the umbrella of the CDISC Open Source Alliance (COSA). Our mission is to support the utilization and enhancement of the OpenStudyBuilder open-source tool. Here, we not only collect valuable feedback and use-cases but also actively run focused projects. Join us to drive innovation forward through both community engagement and project execution.

- Join us on Slack: [Invite](https://join.slack.com/t/osb-mdr/shared_invite/zt-2iwjqjg76-r0NW6pRH5GnGQQ~~izLc_A){target=_blank}
- Feedback on Use-Cases: [Discussions](https://github.com/cdisc-org/osb-hub/discussions/categories/use-cases){target=_blank}
- Checkout information: [Wiki](https://github.com/cdisc-org/osb-hub/wiki){target=_blank}

## Description

This [CDISC Open Source Alliance](https://cosa.cdisc.org/){target=_blank} (COSA) collaboration team is created to support the utilization and modification of the OpenStudyBuilder. 

![Project Logo](./img/OSB-Hub-Logo_150.png)

## Use-Case definitions

We've curated a list of [use-cases](https://github.com/cdisc-org/osb-hub/wiki/UseCases){target=_blank} awaiting your input in [discussions](https://github.com/cdisc-org/osb-hub/discussions/categories/use-cases){target=_blank} to set priorities and expand this list. Your votes help prioritize our work at OSB-Hub, guiding our efforts towards addressing the most critical needs. The results will feed into the OpenStudyBuilder project. Feel empowered to contribute additional use-cases and enrich existing ones with specific requirements. Engage in discussions to shape the future of OpenStudyBuilder according to community insights. Together, we'll chart the course for our upcoming trails.

## OpenStudyBuilder Hub Trails (OSB-Hub-Trails)

We organize focused projects, known as OpenStudyBuilder Hub Trails, where we collaborate to develop documentation and best practices for applying specific use cases in real-life scenarios. These efforts may include creating supporting tools, such as those for import processes, and specifying additional requirements and concepts for potential integration into OpenStudyBuilder.

## OSB-Trail-ControlledTerminology

Kick-off July 2024

Our first OpenStudyBuilder trail focuses on the management of controlled terminology (CT), encompassing CDISC and sponsor standards. Delve into critical questions such as how to seamlessly integrate with new CDISC CT versions? How to load or create sponsor terminology? What kind of additional attributes can I apply? What would I need additionally? How to use this downstream? How to deal with different versions?

Join the corresponding channel in [Slack](https://join.slack.com/t/osb-mdr/shared_invite/zt-2iwjqjg76-r0NW6pRH5GnGQQ~~izLc_A){target=_blank}!

**Status February 2025** 

A community member focus on the development of a user interface to manage import and export controlled terminologies. These activities are still ongoing and a first version might be available in Q1 2025. The specifications are discussed and communicated in our slack channel.

Furthermore, we had a deeper look into the available CT scripts. We identified some challenges where we are planning to solve some of those. One of this are a few discrepancies within different CDISC catalogs. We reported these back to CDISC. The CT needs also some more refactoring, which will happen within the OpenStudyBuilder team in Novo Nordisk. We also see that the upload scripts should ideally be refactored - this is on the to-do list, but needs priorization. 

## OSB-Trail-SystemEngineers

Kick-off January 2025

Our second OpenStudyBuilder trail focuses on the collaboration of system engineers working with OpenStudyBuilder (OSB). This group aims to unite professionals to share experiences, collaborate on deployment and installation strategies, exchange best practices for monitoring and DevOps, and explore integration opportunities with OSB.

Join the corresponding channel in [Slack](https://join.slack.com/t/osb-mdr/shared_invite/zt-2iwjqjg76-r0NW6pRH5GnGQQ~~izLc_A){target=_blank}!

**Our objectives:**

- Share knowledge on deploying and scaling OSB effectively.
- Discuss best practices for monitoring and DevOps tailored to OSB.
- Exchange experiences and solutions for integrating OSB with other systems.
- Build a network of experts to support and innovate within the OSB ecosystem.

**Status February 2025**

We had an initial discussion meeting on 16. December 2024 to checkout who would like to participate and discuss on focus areas.

**Deployments:** On 24.02.2025 we discussed about deployments including their challenges and solutions. Checkout the presentation [here](./presentations/2025-02-24-osb-hub-trail-deployments.pdf){target=_blank} and the summary [here](./presentations/2025-02-24-DeploymentWorkflows.pdf).

**APIs:** On 24.03.2025 we will have a session on APIs. You can join the meeting either via direct invite (please contact us in slack) or using the linkedIn event [here](https://www.linkedin.com/events/osb-trail-systemengineers-focus7300543836559208448/comments/){target=_blank}.

## Community

There are single community members providing additional guidance and support. These projects will be mentioned here.

### Neo4j Community Edition

The current default setup is using the Neo4j enterprise version which requires a license. It is recommended to use the enterprise version for productive environments. When you want to test or run the OpenStudyBuilder in a very small scale - you would be able to use the community version. Currently only the data migration scripts will not be working which could be overcome by using a different data migration strategy. You also have to be aware that consisency checks are not available in the community version among other features. Nevertheless, working with the community version is possible and expecting that you validate your output, e.g. in downstraem systems, there is no issue with using the community version.

To switch to the community edition, a few updates are required in the docker-compose file and some other files. Marius Conjeaud has provided a fork of the OpenStudyBuilder repository with the required changes. You can access the fork [here](https://gitlab.com/mariusconjeaud/OpenStudyBuilder-Solution-ce){target=_blank}.

### OpenStudyBuilder Load Tests

Marius Conjeaud has also provided a load test setup for the OpenStudyBuilder. Performance is a critical aspect. There had been tests setup in GitHub [here](https://github.com/mariusconjeaud/openstudybuilder-load-test){target=_blank}. These tests had been looking very promising, there is not much different on whether there are 20 or 200 studies on the database.

Of course the environment has to be considered. When working in a cloud when the data has to be transferred over the internet, the performance will be different. These tests had been performed on a local machine.