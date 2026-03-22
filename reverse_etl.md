data we need into crm

## Product
    - Account Field: Sana Version. Perhaps, this should be a seperate entity in CRM, and can contain additional fields about each release version. 
    - Account Field: Installation Type => Custom, SaaS (or perhaps, we should think of more specific values)
    - CRM Entity: Success Plans (once those are in the product)
    - CRM Contacts: Sana User Accounts

## BC
- Ideally, BC is the single source of truth for all subscription data. 
- We should depcreate the existing subscription data we have in CRM and create a connection between BC and CRM
- This will then give us, on an account level: 
    - MCV
    - Contract End Date
    - Cancellation Deadline
    - Invoice Period

- In addition, it may be intersting to get invoice data into CRM as well.
- Note: The way we should connect a CRM record to a BC record is via a CRM Customer No. This is a ticket on the CRM roadmap. In BC, a customer may have multiple customer records. For example, if the billing entity changes, or they get acquired. SO ideally, the finance team is able to create and manage customer records in BC, while linking all subscriptions back to a single CRM customer. 
    - In other words, CRM is the SSOT for our customer records. BC is the SSOT for our subscription data. 

## Sphere and Start
- Ideally, both killed and merged into CRM completly. 



