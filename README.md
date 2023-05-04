Download Link: https://assignmentchef.com/product/solved-csci466-assignment-9-transactions-in-mariadb
<br>
The purpose of this assignment is to experiment with the behavior of transactions using a MariaDB database. You will need to use <em>morethanone </em>MariaDB session for these to work. To do this, just open up two separate putty sessions to turing or hopper and log into MariaDB on each of them. Use the same name for the output file for all of the sessions – T assign9out.txt – so that the output from all of your sessions ends up in the same file. When znnnnnnn is used, replace it with your own z-id.

<h1>Part I – The Power of COMMIT</h1>

1) Start your first MariaDB seesion, issue the following SQL queries:

T assign9out.txt

USE znnnnnnn;

CREATE TABLE Fall( pk INT PRIMARY KEY, data CHAR(15));

START TRANSACTION;

INSERT INTO Fall

VALUES(1, ‘dataA’);

INSERT INTO Fall

VALUES(2, ‘dataB’);

INSERT INTO Fall

VALUES(3, ‘dataC’);

<ul>

 <li>Start your second MariaDB session, and run the following SQL queries in it.</li>

</ul>

T assign9out.txt

USE znnnnnnn;

SELECT * from Fall;

<strong>Question1.2</strong>) What is the result of running the SELECT statement. Why?

<ul>

 <li>In that second session, run the following:</li>

</ul>

INSERT INTO FalI VALUES(4, ‘dataD’);

INSERT INTO Fall VALUES(5, ‘dataE’);

<ul>

 <li>Switching back to the first MariaDB session, issue the following queries:</li>

</ul>

COMMIT;

SELECT * FROM Fall;

t exit;

<ul>

 <li>Switch back to the second MariaDB instance, and run the following queries:</li>

</ul>

SELECT * FROM Fall;

t exit;

<strong>Question1.5</strong>) What is the result of the SELECT statement above?

<h1>Part II — The Power of ROLLBACK</h1>

<ul>

 <li>Start another MariaDB session, issue following MariaDB statements:</li>

</ul>

T assign9out.txt

USE znnnnnnn;

START TRANSACTION;

DELETE FROM Fall WHERE pk = 3; SELECT * FROM fall;

<ul>

 <li>Then</li>

</ul>

UPDATE Fall

SET Data = ‘changed’ WHERE pk = 2;

<ul>

 <li>Then</li>

</ul>

UPDATE Fall

SET Data = ‘changed 2’ WHERE pk = 4;

<ul>

 <li>Then</li>

</ul>

INSERT INTO Fall VALUES(6, ‘dataF’);

SELECT * FROM Spring;

<strong>Question2.4</strong>) What is the result of the SELECT statement, and why?

<ul>

 <li>Issue the following MariaDB statements:</li>

</ul>

ROLLBACK;

SELECT * FROM Fall;

<strong>Question2.5</strong>) What is the result of the SELECT statement, and why?

t exit;

<h1>Part III: Be Aware of Deadlock</h1>

Using another two sessions of MariaDB, do the following in the order specified: 1) In session 1,

T assign9out.txt

USE znnnnnn; START TRANSACTION;

<ul>

 <li>In session 2,</li>

</ul>

T assign9out.txt

USE znnnnnn; START TRANSACTION;

<ul>

 <li>In session 1,</li>

</ul>

UPDATE Fall

SET data = ‘data1A’ WHERE pk=1; 4) In session 2,

UPDATE Fall

SET data= ‘data2B’ WHERE pk = 2;

5) In session 1,

UPDATE Fall

SET data = ‘data5E’ WHERE pk = 5; 6) In session 2,

UPDATE Fall

SET DAta = ‘data12B’ WHERE pk = 1;

<strong>Question3</strong>) What happened here?

<h1>Notes</h1>

There may be typos in these statements. If there is a syntax error, fix it. These errors were made to encourage you to pay close attention, and to type the statements in yourself as practice.