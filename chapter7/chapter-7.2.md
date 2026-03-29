# 7.2 I/O Modules

## หน้าที่หลักของ I/O Module

I/O Module ทำหน้าที่เป็นตัวกลางระหว่าง CPU กับอุปกรณ์ภายนอก
มีหน้าที่หลัก 5 ประการ ดังนี้

| หน้าที่ | คำอธิบาย |
|---|---|
| **Control and Timing** | ควบคุมการไหลของข้อมูลระหว่าง internal resources กับ external devices |
| **Processor Communication** | รับคำสั่งจาก CPU และรายงานสถานะกลับ |
| **Device Communication** | สื่อสารกับ external device ด้วยสัญญาณ control, status, data |
| **Data Buffering** | พักข้อมูลชั่วคราว เนื่องจาก CPU และ device ทำงานต่างความเร็วกัน |
| **Error Detection** | ตรวจสอบข้อผิดพลาด เช่น ใช้ parity bit |

---

## Processor Communication

การสื่อสารระหว่าง I/O Module กับ CPU มี 4 รูปแบบ

- **Command decoding** — รับและถอดรหัสคำสั่งจาก CPU เช่น READ SECTOR, WRITE SECTOR
- **Data** — รับและส่งข้อมูลผ่าน data bus
- **Status reporting** — รายงานสถานะเช่น BUSY หรือ READY
- **Address recognition** — จดจำ address ของอุปกรณ์ที่ตัวเองดูแล

---

## โครงสร้างภายในของ I/O Module

| ส่วนประกอบ | หน้าที่ |
|---|---|
| **Data registers** | พักข้อมูลชั่วคราวระหว่างรับ/ส่ง |
| **Status/Control registers** | เก็บสถานะและรับคำสั่งจาก CPU |
| **I/O logic** | ควบคุมการสื่อสารกับ external device |

---

## ประเภทของ I/O Module

- **I/O Controller** — แบบง่าย CPU ต้องควบคุมรายละเอียดเอง พบใน microcomputer ทั่วไป
- **I/O Channel / I/O Processor** — แบบฉลาด จัดการงานแทน CPU ได้เกือบทั้งหมด พบใน mainframe
