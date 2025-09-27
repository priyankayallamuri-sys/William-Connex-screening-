# Walmart QI Automation Screening Challenge 5
Walmart stores submit daily inspections. Failed inspections must be escalated based on dynamic compliance rules, which vary by region, store type, and severity. These rules are maintained by business users via Custom Metadata. The system must support bulk processing, retry logic, and audit logging — all while staying within governor limits.

Challenge Overview

Objects:

• `Inspection__c`• Fields: `Store__c`, `Region__c`, `Severity__c`, `Status__c` (Passed/Failed), `Store_Type__c`, `Escalation_Status__c` (Pending, Escalated, Failed)

• `Escalation__c`• Fields: `Inspection__c`, `Escalation_Level__c`, `Escalated_By__c`, `Escalation_Reason__c`, `Retry_Count__c`, `Audit_Log__c`

• `EscalationRule__mdt` (Custom Metadata Type)• Fields: `Region__c`, `Store_Type__c`, `Severity__c`, `Escalation_Level__c`, `Auto_Escalate__c`, `Notify_Manager__c`, `Escalation_Reason__c`

Task

Write a bulk-safe Apex class that:

1. Accepts a list of failed `Inspection__c` records
2. Matches each inspection to a rule in `EscalationRule__mdt` using `Region__c`, `Store_Type__c`, and `Severity__c`
3. Creates `Escalation__c` records with correct `Escalation_Level__c` and `Escalation_Reason__c`
4. If `Auto_Escalate__c = false`, skip escalation and log reason in `Audit_Log__c`
5. If `Notify_Manager__c = true`, simulate sending a notification (use `System.debug`)
6. Handles failures using `Database.SaveResult[]` and retries failed records using `Queueable` Apex (max 2 retries)
7. Updates `Escalation_Status__c` on `Inspection__c` accordingly
8. Logs total escalations per region using `System.debug`

📦 Bonus (Optional)

• Create a helper class `EscalationRuleService` to abstract metadata lookup
• Create a test class with 90%+ coverage, including edge cases
• Include governor-safe strategies in comments
• Document assumptions and trade-offs in a README

Evaluation Criteria

Skill Area	Weight	
Metadata-driven logic	25%	
Bulk-safe Apex & DML	25%	
Retry logic & async handling	20%	
Audit logging & error handling	15%	
Code clarity & documentation	15%	
