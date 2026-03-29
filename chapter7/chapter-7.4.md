# 7.4 Interrupt-Driven I/O

## หลักการทำงาน

Interrupt-Driven I/O แก้ปัญหาของ Programmed I/O ที่ CPU ต้องวนรอ
โดย CPU ส่งคำสั่ง I/O แล้ว **ไปทำงานอื่นได้เลย**
เมื่อ I/O Module พร้อม จะส่งสัญญาณ **Interrupt** มาหยุด CPU ชั่วคราว

> ข้อดี: CPU ไม่ต้องเสียเวลารอ
> ข้อเสีย: ข้อมูลทุก word ยังต้องผ่าน CPU อยู่

---

## กระบวนการ Interrupt (ฝั่ง Hardware)

1. Device ส่งสัญญาณ interrupt ไปยัง CPU
2. CPU รอให้ instruction ปัจจุบันทำงานเสร็จก่อน
3. CPU ส่ง acknowledgment กลับไปยัง device
4. CPU บันทึก context (PSW + Program Counter) ลง stack
5. CPU โหลด Program Counter ใหม่ไปยัง interrupt handler

## กระบวนการ Interrupt (ฝั่ง Software)

6. Interrupt handler บันทึก register ทั้งหมดลง stack
7. Interrupt handler ประมวลผล interrupt
8. คืนค่า register จาก stack
9. คืนค่า PSW + PC จาก stack → กลับทำงานเดิมต่อ

---

## วิธีระบุว่า Interrupt มาจาก Device ไหน

| วิธี | หลักการ | ข้อดี/ข้อเสีย |
|---|---|---|
| **Multiple interrupt lines** | แต่ละ device มี line ของตัวเอง | ง่าย แต่ใช้ pin เยอะ |
| **Software poll** | CPU ถาม device ทีละตัว | ง่าย แต่ช้า |
| **Daisy chain** | ส่งสัญญาณ acknowledge ไล่ตาม chain | เร็วกว่า poll เป็น vectored interrupt |
| **Bus arbitration** | Device แย่ง bus ก่อนแจ้ง interrupt | ยืดหยุ่น มี priority |

---

## Intel 82C59A Interrupt Controller

ใช้จัดการ interrupt สำหรับ Intel 80386

- จัดการ interrupt ได้ **8 device** ต่อ chip
- ต่อแบบ cascade ได้ถึง **64 device**
- รับ interrupt request → เลือก priority → ส่งสัญญาณไปยัง CPU

### Interrupt Modes ที่รองรับ

| Mode | คำอธิบาย |
|---|---|
| **Fully nested** | เรียง priority จาก IR0 (สูงสุด) ถึง IR7 (ต่ำสุด) |
| **Rotating** | หมุน priority หลังจาก device ได้รับการ service แล้ว |
| **Special mask** | CPU สามารถกัน interrupt จาก device บางตัวได้ |

---

## Intel 8255A Programmable Peripheral Interface

I/O Module อเนกประสงค์สำหรับ Intel 80386

- มี **24 I/O lines** แบ่งเป็น 3 port (A, B, C) ละ 8 bits
- กำหนดแต่ละ port เป็น input หรือ output ได้อิสระ

### Operating Modes

| Mode | คำอธิบาย |
|---|---|
| **Mode 0** | Basic I/O แต่ละ port เป็น input หรือ output |
| **Mode 1** | Handshaking ใช้ port C เป็น control line |
| **Mode 2** | Bidirectional รับ/ส่งได้สองทิศทาง |

---

## เปรียบเทียบ Programmed I/O vs Interrupt-Driven I/O

| หัวข้อ | Programmed I/O | Interrupt-Driven I/O |
|---|---|---|
| CPU ระหว่างรอ | วนรอ (polling) | ทำงานอื่นได้ |
| ข้อมูลผ่าน CPU | ✅ ผ่านทุก word | ✅ ผ่านทุก word |
| ประสิทธิภาพ | ต่ำ | ปานกลาง |
| ความซับซ้อน | ต่ำ | สูงกว่า |
