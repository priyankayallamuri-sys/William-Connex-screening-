# Walmart QI Automation Screening Challenge

## Task: Failed Inspection Grouping

You're helping digitize Walmart's Quality Inspection (QI) process across 37 stores. Your task is to build a backend logic and a frontend component that supports inspection tracking and escalation.

###  Apex Task
Create an Apex class that:
- Accepts a list of `Inspection__c` records
- Filters records where:
  - `Status__c = 'Failed'`
  - `Score__c < 70`
- Groups them by `Store_ID__c`
- Returns a `Map<String, List<Inspection__c>>`

###  Lightning Web Component (Bonus)
Build an LWC that:
- Displays the grouped inspection data in a table
- Includes a dropdown to filter by `Store_ID__c`
- Adds a button to fetch inspection standards via REST API (mock endpoint)
  
### Constraints
- Your Apex logic must be bulk-safe and governor-limit aware
- Your LWC must be reactive and follow best practices
- Include comments explaining your logic

## Submission Instructions
1. Fork this repo
2. Clone your fork locally
3. Add your Apex class and LWC code
4. Commit your changes with meaningful messages
5. Push your code to GitHub
6. Paste your repo link in the Google Form

 Evaluation Criteria
- Correctness and completeness
- Code readability and structure
- Use of Salesforce best practices
- Bonus: REST API integration and UI polish
