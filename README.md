# ggiriDB

```
<CSV TO MYSQL>
load data local infile '/root/ggiriDB/usersong.csv' into table 사용자노래 character set 'utf8'fields terminated by ',';

<DB CRREATE QUERY>

create table 가수(
이름 varchar(45),
성별 varchar(10),
그룹 boolean,
primary key(이름))
default character set utf8;

create table 노래(
노래id int,
제목 varchar(45),
가수 varchar(45),
primary key(노래id),
foreign key(가수) references 가수(이름) on update cascade)
default character set utf8;

create table 태그(
태그 varchar(45),
노래id int,
퍼센트 int,
primary key(태그, 노래id),
foreign key(노래id) references 노래(노래id) on update cascade)
default character set utf8;

create table 사용자(
사용자id int,
이름 varchar(45),
성별 varchar(10),
나이 int,
primary key(사용자id))
default character set utf8;

create table 사용자노래(
노래id int,
사용자id int,
primary key(노래id, 사용자id),
foreign key(노래id) references 노래(노래id) on update cascade,
foreign key(사용자id) references 사용자(사용자id) on update cascade)
default character set utf8;

```
