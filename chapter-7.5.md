# 7.5 Direct Memory Access (DMA)

## ปัญหาของ Programmed I/O และ Interrupt-Driven I/O

แม้ Interrupt-Driven I/O จะดีกว่า Programmed I/O แต่ยังมีข้อเสียอยู่ 2 ประการ

| ข้อเสีย | คำอธิบาย |
|---|---|
| **Transfer rate ต่ำ** | ความเร็วในการโอนข้อมูลถูกจำกัดด้วยความเร็วของ CPU |
| **CPU ยุ่งตลอด** | ข้อมูลทุก word ต้องผ่าน CPU ทำให้ CPU ไม่ว่าง |

---

## หลักการทำงานของ DMA

DMA Module โอนข้อมูล **ตรงระหว่าง Memory กับ I/O Device**
โดยไม่ผ่าน CPU เลย CPU เกี่ยวข้องแค่ **ตอนเริ่ม** และ **ตอนจบ** เท่านั้น

### ข้อมูลที่ต้องส่งให้ DMA ก่อนเริ่มโอน

- อ่านหรือเขียน (Read/Write)
- Address ของ I/O device
- Starting address ใน memory
- จำนวน word ที่ต้องโอน

---

## Cycle Stealing

DMA ใช้เทคนิค **Cycle Stealing** คือการขอยืม bus cycle จาก CPU ชั่วคราว
CPU ไม่ได้บันทึก context แค่หยุดรอ 1 bus cycle แล้วทำงานต่อ

---

## รูปแบบของ DMA

| รูปแบบ | คำอธิบาย | ประสิทธิภาพ |
|---|---|---|
| **Single-bus, detached DMA** | ทุกอย่างใช้ bus เดียวกัน | ต่ำ ใช้ bus cycle เยอะ |
| **Single-bus, integrated
