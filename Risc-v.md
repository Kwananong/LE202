# การทำงานของไมโครคอนโทรลเลอร์ (Risc-v)
<img width="960" alt="123456" src="https://user-images.githubusercontent.com/98943450/160292499-84b3ab70-c881-4025-9daa-42d58a6f9412.png">


ชื่อ-นามสกุล : Kwananong Sonangrong 

อักษรย่อชื่อนามสกุลที่ได้คือ KS

ดังนั้นใน Address ที่ 20 และ 21 จะเป็น 4b และ 53 ตามลำดับ

## อธิบายการทำงาน
### Step 1 :
คำสั่ง addi x1, x0, 32 จะเป็นการนำ 32 ไปบวกกับ x0 แล้วนำไปใส่ใน x1 โดยเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเอา x0 และ 32 ไปบวกกัน แล้วนำไปใส่ไว้ที่ x1 

### Step 2 : 
คำสั่ง lui x2, 0xc0000000 จะเป็นการเอา 0xc0000000 ไปใส่ไว้ใน x2 โดยใส่ไว้แค่ 20 บิตบนแรก การทำงานจะเริ่มจากการนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเอา c0000000 ไปใส่ไว้ใน x2

### Step 3 : 
คำสั่ง lbu x3, 0(x1) จะเป็นการนำข้อมูลที่หน่วยความจำ x1 เพียงไบต์เดียวไปใส่ใน x3 โดยจะเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเอา 1 ไบต์จากหน่วยความจำที่  x1  ซึ่งในที่นี้คือ 4b ไปใส่ไว้ที่ x3

### tep 4 : 
คำสั่ง beq x3, x0, +16  จะเป็นการเช็คดูว่าที่หน่วยความจำ x3 เท่ากับที่ x0 หรือไม่ ถ้าเท่ากันจะกระโดดไปที่ +16 โดยคำสั่งจะเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเช็คที่หน่วยความจำ x3 ว่าเท่ากับที่ x0 หรือไม่ ซึ่งในที่นี้ไม่เท่ากัน ดังนั้นจึงไม่มีการกระโดดไปที่ +16

### Step 5 :
คำสั่ง sb x3, 0(x2) จะเป็นการนำเอาข้อมูลที่หน่วยความจำ x3 ไปเก็บไว้ที่ x2 โดยเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเอาค่าที่เก็บไว้ในหน่วยความจำที่ x3 ซึ่งในที่นี้คือ 4b ไปเก็บไว้ที่หน่วยความจำ x2 ซึ่งก็คือที่ตำแหน่ง c0000000 ดังนั้นจะได้ output ออกมาเป็นตัว K 

### Step 6 : 
คำสั่ง addi x1, x1, 1 จะเป็นการนำเอา x1 บวกเพิ่มเข้าไป 1 แล้วนำไปเก็บไว้ที่ x1 เริ่มจากการนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเอาค่าที่หน่วยความจำ x1 ซึ่งเดิมเป็น 20 บวกเพิ่มเข้าไป 1 เป็น 21 แล้วนำไปเก็บที่ x1

### Step 7 : 
คำสั่ง jal x0, -16 จะเป็นการกระโดดไปที่ -16 โดยเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยกระโดดไปที่ -16 หรือที่ Address 8

### Step 8 : 
คำสั่ง lbu x3, 0(x1) เมื่อกระโดดมาที่ Address 8 จะเป็นการทำตามคำสั่งซ้ำคล้ายการรันตัวอักษรแรก โดยเช่นเดิมคำสั่งนี้จะเป็นการนำข้อมูลที่หน่วยความจำ x1 เพียงไบต์เดียวไปใส่ใน x3 โดยจะเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเอา 1 ไบต์จากหน่วยความจำที่  x1  ซึ่งในที่นี้คือ 53 ไปใส่ไว้ที่ x3

### Step 9 : 
คำสั่ง beq x3, x0, +16  จะเป็นการเช็คดูว่าที่หน่วยความจำ x3 เท่ากับที่ x0 หรือไม่ ถ้าเท่าจะกระโดดไปที่ +16 โดยคำสั่งจะเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเช็คที่หน่วยความจำ x3 ว่าเท่ากับที่ x0 หรือไม่ ซึ่งในที่นี้ไม่เท่ากัน ดังนั้นจึงไม่มีการกระโดไปที่ +16

### Step 10 :
คำสั่ง sb x3, 0(x2) จะเป็นการนำเอาข้อมูลที่หน่วยความจำ x3 ไปเก็บไว้ที่ x2 โดยเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเอาค่าที่เก็บไว้ในหน่วยความจำที่ x3 ซึ่งในที่นี้คือ 53 ไปเก็บไว้ที่หน่วยความจำ x2 ซึ่งก็คือที่ตำแหน่ง c0000000 ดังนั้นจะได้ output ออกมาเป็นตัว S

### Step 11 : 
คำสั่ง addi x1, x1, 1 จะเป็นการนำเอา x1 บวกเพิ่มเข้าไป 1 แล้วนำไปเก็บไว้ที่ x1 เริ่มจากการนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเอาค่าที่หน่วยความจำ x1 ซึ่งเดิมเป็น 21 บวกเพิ่มเข้าไป 1 เป็น 22 แล้วนำไปเก็บที่ x1

### Step 12 : 
คำสั่ง jal x0, -16 จะเป็นกระโดดไปที่ -16 โดยเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยกระโดดไปที่ -16 หรือที่ Address 8

### Step 13 : 
คำสั่ง lbu x3, 0(x1) จะเป็นการนำค่าที่หน่วยความจำ x1 เพียงไบต์เดียวไปใส่ใน x3 โดยจะเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเอา 1 ไบต์จากหน่วยความจำที่  x1  ซึ่งในที่นี้คือ 00 ไปใส่ไว้ที่ x3

### Step 14 : 
คำสั่ง beq x3, x0, +16  จะเป็นการเช็คดูว่าที่หน่วยความจำ x3 เท่ากับที่ x0 หรือไม่ ถ้าเท่ากันจะกระโดดไปที่ +16 โดยคำสั่งจะเริ่มจากนำคำสั่งมาเรียงใหม่ที่ส่วน Bus จากนั้นส่งคำไปยังส่วน Instruction reg เพื่อทำการแปลคำสั่ง แล้วดำเนินการตามคำสั่งโดยเช็คที่หน่วยความจำ x3 ว่าเท่ากับที่ x0 หรือไม่ ซึ่งในที่นี้ที่หน่วยความจำ x3 เท่ากับ 0 ดังนั้นจึงมีการกระโดดไปที่ +16 หรือที่ Address 1c 

### Step 15 : 
คำสั่ง jal x0, 0 จะเป็นการกระโดดไปที่ 0 หรือการรันอยู่ที่เดิม 



ซึ่งก็จะจบการทำงานของคำสั่งนี้ โดย output ที่ได้ หรือที่ตำแหน่ง c0000000 จะมีตัวอักษร KS ซึ่งเป็นตัวย่อของชื่อนามสกุลปรากฎขึ้นอยู่