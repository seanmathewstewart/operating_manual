Louise: 

- CRM: 
- Contact => Person connected to an Account
- Lead => Person not conected to an Account

- Marketo: 
- Lead => Person may or may be connected a Account
- Hubspot
    - Campaigns
    - What to bring over from CRM and Marketo
    - Where the SSOT for each field
    - Contact Cleanup

- Contacts
    - 135k contacts in CRM
    - 35k leads (may be overlap with the contacts)

Goal is to get this down to <120k => gives you 30k to grow into. 

We do this in 3 phases: 
1. Scan the email addresses. For invalid emails: 
    - If there was activity => deactivate the contact
    - If no activity => delete the contact
2. Deduplicate contacts
3. Delete Contacts

Questions: 
1. Do we need to sync data from marketo to hubspot? Can we just sync from CRM to hubspot?
2. What are we syncing over? => Contacts yes, but also leads? 

In terms of what to bring over to Hubspot: 
- Accounts
    - All
    - There are around 45k. Down from 250k 3 years ago. Account data quality is in a good state. 
- Contacts
    - Contacts from CRM
    - Maybe some leads from CRM => If they were generated in the last year and are not linked to a contact
- Form Fills
    - Since 2024
- Event Visits
    - Since 2024
- Email Sends? => Probably not

Questions: 
- What activities are you going to be managing in Hubspot? 
- Definetly yes
    - Marketing Emails
    - Form Fills
    - Event Visits
    - Campaigns
- Probably Yes
    - Unmasked Web Traffic => LeadInfo
    - Intent => Zoominfo, G2
- Need to think about it
    - Outreach => Sales Emails, Phonecalls, Tasks

Single Source of Truth (SSOT)
- We always need to be contientious of where the SSOT is for each field. So either: 
    - CRM is the SSOT and we push data into Hubspot
    - Hubspot is the SSOT and we push data into CR

- To make this easier, think about Account based fields and Contact based fields. For example: 
    - Account List is an Account based field, we do not need this at the contact level. There is is a relationship between account and contact, so it can be pushed from CRM Account to Hubspot Account and then that can be used to filter Hubspot Contacts. 

Account Based Fields => CRM pushes to Hubspot
- Account List => Top 25, TAL, SOM, TAM
- Sana Relationship Type
- Bow Tie Stage (WIP)
- Account Country, Territory, Demand Center
- Parent and Ultimate Parent Account
- ERP System => Although, we may want a two way sync here for form fills
- Industry Classification
- Business Type
- Business Activity
- Revenue Range
- NAICS Code
- Address - street, postal code, etc
- Sana Version
- Installation Type
- Contract Start Date
- Contract End Date
- Account Nurture Reason
- SCC Bucket

Contact Based Fields => CRM pushes to Hubspot
- Contact Type

Account Base Fields => Hubspot Pushes to CRM

Contact Based Fields => Hubspot Pushes to CRM