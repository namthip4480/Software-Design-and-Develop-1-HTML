# ใบงานการทดลอง HTML

## การทดลองที่ 6: การสร้างฟอร์ม
### วัตถุประสงค์
- สร้างฟอร์มรับข้อมูลได้ตามกำหนด
- เลือกใช้ประเภทของ input แบบต่างๆ ได้เหมาะสม
- สามารถใช้งาน form validation ได้

### ขั้นตอนการทดลอง
1. สร้างฟอร์มลงทะเบียนนักศึกษา:
```html
    <!-- กำหนดรูปแบบของฟอร์มบางส่วน -->
  <style>
        .form-group {
            margin-bottom: 15px;
        }
        
        .input-wrapper {
            display: flex;
            align-items: center;
        }
        
        .required-mark {
            color: red;
            margin-left: 5px;
        }
    </style>

    <body>
        <form action="/register" method="post">
            <!-- ส่วนข้อมูลส่วนตัว -->
            <fieldset>
                <legend>ข้อมูลส่วนตัว</legend>
                
                <div class="form-group">
                    <label for="studentId">รหัสนักศึกษา:</label>
                    <input type="text" id="studentId" name="studentId" 
                           pattern="[0-9]{8}" required>
                </div>
        
                <div class="form-group">
                    <label for="prefix">คำนำหน้า:</label>
                     <select id="prefix" name="prefix" required>
                        <option value="">เลือกคำนำหน้า</option>
                        <option value="mr">นาย</option>
                        <option value="ms">นางสาว</option>
                        <option value="mrs">นาง</option>
                    </select>
                </div>
        
                <div class="form-group">
                    <label for="firstName">ชื่อ:</label>
                    <input type="text" id="firstName" name="firstName" required>
                </div>
        
                <div class="form-group">
                    <label for="lastName">นามสกุล:</label>
                    <input type="text" id="lastName" name="lastName" required>
                </div>
        
                <div class="form-group">
                    <label for="birthdate">วันเกิด:</label>
                    <input type="date" id="birthdate" name="birthdate" required>
                </div>
        
                <div class="form-group">
                    <label>เพศ:</label>
                    <input type="radio" id="male" name="gender" value="male" required>
                    <label for="male">ชาย</label>
                    <input type="radio" id="female" name="gender" value="female">
                    <label for="female">หญิง</label>
                </div>
            </fieldset>
        
            <!-- ส่วนข้อมูลการติดต่อ -->
            <fieldset>
                <legend>ข้อมูลการติดต่อ</legend>
        
                <div class="form-group">
                    <label for="email">อีเมล:</label>
                    <input type="email" id="email" name="email" required>
                </div>
        
                <div class="form-group">
                    <label for="phone">เบอร์โทรศัพท์:</label>
                    <input type="tel" id="phone" name="phone" 
                           pattern="[0-9]{10}" required>
                </div>
        
                <div class="form-group">
                    <label for="address">ที่อยู่:</label>
                    <textarea id="address" name="address" 
                              rows="3" required></textarea> <span class="required-mark">*</span>
                </div>
            </fieldset>
        
            <!-- ส่วนข้อมูลการศึกษา -->
            <fieldset>
                <legend>ข้อมูลการศึกษา</legend>
        
                <div class="form-group">
                    <label for="faculty">คณะ:</label>
                    <select id="faculty" name="faculty" required>
                        <option value="">เลือกคณะ</option>
                        <option value="siet">ครุศาสตร์อุตสาหกรรมและเทคโนโลยี</option>
                        <option value="engineering">วิศวกรรมศาสตร์</option>
                        <option value="science">วิทยาศาสตร์</option>
                    </select> <span class="required-mark">*</span>
                </div>
        
                <div class="form-group">
                    <label for="major">สาขาวิชา:</label>
                    <select id="major" name="major" required>
                        <option value="">เลือกสาขาวิชา</option>
                        <!-- ตัวเลือกจะเปลี่ยนตามคณะที่เลือก ส่วนนี้ Code ยังไม่สมบูรณ์-->
                    </select> <span class="required-mark">*</span>
                </div>
        
                <div class="form-group">
                    <label for="gpa">เกรดเฉลี่ยสะสม:</label>
                    <input type="number" id="gpa" name="gpa" 
                           min="0" max="4" step="0.01" required> <span class="required-mark">*</span>
                </div>
            </fieldset>
        
            <!-- ส่วนความสนใจและกิจกรรม -->
            <fieldset>
                <legend>ความสนใจและกิจกรรม</legend>
        
                <div class="form-group">
                    <label>ความสนใจ:</label>
                    <input type="checkbox" id="sport" name="interests" value="sport">
                    <label for="sport">กีฬา</label>
                    <input type="checkbox" id="music" name="interests" value="music">
                    <label for="music">ดนตรี</label>
                    <input type="checkbox" id="art" name="interests" value="art">
                    <label for="art">ศิลปะ</label>
                    <input type="checkbox" id="tech" name="interests" value="tech">
                    <label for="tech">เทคโนโลยี</label>
                </div>
        
                <div class="form-group">
                    <label for="club">ชมรมที่สนใจ:</label>
                    <select id="club" name="club" multiple>
                        <option value="computer">ชมรมคอมพิวเตอร์</option>
                        <option value="robot">ชมรมหุ่นยนต์</option>
                        <option value="sport">ชมรมกีฬา</option>
                        <option value="music">ชมรมดนตรี</option>
                    </select>
                </div>
            </fieldset>
        
            <!-- ส่วนอัพโหลดเอกสาร -->
            <fieldset>
                <legend>เอกสารประกอบ</legend>
                <div class="form-group">
                    <label for="photo">รูปถ่าย:</label>
                    <input type="file" id="photo" name="photo" 
                           accept="image/*" required><span class="required-mark">*</span>
                </div>
        
                <div class="form-group">
                    <label for="transcript">ใบแสดงผลการเรียน:</label>
                    <input type="file" id="transcript" name="transcript" 
                           accept=".pdf,.doc,.docx" required>
                           <span class="required-mark">*</span>
                </div>
            </fieldset>
        
            <!-- ส่วนยืนยันข้อมูล -->
            <fieldset>
                <legend>การยืนยัน</legend>
        
                <div class="form-group">
                    <input type="checkbox" id="agree" name="agree" required>
                    <label for="agree">
                        ข้าพเจ้ายืนยันว่าข้อมูลทั้งหมดเป็นความจริง
                    </label>
                </div>
        
                <div class="form-group">
                    <button type="submit">ลงทะเบียน</button>
                    <button type="reset">ล้างข้อมูล</button>
                </div>
            </fieldset>
        </form>
```

### คำอธิบายเพิ่มเติม
1. Input Types ที่ใช้:
   - text: สำหรับข้อความทั่วไป
   - email: สำหรับอีเมล (มีการตรวจสอบรูปแบบอัตโนมัติ)
   - tel: สำหรับเบอร์โทรศัพท์
   - date: สำหรับวันที่
   - number: สำหรับตัวเลข
   - radio: สำหรับตัวเลือกเดียว
   - checkbox: สำหรับหลายตัวเลือก
   - file: สำหรับอัพโหลดไฟล์
   - select: สำหรับรายการแบบเลือก
   - textarea: สำหรับข้อความหลายบรรทัด

2. Attributes ที่สำคัญ:
   - required: จำเป็นต้องกรอก
   - pattern: กำหนดรูปแบบข้อมูล
   - min/max: กำหนดค่าต่ำสุด/สูงสุด
   - accept: กำหนดประเภทไฟล์ที่ยอมรับ
   - multiple: เลือกได้หลายตัวเลือก

### แบบฝึกหัด
1. สร้างฟอร์มสมัครสมาชิกร้านค้าออนไลน์ที่มี:
   - ข้อมูลส่วนตัว (ชื่อ-นามสกุล, วันเกิด, เพศ)
   - ข้อมูลการติดต่อ (อีเมล, เบอร์โทร, ที่อยู่จัดส่ง)
   - รูปโปรไฟล์
   - การยืนยันรหัสผ่าน
   - ความสนใจในหมวดหมู่สินค้า
   - การยอมรับเงื่อนไขการใช้งาน

2. เพิ่ม validation ที่เหมาะสม:
   - ตรวจสอบรูปแบบอีเมล
   - ตรวจสอบความยาวรหัสผ่าน
   - ตรวจสอบรูปแบบเบอร์โทร
   - ตรวจสอบขนาดไฟล์รูปภาพ

### บันทึกผลการทดลอง

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ฟอร์มสมัครสมาชิกร้านค้าออนไลน์</title>
    <style>
        .form-group {
            margin-bottom: 15px;
        }

        .input-wrapper {
            display: flex;
            align-items: center;
        }

        .required-mark {
            color: red;
            margin-left: 5px;
        }
    </style>
</head>
<body>
    <form action="/register" method="post" enctype="multipart/form-data">
        <!-- ส่วนข้อมูลส่วนตัว -->
        <fieldset>
            <legend>ข้อมูลส่วนตัว</legend>
            <div class="form-group">
                <label for="prefix">คำนำหน้า:</label>
                 <select id="prefix" name="prefix" required>
                    <option value="">เลือกคำนำหน้า</option>
                    <option value="mr">นาย</option>
                    <option value="ms">นางสาว</option>
                    <option value="mrs">นาง</option>
                </select>
            </div>

            <div class="form-group">
                <label for="firstName">ชื่อ:</label>
                <input type="text" id="firstName" name="firstName" required>
            </div>

            <div class="form-group">
                <label for="lastName">นามสกุล:</label>
                <input type="text" id="lastName" name="lastName" required>
            </div>

            <div class="form-group">
                <label for="birthdate">วันเกิด:</label>
                <input type="date" id="birthdate" name="birthdate" required>
            </div>

            <div class="form-group">
                <label>เพศ:</label>
                <input type="radio" id="male" name="gender" value="male" required>
                <label for="male">ชาย</label>
                <input type="radio" id="female" name="gender" value="female">
                <label for="female">หญิง</label>
            </div>
        </fieldset>

        <!-- ส่วนข้อมูลการติดต่อ -->
        <fieldset>
            <legend>ข้อมูลการติดต่อ</legend>

            <div class="form-group">
                <label for="email">อีเมล:</label>
                <input type="email" id="email" name="email" required>
            </div>

            <div class="form-group">
                <label for="phone">เบอร์โทรศัพท์:</label>
                <input type="tel" id="phone" name="phone" pattern="[0-9]{10}" required>
            </div>

            <div class="form-group">
                <label for="address">ที่อยู่จัดส่ง:</label>
                <textarea id="address" name="address" rows="3" required></textarea>
            </div>
        </fieldset>

        <!-- ส่วนรูปโปรไฟล์ -->
        <fieldset>
            <legend>รูปโปรไฟล์</legend>
            <div class="form-group">
                <label for="profilePic">เลือกรูปโปรไฟล์:</label>
                <input type="file" id="profilePic" name="profilePic" accept="image/*" required>
                <span class="required-mark">*</span>
            </div>
        </fieldset>

        <!-- ส่วนการยืนยันรหัสผ่าน -->
        <fieldset>
            <legend>การยืนยันรหัสผ่าน</legend>

            <div class="form-group">
                <label for="password">รหัสผ่าน:</label>
                <input type="password" id="password" name="password" minlength="8" required>
            </div>

            <div class="form-group">
                <label for="confirmPassword">ยืนยันรหัสผ่าน:</label>
                <input type="password" id="confirmPassword" name="confirmPassword" minlength="8" required>
            </div>

            <div class="form-group">
                <label for="passError" id="passError" style="color: red; display:none;">
                    รหัสผ่านไม่ตรงกัน
                </label>
            </div>
        </fieldset>

        <!-- ส่วนความสนใจในหมวดหมู่สินค้า -->
        <fieldset>
            <legend>ความสนใจในหมวดหมู่สินค้า</legend>

            <div class="form-group">
                <label>เลือกหมวดหมู่สินค้า:</label>
                <input type="checkbox" id="electronics" name="interests" value="electronics">
                <label for="electronics">อิเล็กทรอนิกส์</label>
                <input type="checkbox" id="clothing" name="interests" value="clothing">
                <label for="clothing">เสื้อผ้า</label>
                <input type="checkbox" id="beauty" name="interests" value="beauty">
                <label for="beauty">ความงาม</label>
            </div>
        </fieldset>

        <!-- ส่วนการยอมรับเงื่อนไขการใช้งาน -->
        <fieldset>
            <legend>การยอมรับเงื่อนไข</legend>
            <div class="form-group">
                <input type="checkbox" id="terms" name="terms" required>
                <label for="terms">ข้าพเจ้ายอมรับเงื่อนไขการใช้งาน</label>
            </div>
        </fieldset>

        <!-- ส่วนการยืนยันข้อมูล -->
        <fieldset>
            <legend>การยืนยัน</legend>
            <div class="form-group">
                <button type="submit">สมัครสมาชิก</button>
            </div>
        </fieldset>
    </form>

    <script>
        // ฟังก์ชั่นตรวจสอบรหัสผ่าน
        const password = document.getElementById('password');
        const confirmPassword = document.getElementById('confirmPassword');
        const passError = document.getElementById('passError');

        confirmPassword.addEventListener('input', function () {
            if (password.value !== confirmPassword.value) {
                passError.style.display = 'block';
            } else {
                passError.style.display = 'none';
            }
        });
    </script>
</body>
</html>]
```
- ภาพผลลัพธ์:
![image](https://github.com/user-attachments/assets/e7092885-23e0-43fb-9b77-2b47e061673c)




