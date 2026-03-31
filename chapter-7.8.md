# 7.8 External Interconnection Standards

## มาตรฐานการเชื่อมต่ออุปกรณ์ภายนอก

### Universal Serial Bus (USB)

- มาตรฐานที่ใช้กันแพร่หลายที่สุดสำหรับ peripheral
- วิวัฒนาการความเร็ว

| เวอร์ชัน | ความเร็ว |
|---|---|
| USB 1.0 | 1.5 Mbps / 12 Mbps |
| USB 2.0 | 480 Mbps |
| USB 3.0 (SuperSpeed) | 4 Gbps |
| USB 3.1 (SuperSpeed+) | 9.7 Gbps |

---

### FireWire (IEEE 1394)

- พัฒนาขึ้นมาแทน SCSI สำหรับระบบขนาดเล็ก
- ต่อ device ได้สูงสุด **63 ตัว** ต่อ port
- รองรับ **Hot plugging** — เสียบ/ถอดได้โดยไม่ต้องปิดเครื่อง
- ตั้งค่า address อัตโนมัติ ไม่ต้องตั้งเอง
- ความเร็ว 25 Mbps ถึง 3.2 Gbps

---

### Small Computer System Interface (SCSI)

- มาตรฐานเก่าสำหรับเชื่อมต่อ peripheral กับคอมพิวเตอร์ขนาดกลาง
- รองรับ device ได้ 16–32 ตัวต่อ bus
- ความเร็ว 5 Mbps (SCSI-1) ถึง 160 Mbps (SCSI-3 U3)
- ยังคงนิยมใน enterprise storage จนถึงปัจจุบัน

---

### Thunderbolt

- พัฒนาโดย Intel ร่วมกับ Apple
- รวม **data + video + audio + power** ในสายเดียว
- ความเร็ว **10 Gbps** ทั้งขาเข้าและขาออก
- จ่ายไฟได้สูงสุด **10 watts**

---

### InfiniBand

- มาตรฐานสำหรับ high-end server
- เชื่อมต่อ server, storage, และ network device ได้สูงสุด **64,000 nodes**
- นิยมใช้ใน storage area network และ mainframe เช่น IBM zEnterprise

---

### มาตรฐานอื่นๆ

| มาตรฐาน | ความเร็ว | ใช้ทำอะไร |
|---|---|---|
| **PCI Express** | สูง | เชื่อมต่อ peripheral หลายชนิด |
| **SATA** | 6 Gbps | disk storage ใน desktop/embedded |
| **Ethernet** | 10 Mbps – 100 Gbps | networking ทุกรูปแบบ |
| **Wi-Fi (802.11ac)** | 3.2 Gbps | wireless internet |

---

## วิวัฒนาการของ Ethernet

| ปี | ความเร็ว |
|---|---|
| 1983 | 10 Mbps |
| 1995 | 100 Mbps |
| 1998 | 1 Gbps |
| 2003 | 10 Gbps |
| 2010 | 40 / 100 Gbps |

## วิวัฒนาการของ Wi-Fi

| มาตรฐาน | ปี | ความเร็ว |
|---|---|---|
| 802.11 | 1997 | 2 Mbps |
| 802.11b | 1999 | 11 Mbps |
| 802.11a | 1999 | 54 Mbps |
| 802.11g | 2003 | 54 Mbps |
| 802.11n | 2009 | 600 Mbps |
| 802.11ac | 2014 | 3.2 Gbps |
| 802.11ad | 2012 | 6.76 Gbps |
