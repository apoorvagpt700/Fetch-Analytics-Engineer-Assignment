# Fetch-Analytics-Engineer-Assignment
Fetch Rewards Coding Exercise - Analytics Engineer

### First: Review Existing Unstructured Data and Diagram a New Structured Relational Data Model

Uploaded the new structured relational data model as ERD.pdf file in this repository.
There are 5 tables in ERD: 
1. users - Primary key is userId. UserId identifies unique record in users table. This one is generated from users.json file.
2. brands - Primary key is brandId. brandId identifies unique record in brands table. cpgOid is foregin key and it establishes a link to cpgOid in cpg table. brandCode is foregin key and it establishes a link to brandCode in receiptItems table. This one is generated from brands.json file.
3. cpg - Primary key is cpgOid. cpgOid identifies unique record in cpg table. This one is also generated from brands.json file.
4. receipts - Primary key is receiptId. receiptId identifies unique record in receipt table. userId is foregin key and it establishes a link to userId in users table. This one is generated from receipts.json file.
5. receiptItems - Primary key is combination of receiptId and partnerItemId. receiptId and partnerItemId identifies unique record in receiptItems table. receiptId is also a foregin key and it establishes a link to receiptId in receipts table. brandCode is also a foregin key and it establishes a link to brandCode in brands table. This one is generated from receipts.json file.

Relationships: 
1. users to receipts : 1 to Many - 1 userId can have 0 to many receiptIds and 1 receiptId can have only 1 userId
2. cpg to brands: 1 to Many - 1 cpgOid can have 1 to many brandId and 1 brandId can have only 1 cpgOid
3. brands to receiptItems: 1 to Many - 1 brandId can have 0 to many receiptIds-partnerItemId and 1 receiptIds-partnerItemId  can have only 1 brandId
4. receipts to receiptItems: 1 to Many - 1 receiptId can have 1 to many receiptIds-partnerItemId and 1 receiptIds-partnerItemId can have only 1 receiptId

The new structured ERD model is normlaized, meaning that the data is organized to reduce redundancy and improve data integrity in following ways:
1. 1NF - All columns contain atmoic values, meaning individual unit of data
2. 2NF - All non key attributes are dependent on primary key in all tables
3. 3NF - All non key attributes are independent of each other

Removed the redundant columns like category and categoryCode from brands table in order to maintain the normlaization of the model.
