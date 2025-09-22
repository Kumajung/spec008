ผมได้อ่านไฟล์ **LAB 8 Interactive Website – Form and Validation** แล้ว และปรับเป็นภาษาไทยเรียบร้อย

---

# LAB 8 การจัดการอีเวนต์ (Event Handling) และการตรวจสอบฟอร์ม (Form Validation)

## วัตถุประสงค์

นักศึกษาจะได้ฝึกปฏิบัติ:

- การเลือก DOM elements และจัดการอีเวนต์ `submit` / `input`
- การใช้ HTML5 Form Validation (required, type, pattern, minlength)
- การเขียน JavaScript ตรวจสอบข้อมูลเอง (`event.preventDefault()`, `setCustomValidity()`)
- การแสดงข้อความเตือน (inline feedback) และปรับสไตล์ฟอร์ม

---

## คำแนะนำการทำแลบ

- ไฟล์/ทรัพยากรอยู่ใน MS Teams ช่อง: LAB08 – Form and Validation (วิชา 953104)
- ดาวน์โหลด: `resources-lab08.zip`
- มีการบ้าน 4 ข้อ (อ้างอิง LAB06 sheet)
- คะแนนรวม: **18 คะแนน**
- ชื่อโฟลเดอร์: `se_studentID_labname` (เช่น `se104_4921150xx_lab4`)
- ใส่ไฟล์คำตอบในโฟลเดอร์ → บีบอัด zip → ส่ง
- การส่งงาน:
  - อัปโหลด Mango assignments
  - ส่งช้า: หัก 50%
  - ปิดระบบแล้วส่งไม่ได้
  - แจ้งอาจารย์เพื่อตรวจบนเครื่องนักศึกษา

---

## แบบฝึกหัด

### 1) Sign-in (HTML5 Native Validation) – 3 คะแนน

เป้าหมาย: ใช้ validation ของ HTML5 เท่านั้น (ไม่ใช้ JS)

ขั้นตอน:

1. เปิด `q1_native.html`
2. ปรับ input:
   - Email → `type="email" required`
   - Password → `type="password" minlength="8" required`
3. เพิ่ม `<label>` และจัดให้ semantic
4. ทดสอบ: ว่าง / ไม่ถูกต้อง / ถูกต้อง
5. บันทึก

---

### 2) Sign-up (Custom JS Validation + Inline Feedback) – 6 คะแนน

เป้าหมาย: ไม่ใช้ popup เบราว์เซอร์ แสดง error เองในหน้า

ขั้นตอน:

1. เปิด `q2_signup.html`
2. ปรับ HTML:
   - ใช้ `<input type="text">` (ควบคุมเอง)
   - เพิ่ม `<label>`
   - ใส่ `<span class="error">` ใต้แต่ละช่อง
3. เขียน JS:
   - เลือกด้วย `getElementById`
   - ระหว่างพิมพ์ (`input`):
     - Email: ต้องมี `@` และ `.`
     - Password: ≥ 8 ตัว + มีตัวเลข ≥ 1
     - แสดง error + เปลี่ยน border
   - ตอน submit: ถ้าไม่ผ่าน → `event.preventDefault()`
4. ทดสอบทุกกรณี

---

### 3) Terms Checkbox + Disabled Submit – 5 คะแนน

เป้าหมาย: ปุ่ม Create Account กดได้เมื่อ email + password ถูกต้อง และติ๊ก checkbox

ขั้นตอน:

1. คัดลอกเป็น `q3_terms.html`
2. เพิ่ม:
   ```html
   <label><input id="terms" type="checkbox" /> I agree to Terms</label>
   ```
3. ปุ่ม submit → `disabled` เริ่มต้น
4. ฟังก์ชัน `updateButton()`:
   - เรียก `validateEmail()`, `validatePassword()`
   - ตรวจ `terms.checked`
   - ตั้ง `submitBtn.disabled`
5. Events:
   - `input` email/password → validate + updateButton
   - `change` checkbox → updateButton
6. ตรวจซ้ำก่อน submit

---

### 4) Review Page + Success Message – 4 คะแนน

เป้าหมาย: ส่งสำเร็จ → แสดงข้อความสำเร็จ + email แบบ mask (ไม่โชว์รหัสผ่าน)

ขั้นตอน:

1. คัดลอกเป็น `q4_review.html`
2. เมื่อผ่าน validation:
   - `event.preventDefault()`
   - แทนที่ฟอร์มด้วย banner สีเขียว + review block
   - Mask email ด้วยฟังก์ชัน:
     ```js
     function maskEmail(raw) {
       const parts = raw.split("@");
       if (parts.length !== 2) return raw;
       const [u, d] = parts;
       const visible = Math.min(2, u.length);
       return (
         u.slice(0, visible) +
         "*".repeat(Math.max(3, u.length - visible)) +
         "@" +
         d
       );
     }
     ```
3. ห้ามแสดง password
4. UI ต้องมี banner + review table ตามตัวอย่าง

---

ต้องการให้เพิ่มตัวอย่างโค้ดไฟล์แต่ละข้อหรือไม่?
