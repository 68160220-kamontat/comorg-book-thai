# 7.7 I/O Channels and Processors

## วิวัฒนาการของ I/O Function

| ขั้นที่ | พัฒนาการ | คำอธิบาย |
|---|---|---|
| **1** | CPU ควบคุม device โดยตรง | พบในระบบ microprocessor ขนาดเล็ก |
| **2** | เพิ่ม I/O Controller + Programmed I/O | CPU ไม่ต้องรู้รายละเอียดของ device |
| **3** | เพิ่ม Interrupt | CPU ไม่ต้องรอ I/O เพิ่มประสิทธิภาพ |
| **4** | เพิ่ม DMA | โอนข้อมูลตรงไป memory ไม่ผ่าน CPU |
| **5** | I/O Channel | I/O module มี instruction set เอง |
| **6** | I/O Processor | I/O module มี memory เอง เป็นคอมพิวเตอร์ในตัว |

---

## I/O Channel คืออะไร

I/O Channel คือ I/O Module ที่สามารถ **execute I/O instructions ได้เอง**
CPU เพียงแค่สั่งให้ I/O Channel รัน program ใน memory
แล้ว I/O Channel จัดการทุกอย่างเองโดยไม่ต้องให้ CPU เข้ามาเกี่ยว

---

## ประเภทของ I/O Channel

### Selector Channel
- ควบคุม device ความเร็วสูงหลายตัว
- ทำงานกับ **ทีละ 1 device** เท่านั้นในแต่ละช่วงเวลา
- เหมาะกับ disk drive ความเร็วสูง

### Multiplexor Channel
- ทำงานกับ **หลาย device พร้อมกัน**
- แบ่งเป็น 2 ชนิด

| ชนิด | คำอธิบาย | เหมาะกับ |
|---|---|---|
| **Byte multiplexor** | รับ/ส่งทีละ byte สลับระหว่าง device | device ความเร็วต่ำ เช่น keyboard |
| **Block multiplexor** | รับ/ส่งทีละ block สลับระหว่าง device | device ความเร็วสูง |

---

## เปรียบเทียบ I/O Controller vs I/O Channel

| หัวข้อ | I/O Controller | I/O Channel |
|---|---|---|
| ความฉลาด | ต่ำ CPU ต้องควบคุมเอง | สูง จัดการได้เอง |
| ใช้ใน | Microcomputer ทั่วไป | Mainframe |
| CPU involvement | มาก | น้อยมาก |
