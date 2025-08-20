# 🐍 Python Assignments – Data Analysis

This repository contains my **Python assignments** from the Data Science course.  
Each assignment is exported as an **HTML file** (from Jupyter Notebook) for easy viewing.  

## 🐍 Python List Programs  

This repository contains simple Python programs demonstrating **list operations** such as sum, min/max, empty check, count occurrences, sorting, and nested list check.  

---

## 📑 Table of Contents
1. [Sum of all elements in a list](#1️⃣-sum-of-all-elements-in-a-list)  
2. [Find largest and smallest element](#2️⃣-find-largest-and-smallest-element-in-a-list)  
3. [Check if list is empty](#3️⃣-program-to-check-if-list-is-empty-or-not)  
4. [Count occurrences of a specific element](#4️⃣-count-the-number-of-occurrences-of-specific-element-in-the-list)  
5. [Sort numbers and strings separately](#5️⃣-create-a-list-of-string-number-and-sort-both-in-result)  
6. [Check if a list contains another list](#6️⃣-check-whether-a-list-contain-any-list-or-not)  

---

## 1️⃣ Sum of all elements in a list
```python
numbers = [10, 50, 80, 40, 90]
total_sum = sum(numbers)
print("The sum of all elements in a list is:", total_sum)

✅ Output:
The sum of all elements in a list is: 270
```

## 2️⃣ Program to find largest and smallest element in the list
```python
numbers = [90, 45, 5, 85, 50, 15]
smallest = min(numbers)
largest = max(numbers)

print("The smallest element in a list is:", smallest)
print("The largest element in a list is:", largest)

✅ Output:

The smallest element in a list is: 5
The largest element in a list is: 90
```
3️⃣ Program to check if list is empty or not
```python
my_list = []
if not my_list:
    print("The list is empty.")
else:
    print("The list is not empty.")

my_list = [40, 50, 60]
if not my_list:
    print("The list is empty.")
else:
    print("The list is not empty.")


✅ Output:

The list is empty.
The list is not empty.
```
4️⃣ Count the number of occurrences of specific element in the list
```python
my_list = [25, 45, 85, 4, 42, 29, 85, 72, 66]
element_to_count = 72
count = my_list.count(element_to_count)

print(f"The element {element_to_count} occurs {count} times in a list.")


✅ Output:

The element 72 occurs 1 times in a list.
```
5️⃣ Create a list of string & number and sort both in result
```python
mixed_list = ['tejas', 20, 'langhe', 10, 'college', 22, 'data', 55]

numbers = [item for item in mixed_list if isinstance(item, (int, float))]
strings = [item for item in mixed_list if isinstance(item, str)]

numbers.sort()
strings.sort()

sorted_list = numbers + strings
print("Sorted list(numbers first, then strings):", sorted_list)


✅ Output:

Sorted list(numbers first,then strings): [10, 20, 22, 55, 'college', 'data', 'langhe', 'tejas']
```
6️⃣ Check whether a list contain any list or not
```python
list1 = [11, 22, 33, 44, [5, 6]]

for i in list1:
    if type(i) == list:
        print('list present')


✅ Output:
list present
```
# 🐼 Python Pandas Project – Hitters Dataset  

This project demonstrates basic **data analysis with Pandas** on the `hitters.csv` dataset.  
It includes operations like missing value detection, filtering, grouping, and sorting.  

---

## 1️⃣ Load Dataset & Show Missing Values
```python
import pandas as pd

df = pd.read_csv("hitters.csv")
df.isna().sum()

✅ Output:

Name          0
AtBat         0
Hits          0
HmRun         0
Runs          0
RBI           0
Walks         0
Years         0
CAtBat        0
CHits         0
CHmRun        0
CRuns         0
CRBI          0
CWalks        0
League        0
Division      0
PutOuts       0
Assists       0
Errors        0
Salary       59
NewLeague     0
dtype: int64
```
2️⃣ Find Players Who Have Batted More Than 400 Times
```python
df1 = df[df['AtBat'] > 400]
print(df1[['Name','AtBat']])


✅ Output (sample):

                Name  AtBat
2        Alvin Davis    479
3       Andre Dawson    496
5    Alfredo Griffin    594
9     Andre Thornton    401
10     Alan Trammell   574
...
317     Willie McGee    497
318  Willie Randolph    492
319   Wayne Tolleson   475
320    Willie Upshaw   573
321    Willie Wilson   631
[151 rows x 2 columns]
```
3️⃣ Player Who Has Hit Maximum Home Runs
```python
A = df.groupby(by=['Name'])['HmRun'].max()
A


✅ Output (sample):

Al Newman           1
Alan Ashby          7
Alan Trammell      21
Alan Wiggins        0
Alex Trevino        4
...
Will Clark         11
Willie McGee        7
Willie Randolph     5
Willie Upshaw       9
Willie Wilson       9
Name: HmRun, Length: 322, dtype: int64
```
4️⃣ League-Wise Total Number of Players
```python
df.groupby('League')['Name'].count()


✅ Output:

League
A    175
N    147
Name: Name, dtype: int64
```
5️⃣ Division-Wise Total Salary Investment
```python
df.groupby('Division')['Salary'].sum()


✅ Output:

Division
E    80531.006
W    60417.501
Name: Salary, dtype: float64
```
6️⃣ Five Most Senior Players
```python
df.sort_values(by=['Years'], ascending=False).head(5)


✅ Output:

            Name  AtBat  Hits  HmRun  Runs  RBI  Walks  Years  ...
236     Pete Rose    237    52      0    15   25     30     24  ...
302    Tony Perez    200    51      2    14   29     25     23  ...
121  Graig Nettles   354    77     16    36   55     41     20  ...
249 Reggie Jackson   419   101     18    65   58     92     20  ...
306   Ted Simmons    127    32      4    14   25     12     19  ...
[5 rows x 21 columns]
```
# 🚗 Cars93 Dataset Analysis (Python + Pandas)

This project demonstrates exploratory data analysis (EDA) using the **Cars93.csv** dataset.  
We analyze car models, mileage, price ranges, and other attributes.

---

## 📌 Dataset
- File: `Cars93.csv`  
- Rows: 93  
- Columns: 28  

---

## 1️⃣ Find Car Having Highest Mileage in City
```python
df.sort_values(by=['MPG.city'], ascending=False).head(5)

✅ Output (Top 5 Cars by City Mileage):

objectivec
Copy
Edit
   Manufacturer   Model     MPG.city   MPG.highway
38  Geo          Metro          46          50
41  Honda        Civic          42          46
82  Suzuki       Swift          39          43
79  Subaru       Justy          33          37
83  Toyota       Tercel         32          37
```
2️⃣ Find Models of Cars Having Price Between 17 and 25
```python
A = df[(df.Price > 17) & (df.Price < 25)]
A[['Manufacturer','Model','Price']]


✅ Output (sample):

   Manufacturer   Model        Price
7   Buick        Roadmaster   23.7
17  Chevrolet    Caprice      18.8
19  Chrylser     Concorde     18.4
40  Honda        Prelude      19.8
42  Honda        Accord       17.5
84  Toyota       Celica       18.4
... (total 27 cars)
```
3️⃣ Find Top 7 Most Fuel-Efficient Cars for Highway
```python
df.sort_values(by=['MPG.highway'], ascending=False).head(7)


✅ Output:

   Manufacturer   Model     MPG.highway
38  Geo          Metro            50
41  Honda        Civic            46
82  Suzuki       Swift            43
72  Pontiac      LeMans           41
78  Saturn       SL               38
83  Toyota       Tercel           37
79  Subaru       Justy            37
```
4️⃣ Find Compact Cars Below Price 20 with No Airbags
```python
A = df[(df['AirBags'] == 'None') & (df['Type'] == 'Compact') & (df['Price'] < 20)]
A


✅ Output:

No such cars found (0 rows).
```
5️⃣ Find Top 7 Most Fuel-Efficient Cars in City, Sorted by Horsepower
```python
df.sort_values(by=['Horsepower'], ascending=False).head(7)


✅ Output (Top Cars by Horsepower):

   Manufacturer   Model       Horsepower   MPG.city
18  Chevrolet    Corvette       300          17
27  Dodge        Stealth        300          18
10  Cadillac     Seville        295          16
47  Infiniti     Q45            278          17
56  Mazda        RX-7           255          17
49  Lexus        SC300          225          18
58  Mercedes     300E           177          19
```
6️⃣ Find Cars Having Mileage More Than 15 in City
```python
A = df[df['MPG.city'] > 15]


✅ Output:

Total Cars Found: 91
(Sample output below)
Manufacturer   Model     MPG.city
Acura          Integra      25
Acura          Legend       18
Audi           90           20
BMW            535i         22
Toyota         Camry        22
...
```
7️⃣ Find Cars With USA-Based Origin
```python
A = df[df['Origin'] == 'USA']


✅ Output:

Total Cars Found: 48
(Sample output below)
Manufacturer   Model        Origin
Buick          Century       USA
Cadillac       Seville       USA
Chevrolet      Cavalier      USA
Dodge          Spirit        USA
Ford           Taurus        USA
Pontiac        Firebird      USA
Saturn         SL            USA
...
```
