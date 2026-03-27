Saminda
1. data landscape and infrastructure
2. power bi datasets
3. legacy to clean up


Data 

Most of our data comes from SaaS applications. 

Applications
- CRM =>
    - All Account, Opportunity, Contact, NPS Surveys, Event Visits, CRM Tasks, Bizible Touchpoints
    - Some Emails, Phonecalls
    - Storage: Data Wearhouse
    - Offloader: FiveTran
    - Notes: 
        - When we replace Marketo, then we can remove Bizible Touchpoints.

- Marketo
    - All Marketing Forms, Emails and some Web Visits => To be replaced with hubspot this year. 
    Storage: Data Wearhouse
    - Notes: 
        - will be replaced this year with Hubspot. Move of this data can be archived for reporting purposes. 
        - We never did much with this data

- Outreach
    - Sales Emails and Phone Calls
    - Sotrage: FiveTran DataLake
    - Notes: This data is also synced to CRM, but the integration between Outreach and CRM is not perfect. 

- LinkedIn Ads
    - Advertising Campaigns via LinkedIn
    - Storage: FiveTran DataLake
    - Notes: connecting a LinkedIn Account to a CRM Account is not perfect. 

- Google Ads
    - Avertising Campaigns via Google
    - Storage: FiveTran DataLake

- Google Anlayitcs (GA4)
    - Web Traffic Data from Google
    - Storage: FiveTran DataLake

- Navision
    - Contracts and Financial Data
    - Storage: Navision server
    - Notes: 
        - You will not be in charge of the financial data, but you will need to use it. 
        - There is a freelance analyst that is building the financial datasets. His name is Jop. Ask Britta about what the roadmap looks like. 
        - We are replacing our Navision ERP with Business Central in the next few months. 


    The most important data is: 
        - CRM: Opportunity
        - CRM: Accounts
        - Outreach: Phonecalls
        - Outreach: Emails
        - CRM: Surveys


### Data Infrastructure
- Mostly, you will not be in charge of data infrastrcuture. In the medium term, the Data Value Services team will be in charge of the new datalake. But they are not ready yet. So in the short term, you will manage a few data pipelines. 
- There are 6 repos I am leaving you, these will be listed below. All follow the same structure: 
    1. Gather the data from either the databases or the FiveTran datalake
    2. Transform the data for the dataset using SQL executed using DuckDb
- If you don't know SQL yet, don't worry, I also didn't know any SQL when I started this job. Between AI and YouTube you will pick it up quickly. 
- You can execute these pipelines locally by changing the directory variable in the notebooks
- You can change between Prod and Dev by changing the variable in the project file. This just creates a mirror of the data in the 'Dev' folder of Azure Blob Storage. I created the ability to do this, and never really used it, but it's nice to have. 
- You'll notice that in the Bronze layer, I am just pulling data, there are minimal tranformations taking place there. The vast majority of the transformations are in the Silver and Gold layers. 
- I am not a data engineer. The reason we started doing this is because the data wearhouse was so slow, and didn't contain all the data I needed, hence this setup. 

Potential Improvements: 
- All fact tables need the same set of Account Dimensions. I am importing the accounts_silver table to get them. It may be easier to createa seperate accounts_dimensions table. This way, when you are doing a left join between your fact table and your accounts_dimensions, you can just select all dimensions. This is espeically nice when you need to add a new dimensions. For example: accounts_dimensions.*

### How to add a column
- Let's say we just deployed a new column to the account table in CRM, and now we need to report on it. 
- All new columns are automatically added to the database, and are available for you to use. 
- So to add this column to your data models, you would: 
1. Go to the accounts_etl repo
2. In the bronze/sql folder, add the new column to your accounts.sql file
3. In the silver/sql folder, add the new column to your accounts_silver.sql file

Once it's available in your accounts_silver table, it can be added to your other fact tables. 

### Depdencies between the _etl pipelines
- Mostly, these repos are self contained, with the execption of a few tables: 
1. accounts_silver
2. opportunity_silver
3. activities_silver

So just be aware if you are removing a column from one of these tables. 

 
### Power BI Datasets
- There is really only 2 datasets that you will need to manage: revenue_dataset and paidcampaigns_datset
- You'll notice that there is very little happening in pbi reports themself, just the final aggregations. 
- This is a pure constellation model. All Fact tables only have one layer of dimensions around them. 
- All metrics are grouped by topic, Accounts, Opps, CSM, etc. 
- Reporting Documentation: https://ismegroup.sharepoint.com/:x:/s/SalesOperations/EUGA7_aC4DdHhewzpp07wTIB6yo2DOEkJqlJBQGeLVLI0w?e=jdnMD8


### Power BI Dataflows
- You can depreciate all dataflows EXCEPT for the Commercial Targets dataflow. This is the dataflow that we use to transform the Commercial Targets excel sheet. Finance is in charge of this sheet. Coordinate with them. 

My suggestion, disable load on all the tables in the dataflow. Wait a week to see if anything breaks. If nothing, then proceed to delete. 

### Reports
- There are 4 main reports: 
1. Sales
2. CSM
3. Marketing
4. Paid Campaigns

There are other reports you can delete: 
1. RevOps
2. CSM MT

### Applications

Download
- PowerBi
- Tabular Editor 3
- VS Code or Cursur => Talk to Koen about what the DVS uses
- Azure Storage Explorer

Access: 
- CRM 
- Outreach
- LeadInfo
- LinkedIn Ads
- Google Ads
- Google Analytics (GA4)
- Azure DevOps
- Monday.com

Getting Started:
1. Data
    - Sharepoint: https://ismegroup.sharepoint.com/sites/SanaCommercialReporting
    - 
    - Sync Sharepoint Folder to your local machine: https://ismegroup.sharepoint.com/sites/SanaCommercialReporting/Shared%20Documents/Forms/AllItems.aspx?id=%2Fsites%2FSanaCommercialReporting%2FShared%20Documents%2FGeneral%2FPower%20BI%2FLive&viewid=3d897e5a%2D62e3%2D4057%2Dac1a%2D93b0a5abbc06
    - revenue_dataset and paid_campaigns
        - Download them. Refresh them. Publish them. 
    - Azure Devops: https://sanacommerce.visualstudio.com/Business%20Insights
        - repos => Everything with revops_
        - etl => Everything with _etl


Welcome Saminda!

Here's how to get started: 
1. Access the Power BI Workspace: https://app.powerbi.com/groups/2885432c-ba3f-4512-a78c-3fe2df18f65e/list?experience=power-bi
2. The pbix files are stored in this sharepoint: Sharepoint: https://ismegroup.sharepoint.com/sites/SanaCommercialReporting
3. Sync this folder to your local machine: https://ismegroup.sharepoint.com/sites/SanaCommercialReporting/Shared%20Documents/Forms/AllItems.aspx?id=%2Fsites%2FSanaCommercialReporting%2FShared%20Documents%2FGeneral%2FPower%20BI%2FLive&viewid=3d897e5a%2D62e3%2D4057%2Dac1a%2D93b0a5abbc06
4. There are two datasets to manage: revenue_dataset and the paid_campaigns dataset. 
5. Access our devops environment: https://sanacommerce.visualstudio.com/Business%20Insights
    - repos => Everything with revops_
    - etl => Everything with _etl
6. Download 

