create database rental_db;

CREATE TABLE `Student` (
  `Student_ID` int NOT NULL UNIQUE,
  `First_name` varchar(255),
  `Last_name` varchar(255) NOT NULL,
  `Age` int NOT NULL,
  `City` varchar(255) NOT NULL,
  `contact_number` BIGINT NOT NULL UNIQUE ,
  PRIMARY KEY (`Student_ID`)
);

CREATE TABLE `students_search` (
  `search_id` INT NOT NULL AUTO_INCREMENT,
  `student_id` INT NULL,
  `location` VARCHAR(255) NULL,
  `room_type` VARCHAR(45) NULL,
  `search_time` DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `move_date` DATE NOT NULL,
  `parking` BOOL NOT NULL,
  `Disabled_access` BOOL NOT NULL,
  `Furnished` BOOL NOT NULL,
  PRIMARY KEY (`search_id`),
FOREIGN KEY (`Student_id`) REFERENCES `Student`(`Student_ID`)
);


ALTER TABLE students_search
ADD maxRent int;
ALTER TABLE students_search 
ADD still_seeking BOOL DEFAULT 1;


CREATE TABLE `RENTAL_ADDRESS` (
  `Home_id` int NOT NULL AUTO_INCREMENT,
  `location` Varchar(255),
  `parking` BOOL NOT NULL,
  `Disabled_access` BOOL NOT NULL,
  `Number_of_Rooms` int,
  `No_of_toilets` int NOT NULL,
  PRIMARY KEY (`Home_id`)
);

ALTER TABLE rental_address
ADD Furnished BOOL;

ALTER TABLE rental_address
ADD landlord varchar(255) NOT NULL ;

use rental_db;
CREATE TABLE `Rooms` (
  `Room_id` int NOT NULL AUTO_INCREMENT,
  `Home_id` int NOT NULL,
  `Roomnumber` int NOT NULL DEFAULT 1,
  `Room_type` varchar(255),
  `RENT` Int NOT NULL DEFAULT 300 ,
  `Disabled_access` BOOL ,
  PRIMARY KEY (`Room_id`)
);
ALTER TABLE rooms
ADD Availability BOOL DEFAULT 1; 

ALTER TABLE Rooms
ADD FOREIGN KEY (Home_id) REFERENCES rental_address(Home_id); 

CREATE TABLE `APPOINTMENTS` (
  `Appointment_ID` int NOT NULL AUTO_INCREMENT,
  `Home_id` int NOT NULL,
  `Room_id` int NOT NULL,
  `Appointment_TIme` DATETIME NOT NULL,
  PRIMARY KEY (`Appointment_ID`)
);
ALTER TABLE APPOINTMENTS
ADD FOREIGN KEY (Home_id) REFERENCES rental_address(Home_id); 

ALTER TABLE APPOINTMENTS
ADD FOREIGN KEY (Room_id) REFERENCES rooms(Room_id);

Show CREATE TABLE APPOINTMENTS;

use rental_db;

INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100001,'george', 'petter', 25,
 'Paris',  8129650016);
  INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100002,'tom', 'jerry', 35,
 'Newyork',  7129650016); 
 INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100003,'harry', 'kane', 24,
 'london',  6129650016);
 INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100004,'petter', 'parker', 22,
 'delhi',  9031231224);
  INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100005,'tom', 'holland', 35,
 'chicago',  9129650010); 
 INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100006,'harry', 'kane', 24,
 'istanbul',  6129658816);
  INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100007,'liam', 'parker', 28,
 'karachi',  9031231227);
  INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100008,'tom', 'holland', 31,
 'chicago',  9129650017); 
 INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100009,'tom', 'cruze', 21,
 'doha',  6129650017);
 INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100010,'Tony', 'stark', 18,
 'bombai',  9031231624);
  INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100011,'thomas', 'Muller', 23,
 'berlin',  9129650019); 
 INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100012,'Karim', 'Mustafa', 22,
 'tokyo',  6129650031);
  INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100013,'Veni', 'Nagavali', 28,
 'Amsterdam',  9031231447);
  INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100014,'mayura', 'churuli', 26,
 'sydney',  9129650037); 
 INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) VALUES (100015,'william', 'pulli', 33,
 'bali',  6129650033);
INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) 
VALUES (100016,'Vijay', 'Maliya', 38,
 'bangalore',  9037607407);
 
INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) 
VALUES (100017,'Billal', 'john', 28,
 'Kochi',  9031100100);
 
INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) 
VALUES (100018,'Sasi', 'card', 19,
 'cuba',  9324224412);

 
INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) 
VALUES (100019,'vimal', 'dizuza', 24,
 'Agra',  8923432313);
 
INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) 
VALUES (100020,'Xian', 'Chi', 18,
 'Beijeing',  7023123412);





INSERT INTO students_search
 (student_id, location , room_type, move_date ,parking, Disabled_access , Furnished, maxRent) 
VALUES (100011,'SA2', 'single', '2022-12-12',1,0,1, 400);

INSERT INTO students_search
 (student_id, location , room_type, move_date ,parking, Disabled_access , Furnished, maxRent) 
VALUES (100006,'SA3', 'single', '2022-12-12',1,1,1, 600);
INSERT INTO students_search
 (student_id, location , room_type, move_date ,parking, Disabled_access , Furnished, maxRent) 
VALUES (100014,'SA1', 'en-suite', '2022-12-25',0,0,1,450);
INSERT INTO students_search
 (student_id, location , room_type, move_date ,parking, Disabled_access , Furnished,maxRent) 
VALUES (100013,'SA1', 'single', '2022-01-15',1,0,1, 550);
INSERT INTO students_search
 (student_id, location , room_type, move_date ,parking, Disabled_access , Furnished, maxRent) 
VALUES (100002,'SA1', 'double', '2023-01-25',1,0,1, 420);

INSERT INTO students_search
 (student_id, location , room_type, move_date ,parking, Disabled_access , Furnished,maxRent) 
VALUES (100008,'SA2', 'single', '2023-01-16',1,0,1,350);

INSERT INTO rental_address
 (location,parking, Disabled_access,
 Number_of_Rooms,No_of_toilets,Furnished,landlord) 
VALUES ('SA15CD',1,1,4,3,1,'jaime');
INSERT INTO rental_address
 (location,parking,Disabled_access,Number_of_Rooms,No_of_toilets,Furnished,landlord) 
VALUES ('SA23DF',1,0,5,3,1,'john');
INSERT INTO rental_address
 (location,parking,Disabled_access,Number_of_Rooms,No_of_toilets,Furnished,landlord) 
VALUES ('SA12WE',1,1,3,2,0,'miller');
INSERT INTO rental_address
 (location,parking,Disabled_access,Number_of_Rooms,No_of_toilets,Furnished,landlord) 
VALUES ('SA13RF',1,1,4,3,1,'johnson');

INSERT INTO rooms
 (Home_id,Roomnumber,Room_type,
 RENT,Disabled_access) 
VALUES (1,1,'single',430,1);
INSERT INTO rooms
 (Home_id,Roomnumber,Room_type,
 RENT,Disabled_access) 
VALUES (1,2,'double',540,1);
INSERT INTO rooms
 (Home_id,Roomnumber,Room_type,
 RENT,Disabled_access) 
VALUES (1,3,'single',400,1);
INSERT INTO rooms
 (Home_id,Roomnumber,Room_type,
 RENT,Disabled_access) 
VALUES (1,4,'single',350,1);
INSERT INTO rooms
 (Home_id,Roomnumber,Room_type,
 RENT,Disabled_access) 
VALUES (2,1,'en-suite',450,1);
INSERT INTO rooms
 (Home_id,Roomnumber,Room_type,
 RENT,Disabled_access) 
VALUES (3,2,'double',430,0);

INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (1,1,'2022-12-10 10:55:00');

INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (1,2,'2022-12-12 12:00:00');

INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (1,5,'2023-01-05 10:00:00');


INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (1,3,'2023-01-05 10:00:00');

INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (1,4,'2023-01-02 10:00:00');
INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (3,6,'2023-01-05 10:00:00');


INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) 
VALUES (100022,'feran', 'baby', 25,
 'lisbon', 9496840444 );

 
INSERT INTO students_search
 (student_id, location , room_type, move_date ,parking, Disabled_access , 
 Furnished, maxRent) 
VALUES (100022,'SA2', 'en-suite', '2022-01-12',1,0,1, 600);

INSERT INTO rental_address
 (location,parking, Disabled_access,
 Number_of_Rooms,No_of_toilets,Furnished,landlord) 
VALUES ('SA23DB',1,0,2,3,1,'merry');

INSERT INTO rooms
 (Home_id,Roomnumber,Room_type,
 RENT,Disabled_access) 
VALUES (5,3,'en-suite',540,0);

INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (5,7,'2023-01-05 10:00:00');
INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (5,2,'2023-01-06 10:00:00');

INSERT INTO student (Student_ID, First_name, Last_name, Age,City, contact_number) 
VALUES (100023,'anjali', 'nambi', 25,
 'japan', 8796840444 );

 
INSERT INTO students_search
 (student_id, location , room_type, move_date ,parking, Disabled_access , 
 Furnished, maxRent) 
VALUES (100023,'SA4', 'Double', '2022-01-22',1,0,1, 500);

INSERT INTO rental_address
 (location,parking, Disabled_access,
 Number_of_Rooms,No_of_toilets,Furnished,landlord) 
VALUES ('SA43TB',1,0,1,2,1,'Hari');

INSERT INTO rooms
 (Home_id,Roomnumber,Room_type,
 RENT,Disabled_access) 
VALUES (6,1,'double',480,0);

INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (6,8,'2023-01-03 10:00:00');
INSERT INTO APPOINTMENTS
 (Home_id,Room_id,Appointment_TIme) 
VALUES (5,2,'2023-01-06 10:00:00');




use rental_db;

CREATE or replace VIEW RentalDemandSystem_VW as select a.student_id, b.first_name, b.last_name, b.contact_number from students_search a left join student b on a.student_id = b.student_id 
where a.still_seeking = 1 order by a.search_time;

SELECT * FROM `rental_db`.`rentaldemandsystem_vw` LIMIT 1000;



use rental_db;

create or replace TABLE MatchandRent as (
SELECT a.student_id, p.First_name, p.Last_name,p.contact_number ,
c.room_id,
b.Home_id,b.location,d.Appointment_TIme,
 a.search_time, c.availability
from students_search a 
left join student p
on a.student_id = p.student_id
left join rental_address b 
on  substring(b.location,1,3) = a.location
left join rooms c
on b.Home_id = c.Home_id
left join APPOINTMENTS d
on c.home_id = d.Home_id and c.room_id = d.Room_id
where b.parking = a.parking 
and  b.Disabled_access = a.Disabled_access
and  b.Furnished = a.Furnished 
and c.Room_type = a.Room_type
and a.maxRent >= c.RENT
and c.availability = 1
);
CREATE or replace VIEW daily_reception_report_vw  as SELECT student_id, First_name, Last_name,contact_number ,location, Appointment_TIme, availability FROM MatchandRent
order by search_time DESC LIMIT 5;

SELECT * FROM `rental_db`.`daily_reception_report_vw` LIMIT 1000;


CREATE TABLE  IF NOT EXISTS `rental_tracker` (`index` int NOT NULL AUTO_INCREMENT PRIMARY KEY,
`student_id` int(11) DEFAULT NULL,
`First_name` varchar(255) DEFAULT NULL, 
`Last_name` varchar(255), 
`contact_number` bigint(20), 
 `room_id` int(11) DEFAULT 0, `Home_id` int(11) DEFAULT 0, 
 `location` varchar(255) DEFAULT NULL, 
 `Appointment_TIme` TIMESTAMP,
 `ACC_OR_REJ` tinyint(1) NOT NULL DEFAULT 0,
 `availability` BOOL ,
 `Match_time` DATETIME DEFAULT CURRENT_TIMESTAMP );

INSERT into rental_tracker (Student_ID, First_name, Last_name, 
contact_number, room_id, Home_id,location,Appointment_TIme,availability)
SELECT Student_ID, First_name, Last_name, 
contact_number, room_id, Home_id,location,Appointment_TIme,availability
FROM MatchandRent;

CREATE or replace VIEW rental_tracker_vw  as 
SELECT student_id,First_name, Last_name,contact_number,Home_id,room_id
,location, Appointment_TIme,Match_time FROM rental_tracker
order by Match_time;


UPDATE rental_tracker
SET ACC_OR_REJ = 1 
where student_id = 100023;


UPDATE rooms 
SET availability =0
WHERE room_id in (select room_id from rental_tracker where ACC_OR_REJ = 1);

UPDATE students_search
SET still_seeking = 0
WHERE Student_ID in 
(select student_id from rental_tracker where ACC_OR_REJ = 1);


CREATE VIEW system_efficacy as SELECT  SUBSTRING(first_name,1,1) AS FirstName, last_name ,Count(ACC_OR_REJ ) as rejectedCount
  from rental_tracker  where ACC_OR_REJ =0;


CREATE VIEW renterReportVW as SELECT  a.landlord, b.location, COUNT(b.student_id) as NOREjections
FROM rental_tracker b 
INNER JOIN rental_address a
on b.home_id = a.home_id
where b.ACC_OR_REJ = 0;








