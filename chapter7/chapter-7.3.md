# 7.3 Programmed I/O

## หลักการทำงาน

Programmed I/O คือวิธีที่ CPU ส่งคำสั่ง I/O แล้ว **วนรอ (Polling)**
ตรวจสอบสถานะของ I/O Module เองตลอดเวลา จนกว่าการทำงานจะเสร็จสิ้น

> ข้อเสีย: CPU ต้องเสียเวลารอโดยเปล่าประโยชน์ ไม่สามารถทำงานอื่นได้

---

## ประเภทคำสั่ง I/O

| คำสั่ง | หน้าที่ |
|---|---|
| **Control** | สั่งให้ device ทำงาน เช่น rewind tape, seek disk |
| **Test** | ตรวจสอบสถานะว่า device พร้อมใช้งานไหม |
| **Read** | ดึงข้อมูลจาก device เข้ามาใน buffer |
| **Write** | ส่งข้อมูลออกไปยัง device |

---

## วิธีระบุ Address ของ I/O

### Memory-mapped I/O
- ใช้ address space เดียวกับ memory
- CPU ใช้คำสั่ง machine instruction เดียวกันในการเข้าถึง
- **ข้อดี** — ใช้ instruction ได้หลากหลาย เขียนโปรแกรมง่ายกว่า
- **ข้อเสีย** — กินพื้นที่ address ของ memory

### Isolated I/O
- แยก address space ของ I/O ออกจาก memory
- ต้องใช้คำสั่ง I/O พิเศษ เช่น `IN`, `OUT`
- **ข้อดี** — ไม่กินพื้นที่ memory address
- **ข้อเสีย** — มี instruction ให้ใช้น้อยกว่า

---

## เปรียบเทียบ Memory-mapped vs Isolated I/O

| หัวข้อ | Memory-mapped | Isolated I/O |
|---|---|---|
| Address space | รวมกับ memory | แยกต่างหาก |
| คำสั่งที่ใช้ | Machine instruction ทั่วไป | คำสั่ง I/O พิเศษ |
| ความยืดหยุ่น | สูง | ต่ำกว่า |
| การใช้ memory address | สิ้นเปลือง | ไม่สิ้นเปลือง |

---

## ขั้นตอนการทำงาน Programmed I/O

1. CPU ส่งคำสั่งไปยัง I/O Module
2. I/O Module เริ่มทำงานและตั้งค่าใน status register
3. **CPU วนรอ (polling)** ตรวจสอบ status register ซ้ำๆ
4. เมื่อ I/O พร้อม CPU อ่านหรือเขียนข้อมูล
5. ทำซ้ำจนครบทุก word ที่ต้องการ
