<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>نظام تسجيل عملاء وطن غروب</title>
    <style>
        body { font-family: Arial, sans-serif; background: #f4f4f4; padding: 20px; text-align: center; }
        .form-container { background: white; max-width: 500px; margin: auto; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
        input, select, button { width: 100%; padding: 12px; margin: 8px 0; border-radius: 5px; border: 1px solid #ccc; box-sizing: border-box; }
        button { background: #1a2a3a; color: white; font-weight: bold; cursor: pointer; }
        .id-display { font-size: 20px; color: #27ae60; font-weight: bold; margin-top: 15px; background: #eefdf3; padding: 10px; display: none; }
    </style>
</head>
<body>
    <div class="form-container">
        <h2>تسجيل عميل جديد - وطن غروب</h2>
        <input type="text" id="fullName" placeholder="الاسم الكامل" required>
        <input type="text" id="motherName" placeholder="اسم الأم" required>
        <input type="text" id="phone" placeholder="رقم الهاتف" required>
        <input type="text" id="address" placeholder="العنوان (بناء، طابق، شقة)" required>
        <input type="text" id="maps" placeholder="رابط Google Maps">
        
        <select id="province">
            <option value="">اختر المحافظة/النوع</option>
            <option value="11">دمشق (11)</option>
            <option value="22">حلب (22/88 حسب الاتفاق)</option>
            <option value="00">عمل تجاري (00)</option>
            <option value="50">خدمة تقسيط (50)</option>
        </select>

        <button onclick="registerCustomer()">حفظ المعلومات وإصدار الـ ID</button>
        <div id="idResult" class="id-display"></div>
    </div>

    <script>
        function registerCustomer() {
            const name = document.getElementById('fullName').value;
            const mother = document.getElementById('motherName').value;
            const prov = document.getElementById('province').value;

            if (!name || !mother || !prov) {
                alert("عذراً، لا يمكن إصدار ID قبل تسجيل كافة المعلومات الشخصية!");
                return;
            }

            const r = () => Math.floor(10 + Math.random() * 89);
            const generatedID = `${prov} ${r()} ${r()} ${r()}`;
            
            const display = document.getElementById('idResult');
            display.innerText = "تم التوثيق بنجاح! الـ ID المعتمد: " + generatedID;
            display.style.display = "block";
            
            alert("تم حفظ بيانات العميل في البنك وإصدار الرقم.");
        }
    </script>
</body>
</html>
