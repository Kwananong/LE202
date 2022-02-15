# การติดตั้งโปรแกรมสำหรับไอโอที 

ในที่นี้มีการติดตั้งโปรแกรม python ไว้อยู่แล้ว จึงจะต้องทำการ uninstall python ทั้งหมดออกก่อน 

โดยเริ่มจากการ
1.	uninstall python ทั้งหมด
2.	ลบโฟลเดอร์ C:\Users\user\AppData\Local\Programs\Python
3.	ลบโฟลเดอร์ C:\pip
4.	ตรวจสอบตัวแปร PATH ว่ามีเกี่ยวกับ python หรือไม่

  <img width="392" alt="11" src="https://user-images.githubusercontent.com/98943450/154092759-e89c6b89-c4c9-4e4c-83bc-c6f134dffc9e.png">
  
จากนั้นจะทำการติดตั้งโปรแกรม git

<img width="281" alt="22" src="https://user-images.githubusercontent.com/98943450/154093586-a202c549-e55d-4eb8-b57e-83dd56d9b959.png">

  
หลังจากนั้นจึงจะเริ่มทำการติดตั้ง ซอฟต์แวร์ platformio 

โดยเริ่มจาก

1.	ติดตั้งโปรแกรม Python

<img width="398" alt="33" src="https://user-images.githubusercontent.com/98943450/154093922-082dcbb8-bf12-429c-bfb9-b9a57b043a98.png">

2.	ติดตั้ง ซอฟต์แวร์ platformio โดยใช้ command prompt

  - เริ่มจากกการรันคำสั่ง pip install -U platformio 

<img width="591" alt="44" src="https://user-images.githubusercontent.com/98943450/154094983-91346f70-61db-40a1-9049-15a8f71836ac.png">

  - จากนั้นรันคำสั่ง python.exe -m pip install –upgrade pip

<img width="595" alt="44 2" src="https://user-images.githubusercontent.com/98943450/154095209-0a35ddc9-9091-42ec-9b42-ce6ab9aa61f1.png">

3.	หลังจากนั้นจะทำการติดตั้งตัวโปรแกรม nodejs 

<img width="359" alt="55" src="https://user-images.githubusercontent.com/98943450/154095427-909b9046-d5a7-4c7f-824d-a187829a611d.png">

เมื่อติดตั้งตัวโปรแกรมเสร็จแล้ว รันคำสั่งเพื่อเช็ค version โปรแกรม

<img width="587" alt="66" src="https://user-images.githubusercontent.com/98943450/154096149-65052703-59a5-43c3-942f-489e65bc7291.png">

4.	ตรวจสอบดูโฟลเดอร์ตัวอย่าง ex01,ex02,ex03 โดยการเปิด cmd เข้าไปในโฟลเดอร์ iotset1 แล้วรันคำสั่ง

	cd iotset1/examples
  
	dir
  
  <img width="589" alt="77" src="https://user-images.githubusercontent.com/98943450/154096424-b83d99a3-346d-4514-900f-395e22d0fe92.png">
  
5.	ลองรันโปรแกรมตัวอย่างที่ 1 เพื่อเช็คว่าติดตั้งโปรแกรมพร้อมใช้งานแล้ว

โดยการรันคำสั่ง cd iotset1/examples/ex01 ต่อด้วย pio run

<img width="592" alt="88" src="https://user-images.githubusercontent.com/98943450/154096600-6b87f458-5de7-447b-aaff-4628017d82e7.png">


โดยจะเห็นว่าผลการติดตั้ง ซอฟต์แวร์ platformio : สามารถติดตั้งได้สำเร็จ พร้อมใช้งาน

  


