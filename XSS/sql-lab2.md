Description 
2.	% ‘ UNION SELECT 1 , @@VERSION #

HOW THIS WORK:
•	% ': The % is a wildcard, but the ' (single quote) is the most important part. It tells the database: "The search for the ID ends here."
•	UNION: This tells the database to run a second query and attach the results to the first one.
•	SELECT 1, @@version: This is your secret query.
o	Since the original query wanted two things (first_name and last_name), you must provide two things.
o	1 fills the "First name" slot.
o	@@version fills the "Surname" slot with the database's version number.
•	#: This is the "comment" character. It tells the database to ignore everything after it. This deletes the final ' that the developer originally put in the code, preventing a syntax error.
proof of concept
![ sql-lab2](Picture2.png)
