# CapstoneDB
Database for my Database portion of my CS Capstone course. I showcase my ability to complete CRUD operations & implement a security feature.

# CREATE

I created a golfer named John Johnson and insterted him into the database with the following code:

INSERT INTO dkstats (player, tournamentname, course, made_cut, pos, finish_DKP, total_DKP, DKdate, no_cut, Finish, sg_putt, sg_arg, sg_app, sg_ott, sg_t2g, sg_total) 

VALUES ('John Johnson', 'BMW Championship', 'Wilmington Country Club - Wilmington DE', 1, 1, 1, 100, '8/21/2022', 1, 1, 0, 0, 0, 0, 0, 0);

# READ

I read into the top 5 finishers (including ties) at each tournament and removed all others from the database. This removed thousands of rows and reduced my database to 250 total rows:

DELETE FROM dkstats

WHERE pos > 5 AND tournamentname IN (SELECT tournamentname

FROM dkstats

GROUP BY tournamentname)

# Update

I updated the golfer I created 'John Johnson' and inserted key stats into the table:

UPDATE dkstats

SET pos = 3, total_DKP = 123, sg_putt = 4.4, sg_arg = 3.7, sg_app = 2.1, sg_ott = 3.3, sg_t2g = 2.8, sg_total = 5.6

WHERE player = 'John Johnson';

# DELETE

I deleted rows that contained 'NA' to clear more clutter. This decreased the database to 213 rows:

DELETE FROM dkstats

WHERE Finish = 'NA';

I also deleted columns that I felt did not provide any value to the database:

ALTER TABLE dkstats DROP COLUMN made_cut;

ALTER TABLE dkstats DROP COLUMN finish_DKP;

ALTER TABLE dkstats DROP COLUMN course;

ALTER TABLE dkstats DROP COLUMN DKdate;

ALTER TABLE dkstats DROP COLUMN no_cut;

ALTER TABLE dkstats DROP COLUMN pos;

# SECURITY

Because I am using DB Browser SQLITE - I have some limited options for security measures. I decided to add password encryption to my zip file that will block anyone access without the password.
