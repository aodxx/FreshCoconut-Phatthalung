# Integrations & Credentials Inventory

## Purpose
ทะเบียนกลางสำหรับบัญชี, Project ID, Channel ID, App ID, API Key, Token และ Secret ที่ระบบมีแนวโน้มต้องใช้ เพื่อให้ผู้พัฒนาหรือ GPT Work เตรียมการเชื่อมต่อได้โดยไม่ต้องค้นหาใหม่ทุกครั้ง

> **กฎความปลอดภัย:** ห้ามบันทึก Token, Secret, Private Key หรือค่า credential จริงลง GitHub ไฟล์นี้เด็ดขาด ให้เก็บเฉพาะชื่อ credential, สถานะ, ตำแหน่งที่เก็บ และวิธีนำไปใช้

## Status Legend
- `CONFIRMED` = ต้องใช้แน่นอนตามทิศทางที่ยืนยันแล้ว
- `PREPARE_NOW` = ควรเตรียมบัญชี/ID ในช่วง Foundation แม้ยังไม่เริ่มเขียนระบบ
- `REQUIRED_AT_BUILD` = ต้องมีเมื่อเริ่มพัฒนาส่วนนี้
- `OPTIONAL` = ใช้เมื่อเลือกฟีเจอร์นั้น
- `OPEN` = ยังไม่ควรสร้างจนกว่าจะตัดสินใจ
- `NOT_STORED_HERE` = Secret จริงไม่เก็บใน repository

## 1. GitHub
Status: `CONFIRMED`

Repository: `aodxx/FreshCoconut-Phatthalung`
Default branch: `main`

สิ่งที่ต้องพร้อม:
- Repository access
- GitHub account ที่ใช้ดูแล repository
- สิทธิ์สำหรับ AI/Developer ที่จะทำงานใน repository

Secret: ไม่มี token ของแอปธุรกิจที่ต้องเก็บในเอกสารนี้

## 2. LINE Official Account / Messaging API
Status: `PREPARE_NOW` / `CONFIRMED FOR FUTURE PRODUCT`

ระบบเป้าหมายใช้ LINE OA เป็นช่องทางหลักของลูกค้าและ LINE Messaging API สำหรับการแจ้งสถานะ/การสื่อสาร

ต้องเตรียม:
- LINE Official Account
- Messaging API Channel
- Channel ID
- Channel Secret
- Channel Access Token
- Provider information ถ้าจำเป็น
- Webhook endpoint เมื่อเริ่มพัฒนา

Credential inventory:
- `LINE_CHANNEL_ID` — ID — `PREPARE_NOW`
- `LINE_CHANNEL_SECRET` — Secret — `PREPARE_NOW` — `NOT_STORED_HERE`
- `LINE_CHANNEL_ACCESS_TOKEN` — Secret — `PREPARE_NOW` — `NOT_STORED_HERE`

เก็บ Secret จริงในระบบ Secrets/Environment ของ backend หรือ hosting ไม่เก็บใน GitHub

## 3. LINE LIFF
Status: `PREPARE_NOW`

LIFF จะเป็น transaction/order experience ที่ทำงานภายใน LINE และเชื่อมกับระบบกลาง

ต้องเตรียมเมื่อสร้าง LIFF:
- LIFF ID
- LIFF URL / Endpoint URL
- LIFF app configuration
- Login scope ที่จำเป็น

Credential inventory:
- `LINE_LIFF_ID` — Public identifier — `PREPARE_NOW`
- `LIFF_ENDPOINT_URL` — URL — `REQUIRED_AT_BUILD`

หมายเหตุ: LIFF ID ไม่ใช่ Secret แต่ต้องบันทึกใน project configuration เพื่อให้ GPT Work รู้ว่าแอปใดเชื่อมกับระบบ

## 4. Central Database — Supabase
Status: `REQUIRED_AT_BUILD` / architecture candidate

ทิศทางที่วางไว้คือฐานข้อมูลกลางสำหรับออเดอร์ ลูกค้า สินค้า รอบส่ง การตั้งค่า และสถานะงาน แต่ยังต้องยืนยัน final technology stack ก่อนสร้าง production project

หากเลือก Supabase ต้องเตรียม:
- Supabase project
- Project Reference ID
- Project URL
- Database schema
- Auth configuration ถ้าใช้
- Storage buckets ถ้าเก็บสลิป/รูปภาพ
- Realtime configuration หากใช้สถานะสด
- Server-side secret / service role key
- Client-side publishable/anon key ตาม SDK/version ที่ใช้

Credential inventory:
- `SUPABASE_PROJECT_REF` — Identifier — `REQUIRED_AT_BUILD`
- `SUPABASE_URL` — URL — `REQUIRED_AT_BUILD`
- `SUPABASE_ANON_KEY` / publishable key — Client configuration — `REQUIRED_AT_BUILD`
- `SUPABASE_SERVICE_ROLE_KEY` / server secret — Secret — `REQUIRED_AT_BUILD` — `NOT_STORED_HERE`

## 5. Hosting / Deployment
Status: `REQUIRED_AT_BUILD`

ยังไม่ล็อก provider สุดท้าย

ต้องมีเมื่อเลือก hosting:
- Hosting account/project
- Production URL
- Preview URL ถ้ามี
- Environment variables
- Domain configuration ถ้ามี
- Secret storage

ห้ามเขียน credential จริงลง repository

## 6. Maps / Distance / Route
Status: `REQUIRED_AT_BUILD` เมื่อเริ่มระบบจัดรอบ/เส้นทางจริง

ระบบในอนาคตต้องสามารถพิจารณาระยะทางและความเหมาะสมของเส้นทางได้ แต่ provider ยังไม่ล็อก

เมื่อเลือก provider ต้องเก็บ:
- Project/Account ID
- API key ที่จำเป็น
- API enablement list
- Billing/quota status
- จำกัดการใช้งานเพื่อป้องกันค่าใช้จ่ายเกิน

Credential inventory:
- `MAPS_PROVIDER` — Config — `OPEN`
- `MAPS_PROJECT_ID` — Identifier — `REQUIRED_AT_BUILD`
- `MAPS_API_KEY` — Secret — `REQUIRED_AT_BUILD` — `NOT_STORED_HERE`

## 7. AI / OCR
Status: `OPEN`

ยังไม่ล็อกว่า AI provider ใดจะเป็น production provider และฟีเจอร์ AI ใดจำเป็นจริง

หากภายหลังต้องใช้ AI/OCR ให้บันทึก:
- Provider
- Project ID
- API key
- Model
- Quota/billing settings
- Server-side integration location

Credential inventory:
- `AI_PROVIDER` — Config — `OPEN`
- `AI_API_KEY` — Secret — `OPEN` — `NOT_STORED_HERE`

ห้ามเพิ่ม AI เพียงเพราะเป็นเทคโนโลยีที่น่าสนใจ หากไม่มี use case ที่ช่วยธุรกิจจริง

## 8. Canva / Brand Assets
Status: `PREPARE_NOW`

ใช้สำหรับสร้างและจัดการ Brand Foundation และชิ้นงานภาพ เช่น โลโก้, LINE OA cover, Rich Menu, profile, product visuals, packaging และ social assets

ต้องมี:
- Canva account/workspace ที่ใช้ทำงาน
- Design links
- Brand assets
- Asset status (Draft / Direction / Approved / Final)

Secret ของ Canva ไม่ต้องบันทึกใน repository

## 9. Google Drive — Original Assets
Status: `PREPARE_NOW`

Source folder ที่เจ้าของระบุ:
`https://drive.google.com/drive/folders/1hefdJG9wiomObbCDEYx0FqndTRVkdSVw`

ใช้เป็นแหล่งเก็บไฟล์ต้นฉบับ/ภาพ/เอกสารประกอบตามที่ตกลง

ไม่ควรถือว่า URL นี้เป็นที่เก็บ production secrets

## 10. Domain / Web URLs
Status: `REQUIRED_AT_BUILD`

ต้องเตรียมเมื่อระบบพร้อมเผยแพร่:
- Production web URL
- LIFF endpoint URL
- Backend/API URL ถ้าแยก
- Webhook URL
- Custom domain ถ้าต้องการ

## 11. Secrets Management Rule

### ห้ามเก็บใน GitHub
- Channel Secret
- Channel Access Token
- Database password
- Supabase service role key
- API keys ที่มีสิทธิ์สูง
- Private keys
- OAuth client secrets
- Webhook signing secrets ถ้ามี

### เก็บได้ใน GitHub
- ชื่อ environment variable
- Project/Channel ID ที่ไม่ใช่ secret
- Endpoint URL
- Provider name
- สถานะการเตรียม credential
- ขั้นตอน setup

## 12. Pre-Work Checklist Before GPT Work Build

ก่อนเริ่ม development จริง ให้ตรวจ:

- [ ] LINE OA พร้อม
- [ ] LINE Messaging API Channel พร้อม
- [ ] Channel ID บันทึกไว้ใน inventory
- [ ] Channel Secret สร้างแล้วและเก็บใน Secret Manager
- [ ] Channel Access Token สร้างแล้วและเก็บใน Secret Manager
- [ ] LIFF app สร้างแล้ว
- [ ] LIFF ID บันทึกไว้ใน inventory
- [ ] Production/Preview URL พร้อมเมื่อเลือก hosting
- [ ] Central database provider ยืนยันแล้ว
- [ ] Database project ID/URL พร้อม
- [ ] Server-side secrets พร้อม
- [ ] Maps provider ยืนยันก่อนทำ route engine
- [ ] AI/OCR provider ยืนยันเฉพาะเมื่อมี use case
- [ ] Canva workspace พร้อมสำหรับ Brand work
- [ ] Brand assets มีสถานะ Draft/Approved/Final ชัดเจน
- [ ] Google Drive source folder พร้อม

## 13. Rule for GPT Work

เมื่อ GPT Work ต้องเชื่อมต่อ service ใหม่:
1. ตรวจเอกสารนี้ก่อน
2. ถ้ามี credential inventory อยู่แล้ว ห้ามถามเจ้าของให้ค้นหาใหม่โดยไม่จำเป็น
3. ถ้าขาดเฉพาะ Secret จริง ให้ระบุชื่อ Secret ที่ต้องใส่และตำแหน่งที่ต้องใส่ ไม่ขอให้เจ้าของใส่ Secret ลง GitHub
4. ถ้า provider ยังเป็น `OPEN` ห้ามถือว่า provider ใดเป็นข้อสรุปแล้ว
5. หลังสร้าง/เชื่อมต่อ service ให้ปรับเอกสารนี้และ `DECISION_LOG.md` ให้ตรงกับสถานะจริง

## 14. Important

เอกสารนี้เป็นทะเบียนความพร้อมในการเชื่อมต่อ ไม่ใช่ที่เก็บรหัสลับ

เป้าหมายคือให้ GPT Work รู้ว่า **ต้องใช้กุญแจอะไร, ของชิ้นนั้นอยู่ที่ไหน, ต้องสร้างเมื่อไร และอะไรยังไม่ควรสร้าง** โดยไม่เปิดเผย Secret จริงใน source control.
