# Ceo Weather Watch

เว็บติดตามสภาพอากาศภาษาไทย ใช้งานบนมือถือและคอมพิวเตอร์ ข้อมูลพยากรณ์จริงจาก Open-Meteo และแผนที่จาก OpenStreetMap

## ใช้งาน

เปิด `index.html` ในเบราว์เซอร์ หรือให้บริการผ่าน static web server เช่น `python3 -m http.server 8000` แล้วเปิด `http://localhost:8000`.

## แหล่งข้อมูล

- [Open-Meteo Forecast API](https://open-meteo.com/en/docs): อุณหภูมิ ความชื้น ลม ฝนและโอกาสฝน รายชั่วโมงและรายวัน; ตรวจเงื่อนไขการใช้เชิงพาณิชย์ก่อนเผยแพร่เชิงธุรกิจ
- [OpenStreetMap](https://www.openstreetmap.org/copyright): แผนที่พื้นฐาน; แผนที่นี้ไม่ใช่ภาพเรดาร์
- [กรมอุตุนิยมวิทยา](https://www.tmd.go.th/service/serviceData): ลิงก์ประกาศเตือนทางการ; ยังไม่ได้เชื่อม API ประกาศเตือน
- RainViewer เป็นทางเลือกเรดาร์ในระยะถัดไป โดยต้องตรวจเงื่อนไขการใช้และขอบเขตข้อมูลก่อนเปิดจริง

## Deploy บน Cloudflare Pages

สร้าง Pages project แล้วเลือก GitHub repo นี้, production branch `main`, Framework preset `None`, Build command เว้นว่าง, Output directory `/` (หรือเลือกอัปโหลด directory ที่มี `index.html`). ไม่ต้องตั้ง API key สำหรับเวอร์ชันนี้.

## ขอบเขตเวอร์ชันแรก

เลือกจังหวัดได้ครบ 77 จังหวัดจากขอบเขต GeoJSON, คลิกจุดบนแผนที่เพื่อดูพยากรณ์เฉพาะพิกัด, ตำแหน่งปัจจุบัน, พยากรณ์ 12 ชั่วโมงและ 7 วัน, สถานะเมื่อ API ใช้ไม่ได้. ยังไม่มีภาพเรดาร์ การแจ้งเตือนอัตโนมัติ หรือประกาศเตือนผ่าน API.

## ข้อมูลขอบเขตจังหวัด

`provinces.geojson` จาก [Thailand canonical admin names](https://github.com/DevelopedbyWill/thailand-canonical-admin-names) ภายใต้ CC BY 4.0 (ข้อมูลขอบเขตต้นทางระบุปี 2019). แผนที่ใช้ Leaflet และแผ่นภาพ OpenStreetMap พร้อมแสดงเครดิต.
