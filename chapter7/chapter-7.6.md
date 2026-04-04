# 7.6 Direct Cache Access (DCA)

## ปัญหาของ DMA กับ Network ความเร็วสูง

DMA ทำงานได้ดีกับ I/O ทั่วไป แต่เมื่อ network ความเร็วสูงมากขึ้น
เช่น **10 Gbps** หรือ **100 Gbps** DMA ไม่เพียงพออีกต่อไป
เพราะข้อมูลต้องเขียนลง **main memory** ก่อน แล้ว CPU ค่อยอ่านขึ้น cache อีกที
ทำให้เสีย latency มาก

---

## หลักการของ DCA

แทนที่จะโอนข้อมูลไปยัง main memory
DCA โอนข้อมูล **ตรงเข้า Cache** เลย ทำให้ CPU เข้าถึงข้อมูลได้เร็วขึ้นมาก

---

## Intel Direct Data I/O (DDIO)

Intel พัฒนา DDIO สำหรับ **Xeon E5 family** โดยใช้กลยุทธ์ 2 แบบ

| กลยุทธ์ | เงื่อนไข | การทำงาน |
|---|---|---|
| **Write update** | Cache hit | อัปเดต cache โดยตรง ไม่ผ่าน memory |
| **Write allocate** | Cache miss | เขียนลง cache โดยไม่เขียนกลับ memory |

---

## เปรียบเทียบ DMA vs DDIO

### Packet Input (ข้อมูลขาเข้า)

| วิธี | ขั้นตอน |
|---|---|
| **DMA** | NIC → memory → cache → CPU |
| **DDIO** | NIC → cache → CPU |

### Packet Output (ข้อมูลขาออก)

| วิธี | ขั้นตอน |
|---|---|
| **DMA** | CPU เขียนลง cache → evict ออ
