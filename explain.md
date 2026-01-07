# Week 5: JavaScript Fundamentals – explain.md

ไฟล์นี้อธิบายการทำงานของโค้ด JavaScript พร้อมแสดงตัวอย่างผลลัพธ์ (Output)  
สำหรับทุกกิจกรรมที่กำหนดในสัปดาห์ที่ 5

---

## 2.1 01-variables.js – Challenge: Create a Person Object

### โค้ด

```js
const student = {
  firstName: "Alice",
  lastName: "Smith",
  age: 20,
  gpa: 3.8,
  courses: ["HTML", "CSS", "JavaScript"],
  isActive: true,

  getFullName: function () {
    return `${this.firstName} ${this.lastName}`;
  },

  getInfo: function () {
    return `${this.getFullName()}, Age: ${this.age}, GPA: ${this.gpa}`;
  },
};

console.log(student);
console.log(student.getFullName());
console.log(student.getInfo());
console.log(student.courses.join(", "));
```

Output

```text
{ firstName: 'Alice', lastName: 'Smith', age: 20, gpa: 3.8, ... }
Alice Smith
Alice Smith, Age: 20, GPA: 3.8
HTML, CSS, JavaScript
```

อธิบายการทำงาน
student เป็น Object ที่เก็บทั้งข้อมูลและ function (method)

this ใช้อ้างถึง object ปัจจุบัน

getFullName() เรียกใช้ข้อมูลภายใน object เดียวกัน

join() ใช้รวม array ให้เป็น string เดียว

2.2 02-functions.js 8. Returning Objects
โค้ด

```js
function createUser(firstName, lastName, age) {
  return {
    firstName,
    lastName,
    age,
    email: `${firstName.toLowerCase()}.${lastName.toLowerCase()}@example.com`,
    getFullName() {
      return `${this.firstName} ${this.lastName}`;
    },
  };
}

const user = createUser("John", "Doe", 30);
console.log(user);
console.log(user.getFullName());
```

Output

```text
{ firstName: 'John', lastName: 'Doe', age: 30, email: 'john.doe@example.com' }
John Doe
```

อธิบาย
function สามารถคืนค่าเป็น object ได้

ใช้ object shorthand (firstName แทน firstName: firstName)

method ภายใน object ใช้ this เพื่ออ้างถึงข้อมูลของ object

9. Function as Parameter (Callback)
   โค้ด

```js
function processArray(arr, callback) {
  const result = [];
  for (const item of arr) {
    result.push(callback(item));
  }
  return result;
}

const numbers = [1, 2, 3];
console.log(processArray(numbers, (x) => x * 2));
console.log(processArray(numbers, (x) => x * x));
```

Output

```text
[2, 4, 6]
[1, 4, 9]
```

อธิบาย
function สามารถรับ function อื่นเป็นพารามิเตอร์ได้

callback(item) คือการเรียก function ที่ถูกส่งเข้ามา

2.3 03-control-flow.js 5. Short-Circuit Evaluation
โค้ด

```js
const user = { name: "John" };
const admin = null;

const userName = admin?.name || user.name || "Anonymous";
console.log(userName);
```

Output

```text
John
```

อธิบาย
admin?.name ให้ค่า undefined โดยไม่เกิด error

|| จะเลือกค่าที่เป็น true ตัวแรก

JavaScript จะหยุดประเมินทันทีเมื่อรู้ผลลัพธ์

7. Form Validation
   โค้ด

```js
function validateRegistration(formData) {
  const errors = [];

  if (!formData.name || formData.name.length < 3) errors.push("Invalid name");

  if (!formData.email.includes("@")) errors.push("Invalid email");

  return { isValid: errors.length === 0, errors };
}

console.log(validateRegistration({ name: "Jo", email: "abc" }));
```

Output

```text
{ isValid: false, errors: [ 'Invalid name', 'Invalid email' ] }
```

อธิบาย
ใช้ if ตรวจสอบเงื่อนไขทีละข้อ

ถ้าไม่ผ่านจะ push error ลงใน array

errors.length === 0 ใช้ตรวจสอบว่าฟอร์มถูกต้องหรือไม่

2.4 04-loops.js 9. Chaining Methods
โค้ด

```js
const data = [1, 2, 3, 4, 5];

const result = data
  .filter((n) => n % 2 === 0)
  .map((n) => n * n)
  .join(", ");

console.log(result);
```

Output

```text
4, 16
```

อธิบาย
filter เลือกเฉพาะเลขคู่ → [2, 4]

map ยกกำลังสอง → [4, 16]

join รวมค่าเป็น string

10. Challenge: Student Grades
    โค้ด

```js
const students = [
  { name: "Alice", score: 95 },
  { name: "Bob", score: 75 },
];

const average = students.reduce((sum, s) => sum + s.score, 0) / students.length;

console.log(average);
```

Output

```text
85
```

อธิบาย
reduce ใช้รวมคะแนนทั้งหมด

หารด้วยจำนวนนักเรียนเพื่อหาค่าเฉลี่ย

2.5 05-integration.js – Quiz Application
โค้ด

```js
const quizzes = [
  { question: "5 + 3 = ?", options: ["8", "7"], correctAnswer: 0 },
];

let results = [];

quizzes.forEach((quiz) => {
  const userAnswer = Math.floor(Math.random() * quiz.options.length);
  results.push({
    question: quiz.question,
    isCorrect: userAnswer === quiz.correctAnswer,
  });
});

console.log(results);
```

Output (ตัวอย่าง)

```text
[ { question: '5 + 3 = ?', isCorrect: true } ]
```

อธิบายการทำงาน
ใช้ array, loop และ condition ร่วมกัน

Math.random() ใช้สุ่มคำตอบ

เก็บผลลัพธ์ไว้ใน results

สามารถนำไปใช้ร่วมกับ filter และ reduce เพื่อคำนวณคะแนนได้

```

```
