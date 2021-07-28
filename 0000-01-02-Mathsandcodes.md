create database my_school;
use my_school;
create table roles (
id int(11) unsigned auto_increment primary key,
title varchar(16) not null unique
);

create roles(
id int(11) unsigned auto_increment primary key,
title varchar(16) not null unique
);

create table users (
id int(11) unsigned auto_increment primary key,
role_id int(11) unsigned,
first_name varchar(32) not null,
phone varchar(14),
national_id int(10) not null unique,
email varchar(128) unique,
second_name varchar(32) not null,
third_name varchar(32) not null,
last_name varchar(32) not null,
dob date not null,

constraint foreign key(role_id)
references roles(id)
);


create table courses (
id int(11) unsigned auto_increment primary key,
title varchar(32) not null unique,
short_name varchar(11) not null unique,
description varchar(255)
);

create table classrooms(
id int(11) unsigned auto_increment primary key,
location varchar(128) not null unique,
title varchar(32) not null unique
);


create table classes(
id int(11) unsigned auto_increment primary key,
course_id int(11) unsigned not null,
teacher_id int(11) unsigned not null,

constraint foreign key(course_id)
references courses(id),

constraint foreign key(course_id)
references users(id)

);

create table class_student(
student_id int(11) unsigned not null,
class_id int(11) unsigned not null
);

create table exam (
id int(11) unsigned auto_increment primary key,
class_id int(11) unsigned not null,

constraint foreign key(class_id)
references classes (id)
);

create table exam_result (
student_id int(11) unsigned not null,
exam_id int(11) unsigned not null,
grade int(3) unsigned not null,
constraint foreign key(student_id)
references users(id),
constraint primary key(student_id, exam_id)
);


create table class_student(
student_id int(11) unsigned not null,
class_id int(11) unsigned not null,

constraint foreign key(class_id)
references classes(id),

constraint primary key(student_id, class_id)
);
