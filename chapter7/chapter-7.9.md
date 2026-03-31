# 7.9 IBM zEnterprise EC12 I/O Structure

## ภาพรวมของระบบ

IBM zEnterprise EC12 คือ mainframe ระดับ enterprise ของ IBM
ใช้ **zEC12 processor chip** ความเร็ว 5.5 GHz มี 6 cores ต่อ chip
รองรับได้สูงสุด **101 processor chips** รวม **606 cores**

---

## Channel Subsystem (CSS)

ระบบ I/O ของ zEC12 ใช้ **dedicated core** จัดการ I/O แยกออกมาต่างหาก
ทำให้ CPU หลักทุ่มเทกับ application ได้เต็มที่

### องค์ประกอบของแต่ละ CSS

| องค์ประกอบ | หน้าที่ |
|---|---|
| **SAP** (System Assist Processor) | core ที่ถูกตั้งค่าให้จัดการ I/O โดยเฉพาะ |
| **HSA** (Hardware System Area) | memory สำรอง 32 GB สำหรับ I/O configuration |
| **Logical partitions** | virtual machine แต่ละ CSS รองรับได้ 16 partitions |
| **Subchannels** | logical device สำหรับแต่ละ I/O device รองรับได้ 196,000 ต่อ CSS |
| **Channel path** | เส้นทางระหว่าง CSS กับ control unit รองรับได้ 256 paths ต่อ CSS |
| **Channel** | processor ขนาดเล็กที่สื่อสารกับ I/O control unit |

---

## ตัวเลขสำคัญของระบบ

| หัวข้อ | จำนวน |
|---|---|
| Channel Subsystems | 4 |
| Channel paths ต่อ CSS | สูงสุด 256 |
| Subchannels ต่อ CSS | สูงสุด 196,000 |
| Logical partitions ต่อระบบ | สูงสุด 1,024 |

---

## การเชื่อมต่อ I/O

ระบบใช้ **2 interconnect** หลัก

| Interconnect | ใช้กับ |
|---|---|
| **InfiniBand (HCA)** | I/O cage และ I/O drawer |
| **PCI Express (PCIe)** | I/O drawer |

### อุปกรณ์ที่รองรับ
- **ESCON** — disk, tape, printer ผ่าน fiber
- **Ethernet** — 1 Gbps และ 10 Gbps
- **Fibre Channel** — high-speed storage
