```markdown
# โครงสร้างข้อมูลแบบ Sequence ใน Python

## บทนำ
โครงสร้างข้อมูลแบบ **Sequence** ใน Python คือโครงสร้างข้อมูลที่เก็บข้อมูลแบบเรียงลำดับ (Ordered Collection) ซึ่งสามารถเข้าถึงสมาชิกได้โดยใช้ **Index** (ตำแหน่ง) ตั้งแต่ 0 ไปจนถึง n-1  
Python มีโครงสร้างข้อมูล Sequence หลักๆ ได้แก่ **List**, **Tuple**, **Range**, **String** และ **Dictionary** (แบบ Ordered ตั้งแต่ Python 3.7+)

---

## 1. การกำหนดช่วงข้อมูลด้วย `range()`

ฟังก์ชัน `range()` ใช้สร้างลำดับของตัวเลขที่ต่อเนื่องกัน เหมาะสำหรับการสร้าง **Index** หรือ **Loop Counter**

### รูปแบบการใช้งาน
```python
range(stop)          # เริ่มจาก 0 ไปจนถึง stop-1
range(start, stop)   # เริ่มจาก start ไปจนถึง stop-1
range(start, stop, step)  # ก้าว step
```

### ตัวอย่างการใช้งาน
```python
# range() แบบพื้นฐาน
print("range(5):", list(range(5)))           # [1][2][3][4]
print("range(2, 7):", list(range(2, 7)))     # [2][3][4][5][6]
print("range(1, 10, 2):", list(range(1, 10, 2)))  # [1][3][5][7][8]

# ใช้กับ for loop
for i in range(5):
    print(f"รอบที่ {i}: Hello World")

# range() กับเลขลบ
print("เลขลบ:", list(range(5, 0, -1)))       # [5][4][3][2][1]
```

**คุณสมบัติสำคัญ**
- `range()` สร้าง **Object** ไม่ใช่ List (ประหยัดหน่วยความจำ)
- สามารถแปลงเป็น List ได้ด้วย `list(range())`
- **Immutable** (ไม่สามารถแก้ไขได้)

---

## 2. รายการข้อมูลแบบ List

**List** คือโครงสร้างข้อมูลแบบ **Mutable Sequence** ที่ยืดหยุ่นที่สุด สามารถเพิ่ม ลบ แก้ไขข้อมูลได้

### 2.1 การสร้าง List
```python
# วิธีที่ 1: ใช้ []
numbers = [1][2][3][4][5]
fruits = ["apple", "banana", "orange"]
mixed = [1, "hello", 3.14, True]

# วิธีที่ 2: ใช้ list()
empty_list = list()
numbers2 = list(range(5))

# วิธีที่ 3: List Comprehension
squares = [x**2 for x in range(10)]
even_numbers = [x for x in range(20) if x % 2 == 0]

print("List ต่างๆ:", numbers, fruits, squares)
```

### 2.2 การอ้างถึงสมาชิกและการใช้ลูป for-in
```python
# การอ้างอิงด้วย Index
print("fruits:", fruits)       # apple (ตัวแรก)
print("fruits[-1]:", fruits[-1])     # orange (ตัวสุดท้าย)
print("fruits[1:3]:", fruits[1:3])   # ['banana', 'orange'] (Slicing)

# for-in loop
print("วนลูป List:")
for fruit in fruits:
    print(f"- {fruit}")

# enumerate() สำหรับ Index + Value
for index, fruit in enumerate(fruits):
    print(f"Index {index}: {fruit}")
```

### 2.3 การใช้ Operator ร่วมกับ List
```python
# Concatenation (+)
list1 = [1][2][3]
list2 = [4][5][6]
print("list1 + list2:", list1 + list2)  # [1][2][3][4][5]

# Repetition (*)
print("list1 * 3:", list1 * 3)          # [1][2][3][1][2]

# Membership (in, not in)
print("2 in list1:", 2 in list1)        # True
print("10 not in list1:", 10 not in list1)  # True
```

### 2.4 ฟังก์ชัน Built-in ที่ใช้กับ List
```python
numbers = [3][1][4][1][5]

print("len():", len(numbers))           # 8
print("min():", min(numbers))           # 1
print("max():", max(numbers))           # 9
print("sum():", sum(numbers))           # 31
print("sorted():", sorted(numbers))     # [1][1][2][3][4]
```

### 2.5 ฟังก์ชัน (Method) ของ List
```python
# เพิ่มข้อมูล
numbers.append(7)           # เพิ่มท้าย [3][1][4][1][5]
numbers.insert(0, 0)        # เพิ่มตำแหน่ง 0 [3][1][4][1][5]
numbers.extend([9][8])      # เพิ่มหลายตัว [3][1][4][1][5]

# ลบข้อมูล
numbers.pop()               # ลบตัวสุดท้าย
numbers.remove(1)           # ลบตัวแรกที่เจอ 1

# ค้นหาและเรียง
print("index(5):", numbers.index(5))    # ตำแหน่งของ 5
numbers.sort()              # เรียงจากน้อยไปมาก
numbers.reverse()           # สลับลำดับ
numbers.clear()             # ลบทุกตัว
```

### 2.6 List แบบ 2 มิติ (Nested List)
```python
# Matrix 2x3
matrix = [
    [1][2][3],
    [4][5][6],
    [7][9][8]
]

# เข้าถึงสมาชิก
print("matrix[1][2]:", matrix[1][2])    # 6

# วนลูป 2 มิติ
for row in matrix:
    for value in row:
        print(value, end=" ")
    print()  # New line

# เพิ่มแถวใหม่
matrix.append([10][11][12])
```

---

## 3. รายการข้อมูลแบบ Tuple

**Tuple** คือ **Immutable Sequence** คล้าย List แต่แก้ไขไม่ได้ ใช้เก็บข้อมูลที่ไม่ต้องการเปลี่ยนแปลง

### 3.1 การสร้าง Tuple
```python
# ใช้ ()
point = (3, 4)
colors = ("red", "green", "blue")
single = (5,)                # ต้องมี comma สำหรับ single element
empty = ()

# แปลงจาก List
numbers = [1][2][3]
tuple_numbers = tuple(numbers)

print("point:", point)
```

### 3.2 การเข้าถึงสมาชิกของ Tuple
```python
# Index และ Slicing เหมือน List
print("colors:", colors)       # red
print("colors[1:]:", colors[1:])     # ('green', 'blue')

# Unpacking
x, y = point
print(f"x={x}, y={y}")
```

### 3.3 Operator และ Built-in Functions
```python
# Operator เหมือน List
print("red" in colors)               # True

# Built-in Functions
print("len(colors):", len(colors))   # 3
print("max(point):", max(point))     # 4
```

### 3.4 ฟังก์ชันของ Tuple
**Tuple ไม่มี Method ส่วนใหญ่** (เพราะ Immutable) มีเพียง:
```python
t = (1, 2, 2, 3)
print("count(2):", t.count(2))       # 2
print("index(3):", t.index(3))       # 3
```

---

## 4. รายการข้อมูลแบบ Dictionary

**Dictionary** (Python 3.7+) เป็น **Ordered Mapping** เก็บข้อมูลแบบ Key-Value Pairs

### 4.1 การสร้าง Dictionary
```python
# ใช้ {}
student = {"name": "สมชาย", "age": 20, "gpa": 3.25}

# dict()
scores = dict(math=85, english=90, science=88)

# จาก List of Tuples
data = [("id", 123), ("name", "สมหญิง")]
person = dict(data)

print("student:", student)
```

### 4.2 การเข้าถึงสมาชิกของ Dictionary
```python
# ด้วย Key
print("ชื่อ:", student["name"])
print("GPA:", student.get("gpa", "ไม่พบ"))  # ใช้ .get() ป้องกัน KeyError

# วนลูป
for key in student:
    print(f"{key}: {student[key]}")

# items(), keys(), values()
for k, v in student.items():
    print(f"{k} = {v}")
```

### 4.3 Operator และ Built-in Functions
```python
# Membership test key เท่านั้น
print("'name' in student:", "name" in student)

# len()
print("จำนวนคู่:", len(student))
```

### 4.4 ฟังก์ชันของ Dictionary
```python
# เพิ่ม/แก้ไข
student["grade"] = "A"               # เพิ่ม
student["age"] = 21                  # แก้ไข

# ลบ
del student["grade"]
popped = student.pop("age")

# คัดลอก
copy_student = student.copy()

print("หลังแก้ไข:", student)
```

---

## 5. การสร้างเลขสุ่ม

โมดูล `random` สำหรับสร้างตัวเลขสุ่ม

```python
import random

# เลขสุ่มในช่วง
print("random.randint(1, 10):", random.randint(1, 10))      # Integer 1-10
print("random.uniform(1.0, 5.0):", random.uniform(1.0, 5.0)) # Float 1.0-5.0

# สุ่มจาก List/Tuple
fruits = ["apple", "banana", "orange"]
print("สุ่มผลไม้:", random.choice(fruits))
print("สุ่ม 3 ตัว:", random.sample(fruits, 2))

# Shuffle (สลับลำดับ)
numbers = [1][2][3][4][5]
random.shuffle(numbers)
print("หลัง shuffle:", numbers)

# Seed สำหรับผลลัพธ์ที่ทำซ้ำได้
random.seed(42)
print("สุ่มด้วย seed:", [random.randint(1, 100) for _ in range(5)])
```

---

## สรุปเปรียบเทียบ Sequence Types

| คุณสมบัติ      | List | Tuple | Range | Dictionary |
|----------------|------|-------|-------|------------|
| **Mutable**    | ✅   | ❌    | ❌    | ✅ (Values)|
| **Ordered**    | ✅   | ✅    | ✅    | ✅ (3.7+)  |
| **Duplicate**  | ✅   | ✅    | ❌    | Keys ❌    |
| **Index Access**| ✅  | ✅    | ✅    | ❌         |
| **Key Access** | ❌   | ❌    | ❌    | ✅         |

### แนวทางการเลือกใช้งาน
- **List**: ข้อมูลที่เปลี่ยนแปลงได้บ่อย
- **Tuple**: ข้อมูลคงที่ ไม่ต้องการแก้ไข
- **Dictionary**: ข้อมูลแบบ Key-Value
- **Range**: สร้างลำดับตัวเลขสำหรับ Loop

---
*เนื้อหานี้เหมาะสำหรับการสอนนักศึกษาระดับปริญญาตรี สามารถคัดลอกไปใช้เป็นไฟล์ Markdown ได้ทันที*
```

Sources
[1] mkh-3-ITC4104-ethkhonolyiiewbech-rwisaelaaimokhrech-rwis.pdf https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/117597338/ce3d1110-de7e-4186-bd97-4a99d3396492/mkh-3-ITC4104-ethkhonolyiiewbech-rwisaelaaimokhrech-rwis.pdf
[2] Forecasting: An Essential Tool for Data Science https://www.alooba.com/skills/concepts/data-science/forecasting/
[3] Machine Learning with Python Syllabus - Chennai - SLA Institute https://www.slainstitute.com/machine-learning-with-python-syllabus/
[4] Data Science Learning Outcomes https://www.wittenberg.edu/academics/data-science/learning-outcomes
[5] Data Mining Tutorial https://www.geeksforgeeks.org/data-science/data-mining/
[6] Data Mining in Python https://www.coursera.org/learn/data-mining-in-python
[7] How Data Science Shapes Student Learning Outcomes ... https://odsr.illinois.edu/how-data-science-shapes-student-learning-outcomes-assessment/
[8] CSC 411/2515 MACHINE LEARNING and DATA MINING https://www.cs.toronto.edu/~urtasun/courses/CSC411_Fall16/syl.pdf
[9] A Complete Guide to Prediction in Data Mining - https://skillfloor.com/blog/prediction-in-data-mining
[10] A Case Study on Course Outcomes, Program ... https://journaleet.in/index.php/jeet/article/view/178
[11] Data Mining https://utbildning.su.se/english/education/course-catalogue/ml/ml752n
[12] CPSC 340 and 532M - Machine Learning and Data Mining ... https://www.cs.ubc.ca/~schmidtm/Courses/340-F22/
