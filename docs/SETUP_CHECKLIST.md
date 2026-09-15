# Setup Checklist — Prepare Before GPT Work Development

## Purpose
เช็กลิสต์เตรียมบัญชี Project ID, App ID, Channel ID, URL และ Credential ที่จำเป็นก่อนเข้าสู่การพัฒนาจริง เพื่อไม่ให้เวลาของ GPT Work สูญเสียไปกับการค้นหาข้อมูลการเชื่อมต่อ

> **Security:** ไม่ใส่ Token/Secret จริงใน GitHub ให้ใส่เฉพาะชื่อ credential และสถานะ

## A. Business / Project Foundation
- [x] GitHub repository พร้อม
- [x] README.md เป็นจุดเริ่มต้น
- [x] AI Working Rules พร้อม
- [x] Decision Log พร้อม
- [x] Business Foundation / Rules / Configurable Settings อยู่ใน project docs
- [ ] Brand Identity Final
- [ ] ชื่อแบรนด์สุดท้าย
- [ ] สโลแกนสุดท้าย

## B. LINE
- [ ] สร้าง/ยืนยัน LINE Official Account
- [ ] เปิด Messaging API
- [ ] บันทึก Channel ID ใน `INTEGRATIONS_AND_CREDENTIALS.md`
- [ ] สร้าง Channel Secret และเก็บใน Secret Manager
- [ ] สร้าง Channel Access Token และเก็บใน Secret Manager
- [ ] ตรวจ Webhook configuration เมื่อ backend พร้อม

## C. LIFF
- [ ] สร้าง LIFF app
- [ ] บันทึก LIFF ID
- [ ] กำหนด LIFF Endpoint URL เมื่อ hosting พร้อม
- [ ] ตรวจ login/profile scope ที่จำเป็น
- [ ] ทดสอบเปิด LIFF จาก LINE จริง

## D. Database
- [ ] ยืนยัน final database provider
- [ ] สร้าง project
- [ ] บันทึก Project Reference ID
- [ ] บันทึก Project URL
- [ ] เตรียม client/public key ตาม provider
- [ ] เตรียม server-side secret
- [ ] วาง schema ก่อน production data
- [ ] ตั้ง backup / recovery strategy ก่อนใช้งานจริง

## E. Hosting
- [ ] ยืนยัน hosting provider
- [ ] สร้าง project
- [ ] ได้ production URL
- [ ] เตรียม environment variables
- [ ] เตรียม secret variables
- [ ] เตรียม preview/staging strategy ถ้าจำเป็น

## F. Maps / Route
- [ ] เลือก provider หลังสรุป requirement เรื่องระยะทาง/เส้นทาง
- [ ] สร้าง project/account
- [ ] เปิด API ที่จำเป็นเท่านั้น
- [ ] สร้าง API key
- [ ] ตั้ง quota/budget protection
- [ ] บันทึกชื่อ credential โดยไม่บันทึกค่าจริง

## G. AI / OCR
- [ ] ระบุ use case ที่ต้องใช้ AI ก่อน
- [ ] เลือก provider เมื่อ requirement ชัด
- [ ] สร้าง API key เฉพาะ server-side
- [ ] ตั้ง quota/budget protection
- [ ] บันทึก provider/model ใน project docs

## H. Canva / Brand
- [ ] Canva workspace พร้อม
- [ ] Brand Direction มีสถานะชัดเจน
- [ ] Logo draft
- [ ] Logo final หลังเจ้าของยืนยัน
- [ ] Profile image
- [ ] LINE OA cover
- [ ] Rich Menu
- [ ] Product visual
- [ ] Packaging/label direction
- [ ] Asset Manifest อัปเดตสถานะทุกไฟล์

## I. Google Drive
- [x] Source folder URL ถูกบันทึกใน README และ integration inventory
- [ ] จัดหมวด original assets
- [ ] กำหนดไฟล์ใดเป็น source/master
- [ ] กำหนดชื่อไฟล์/เวอร์ชันที่สอดคล้องกับ GitHub

## J. Final Handoff Gate
ก่อนให้ GPT Work เริ่ม build จริง ต้องตรวจว่า:

- [ ] ทุก service ที่สถานะ `PREPARE_NOW` มีบัญชี/ID พร้อม
- [ ] Secret จริงเก็บนอก GitHub
- [ ] ทุก ID/URL ที่ไม่ใช่ secret บันทึกไว้แล้ว
- [ ] Provider ที่ยังเป็น `OPEN` ยังไม่ถูก hard-code
- [ ] Business decisions ที่ยืนยันแล้วอยู่ใน Decision Log
- [ ] Configurable capabilities ถูกระบุครบ
- [ ] Open decisions ถูกแยกออกจาก system requirements
- [ ] GPT Work สามารถเริ่มงานจาก repository โดยไม่ต้องค้นข้อมูลพื้นฐานซ้ำ

## Handoff Principle

**เตรียมข้อมูลเชื่อมต่อให้พร้อมก่อนเริ่มเขียนระบบ แต่ไม่สร้าง service ที่ยังไม่มีเหตุผลต้องใช้ และไม่เก็บ Secret จริงไว้ใน source control**
