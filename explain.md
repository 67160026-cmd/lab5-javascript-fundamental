Week 5: JavaScript Fundamentals – explain.md
ไฟล์นี้อธิบาย การทำงานของโค้ด + แสดงตัวอย่างผลลัพธ์ (Output) สำหรับทุกกิจกรรมตามที่กำหนด สามารถ คัดลอกทั้งไฟล์ไปใช้บน GitHub ได้ทันที

2.1 01-variables.js – Challenge: Create a Person Object
โค้ด
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
ผลลัพธ์ที่ได้
{ firstName: 'Alice', lastName: 'Smith', age: 20, gpa: 3.8, ... }
Alice Smith
Alice Smith, Age: 20, GPA: 3.8
HTML, CSS, JavaScript
อธิบายการทำงาน
student เป็น Object ที่เก็บข้อมูลและ function (method)
this ใช้อ้างถึง object ปัจจุบัน
getFullName() เรียกใช้ข้อมูลภายใน object เดียวกัน
join() ใช้รวม array เป็น string เดียว
2.2 02-functions.js 8. Returning Objects
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
Output
{ firstName: 'John', lastName: 'Doe', age: 30, email: 'john.doe@example.com' }
John Doe
อธิบาย
function คืนค่าเป็น object
ใช้ object shorthand (firstName แทน firstName: firstName)
method ภายใน object ใช้ this 9. Function as Parameter (Callback)
function processArray(arr, callback) {
const result = [];
for (const item of arr) {
result.push(callback(item));
}
return result;
}

const numbers = [1, 2, 3];
console.log(processArray(numbers, (x) => x _ 2));
console.log(processArray(numbers, (x) => x _ x));
Output
[2, 4, 6]
[1, 4, 9]
อธิบาย
function สามารถรับ function เป็นพารามิเตอร์ได้
callback(item) คือการเรียก function ที่ส่งเข้ามา
2.3 03-control-flow.js 5. Short-Circuit Evaluation
const user = { name: "John" };
const admin = null;

const userName = admin?.name || user.name || "Anonymous";
console.log(userName);
Output
John
อธิบาย
admin?.name → undefined (ไม่ error)
undefined || user.name → เลือกค่าที่เป็น true ตัวแรก
JavaScript หยุดประเมินทันทีเมื่อรู้ผลลัพธ์ 7. Form Validation
function validateRegistration(formData) {
const errors = [];

if (!formData.name || formData.name.length < 3) errors.push("Invalid name");

if (!formData.email.includes("@")) errors.push("Invalid email");

return { isValid: errors.length === 0, errors };
}

console.log(validateRegistration({ name: "Jo", email: "abc" }));
Output
{ isValid: false, errors: [ 'Invalid name', 'Invalid email' ] }
อธิบาย
ใช้ if ตรวจสอบเงื่อนไขทีละข้อ
ถ้าไม่ผ่าน → push error ลง array
errors.length === 0 ใช้ตัดสินว่าฟอร์มถูกต้องหรือไม่
2.4 04-loops.js 9. Chaining Methods
const data = [1, 2, 3, 4, 5];

const result = data
.filter((n) => n % 2 === 0)
.map((n) => n \* n)
.join(", ");

console.log(result);
Output
4, 16
อธิบาย
filter เลือกเฉพาะเลขคู่ → [2,4]
map ยกกำลังสอง → [4,16]
join รวมเป็น string 10. Challenge: Student Grades
const students = [
{ name: "Alice", score: 95 },
{ name: "Bob", score: 75 },
];

const average = students.reduce((sum, s) => sum + s.score, 0) / students.length;
console.log(average);
Output
85
อธิบาย
reduce รวมคะแนนทั้งหมด
หารด้วยจำนวนนักเรียนเพื่อหาค่าเฉลี่ย
2.5 05-integration.js – Quiz Application
const quizzes = [
{ question: "5 + 3 = ?", options: ["8", "7"], correctAnswer: 0 },
];

let results = [];

quizzes.forEach((quiz, i) => {
const userAnswer = Math.floor(Math.random() \* quiz.options.length);
results.push({
question: quiz.question,
isCorrect: userAnswer === quiz.correctAnswer,
});
});

console.log(results);
Output (ตัวอย่าง)
[ { question: '5 + 3 = ?', isCorrect: true } ]
อธิบายการทำงาน
ใช้ array + loop + condition ร่วมกัน
Math.random() ใช้สุ่มคำตอบ
เก็บผลลัพธ์ใน results
ใช้ filter และ reduce เพื่อคำนวณคะแนนภายหลัง
✅ สรุป
ไฟล์นี้รวม

โค้ดทั้งหมด
ตัวอย่างผลลัพธ์
คำอธิบายว่าโค้ดสร้างผลลัพธ์ได้อย่างไร
