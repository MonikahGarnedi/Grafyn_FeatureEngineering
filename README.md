# Grafyn_FeatureEngineering
Includes: Snowflask view-only access links, ppt

#Initial ML utilization: https://app.snowflake.com/baadqcf/vw37862/w326plpoBV8W#query

#decision tree:  https://app.snowflake.com/baadqcf/vw37862/w4PsDVoy5ln6/query

#logistic regression: https://app.snowflake.com/baadqcf/vw37862/w40cjHuckK0z/query

#SQL queries:
use role accountadmin;  -- or a role with enough privileges
 
use warehouse compute_wh;

create or replace database customer;
use customer;

create or replace schema my_schema;
use schema my_schema;

create table student_info(
    student_id INT,
    name STRING,
    attendance_percentage FLOAT,
    assignments_submitted INT,
    extracurricular_participation INT,
    final_exam_score FLOAT
);

insert into student_info values
(1, 'Amit', 92.5, 10, 1, 85.0),
(2, 'Priya', 80.0, 8, 0, 65.0),
(3, 'Rahul', 60.0, 5, 0, 45.0),
(4, 'Sneha', 88.0, 9, 1, 78.0),
(5, 'Arjun', 55.0, 3, 0, 35.0),
(6, 'Meena', 97.0, 10, 1, 90.0),
(7, 'Ravi', 72.0, 6, 1, 58.0),
(8, 'Divya', 85.0, 9, 0, 82.0),
(9, 'Vikram', 65.0, 5, 0, 50.0),
(10, 'Kiran', 90.0, 10, 1, 88.0),
(11, 'Anjali', 78.0, 7, 1, 62.0),
(12, 'Manish', 81.0, 8, 0, 70.0),
(13, 'Neha', 95.0, 10, 1, 92.0),
(14, 'Suresh', 68.0, 6, 0, 48.0),
(15, 'Lakshmi', 89.0, 9, 1, 80.0),
(16, 'Harish', 74.0, 7, 0, 60.0),
(17, 'Pooja', 91.0, 10, 1, 87.0),
(18, 'Akash', 57.0, 4, 0, 38.0),
(19, 'Swati', 84.0, 8, 1, 72.0),
(20, 'Gopal', 63.0, 5, 0, 42.0),
(21, 'Jyoti', 82.0, 8, 1, 69.0),
(22, 'Tarun', 70.0, 6, 0, 55.0),
(23, 'Ritika', 94.0, 10, 1, 89.0),
(24, 'Vikas', 61.0, 5, 0, 40.0),
(25, 'Komal', 87.0, 9, 1, 77.0),
(26, 'Sunil', 66.0, 6, 0, 46.0),
(27, 'Shweta', 93.0, 10, 1, 91.0),
(28, 'Deepak', 58.0, 4, 0, 37.0),
(29, 'Kavita', 76.0, 7, 0, 59.0),
(30, 'Rohit', 85.0, 9, 1, 83.0),
(31, 'Suman', 64.0, 5, 0, 43.0),
(32, 'Aditya', 96.0, 10, 1, 94.0),
(33, 'Nisha', 73.0, 7, 1, 61.0),
(34, 'Santosh', 69.0, 6, 0, 49.0),
(35, 'Payal', 90.0, 10, 1, 86.0),
(36, 'Ashok', 62.0, 5, 0, 41.0),
(37, 'Kirti', 83.0, 8, 1, 71.0),
(38, 'Ankur', 59.0, 4, 0, 36.0),
(39, 'Geeta', 88.0, 9, 0, 79.0),
(40, 'Dinesh', 75.0, 7, 1, 63.0),
(41, 'Mona', 92.0, 10, 1, 90.0),
(42, 'Kunal', 67.0, 6, 0, 47.0),
(43, 'Isha', 86.0, 9, 1, 81.0),
(44, 'Rajesh', 71.0, 7, 0, 56.0),
(45, 'Poonam', 79.0, 8, 1, 66.0),
(46, 'Ramesh', 65.0, 5, 0, 44.0),
(47, 'Seema', 91.0, 10, 1, 89.0),
(48, 'Nitin', 60.0, 4, 0, 39.0),
(49, 'Alka', 82.0, 8, 1, 70.0),
(50, 'Farhan', 74.0, 7, 0, 57.0),
(51, 'Lata', 95.0, 10, 1, 93.0),
(52, 'Kabir', 63.0, 5, 0, 42.0),
(53, 'Renu', 89.0, 9, 1, 84.0),
(54, 'Amar', 56.0, 3, 0, 34.0),
(55, 'Preeti', 81.0, 8, 1, 68.0),
(56, 'Mahesh', 77.0, 7, 0, 60.0),
(57, 'Shilpa', 93.0, 10, 1, 91.0),
(58, 'Gaurav', 69.0, 6, 0, 48.0),
(59, 'Anita', 84.0, 9, 1, 73.0),
(60, 'Hemant', 61.0, 5, 0, 40.0),
(61, 'Jaya', 90.0, 10, 1, 87.0),
(62, 'Varun', 72.0, 7, 0, 58.0),
(63, 'Nandita', 85.0, 9, 1, 80.0),
(64, 'Ajay', 59.0, 4, 0, 38.0),
(65, 'Sonia', 94.0, 10, 1, 92.0),
(66, 'Arvind', 66.0, 6, 0, 45.0),
(67, 'Bhavna', 87.0, 9, 1, 82.0),
(68, 'Kartik', 70.0, 7, 0, 55.0),
(69, 'Chitra', 78.0, 8, 1, 67.0),
(70, 'Vijay', 64.0, 5, 0, 43.0),
(71, 'Smita', 91.0, 10, 1, 89.0),
(72, 'Manoj', 57.0, 4, 0, 37.0),
(73, 'Rekha', 83.0, 8, 1, 71.0),
(74, 'Siddharth', 75.0, 7, 0, 62.0),
(75, 'Tanya', 96.0, 10, 1, 94.0),
(76, 'Lokesh', 68.0, 6, 0, 46.0),
(77, 'Pallavi', 86.0, 9, 1, 79.0),
(78, 'Ashwin', 62.0, 5, 0, 41.0),
(79, 'Monica', 88.0, 9, 0, 77.0),
(80, 'Naveen', 73.0, 7, 1, 60.0),
(81, 'Radha', 95.0, 10, 1, 92.0),
(82, 'Dev', 65.0, 5, 0, 44.0),
(83, 'Shalini', 89.0, 9, 1, 83.0),
(84, 'Omkar', 58.0, 4, 0, 36.0),
(85, 'Sarita', 82.0, 8, 1, 70.0),
(86, 'Harpreet', 76.0, 7, 0, 61.0),
(87, 'Rashmi', 93.0, 10, 1, 90.0),
(88, 'Tejas', 67.0, 6, 0, 47.0),
(89, 'Aarti', 84.0, 9, 1, 74.0),
(90, 'Yash', 60.0, 5, 0, 39.0),
(91, 'Kusum', 90.0, 10, 1, 88.0),
(92, 'Sameer', 71.0, 7, 0, 56.0),
(93, 'Meera', 85.0, 9, 1, 81.0),
(94, 'Prakash', 63.0, 5, 0, 42.0),
(95, 'Uma', 94.0, 10, 1, 91.0),
(96, 'Vinod', 69.0, 6, 0, 49.0),
(97, 'Anushka', 87.0, 9, 1, 79.0),
(98, 'Parth', 74.0, 7, 0, 59.0),
(99, 'Gayatri', 92.0, 10, 1, 90.0),
(100, 'Shankar', 55.0, 3, 0, 34.0);

select name from student_info 
where attendance_percentage>75.0 
and extracurricular_participation=1;

create or replace table extract_data_1 as   --minimal feature extraction
select
    student_id,
    attendance_percentage,
    assignments_submitted,
    extracurricular_participation,
    final_exam_score,
    case when final_exam_score >= 50 then 1 else 0 end as pass_or_fail from student_info;

select * from extract_data_1;

create or replace table extract_data_1 as   -- much better version for feature extraction
select 
  student_id,
  attendance_percentage,
  assignments_submitted,
  extracurricular_participation,
  final_exam_score,
  case
    when attendance_percentage >= 90 then 'A'
    when attendance_percentage >= 80 then 'B'
    when attendance_percentage >= 70 then 'C'
    else 'D'
  end as attendance_grade,
  (final_exam_score - avg_score) / nullif(stddev_score,0) AS score_z,
  case when final_exam_score >= 50 then 1 else 0 end as pass_or_fail
from student_info,
  (select avg(final_exam_score) as avg_score, stddev_pop(final_exam_score) as stddev_score from student_info);

select * from extract_data_1;

--feature store
create or replace table feature_store as
select
  student_id,
  assignments_submitted,
  extracurricular_participation,
  final_exam_score,
  pass_or_fail,attendance_grade,score_z
  
from extract_data_1;

select * from feature_store ;

show warehouses;

#warehouse can be created with a sql query too.
  
use role accountadmin;  -- or a role with enough privileges

use warehouse compute_wh;

