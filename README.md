
Project Information
Project Name: Data Analytics Final Project

Dataset Name: student_exam_performance

Student Name: Rakend Vijayan.K

Batch Name: DA/ML-DAF50

Dataset Source: Kaggle

Dataset Link: https://www.kaggle.com/datasets/mobeenfatimah/student-exam-performance-and-success-dataset

Domain: Education

Project Title : Student Exam Performancee Analysis using Python
Domain : Education / Academic Performance Analytics
❖ Step 1: Importing file and libraries

# Importing Libraries which is needed

import pandas as pd
import numpy as np
     

# importing data

from google.colab import files
upload = files.upload()
     
Upload widget is only available when the cell has been executed in the current browser session. Please rerun this cell to enable.
Saving student_exam_performance.csv to student_exam_performance.csv

df=pd.read_csv("student_exam_performance.csv")
     
● Now the dataset is imported before cleaning we need to check the dataset first

# checking the dataset

df
     
student_id	age	gender	education_level	school_type	family_income	parent_education	urban_rural	previous_exam_score	previous_gpa	...	exam_difficulty	exam_preparation_days	questions_attempted	questions_correct	time_management_score	exam_anxiety_level	exam_score	performance_grade	pass_status	performance_level
0	STU_000001	20	Female	High School	Public	Middle	NaN	Rural	78.36	2.95	...	Medium	27	95	86	NaN	9.39	90.40	A	Pass	High
1	STU_000002	17	Male	High School	Public	Middle	NaN	Suburban	73.40	2.89	...	Easy	4	100	86	87.17	6.31	86.21	A	Pass	High
2	STU_000003	18	Other	Undergraduate	Public	Middle	Master	Urban	82.76	3.35	...	Easy	28	96	74	63.77	9.87	76.11	B	Pass	Medium
3	STU_000004	20	Male	High School	Public	Middle	High School	Suburban	60.61	2.57	...	Medium	16	97	77	59.51	9.68	79.74	B	Pass	Medium
4	STU_000005	16	Female	High School	Private	High	Bachelor	Suburban	74.79	2.84	...	Medium	28	98	52	84.64	10.00	50.66	D	Pass	Low
...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...
99995	STU_099996	17	Male	Undergraduate	Public	Upper-Middle	NaN	Suburban	78.73	NaN	...	Medium	5	95	62	76.13	8.36	66.46	C	Pass	Medium
99996	STU_099997	14	Female	High School	Public	Upper-Middle	Bachelor	Suburban	75.70	2.98	...	Easy	24	94	91	84.29	8.68	96.54	A	Pass	High
99997	STU_099998	16	Female	High School	Public	Upper-Middle	High School	Suburban	84.69	3.27	...	Medium	24	85	65	62.32	9.97	74.66	C	Pass	Medium
99998	STU_099999	15	Female	High School	Private	High	Master	Rural	74.70	3.06	...	Medium	28	93	81	100.00	10.00	85.85	A	Pass	High
99999	STU_100000	18	Female	Undergraduate	Charter	Lower-Middle	NaN	Urban	76.73	2.97	...	Medium	1	92	52	NaN	10.00	54.40	D	Pass	Low
100000 rows × 44 columns


# cheking how many columns and rows are there

df.shape
     
(100000, 44)

# Verifying columns

df.columns
     
Index(['student_id', 'age', 'gender', 'education_level', 'school_type',
       'family_income', 'parent_education', 'urban_rural',
       'previous_exam_score', 'previous_gpa', 'attendance_percentage',
       'assignment_completion_rate', 'class_participation',
       'study_hours_per_day', 'self_study_hours', 'private_tuition',
       'online_learning_hours', 'study_consistency', 'study_environment',
       'study_method', 'revision_frequency', 'practice_tests_completed',
       'notes_quality', 'sleep_hours', 'sleep_quality', 'daily_screen_time',
       'physical_activity_hours', 'break_frequency', 'stress_level',
       'motivation_level', 'internet_access', 'device_availability',
       'educational_app_usage', 'online_course_hours', 'exam_difficulty',
       'exam_preparation_days', 'questions_attempted', 'questions_correct',
       'time_management_score', 'exam_anxiety_level', 'exam_score',
       'performance_grade', 'pass_status', 'performance_level'],
      dtype='object')

# Checking the datatype and null value count

df.info()
     
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 100000 entries, 0 to 99999
Data columns (total 44 columns):
 #   Column                      Non-Null Count   Dtype  
---  ------                      --------------   -----  
 0   student_id                  100000 non-null  object 
 1   age                         100000 non-null  int64  
 2   gender                      100000 non-null  object 
 3   education_level             100000 non-null  object 
 4   school_type                 100000 non-null  object 
 5   family_income               100000 non-null  object 
 6   parent_education            93474 non-null   object 
 7   urban_rural                 100000 non-null  object 
 8   previous_exam_score         100000 non-null  float64
 9   previous_gpa                92207 non-null   float64
 10  attendance_percentage       90137 non-null   float64
 11  assignment_completion_rate  100000 non-null  float64
 12  class_participation         100000 non-null  object 
 13  study_hours_per_day         100000 non-null  float64
 14  self_study_hours            100000 non-null  float64
 15  private_tuition             100000 non-null  int64  
 16  online_learning_hours       100000 non-null  float64
 17  study_consistency           100000 non-null  object 
 18  study_environment           100000 non-null  object 
 19  study_method                100000 non-null  object 
 20  revision_frequency          100000 non-null  object 
 21  practice_tests_completed    100000 non-null  int64  
 22  notes_quality               91593 non-null   object 
 23  sleep_hours                 100000 non-null  float64
 24  sleep_quality               93006 non-null   object 
 25  daily_screen_time           100000 non-null  float64
 26  physical_activity_hours     100000 non-null  float64
 27  break_frequency             100000 non-null  object 
 28  stress_level                100000 non-null  int64  
 29  motivation_level            100000 non-null  object 
 30  internet_access             100000 non-null  int64  
 31  device_availability         97035 non-null   object 
 32  educational_app_usage       100000 non-null  object 
 33  online_course_hours         100000 non-null  float64
 34  exam_difficulty             100000 non-null  object 
 35  exam_preparation_days       100000 non-null  int64  
 36  questions_attempted         100000 non-null  int64  
 37  questions_correct           100000 non-null  int64  
 38  time_management_score       90387 non-null   float64
 39  exam_anxiety_level          100000 non-null  float64
 40  exam_score                  100000 non-null  float64
 41  performance_grade           100000 non-null  object 
 42  pass_status                 100000 non-null  object 
 43  performance_level           100000 non-null  object 
dtypes: float64(14), int64(8), object(22)
memory usage: 33.6+ MB
❖ Step 2 : Data Cleaning & Pre-processing
Data Cleaning and Pre-Processing is an important step in Data preparation. It helps us understand the data we have, identify any errors or missing values, and get a clear idea of what needs to be done next. This makes the data ready for further analysis and visualization.

Finding Null values

# Checking how many null values are there using isnull

df.isnull().sum()
     
0
student_id	0
age	0
gender	0
education_level	0
school_type	0
family_income	0
parent_education	6526
urban_rural	0
previous_exam_score	0
previous_gpa	7793
attendance_percentage	9863
assignment_completion_rate	0
class_participation	0
study_hours_per_day	0
self_study_hours	0
private_tuition	0
online_learning_hours	0
study_consistency	0
study_environment	0
study_method	0
revision_frequency	0
practice_tests_completed	0
notes_quality	8407
sleep_hours	0
sleep_quality	6994
daily_screen_time	0
physical_activity_hours	0
break_frequency	0
stress_level	0
motivation_level	0
internet_access	0
device_availability	2965
educational_app_usage	0
online_course_hours	0
exam_difficulty	0
exam_preparation_days	0
questions_attempted	0
questions_correct	0
time_management_score	9613
exam_anxiety_level	0
exam_score	0
performance_grade	0
pass_status	0
performance_level	0

dtype: int64
Handlingthe missing values

# Handling the numerical missing values from the data

df['previous_gpa'].fillna(df['previous_gpa'].mean(), inplace=True)

df['attendance_percentage'].fillna(df['attendance_percentage'].mean(), inplace=True)

df['time_management_score'].fillna(df['time_management_score'].mean(), inplace=True)
     
/tmp/ipykernel_1650/1074933090.py:3: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df['previous_gpa'].fillna(df['previous_gpa'].mean(), inplace=True)
/tmp/ipykernel_1650/1074933090.py:5: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df['attendance_percentage'].fillna(df['attendance_percentage'].mean(), inplace=True)
/tmp/ipykernel_1650/1074933090.py:7: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df['time_management_score'].fillna(df['time_management_score'].mean(), inplace=True)
In here previous_gpa, attendance_percentage, time_management_score are numerical columns to handel the numerical missing values we use "Mean"


# Handling the non numerical values from the data

df['parent_education'].fillna(df['parent_education'].mode()[0],inplace=True)

df['notes_quality'].fillna(df['notes_quality'].mode()[0],inplace=True)

df['device_availability'].fillna(df['device_availability'].mode()[0],inplace=True)

df['sleep_quality'].fillna(df['sleep_quality'].mode()[0],inplace=True)
     
/tmp/ipykernel_1650/3030907395.py:3: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df['parent_education'].fillna(df['parent_education'].mode()[0],inplace=True)
/tmp/ipykernel_1650/3030907395.py:5: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df['notes_quality'].fillna(df['notes_quality'].mode()[0],inplace=True)
/tmp/ipykernel_1650/3030907395.py:7: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df['device_availability'].fillna(df['device_availability'].mode()[0],inplace=True)
/tmp/ipykernel_1650/3030907395.py:9: FutureWarning: A value is trying to be set on a copy of a DataFrame or Series through chained assignment using an inplace method.
The behavior will change in pandas 3.0. This inplace method will never work because the intermediate object on which we are setting values always behaves as a copy.

For example, when doing 'df[col].method(value, inplace=True)', try using 'df.method({col: value}, inplace=True)' or df[col] = df[col].method(value) instead, to perform the operation inplace on the original object.


  df['sleep_quality'].fillna(df['sleep_quality'].mode()[0],inplace=True)
In here parent_education, notes_quality, device_availability, sleep_quality are categorical columns. Instead of "Mean" we use "Mode" to fill the missing values


# Cheking if there any missing value still remains

df.isnull().sum()
     
0
student_id	0
age	0
gender	0
education_level	0
school_type	0
family_income	0
parent_education	0
urban_rural	0
previous_exam_score	0
previous_gpa	0
attendance_percentage	0
assignment_completion_rate	0
class_participation	0
study_hours_per_day	0
self_study_hours	0
private_tuition	0
online_learning_hours	0
study_consistency	0
study_environment	0
study_method	0
revision_frequency	0
practice_tests_completed	0
notes_quality	0
sleep_hours	0
sleep_quality	0
daily_screen_time	0
physical_activity_hours	0
break_frequency	0
stress_level	0
motivation_level	0
internet_access	0
device_availability	0
educational_app_usage	0
online_course_hours	0
exam_difficulty	0
exam_preparation_days	0
questions_attempted	0
questions_correct	0
time_management_score	0
exam_anxiety_level	0
exam_score	0
performance_grade	0
pass_status	0
performance_level	0

dtype: int64
After handling the missing values, the dataset was checked again to make sure that no missing values were remaining. This helped to ensure that the dataset was complete and ready for further analysis and visualization.

Handeling the Duplicates

# Checking any duplicates contains in the data

df.duplicated().sum()
     
np.int64(0)
The dataset was checked for duplicate records, and no duplicate records were found. This ensures that the dataset does not contain repeated entries that could affect the accuracy of the analysis.

Removing the Columns
The dataset contains many columns, which can make the data more complicated and difficult to understand. Therefore, the unnecessary columns were removed to make the dataset simpler, more organized, and easier to understand for further analysis.


# Checking any columns which is necessary or not


avg_school_score = df.groupby('school_type')['exam_score'].mean()
print(avg_school_score)
     
school_type
Charter    61.631952
Private    62.058819
Public     61.938776
Name: exam_score, dtype: float64
The difference between the highest and lowest is less than 0.5 points — essentially no meaningful variation. Whether a student attends a Public, Private, or Charter school shows no real relationship with their exam performance in this dataset.

From this dataset i have selected some columns for analysing

Categorical columns

categorical_cols = ['school_type', 'urban_rural', 'notes_quality',
                     'educational_app_usage', 'revision_frequency',
                     'sleep_quality', 'motivation_level']

for col in categorical_cols:
  print(f"---{col}---")
  print(df.groupby(col)['exam_score'].mean())
  print()
     
---school_type---
school_type
Charter    61.631952
Private    62.058819
Public     61.938776
Name: exam_score, dtype: float64

---urban_rural---
urban_rural
Rural       61.836337
Suburban    61.995257
Urban       61.965086
Name: exam_score, dtype: float64

---notes_quality---
notes_quality
Average      62.004812
Excellent    61.959762
Poor         61.749985
Name: exam_score, dtype: float64

---educational_app_usage---
educational_app_usage
High        61.936973
Low         61.942683
Moderate    61.963932
Name: exam_score, dtype: float64

---revision_frequency---
revision_frequency
Daily     61.985154
Rarely    61.910171
Weekly    61.944882
Name: exam_score, dtype: float64

---sleep_quality---
sleep_quality
Excellent    61.888087
Fair         61.963504
Good         61.898293
Poor         62.094030
Name: exam_score, dtype: float64

---motivation_level---
motivation_level
High      61.959460
Low       61.871066
Medium    61.976086
Name: exam_score, dtype: float64

In this output, I grouped categorical column and checked the average exam_score for every category inside it. If a column is actually important, the scores across its categories should be noticeably different. But here, you can see that's not happening:

school_type → Charter 61.6, Private 62.0, Public 61.9 — a small diffrence
urban_rural → Rural 61.8, Suburban 62.0, Urban 61.9 — a small diffrence
notes_quality → Average 62.0, Excellent 61.9, Poor 61.7 — a small diffrence
educational_app_usage → High 61.9, Low 61.9, Moderate 61.9 — no diffrence at all
revision_frequency → Daily 61.9, Rarely 61.9, Weekly 61.9 — no difference at all
This shows that no matter which category a student falls into for these columns, their average exam score stays roughly the same (60-62). That means these columns have no real relationship with performance — they're not separating high scorers from low scorers, so they're unnecessary

Numerical columns

numeric_cols = ['age', 'previous_exam_score', 'previous_gpa', 'attendance_percentage',
 'assignment_completion_rate', 'study_hours_per_day', 'self_study_hours',
 'private_tuition', 'online_learning_hours', 'practice_tests_completed',
 'sleep_hours', 'daily_screen_time', 'physical_activity_hours',
 'stress_level', 'internet_access', 'online_course_hours',
 'exam_preparation_days', 'questions_attempted', 'questions_correct',
 'time_management_score', 'exam_anxiety_level', 'exam_score']


for col in numeric_cols:
  corr = df[col].corr(df['exam_score'])
  print(f"{col}: correlation = {corr:.5f}")
     
age: correlation = -0.00349
previous_exam_score: correlation = 0.49444
previous_gpa: correlation = 0.44975
attendance_percentage: correlation = 0.16072
assignment_completion_rate: correlation = 0.22112
study_hours_per_day: correlation = 0.36324
self_study_hours: correlation = 0.34296
private_tuition: correlation = 0.00383
online_learning_hours: correlation = -0.00257
practice_tests_completed: correlation = 0.31648
sleep_hours: correlation = 0.17060
daily_screen_time: correlation = 0.00476
physical_activity_hours: correlation = -0.00031
stress_level: correlation = -0.16234
internet_access: correlation = 0.00220
online_course_hours: correlation = 0.00067
exam_preparation_days: correlation = 0.19858
questions_attempted: correlation = 0.00354
questions_correct: correlation = 0.97531
time_management_score: correlation = 0.10153
exam_anxiety_level: correlation = -0.12993
exam_score: correlation = 1.00000
For numerical columns, correlation tells us how strongly a column is connected to exam_score. The closer the value is to 0, the weaker (or non-existent) the relationship — meaning that column doesn't actually affect exam performance in any meaningful way.

Looking at the output, several columns have correlation values that are basically 0.00:

age → -0.003
private_tuition → 0.004
online_learning_hours → -0.003
daily_screen_time → 0.005
physical_activity_hours → -0.0003
internet_access → 0.002
online_course_hours → 0.0007
questions_attempted → 0.004
All of these round to essentially 0.00, which means there's no real correlation between them and exam_score. In simple terms, whether a student is older or younger, takes private tuition or not, or spends more/less time online — none of it actually changes their exam performance in this dataset. Since these columns carry no useful signal, they're unnecessary and were removed.


columns_to_drop = [
    # Categorical - no real difference across categories
    'school_type', 'urban_rural', 'notes_quality',
    'educational_app_usage', 'revision_frequency',
    'sleep_quality', 'motivation_level',

    # Numerical - correlation ~0.00, no relationship
    'private_tuition', 'online_learning_hours',
    'daily_screen_time', 'physical_activity_hours',
    'internet_access', 'online_course_hours', 'questions_attempted',
]

df = df.drop(columns=columns_to_drop)
     
The columns were checked based on their importance and relationship with the target variable. Some numerical columns had very low or almost no correlation, while some categorical columns were not useful for the analysis. Therefore, these columns were removed to reduce unnecessary information and make the dataset simpler for further analysis and visualization.

Which all columns are finaly selected
Category	Columns which is taken
| Identifier | Student_id | Demographics | Age, Gender, Education_level, Family_income, Parent_education | | Academic history |Previous_exam_score, Previous_gpa, Attendance_percentage, Assignment_completion_rate, Class_participation | | Study behavior | Study_hours_per_day, Self_study_hours, Study_consistency, Study_environment, Study_method, Practice_tests_completed, | | Lifestyle | Sleep_hours, Break_frequency, Stress_level,| | Access/resources | Device_availability | Exam context | Exam_difficulty, Exam_preparation_days, Questions_correct, Time_management_score, Exam_anxiety_level | Outcome | Exam_score, Performance_grade, Pass_status, Performance_level |

Creating a derived columns

# To see how much effort are taken by students


df['total_effort_score'] = df['study_hours_per_day'] + (df['practice_tests_completed']/2)

df['total_effort_score']
     
total_effort_score
0	8.94
1	8.42
2	3.56
3	11.89
4	3.13
...	...
99995	4.66
99996	14.59
99997	4.95
99998	8.27
99999	6.61
100000 rows × 1 columns


dtype: float64
A new column called total_effort_score was created by combining the study_hours_per_day and practice_testes_completed in the dataset. This helps to represent the overall effort of each student in a single column and makes it easier to analyze how student effort is related to exam performance.


# Checking the columns

df.columns.tolist()
     
['student_id',
 'age',
 'gender',
 'education_level',
 'family_income',
 'parent_education',
 'previous_exam_score',
 'previous_gpa',
 'attendance_percentage',
 'assignment_completion_rate',
 'class_participation',
 'study_hours_per_day',
 'self_study_hours',
 'study_consistency',
 'study_environment',
 'study_method',
 'practice_tests_completed',
 'sleep_hours',
 'break_frequency',
 'stress_level',
 'device_availability',
 'exam_difficulty',
 'exam_preparation_days',
 'questions_correct',
 'time_management_score',
 'exam_anxiety_level',
 'exam_score',
 'performance_grade',
 'pass_status',
 'performance_level',
 'total_effort_score']

df.shape
     
(100000, 31)
The dataset was trimmed from 44 columns to 30 columns . Columns were removed because they showed no real relationship with exam_score (via correlation or group-mean comparison)

Checking the datatypes

# Checking the formate of "float columns"

flot_df =  df.select_dtypes(include=['float64'])
print(flot_df.head())
     
   previous_exam_score  previous_gpa  attendance_percentage  \
0                78.36          2.95              81.490000   
1                73.40          2.89              84.616882   
2                82.76          3.35             100.000000   
3                60.61          2.57              84.910000   
4                74.79          2.84              88.210000   

   assignment_completion_rate  study_hours_per_day  self_study_hours  \
0                       65.18                 4.94              2.63   
1                       76.53                 3.42              2.64   
2                       70.39                 1.06              0.83   
3                       75.06                 7.89              5.51   
4                       61.54                 2.63              2.29   

   sleep_hours  time_management_score  exam_anxiety_level  exam_score  \
0         6.31              78.398551                9.39       90.40   
1         6.81              87.170000                6.31       86.21   
2         6.53              63.770000                9.87       76.11   
3         6.60              59.510000                9.68       79.74   
4         7.83              84.640000               10.00       50.66   

   total_effort_score  
0                8.94  
1                8.42  
2                3.56  
3               11.89  
4                3.13  

# Checking the formate of "integer columns"

int_df = df.select_dtypes(include=['int64'])
print(int_df.head())
     
   age  practice_tests_completed  stress_level  exam_preparation_days  \
0   20                         8            10                     27   
1   17                        10             8                      4   
2   18                         5             9                     28   
3   20                         8            10                     16   
4   16                         1            10                     28   

   questions_correct  
0                 86  
1                 86  
2                 74  
3                 77  
4                 52  

# Checking the formate of "object columns"

object_df = df.select_dtypes(include=['object'])
print(object_df.head())
     
   student_id  gender education_level family_income parent_education  \
0  STU_000001  Female     High School        Middle      High School   
1  STU_000002    Male     High School        Middle      High School   
2  STU_000003   Other   Undergraduate        Middle           Master   
3  STU_000004    Male     High School        Middle      High School   
4  STU_000005  Female     High School          High         Bachelor   

  class_participation study_consistency study_environment  study_method  \
0              Medium            Medium          Moderate    Flashcards   
1                 Low            Medium          Moderate    Flashcards   
2              Medium               Low          Moderate   Summarizing   
3                 Low            Medium             Quiet   Summarizing   
4              Medium            Medium             Noisy  Self-Reading   

  break_frequency device_availability exam_difficulty performance_grade  \
0      Frequently              Shared          Medium                 A   
1      Frequently              Shared            Easy                 A   
2          Rarely           Dedicated            Easy                 B   
3          Rarely           Dedicated          Medium                 B   
4      Frequently           Dedicated          Medium                 D   

  pass_status performance_level  
0        Pass              High  
1        Pass              High  
2        Pass            Medium  
3        Pass            Medium  
4        Pass               Low  
The data types of all the columns were checked to make sure that the values were stored in the correct format. The numerical and categorycal columns were already in the appropriate data types, so no changes were required. This ensures that the data is ready for further analysis and visualization.

❖ Step 3: EDA(Exploratory Data Analysis) AND VISUALIZATION

df.head()
     
student_id	age	gender	education_level	family_income	parent_education	previous_exam_score	previous_gpa	attendance_percentage	assignment_completion_rate	...	exam_difficulty	exam_preparation_days	questions_correct	time_management_score	exam_anxiety_level	exam_score	performance_grade	pass_status	performance_level	total_effort_score
0	STU_000001	20	Female	High School	Middle	High School	78.36	2.95	81.490000	65.18	...	Medium	27	86	78.398551	9.39	90.40	A	Pass	High	8.94
1	STU_000002	17	Male	High School	Middle	High School	73.40	2.89	84.616882	76.53	...	Easy	4	86	87.170000	6.31	86.21	A	Pass	High	8.42
2	STU_000003	18	Other	Undergraduate	Middle	Master	82.76	3.35	100.000000	70.39	...	Easy	28	74	63.770000	9.87	76.11	B	Pass	Medium	3.56
3	STU_000004	20	Male	High School	Middle	High School	60.61	2.57	84.910000	75.06	...	Medium	16	77	59.510000	9.68	79.74	B	Pass	Medium	11.89
4	STU_000005	16	Female	High School	High	Bachelor	74.79	2.84	88.210000	61.54	...	Medium	28	52	84.640000	10.00	50.66	D	Pass	Low	3.13
5 rows × 31 columns


df.tail()
     
student_id	age	gender	education_level	family_income	parent_education	previous_exam_score	previous_gpa	attendance_percentage	assignment_completion_rate	...	exam_difficulty	exam_preparation_days	questions_correct	time_management_score	exam_anxiety_level	exam_score	performance_grade	pass_status	performance_level	total_effort_score
99995	STU_099996	17	Male	Undergraduate	Upper-Middle	High School	78.73	2.780892	89.67	60.97	...	Medium	5	62	76.130000	8.36	66.46	C	Pass	Medium	4.66
99996	STU_099997	14	Female	High School	Upper-Middle	Bachelor	75.70	2.980000	83.87	94.38	...	Easy	24	91	84.290000	8.68	96.54	A	Pass	High	14.59
99997	STU_099998	16	Female	High School	Upper-Middle	High School	84.69	3.270000	89.57	71.28	...	Medium	24	65	62.320000	9.97	74.66	C	Pass	Medium	4.95
99998	STU_099999	15	Female	High School	High	Master	74.70	3.060000	92.61	69.26	...	Medium	28	81	100.000000	10.00	85.85	A	Pass	High	8.27
99999	STU_100000	18	Female	Undergraduate	Lower-Middle	High School	76.73	2.970000	90.32	81.80	...	Medium	1	52	78.398551	10.00	54.40	D	Pass	Low	6.61
5 rows × 31 columns


df.columns.to_list()
     
['student_id',
 'age',
 'gender',
 'education_level',
 'family_income',
 'parent_education',
 'previous_exam_score',
 'previous_gpa',
 'attendance_percentage',
 'assignment_completion_rate',
 'class_participation',
 'study_hours_per_day',
 'self_study_hours',
 'study_consistency',
 'study_environment',
 'study_method',
 'practice_tests_completed',
 'sleep_hours',
 'break_frequency',
 'stress_level',
 'device_availability',
 'exam_difficulty',
 'exam_preparation_days',
 'questions_correct',
 'time_management_score',
 'exam_anxiety_level',
 'exam_score',
 'performance_grade',
 'pass_status',
 'performance_level',
 'total_effort_score']

# Checking the shape of the dataset

df.shape
     
(100000, 31)

# Checking any duplicates remains

df.duplicated().sum()
     
np.int64(0)

df.info()
     
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 100000 entries, 0 to 99999
Data columns (total 31 columns):
 #   Column                      Non-Null Count   Dtype  
---  ------                      --------------   -----  
 0   student_id                  100000 non-null  object 
 1   age                         100000 non-null  int64  
 2   gender                      100000 non-null  object 
 3   education_level             100000 non-null  object 
 4   family_income               100000 non-null  object 
 5   parent_education            100000 non-null  object 
 6   previous_exam_score         100000 non-null  float64
 7   previous_gpa                100000 non-null  float64
 8   attendance_percentage       100000 non-null  float64
 9   assignment_completion_rate  100000 non-null  float64
 10  class_participation         100000 non-null  object 
 11  study_hours_per_day         100000 non-null  float64
 12  self_study_hours            100000 non-null  float64
 13  study_consistency           100000 non-null  object 
 14  study_environment           100000 non-null  object 
 15  study_method                100000 non-null  object 
 16  practice_tests_completed    100000 non-null  int64  
 17  sleep_hours                 100000 non-null  float64
 18  break_frequency             100000 non-null  object 
 19  stress_level                100000 non-null  int64  
 20  device_availability         100000 non-null  object 
 21  exam_difficulty             100000 non-null  object 
 22  exam_preparation_days       100000 non-null  int64  
 23  questions_correct           100000 non-null  int64  
 24  time_management_score       100000 non-null  float64
 25  exam_anxiety_level          100000 non-null  float64
 26  exam_score                  100000 non-null  float64
 27  performance_grade           100000 non-null  object 
 28  pass_status                 100000 non-null  object 
 29  performance_level           100000 non-null  object 
 30  total_effort_score          100000 non-null  float64
dtypes: float64(11), int64(5), object(15)
memory usage: 23.7+ MB
The df.describe() function was used to get a summary of the numerical columns in the dataset. It provides information such as count, mean, standard deviation, minimum value, maximum value, and percentile values. This helps to understand the overall distribution and range of the data before performing further analysis.


df.describe()
     
age	previous_exam_score	previous_gpa	attendance_percentage	assignment_completion_rate	study_hours_per_day	self_study_hours	practice_tests_completed	sleep_hours	stress_level	exam_preparation_days	questions_correct	time_management_score	exam_anxiety_level	exam_score	total_effort_score
count	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000	100000.000000
mean	17.005740	69.531033	2.780892	84.616882	69.724405	2.995725	2.094970	5.509170	6.995102	9.375640	15.501440	57.298240	78.398551	8.927373	61.950072	5.750310
std	1.999562	11.379108	0.459206	7.521644	12.127179	1.719466	1.266066	2.501131	1.200874	1.081613	8.644356	15.028787	13.410057	1.354875	15.863644	2.453408
min	14.000000	30.000000	1.000000	46.340000	20.000000	0.500000	0.250000	0.000000	3.000000	5.000000	1.000000	0.000000	17.030000	1.000000	0.000000	0.500000
25%	15.000000	61.820000	2.490000	79.900000	61.480000	1.720000	1.170000	4.000000	6.180000	9.000000	8.000000	47.000000	69.990000	8.220000	51.240000	3.990000
50%	17.000000	69.530000	2.780892	84.616882	69.570000	2.670000	1.840000	5.000000	7.000000	10.000000	16.000000	57.000000	78.398551	9.490000	61.960000	5.400000
75%	19.000000	77.232500	3.070000	89.500000	77.920000	3.910000	2.730000	7.000000	7.810000	10.000000	23.000000	67.000000	87.980000	10.000000	72.730000	7.110000
max	20.000000	100.000000	4.000000	100.000000	100.000000	12.000000	10.000000	20.000000	11.000000	10.000000	30.000000	100.000000	100.000000	10.000000	100.000000	21.150000
The df.describe(include='object') function was used to get a summary of the categorical columns in the dataset. It provides information such as the number of unique values, the most frequently occurring value, and its frequency. This helps to understand the different categories present in the dataset before further analysis.


df.describe(include='object')
     
student_id	gender	education_level	family_income	parent_education	class_participation	study_consistency	study_environment	study_method	break_frequency	device_availability	exam_difficulty	performance_grade	pass_status	performance_level
count	100000	100000	100000	100000	100000	100000	100000	100000	100000	100000	100000	100000	100000	100000	100000
unique	100000	3	2	5	5	3	3	3	5	3	2	3	5	2	3
top	STU_099984	Male	High School	Middle	High School	Medium	Medium	Quiet	Flashcards	Occasionally	Dedicated	Medium	D	Pass	Low
freq	1	49130	59752	30112	34648	50109	55137	49789	20239	49866	74827	50242	34886	77389	45123
Importing libraries which are nedded
Matplotlib
Seaborn
Plotly

# importing libraries which is needed

import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
     
1: Study Hours vs Exam Score (Using Scatter plot)

# Scatter plot of Study hours vs Exam score

plt.figure(figsize=(7,5))
sns.set_style('whitegrid')
sns.scatterplot(data=df, x='study_hours_per_day', y= 'exam_score', marker= 'o', color='teal')
plt.title('Study Hours v/s Exam Score')
plt.xlabel('Study Hours per day')
plt.ylabel('Exam Score')
plt.show()
     

The scatter plot shows a positive relationship between study hour per day and exam score. As the study hours increases the students are achieving a higher exam score .

However, as we can see the points are widely scattered which means that study hours per day alone do not completely determine exam performance. Other factors may also influence student's scores.

2: Previous Exam Score vs Exam Score

plt.figure(figsize=(7,5))
sns.set_style('whitegrid')
sns.scatterplot(data= df, x='previous_exam_score', y='exam_score', marker='o', color='steelblue')
plt.title('Previous Exam Score v/s Exam Score')
plt.xlabel('Previous Exam Score')
plt.ylabel('Exam Score')
plt.show()
     

In this scatter plot shows a good positive relationship between previous_exam_score and current_exam_score. Students with higher previous score are scoring high marks in the current exam score .As we can see the graph moving left bottom to right corner

This suggest that previous academic performance is an important indicator of current performance

3: Distribution of Exam Score

plt.figure(figsize=(7,5))
sns.histplot(df['exam_score'], bins=30, kde=True, color='red')
plt.title('Distribution of Exam Score')
plt.xlabel('Exam Score')
plt.ylabel('Frequency')
plt.show()
     

Insight
In here the graph shows that the exam score are approximately normaly distributed, with most students scoring around 50-70 marks

The highest concentration of students is around 55-65 marks
A very few students scored below 20
The number of students gradually decreases as score move away from the center
Score above 90 are also less frequant
The exam scores are mainly concentrated between around 40 and 80, with most students scoring around the 60–70 range. The graph is in a bell shape which means very low and very high scores are less common. This shows that the majority of students have moderate exam performance.

4: Exam Score Outliers

# Exam score outliers

fig = px.box(df, y='exam_score', title='Exam Score Outlier Check',
              labels={'exam_score': 'Exam Score'})
fig.show()
     
Insight
The box plot shows that the typical exam score is around 62, with most students scoring between 51 and 73. A few number of students have usually low scores

Median = 61.96
Q1 = 51.24
Q3 = 72.73
The low scored students are below 19.02
The box plot shows that exam scores range from 0 to 100, with the median score around 62. There are no major outliers beyond the normal range, indicating that the exam score data is generally within a reasonable range and small number of students have unusually low scores, which may the students who are stuggling academically

5: Exam Performance Level Using Violin Plot

fig = px.violin(df, x='performance_level', y='exam_score', color='performance_level', box=True, points=False,
                title='Exam Performance Distribution by Performance Level',
                labels={'exam_score':'Exam Score','performance_level': 'Performance Level'})
fig.show()
     
Insight
High Performance : Score are concentrated around 80-90, with the center around the mid-to-high 80s
Medium Performance : Score are mainly around 60-75, with the center around the upper 60s
Lower Performance : Score are mostly around 40-60, with the center around the low-to-mid 50s. It also has a wider spread toward lower scores
The violin plot shows a clear difference in exam scores across the three performance levels. High-performing students have scores mainly around 80–90, medium-performing students are concentrated around 60–75, while low-performing students generally have lower scores around 40–60. This shows that exam scores clearly distinguish the different performance levels.
6: Correlation of Heatmap of all Numerical values

plt.figure(figsize=(12,9))
numerical_columns = df.select_dtypes(include=['int64','float64']).columns
sns.heatmap(df[numerical_columns].corr(), annot=True, fmt='.2f', cmap='coolwarm', linewidths=0.5)
plt.title('Correlation Heatmap of Numerical Values',fontsize=14)
plt.show()
     

Insight
The strogest relationship with exam score is "questions_correct"(0.98). This means students who answer more questions correctly tend to have higher exam scores.

There is also a moderate positive relationship with previous exam score, previous GPA, total effort, and study hours.

While stress level(-0.16) and exam anxiety level (-0.13) have weak negative relationships with exam score.Which meaning that the higher stress/anxiety can cause lower score in the student exam performance

7: Stress Level by Sleep Hours

# Creating sleep groups
df['sleep_group'] = pd.cut(
    df['sleep_hours'],
    bins=[0, 5, 7, 12],
    labels=['Low Sleep', 'Moderate Sleep', 'High Sleep']
)

fig = px.box(
    df,
    x='sleep_group',
    y='stress_level',
    title='Stress Level by Sleep Hours',
    labels={
        'sleep_group': 'Sleep Hours',
        'stress_level': 'Stress Level'
    }
)

fig.show()
     
Insight from the Stress Level by Sleep Hours
Low sleep students generally show higher stress levels (9–10)

Moderate sleep students also mostly have high stress levels (8–10)

High sleep students show a wider range of stress levels, including lower levels around 5–7

Overall, more sleep is associated with lower stress levels in some students

The relationship varies between students, so sleep hours alone do not explain stress levels.

8: Break Frequancy vs Avg Exam Score

avg_break = df.groupby('break_frequency')['exam_score'].mean().reindex(['Rarely','Occasionally','Frequently'])

plt.figure(figsize=(7,5))
avg_break.plot(kind='bar', color='orange')
plt.title('Break Frequency vs Average Exam Score', fontsize=13)
plt.xlabel('Break Frequency')
plt.ylabel('Average Exam Score')
plt.xticks(rotation=0)
plt.show()
     

Insight
This bar chart compares the averag exam score based on the how Frequently students take breaks

Rarely: average score is about 61 - 64
Occasionally: average score is about 61 - 64
Frequently: average score is about 61 - 64
The average exam scores are almost the same for students who take breaks rarely, occasionally, or frequently, at around 62. So break frequancy does not affect much in students exam performance

9: Study Hours vs Performance Level

fig = px.box(df, x='performance_level', y='study_hours_per_day', color='performance_level',
                title='Study Hours by Performance Level',
                labels={'performance_level': 'Performance Level', 'study_hours_per_day': 'Study Hours per Day'})
fig.show()
     
Insight
High Performance Students: They have the highest typical study time, with a median of 4 hours/day
Medium Performance Students: This students have the median of around 3hours/day
Low Performance Students: This students have the lowest median, around 2hours/day
The medium study hours decreases from about 4 hours for high performance to 3 hours for medium performance and 2 hours for low performers.Which means that Study hours plays an important role in the performance of students the higher study hour increases the performance also increases

10: Exam Score vs Stress Level

avg_stress =df.groupby('stress_level')['exam_score'].mean().reset_index()

fig = px.line(avg_stress, x='stress_level', y= 'exam_score', markers=True,
              title='Average Exam Score by Stree Level',
              labels={'stress_level':'Stress Levell','exam_score':'Exam Score'})
fig.show()
     
Insight
This graph shows a clear negative relationship between stress level and average exam score. As stress level increases from 5 to 10, the avg exam score decreases from abhout 76 to 61.

Which means students with higher stress level tend to have a lower exam scores

11: Pass vs Fail

fig = px.pie(df, names='pass_status',title='Pass v/s Fail Propotion')
fig.show()
     
Insight
The pie chart shows that 77.4% of students passed the exam, while 22.6% failed. This shows that the majority of the students were able to pass the exam, although nearly one fourth of the students did not pass



     
FINAL INSIGHT OF THE DATA
STUDENT EXAM PERFORMANCE ANALYSIS
Using Python — Data Analytics Final Project

Project Information
Project Name: Data Analytics Final Project

Project Title: Student Exam Performance Analysis using Python

Domain: Education / Academic Performance Analytics

Student Name:	Rakend Vijayan K.

Batch: DA/ML-DAF50

Dataset: student_exam_performance

Dataset Source:	Kaggle

Tools Used:	Python, Pandas, NumPy, Matplotlib, Seaborn, Plotly Express

1. Project Overview
Student academic performance is shaped by a wide range of factors — study habits, attendance, lifestyle choices, and socio-demographic background among them — yet raw educational data is often messy, incomplete, and cluttered with attributes that carry little real signal. This makes it difficult for educators and institutions to draw meaningful, reliable insights into what actually drives student success.

This project cleans, pre-processes, and analyzes the student exam performance dataset to identify the behavioral and academic factors most strongly associated with exam outcomes. Statistical summaries and visualizations are used throughout to surface patterns and relationships that could support academic interventions, early performance prediction, or student support strategies.

2. Project Workflow
Step 1 → Importing files & Libraries

Step 2 → Data Cleaning & Pre-proccesing

Step 3 → EDA & Visualization

Step 4 → Final Findings & Presentation

Step 1 — Importing files & Liabraraies
1.1 Importing Required Libraries

import pandas as pd

import numpy as np

Python libraries were imported to support data manipulation, numerical operations, cleaning, and analysis.

1.2 Importing the Dataset

df = pd.read_csv("student_exam_performance.csv")

The student exam performance dataset was imported using Pandas. Once loaded, the data was checked to understand its structure, columns, data types, and overall contents before any cleaning began.

1.3 Checking the Dataset

df

df.shape

df.columns

df.info()

These checks confirmed the number of rows and columns, the column names, the data types, and the count of non-null values in each column — giving a clear picture of the dataset's structure before cleaning.

Step 2 — Data Cleaning and Pre-Processing
Data cleaning and pre-processing is a foundational step in preparing any dataset for analysis. It surfaces errors and missing values and gives a clear picture of what needs to be fixed before the data can be reliably explored and visualized.

2.1 Checking Missing Values

df.isnull().sum()

Each column was checked for missing values using isnull().sum(), identifying which columns required treatment before analysis.

2.2 Handling Missing Values

Numerical columns — filled with the mean

df['previous_gpa'].fillna(df['previous_gpa'].mean(), inplace=True)

df['attendance_percentage'].fillna(df['attendance_percentage'].mean()inplace=True)

df['time_management_score'].fillna(df['time_management_score'].mean(), inplace=True)

Categorical columns — filled with the mode

df['parent_education'].fillna(df['parent_education'].mode()[0], inplace=True)

df['notes_quality'].fillna(df['notes_quality'].mode()[0], inplace=True)

df['device_availability'].fillna(df['device_availability'].mode()[0], inplace=True)

df['sleep_quality'].fillna(df['sleep_quality'].mode()[0], inplace=True)

Missing values in the numerical columns (previous_gpa, attendance_percentage, time_management_score) were filled with the column mean, since this preserves the overall distribution without being distorted by outliers. Missing values in the categorical columns (parent_education, notes_quality, device_availability, sleep_quality) were filled with the column mode, the most representative category.

The dataset was then re-checked to confirm no missing values remained:

df.isnull().sum()

0 missing values across all columns

2.3 Checking Duplicate Records

df.duplicated().sum()

the out put is 0 which means no duplicate records were found, confirming the dataset does not contain repeated entries that could bias the analysis.

2.4 Selecting and Removing Unnecessary Columns

Before dropping any column, every categorical and numerical field was compared against exam_score to check whether it actually carried a meaningful relationship with performance.

Categorical columns — average exam_score by category
categorical_cols = ['school_type', 'urban_rural', 'notes_quality',
                     'educational_app_usage', 'revision_frequency',
                     'sleep_quality', 'motivation_level']`

for col in categorical_cols:
    print(f"---{col}---")
    print(df.groupby(col)['exam_score'].mean())

Column	Category avg (exam_score)
| school_type | Charter 61.6 , Private 62.0 , Public 61.9 | urban_rural | Rural 61.8 , Suburban 62.0 , Urban 61.9 | |notes_quality |Average 62.0 · Excellent 61.9 · Poor 61.7 | | educational_app_usage | High 61.9 · Low 61.9 · Moderate 61.9 | | revision_frequency | Daily 61.9 · Rarely 61.9 · Weekly 61.9|

For every one of these columns, the average exam_score barely moves between categories — the values cluster tightly around 60–62 regardless of which group a student falls into. If a column genuinely mattered, its categories would separate high scorers from low scorers; none of these do, so they carry no useful signal for this analysis.

Numerical columns — correlation with exam_score
numeric_cols = ['age', 'previous_exam_score', 'previous_gpa', 'attendance_percentage',
    'assignment_completion_rate', 'study_hours_per_day', 'self_study_hours',
    'private_tuition', 'online_learning_hours', 'practice_tests_completed',
    'sleep_hours', 'daily_screen_time', 'physical_activity_hours',
    'stress_level', 'internet_access', 'online_course_hours',
    'exam_preparation_days', 'questions_attempted', 'questions_correct',
    'time_management_score', 'exam_anxiety_level', 'exam_score']

for col in numeric_cols:
    corr = df[col].corr(df['exam_score'])
    print(f"{col}: correlation = {corr:.5f}")
Column	Correlation with exam_score
age	-0.003
|private_tuition | 0.004 |online_learning_hours | -0.003 |daily_screen_time | 0.005 |physical_activity_hours | -0.0003 |internet_access | 0.002 |online_course_hours | 0.0007 |questions_attempted | 0.004

All eight columns round to essentially 0.00 correlation with exam_score. Whether a student is older or younger, takes private tuition, or spends more time online makes no measurable difference to their exam performance in this dataset — so these columns were removed as noise.

Final drop list
columns_to_drop = [
    # Categorical - no real difference across categories
    'school_type', 'urban_rural', 'notes_quality',
    'educational_app_usage', 'revision_frequency',
    'sleep_quality', 'motivation_level',

    # Numerical - correlation ~0.00, no relationship
    'private_tuition', 'online_learning_hours',
    'daily_screen_time', 'physical_activity_hours',
    'internet_access', 'online_course_hours', 'questions_attempted',
]

df = df.drop(columns=columns_to_drop)
The dataset was trimmed from 44 columns down to 30 — every dropped column had already been shown, by correlation or group-mean comparison, to have no meaningful relationship with exam_score.

2.5 Creating a Derived Column — total_effort_score

df['total_effort_score'] = df['study_hours_per_day'] + (df['practice_tests_completed'] / 2)

A new column, total_effort_score, was engineered by combining study_hours_per_day with practice_tests_completed. Blending these two effort-related signals into a single measure makes it easier to analyze the overall relationship between student effort and exam performance in the visualizations that follow.

2.6 Checking Data Types

df.dtypes

All numerical and categorical columns were already stored in appropriate data types, so no type conversions were required — the dataset was ready for exploratory analysis.

Step 3 — EDA and Visualization
Exploratory Data Analysis (EDA) and visualization were performed on the cleaned dataset to understand the distribution of exam scores and to identify relationships between different factors and student performance. A mix of statistical summaries and Matplotlib, Seaborn, and Plotly Express visualizations were used to surface meaningful patterns and trends.

3.1 Descriptive Statistics — Numerical Data

df.describe()

df.describe() returns count, mean, standard deviation, minimum, maximum, and percentile values for every numerical column, giving an overall sense of range and distribution before deeper analysis.

3.2 Descriptive Statistics — Categorical Data

df.describe(include='object')

df.describe(include='object') summarizes the categorical columns — the number of unique values, the most frequent category, and its frequency — clarifying which categories dominate the dataset.

3.3 Study Hours vs Exam Score (Scatter Plot)

Purpose

This visualization was created to understand whether the number of study hours per day is related to students' exam scores.

Screenshot 2026-09-25 160955.png

Finding

The graph shows a positive relationship between study hours and exam score. Students who spend more time studying generally tend to achieve higher exam scores. However, the points are widely scattered, which indicates that study hours alone do not completely determine exam performance and other factors may also influence the scores.

3.4 Previous Exam Score vs Exam Score

Purpose

This visualization was created to understand the relationship between students' previous exam scores and their current exam scores.

Screenshot 2026-09-25 161720.png

Finding

The graph shows a positive relationship between previous exam score and current exam score. Students who scored higher in their previous exam generally tend to achieve higher scores in the current exam as well. However, the points are widely scattered, which shows that previous exam score alone does not completely determine current exam performance. Other factors may also be related to students' performance.

3.5 Distribution of Exam Score

Purpose

This visualization was created to understand how the exam scores are distributed among the students and to identify the score range where most students are concentrated.

Screenshot 2026-09-25 161734.png

Finding

The graph shows that most students' exam scores are concentrated around the 50 to 75 range, with the highest frequency appearing around 60 to 65. Very low and very high scores are less common compared to the middle score range. Overall, the distribution shows that most students have moderate exam scores.

3.6 Exam Score Outlier Check (Box Plot)

Purpose

This visualization was created to check the distribution of exam scores and identify whether there are any unusual or extreme values in the dataset.

Screenshot 2026-09-25 161755.png

Finding

The box plot shows that the median exam score is around 62, while most of the scores are between approximately 51 and 73. The minimum score is 0 and the maximum score is 100. There are some low scores below the lower fence of 19.02, which can be considered potential outliers. This shows that the dataset contains a few unusually low exam scores.

3.7 Exam Performance by Performance Level (Violin Plot)

Purpose

This visualization was created to compare the distribution of exam scores among students with different performance levels: High, Medium, and Low.

Screenshot 2026-09-25 161818.png

Finding

The graph shows a clear difference in exam scores across the three performance levels. High-performing students generally have scores between 80 and 100, while medium-performing students are mainly between 60 and 80. Low-performing students mostly have scores between 40 and 60, with some lower scores as well. This shows that the performance levels are clearly separated based on students' exam scores.

3.8 Correlation Heatmap

Purpose

This visualization was created to understand the relationships between the numerical variables in the dataset and identify which variables have a stronger or weaker relationship with exam score.

Screenshot 2026-09-25 161841.png

Finding

The heatmap shows that questions correct has a very strong positive relationship with exam score (0.98). Previous exam score also shows a positive relationship with exam score (0.49), followed by previous GPA (0.45) and total effort score (0.42). Study hours per day has a positive relationship with exam score (0.36). Stress level and exam anxiety level show weak negative relationships with exam score. Overall, the heatmap helps to identify the variables that have stronger and weaker relationships with students' exam scores.

3.9 Stress Level by Sleep Hours

Purpose

This visualization was created to compare the stress levels of students based on their sleep hours and to understand whether sleep duration is related to stress level.

Screenshot 2026-09-27 142742.png

Finding

The graph shows that students in the Low Sleep group mostly have high stress levels, mainly around 9–10. The Moderate Sleep group also shows relatively high stress levels, mostly between 8 and 10. The High Sleep group has a wider range of stress levels, including some students with lower stress levels of 5–7. Overall, the graph suggests that students with more sleep can have lower stress levels, although the relationship is not the same for every student

3.10 Break Frequency vs Average Exam Score (Bar Chart)

Purpose

This visualization was created to understand whether the frequency of taking breaks is related to students' average exam scores.

Screenshot 2026-09-25 164543.png

Finding

The graph shows that the average exam scores are very similar for students who take breaks rarely, occasionally, or frequently, with all three groups having an average score of around 62. This indicates that break frequency does not show a major difference in the average exam scores in this dataset.

3.11 Study Hours vs Performance Level (Box Plot)

Purpose

This visualization was created to compare the number of study hours per day among students with different performance levels: High, Medium, and Low.

Screenshot 2026-09-25 164555.png

Finding

The graph shows that high-performing students generally spend more time studying compared to medium- and low-performing students. The median study time is around 4 hours for high performers, 3 hours for medium performers, and 2 hours for low performers. This suggests that higher study hours are associated with higher performance levels, although there are some variations within each group.

3.12 Exam Score vs Stress Level (Line Chart)

Purpose

This visualization was created to understand the relationship between stress level and students' average exam scores.

Screenshot 2026-09-25 164612.png

Finding

The graph shows that the average exam score decreases as the stress level increases. The average score is around 76 at stress level 5 and gradually decreases to around 60 at stress level 10. This indicates a negative relationship between stress level and exam score, where higher stress levels are associated with lower average exam scores.

3.13 Pass vs Fail (Pie Chart)

Purpose

This visualization was created to understand the proportion of students who passed and failed the exam.

Screenshot 2026-09-25 164635.png

Finding

The graph shows that 77.4% of the students passed the exam, while 22.6% of the students failed. This means that the majority of the students in the dataset were able to pass the exam, while a smaller portion did not pass.

Step 4 — Overall Findings
The analysis of the student exam performance dataset shows that several factors are consistently associated with exam outcomes. Previous exam score has a clear positive relationship with current exam score, indicating that students who performed well before generally continue to perform well. Study hours also show a positive relationship with performance — high-performing students study noticeably more, on average, than medium- and low-performing students. Stress level shows a negative relationship with average exam score: as stress rises, average performance falls. Sleep hours and stress level also show a relationship, where students with lower sleep generally tend to have higher stress levels, while students with higher sleep show some lower stress levels. Break frequency, by contrast, shows almost no difference in average exam scores across groups. The performance-level analysis clearly separates high, medium, and low-performing students on the basis of their exam scores. Overall, 77.4% of students passed the exam, while 22.6% failed.

Through this project, the dataset was cleaned and prepared, explored using statistical methods, visualized from multiple angles, and interpreted to surface the main patterns and relationships in student exam performance.

Conclusion
This project demonstrates how data cleaning, pre-processing, EDA, and visualization come together to analyze real-world academic performance data. After cleaning the dataset, a range of academic, study, and behavioral factors were compared against exam scores. The resulting visualizations highlighted the most important patterns — particularly the relationships between previous academic performance, study hours, stress levels, and current exam scores — providing a clearer, evidence-based understanding of what is associated with student performance in this dataset.



     
