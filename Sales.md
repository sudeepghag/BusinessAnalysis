1. Required fields for Lead Conversion

Validation Rule Example:

	IsConverted
	&&
	OR(
		ISBLANK (Phone),
		ISBLANK (Email),
		ISPICKVAL (Rating, “”)
	)
  
2. An Account can only be created through Lead Conversion
   
	   ISBLANK ( LeadCreatedDate__c )

3. Customer Contacts can only be related to Customer Accounts

		RecordType.Id = ‘01234000000kL1i’ && NOT(Account.RecordTypeId = ‘02345000000kL1d’)

  Additional Use: If you are also using different Opportunity record types for each of your Account record types, 
  you can use the same type of Validation on the Opportunity object to keep data consistent.

4. One Open Opportunity at a time

		Account.NumberofOpenOpportunities__c > 1

5. Won Opportunities must have an Amount above 0:

	    OR(
	    ISBLANK(Amount),
	    Amount <= 0
	    )

6. Lost Opportunities must have a Lost Reason:

	    ISPICKVAL (StageName, “Closed Lost”)
	    &&
	    ISPICKVAL (LostReason__c ,””)

7. Contract Start Date must be prior to Contract End Date

		StartDate > EndDate
    
8. Order Products cannot be modified if Orders are “Activated”

		ISPICKVAL (Order.Status, “Activated”)

9.  

10.
