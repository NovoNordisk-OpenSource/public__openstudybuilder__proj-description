# Cost Considerations {: class="guideH1"}

(created 2023-11-15) 
{: class="guideCreated"}

While the OpenStudyBuilder operates on an open-source model, it's crucial to acknowledge underlying expenses. Software-wise, excluding the Neo4j database, the OpenStudyBuilder utilizes open-source components. Although a Docker image housing a Neo4j database is available, it might not suffice for production settings. Additionally, operational costs arise when running on local machines, servers, or within cloud environments. Furthermore, setup, management, and ongoing maintenance demand dedicated resources.

## Hosting Expenses

For individual use, running the solution on a local PC might seem sufficient but poses risks such as potential crashes or resource constraints. Collaborative work often demands server or cloud hosting. Server maintenance and operational costs vary based on the chosen model and associated risks.

Cloud systems offer managed services but entail expenses influenced by resource usage, service agreements, and contract details. For instance, deploying the OpenStudyBuilder on Azure cloud services for regular usage might average around 650-800&#8364; per month, escalating to approximately 1200&#8364; for extensive development versions.

![OpenStudyBuilder Installation Opportunities](./img/info_costs1.png){ width="70%" }

## Software Costs & Neo4j Enterprise

Transitioning to a productive system may necessitate leveraging Neo4j's management functionality. Options include deploying Neo4j Enterprise on dedicated servers or opting for Neo4j Aura's managed database services, each with associated costs for essential services like backups, disaster recovery, and upgrades. 

Exploring Neo4j Aura, the cloud-based solution, reveals nuances in its pricing options. The free version may not meet the requirements due to node limitations. As an example, our public sandbox environment's configuration aligns well with the 'AuraDB Professional' package, priced at $129.60 per month. However, in a production environment, the 'AuraDB Enterprise' version might emerge as a more fitting choice, offering enhanced security features alongside its functionalities.

## Operational and Update Costs

Beyond explicit expenses, considerable resources are required for training, change management, data migration, and software integrations. Continuous updates, testing, and validation are recurrent tasks essential for ongoing development and productive releases.

## Collaboration, Enhancements & Add-Ons

Certain functionalities might not be available initially. Prioritizing specific features or developing custom tools may involve additional investment for collaboration or development. Modifying the default interface, for instance, incurs supplementary development costs.

## Community vs. Commercial Support

The community provides support, yet commercial services may be necessary. Interested parties can contact our contributors or preferred service providers. We are keen on supporting vendors to enable wider use of our tool.

## Summary of Costs

-	**Software**: Docker image incurs no cost; Neo4j Enterprise or Neo4j Aura involves fees.
-	**Hosting**: Varied expenses for server, cloud, or local hosting.
-	**Installation/Running**: Costs for training, change management, content management, data migration, software integrations, and update management.
-	**Development**: Resources required for ongoing development and enhancements.
