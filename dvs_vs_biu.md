I don't have a good recomendation for how to divide work between the BVS and BIU. I am still lack the context of what the vision for the DVS is. 

IMO - there should be a brick wall between what the product needs to power features, and the what the operations team needs to run the company. The product team needs to optimize for stability and the company needs to optimize for speed and simplicty. I see these two competing priorities being at odds with each other.

The short term: 
- There are several data pipelines being run in databricks for our operational reporting. Saminda and the BIU will manage these, with the support of the DVS. 
- What this means is that: 
    - The BIU will monitor to ensure these run
    - They will be the first line of defense of one of the fails
    - They need support, they may need the DVS help to resolve. 
- New data, being offloaded to the data wearhouse, or the FiveTran blob storage account is still managed by Lalantha, nothing changes here. 
    - The only new offload that will be needed in the near future will be HubSpot.
- The DVS needs to build out a roadmap for when the other operational data sources will be managed in the DVS' data lake. Let's use CRM as an example:
    - DVS: Responsible for offloading this data into the datalake
    - DVS: Repsonsible for the basic transformations to make this data usable. For example, the account table is offloaded with out field values. So instead of seeing 'Netherlands' as a country name, we see 'abdke3w0ufda' as the countryid. One responsibility of the DVS will be adding the field values to the table. 
    - These first two steps are the bare minimum of what the DVS should do for the operations team. How much further the DVS goes to transform data is unknown to me. 

Once this CRM data is offloaded and transformed to the datalake, the BIU can then start to rebuild the data pipelines using the datalake as the main data source. This is important, but not urgent, as the existing data pipelines are currently working. We can deprecate the old pipelines as soon as the new ones are working as expected. 

Things to think about: 
- What types of transformations does the DVS do for the BIU?
    - To me, this is completely unclear. 
    - Tranforming data for the business it one of the core responsibilities of the data anlaysts, as this position is currently structured at Sana. THis enables the data analyst to consult with the business, and translate their needs into business tranformations. 
    - You have two paths you can take: 
        - DVS does all important data transformation. So any KPI that is being reported to the MT or ELT, is managed by the DVS. 
            - But then the DVS needs to clarity how they want to work with the analyst team. Does the analyst just turn into a product owner? Telling the DVS what they need buit?
        - The DVS creates the foundational data tables (so the account table with the field names), and then the BIU adds all the core business tranformations. 
            - But then I want the DVS to have a STRONG opinion on how to do these tranformations, and where we store them. Ideally, they are done in code. 

In scenario 1, I fear the DVS won't have time to prioritize what the BIU neesd and becomes the bottole neck. In scenario 2, the DVS is offering minimal value to the BIU (adding field names to accounts does not offer much value). And if the DVS doesn't have a strong opinion about where data transformations take place, then that opens the door for transformations to be spread around between the pbi report, pbi dataset, pbi dataflow, databricks, etc. 

What we need most is: 
1. A vision for what the DVS does? Where do you offer value? 
2. Practical boundaries for what the DVS does vs the BIU
3. A shared way of working, to ensure aliagnment. 
4. A roadmap for the DVS, so that the BIU can plan

