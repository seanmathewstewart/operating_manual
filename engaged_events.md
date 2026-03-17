Issues: 
1. We want to label some events as being 'engaged events' 
- Solution: Event => New Field: Event Type => Self-hosted Event

Event Type field: 
- Events - Online Partner Event	500000018
- Events - Online Tradeshow	500000016
- Events - Online User Group	500000019
- Events - User Group	100000016
- Events - Online Self Hosted Event	500000017
- Events - Partner Event	100000015
- Events - Partner Webinar	100000001
- Events - Self Hosted Live Event	100000003
- Events - Tradeshow	100000012
- Events - Webinar	100000014

2. Does the list contain only the self-hosted event? or the entire event? => Iris\

3. Iris' list contains 46 visits, but the crm event visits only contains 26

We have a excel sheet with: 
- Event name => Always
- Name => Always
- Email => Always
- Notes => Always
- Score => Hot, Warm or Cold
- Country*
- Companies*


We need a workflow that does the following: 
1. Step 1: Match the email address to our contact database.
=> If it exists, create the event visit
=> If it doesn't exist, move to the next step
2. Step 2: Match the domain to the  
=> If it exists, create a contact under this account
=> then create an event visit for this contact
3. Step 3: Since both the contact and the account don't exist then:
=> Create the account
=> Create the contact
=> Create the event visit

At the end of this process, we expect that the number of event visits matches the rows in the excel file. 

Problems: 
1. What information do we use to create the account? => All we have is domain
2. Domains are not perfectly unique and I can't always assume country. Which domain do I match to if multiple exist?

Potential Solutions: 
1. Leverage Zoominfo API


Work around: 
1. Bulk create appointments with the sheet Iris gave us
2. Match to accounts




