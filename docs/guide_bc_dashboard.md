# Guide for Activity Dashboard {: class="guideH1"}

(created 2024-01-05 using v0.7.3) 
{: class="guideCreated"}

## Load dashboard in local envirionment

To load the dashboard into the local environment, a few steps are required

- Adopt the JSON file to use the correct "database" (search/replace)
- Use [http://neodash.graphapp.io/](http://neodash.graphapp.io/){target=_blank} to connect to the local neo4j database
- Load the JSON file and save this with a name 'My dashboard' (CASE sensitive)
- When loading [http://localhost:5007/](http://localhost:5007/){target=_blank} the dashboard will appear

First, we do have to update the database name with the one used in the current environment. We can open the Neo4j database browser with this URL: [http://localhost:5001/browser/](http://localhost:5001/browser/){target=_blank}. By clicking the database symbol at the right, we can select different databases. There should be a database named `mdrdb-2024.01.05-08.52` or similar. This is the database name we need.

The next step is to open the available dashboard which is located in `\neo4j-mdr-db\neodash_reports`. The name might be something like `Activity_Library_content_dashboard_OSB_v0_6_1.json`. We open this file for example in a simple editor and replace all occurences of `mdrdev1` with the name of the actual database, for example with `mdrdb-2024.01.05-08.52`.

Now we open the neodash web application under [http://neodash.graphapp.io/](http://neodash.graphapp.io/){target=_blank} to open our existing dashboard. First we need to create a "New Dashboard". Here we can connect to our local database. If you have not changed the default settings for the docker setup, your port will be `5002`, the username `neo4j` and the password `changeme1234`.

![Screenshot for connecting to local database](./img/guide_bc_dash_01.png)

When you click on the right pane, a menu with all dashboards opens up. You can click the `+` next to Dashboards to import the json file. Either copy and paste the content from the modified file or select the file itself. Now the dashboard is loaded.

You might receive a upgrade notification:

![Screenshot for upgrade notification](./img/guide_bc_dash_02.png)

When you do a refresh, you can start your existing dashboard by clicking "Existing Dashboard".

Now you can change the name of the dashboard to 'My dashboard' by clicking the Edit button next to the title. After clicking "stop editing", this is the new title. On the left title menu, click to the cloud icon to save this dashboard on your database. Now, when you open up the dashboard local URL, this dashboard will be shown: [http://localhost:5007/](http://localhost:5007/){target=_blank}.

![Screenshot for upgrade notification](./img/guide_bc_dash_03.png)

## Create own dashboards

You can also design your own dashboard. For this you can visit [http://neodash.graphapp.io/](http://neodash.graphapp.io/){target=_blank} and create a new dashboard. By clicking the grey box, you can add additional elements to the dashboard. You could for example create a "Markdown" box to start with a simple description. Click the "settings" on the box to edit the type - for markdown you can simple edit the content and apply it by pressing "play". 

You can also create a table output. For this you can select the type "Table". Make sure to choose the correct database, which could be for example `mdrdb-2024.01.05-08.52`. Then in the coding box you can put the cypher query in. For example the following to get a simple table with all your compounds:

```cypher
MATCH (n:CompoundValue)
RETURN n.name AS `Compound name`
```

By pressing "play" the query is executed and the result (or the error message) is displayed. You can also resize the boxes and position them in any order. This way various dashboards can be designed.

**Tips**

To investigate which types of nodes are available, which connections are available and to work on complex cypher queries, you might want to access the neo4j database browser - in your local installation it's available via [http://localhost:5001/browser/](http://localhost:5001/browser/){target=_blank}. Make sure you select the correct database. You could click on a node label to see which nodes are available. By clicking "CompoundValue", you would see different compounds. When you click one node, you see the different attributes. Additionally you can click the "tree" to show all connection from this node to somewhere else.

![Screenshot of node propoerties](./img/guide_bc_dash_04.png)

If you are not familar with Cypher, you might find ChatGPT or similar tools helpful.

To get a better understanding of the database structure, you might want to check out the model as documented in GitLab [`/neo4j-mdr-db/model`](https://gitlab.com/Novo-Nordisk/nn-public/openstudybuilder/OpenStudyBuilder-Solution/-/tree/main/neo4j-mdr-db/model?ref_type=heads){target=_blank}.