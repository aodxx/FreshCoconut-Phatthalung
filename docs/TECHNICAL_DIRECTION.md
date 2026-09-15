# Technical Direction

## Target Architecture

```text
Customer
  ↓
LINE OA / LIFF
  ↓
Order Experience
  ↓
Order & Delivery Engine
  ↓
Shared Database
  ↓
Owner Admin PWA
  ↓
LINE Notifications
```

## Direction

ระบบในอนาคตควรเป็น PWA สำหรับเจ้าของร้าน + LIFF/Web App สำหรับลูกค้า โดยใช้ข้อมูลกลางชุดเดียวกัน

แนวทางฐานข้อมูลที่กำลังพิจารณา: Supabase/Postgres เพื่อรองรับ order state, realtime updates, authentication และ storage อย่างเป็นระบบ

## Important Technical Principles

- Single source of truth สำหรับราคา ออเดอร์ รอบส่ง เส้นทาง และสถานะ
- Customer UI และ Owner PWA ห้ามมี business values ซ้ำกันเอง
- Event/status ที่ส่ง LINE ต้องมาจากสถานะจริงในระบบ
- รองรับการปรับ configuration โดยไม่แก้ source code
- ออกแบบ mobile-first
- ภาษา UI เป็นไทยและเหมาะกับผู้ใช้ท้องถิ่น

## Current Status

ยังไม่เริ่ม implementation และยังไม่ถือว่า technology stack เป็น final decision จนกว่าจะผ่านการออกแบบ Foundation และ technical review
