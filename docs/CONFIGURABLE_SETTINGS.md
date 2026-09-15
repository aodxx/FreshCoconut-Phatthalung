# Configurable Settings

## Principle

ความสามารถที่เจ้าของควรเปลี่ยนค่าได้จากหลังบ้าน ถือเป็น **System Requirement** ตั้งแต่ต้น แม้ค่าจริงยังไม่ถูกเลือก

## Settings Groups

### Product & Pricing
- product name
- product description
- standard grating description
- selling price per kg
- optional customer/pricing tiers
- promotion rules

### Delivery
- normal delivery rounds
- round start/end times
- cutoff times
- route definitions
- service area rules
- maximum distance if used
- free-delivery conditions
- special delivery enable/disable
- special delivery fee rules
- operational constraints and alerts

### Customer Experience
- order confirmation message
- delivery option messages
- status messages
- storage/use guidance
- contact information
- LINE notification templates

### Operations
- preparation lead time
- order aggregation rules
- dispatch status rules
- manual override controls

## Data Rule

ค่าตั้งค่าต้องเป็นข้อมูลกลางที่ทั้ง PWA และ LINE/LIFF ใช้ร่วมกัน ไม่ควรมีค่าชุดเดียวกันซ้ำในหลาย frontend
