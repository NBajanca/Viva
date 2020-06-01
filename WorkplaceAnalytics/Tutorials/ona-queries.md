---

title: Organizational network analysis (ONA) queries 
description: Describes how to use Organizational network analysis (ONA) queries in Workplace Analytics to determine the "Influence" metric of individuals in your organization
author: paul9955
ms.author: v-pausch
ms.topic: article
localization_priority: normal 
ms.prod: wpa
---

# Organizational network analysis (ONA) queries

It’s frequently necessary to implement changes within organizations, whether this be introducing new procedures or rolling out new systems or technology. The traditional top-down method of using formal authority to drive change – perhaps starting with mass emails – it’s not always the most effective way. It might fail for any of several reasons including company culture, technical challenges, or problems with personality.   

Instead, a more successful strategy uses change agents -- influential, well-connected people who are positioned at various levels within the hierarchy, not just at the top. Beyond an organization’s formal hierarchy there also exist informal networks; individuals can exert influence within those networks and between them. The most influential people are the ones who have large personal networks – that is, above-average numbers of relationships with colleagues.

Therefore, to help implement change, it pays to know who the influencers are. The Workplace Analytics ONA query was designed for this purpose. It can help you find out who the best-connected people in the company are. It bases this determination on their collaboration characteristics.

This query type lets analysts use a metric called [Influence](../use/metric-definitions.md#organizational-network-analysis-ona-metrics). This metric is a score of how well connected you are in the company. It acts recursively: if you’re connected to others who are well connected, you benefit from their connections as well. After you learn who the best connected people are in the company, division, or other group, you can act on the likelihood that these people can connect effectively within or across groups and become efficient drivers of change. 

Also see [How Workplace Analytics calculates influence](#how-workplace-analytics-calculates-influence).

## Run a query to determine Influence

**Role:** analyst

1.	In Workplace Analytics, select **Analyze > Queries**.

2.	Under **Start custom query**, select **Network: Person**:

    ![ONA person query](../images/wpa/tutorials/person-ona-query.png)

3.	Select and change **Enter query name here** to a name, and then enter a description for the query.
4.	For **Group by**, select a time-grouping option: **Monthly** or **Aggregated**. If you choose Monthly, the query results will contain one row with data for each month in the time period that you chose. If you choose **Aggregated**, the query results will contain one row for the entire time period that you chose. 

    > [!Note] 
    > Currently, the only [meeting-exclusion rule](meeting-exclusions-intro.md) that can be used with an ONA query is the [Tenant default meeting exclusion rule](meeting-exclusion-concept.md#default-meeting-exclusion-rule). As you build your query, this rule is selected by default; it cannot be deselected.   

5.	Under **Select metrics**, select **Influence**. If you choose, you can also edit the **Display name** of this metric; the edited name will appear as a column name in the query results. (Other metric customization options are not available.)
6.	Under **Select filters**, select the groups of people for whom you want to see results. For example, to query about people in the engineering department or financial division, set this filter to **Domain Equals Engineering** or **Domain Equals Finance**.
7.	Under **Organizational data**, select the attributes that you want to appear in the results along with the metrics data. You can use these attributes to further summarize the results to create analyses that compare and contrast the collaboration of different groups in the organization.
8.	Select **Run**. The query takes a few minutes to complete. 
9.	On the **Queries > Results** page, the query status initially shows as **Submitted**. After the query status changes to **Succeeded**, you can view it or download it (as a .csv file).

> [!Note] 
> You can view, copy, export, and visualize query results in different ways for different query types. The topic [View, download, and export query results](../use/view-download-and-export-query-results.md) describes how to see and share results. For example, you can [view query results](../use/view-download-and-export-query-results.md#view-query-results), [download and import query results](../use/view-download-and-export-query-results.md#download-and-import-query-results), and [use an OData feed in Power BI](../use/view-download-and-export-query-results.md#get-a-link-for-an-odata-feed-to-use-in-power-bi).

## ONA query output

The following columns are included in the query results for ONA queries:

 * **Person ID.** De-identified ID number for the person represented in that data row.
  * **Date.** The start date of the aggregated output (for example, for the week of June 3rd to June 10th, the start date would be the 3rd. For a month, it's the first day of the month that your data encompasses).
 * **Person attributes.** Attributes about the person supplied through the latest organizational (HR) data upload.
 * **Metrics.** Any metrics that you include in the query. For more information, see [Metric definition: Influence](../use/metric-definitions.md#organizational-network-analysis-ona-metrics).


## How Workplace Analytics calculates influence

The terminology in the following description comes from graph theory. In graph theory, a "node" (also called a "vertex") is an object that can relate to other nodes -- other objects -- in the graph. This model becomes useful when we extend it to the workplace, where a "node" represents a person who has connections to co-workers and others.  

Influence indicates a node's potential influence on opinions of the network or an estimate of social status. Essentially, it uses the number and strength of connections coming into a node to rank the nodes. The values are between 0 and 1.

The most meaningful information to glean from Influence is the rank of the nodes. For example, assume that node A has an Influence of 0.6 and node B has an Influence of 0.3. You can accurately assume that node A is a more influential than node B, because node A ranks higher than node B. However, you cannot assume node A is twice as influential as node B because the values indicate a ranking or source of influence, not the amount of influence. The calculations for Influence use the relative collaboration time between individuals as the strengths of the connections for a person's influence measure.


## Related topics

[Metric descriptions](../use/metric-definitions.md)

[View, download, and export query results](../use/view-download-and-export-query-results.md)

[Best practices for influencers](https://review.docs.microsoft.com/en-us/Workplace-Analytics/tutorials/gm-influencer?branch=pas-sr-ona-flexible-query)
