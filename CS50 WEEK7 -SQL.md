# Week7 -SQL

* Blog
* Integer
  * smallint (2 byte)
  * integer (4 byte around 4 billion all positive)
  * bigint (8 byte)
* Numeric
  * boolean
  * date
  * datetime
  * numeric(scale, precision)
  * time
  * timestamp
* Real
  * real (4 byte)
  * double precision (8 byte)
* Text
  * char(n)
  * varchar(n)
  * text

>> sqlite3 fromshi.db
>> CREATE TABLE 'registrants' ('id' integer, 'name' varchar(255), 'dorm' varchar(255));
>> INSERT INTO registrants (id, name, dorm) VALUES (1, 'Brian', 'A');
>> SELECT * FROM registrans WHERE dorm = 'A';
>> UPDATE registrants SET dorm = 'B' where id = 1;
>>
