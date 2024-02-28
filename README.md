# Zoo-Database
Overview:
The Zoo Database aims to fulfill all the operational needs of a zoo, managing various aspects including animal details, visitor information, sales, employee records, and departmental functionalities.
 
Schema:
Tables:
amenity_sales: Records sales transactions for zoo amenities.
DATA:
Employee ID
Location ID
Sale Type
Sale Date
Sale Total
Sale ID - Primary key

animal: Stores information about zoo animals.
DATA:
Animal ID - Primary key
Name
Scientific Name
Common Name
Sex
Birth Date
Status
Location ID

department: Contains departmental details within the zoo.
DATA:
Department Number - Primary key
Department Name

employee: Manages employee records and details.
DATA:
Employee ID - Primary key
Phone Num
Department Number
Supervisor ID
Email
First Name
Last Name
Salary

enclosure: Stores information about animal enclosures.
DATA:
Location ID- Primary key
Enclosure Type
Capacity
Number of Occupants

feeding_pattern: Tracks feeding patterns of animals (linked to animal table).
DATA:
Animal ID
Meal
Portion
Days
Time

notification: Logs notifications and messages within the zoo.
DATA:
Message ID- Primary key
Title
Message
Recipient
Time

restricted: Manages restricted areas within the zoo.
DATA:
Location ID- Primary key
Close Date
Open Date

revenue: Records revenue and financial details.
DATA:
Total
Reciept Source
Reciept Number- Primary key
Date
Employee ID

ticket_sales: Tracks ticket sales information.
DATA:
Ticket ID- Primary key
Pass
Employee ID
Visitor Phone Number
Reciept Date
Reciept Total

visitor: Stores visitor details.
DATA:
Phone Number- Primary key
First Name
Last Name
Birth Date

zoo_user: Manages user accounts within the zoo.
DATA:
User ID- Primary key
Username
Password
Status
Role
Creation Date

zoo_user_role: Defines roles and permissions for zoo users.
DATA:
Role ID- Primary key
Role Name
 
Relationships:
feeding_pattern links to animal using Animal_ID.
Relationships exist between employee and department tables.
Further relationships are established between sales tables and respective entities.

 Roles:
Zoo Admin:
Can view/edit/and modify all pages inside the website
Zoo keeper:
Can view/edit/modify anima relatedl pages as well as receive notifications if needed
Visitor:
Limited view of the website

Triggers Overview:
These triggers enforce data integrity, implement business rules, or perform additional actions based on defined conditions.
 
Existing Triggers:
 PreventOvercrowding Trigger:
o    Semantic constraint: ensure that an enclosure doesn't allow more than its stated capacity, reflecting real world policies.
o    Event: AFTER INSERT, UPDATE on enclosure.
o    Action: Checks if the number of occupants exceeds the defined capacity and rolls back the transaction if the condition is met.
 
 UpdateLocationOnTransfer Trigger:
o    Semantic constraint: Every time an animal's status is updated to transferred, all zookeepers must be notified.
o    Event: AFTER UPDATE on animal.
o    Action: Updates location information and generates a notification to zookeepers regarding the animal transfer event.
trgUpdateEnclosureOccupantNum
Semantic constraint: when animal is added, moved, or removed, update the appropriate occupant number field(s)
Event: AFTER UPDATE, INSERT, DELETE
Action: when an animal is added or updated, update the appropriate occupant number fields. Do the same on delete.

trgPreventDisableAllUsers
Semantic constraint: ensure at least one admin account remains active. Note that this effectively only applies to the user-facing CRUD page; such users can be deleted (but not updated) directly from the database
Event: AFTER UPDATE
Action: if after the update, there are no user accounts with the admin role that are marked as enabled, rollback the transaction 

trgAfterAmenitySales
Semantic constraint: when a sale occurs or is removed, insert/remove the sale data into/from the revenue table
Event: AFTER INSERT, UPDATE, DELETE
Action: insert/remove the sale data into/from the revenue table, and prefix the saleid with “AMENSALES” to prevent conflicts

trgAfterTicketSales
Same as AfterAmenitySales but for ticket sales
Reports:
Feeding Report:
Report that joins the Animal and the Feeding Pattern tables and gives a report on what an animal is supposed to be eating that day based on a unique Animal ID
Ticket Sales Report:
The report generates a comprehensive list of tickets linked to a specific pass type and employee ID, accompanied by a summary of the total count of such tickets.
Revenue Report:
This report takes in data from both the ticket and amenity sales tables and gives a detailed view of each transaction within the specified date range. A user may select to view sales from a specific employee or all employees. The source of sales can also be chosen.
 
