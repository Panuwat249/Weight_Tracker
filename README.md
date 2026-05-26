# Weight Tracker — GitHub-only database

เว็บติดตามน้ำหนักที่ใช้ GitHub repo เป็นฐานข้อมูล โดยอ่าน/เขียนไฟล์ `data.json` ผ่าน GitHub Contents API

## ไฟล์

- `index.html` — หน้าเว็บ
- `app.js` — logic + GitHub API
- `data.json` — ข้อมูลน้ำหนักกลาง
- `.nojekyll` — ป้องกัน Jekyll

## วิธีลง GitHub Pages

1. สร้าง repository เช่น `weight-tracker`
2. อัปโหลดไฟล์ทั้งหมดไปไว้ที่ root ของ repo
3. ไปที่ Settings > Pages
4. Source: Deploy from branch
5. Branch: `main`, Folder: `/ (root)`
6. Save

## สร้าง Token

สร้าง Fine-grained personal access token ให้ repo นี้ และให้สิทธิ์ Contents: Read and write

จากนั้นเปิดเว็บ ใส่ Owner / Repo / Branch / Token แล้วกดบันทึกค่า

## วิธีทำงาน

- เว็บโหลด `data.json` จาก repo
- เมื่อเพิ่ม/แก้น้ำหนัก เว็บ PUT ไฟล์ `data.json` กลับเข้า repo พร้อม commit ใหม่
- เครื่องอื่นกดรีเฟรชจาก GitHub หรือเปิดเว็บใหม่ก็จะเห็นข้อมูลล่าสุด

## หมายเหตุ

Token ถูกเก็บใน localStorage ของ browser แต่ถ้าคุณต้องการฝัง token ไว้ในโค้ดก็ทำได้โดยแก้ `app.js` เอง ไม่แนะนำถ้าแชร์ URL/Repo กับคนอื่น
