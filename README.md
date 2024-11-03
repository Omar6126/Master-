<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>صفحة تسجيل الدخول</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f0f0;
      margin: 0;
      padding: 0;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #333;
    }

    .login-container {
      background: white;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 10px;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
      width: 100%;
      max-width: 400px;
    }

    .login-container h2 {
      text-align: center;
      font-size: 1.5em;
      margin-top: 0;
    }

    .market-info, .market-summary {
      text-align: center;
      background-color: #e9f5e9;
      padding: 10px;
      border-radius: 5px;
      margin-bottom: 20px;
      font-size: 0.9em;
    }

    .form-group {
      margin-bottom: 15px;
    }

    .form-group label {
      display: block;
      font-weight: bold;
      margin-bottom: 5px;
    }

    .form-group input {
      width: 100%;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      background-color: #f9f9f9;
      box-sizing: border-box;
    }

    .form-group input[type="submit"] {
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    .form-group input[type="submit"]:hover {
      background-color: #45a049;
    }

    .create-account {
      text-align: center;
      margin-top: 15px;
    }

    .create-account a {
      color: #4CAF50;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <div class="login-container">
    
    <!-- قسم أسعار العملات الحية -->
    <div class="market-info">
      <p><strong>أسعار العملات الحية</strong></p>
      <p>USD/EUR: <span id="usd-eur">جارٍ التحميل...</span></p>
      <p>USD/JPY: <span id="usd-jpy">جارٍ التحميل...</span></p>
    </div>

    <!-- ملخص السوق والتحليلات -->
    <div class="market-summary">
      <h3>ملخص السوق اليومي</h3>
      <p>اليوم شهدت الأسواق تقلبات بسبب الأخبار الاقتصادية العالمية، تابع تحليلاتنا لمعرفة المزيد.</p>
    </div>

    <!-- نموذج تسجيل الدخول -->
    <h2>تسجيل الدخول</h2>
    <form onsubmit="login(event)">
      <div class="form-group">
        <label for="username">اسم المستخدم:</label>
        <input type="text" id="username" name="username" required>
      </div>
      <div class="form-group">
        <label for="password">كلمة المرور:</label>
        <input type="password" id="password" name="password" required>
      </div>
      <div class="form-group">
        <input type="submit" value="تسجيل الدخول">
      </div>
    </form>

    <div class="create-account">
      <p>ليس لديك حساب؟ <a href="https://checkouts.kashier.io/ar/paymentpage?ppLink=PP-2900851101,live">الاشتراك في الكورس</a></p>
    </div>
  </div>

  <script>
    // جلب بيانات العملات باستخدام API الخاص بك
    async function fetchCurrencyRates() {
      try {
        const response = await fetch('https://v6.exchangerate-api.com/v6/2be3e12d9b0850610c4e350e/latest/USD');
        const data = await response.json();

        // تعيين القيم للعرض
        document.getElementById('usd-eur').textContent = data.conversion_rates.EUR.toFixed(2);
        document.getElementById('usd-jpy').textContent = data.conversion_rates.JPY.toFixed(2);
      } catch (error) {
        console.error('حدث خطأ في جلب أسعار العملات:', error);
        document.getElementById('usd-eur').textContent = "غير متاح";
        document.getElementById('usd-jpy').textContent = "غير متاح";
      }
    }

    // استدعاء الدالة عند تحميل الصفحة
    fetchCurrencyRates();

    function login(event) {
      event.preventDefault();
      var username = document.getElementById('username').value;
      var password = document.getElementById('password').value;

      var validUsernames = ['491573729879', '201091327409', '...']; // قائمة بأسماء المستخدمين الصحيحة
      var commonPassword = 'master2024';

      if (validUsernames.includes(username) && password === commonPassword) {
        window.location.href = 'https://master6trade.blogspot.com';
      } else {
        alert('اسم المستخدم أو كلمة المرور غير صحيحة. يرجى التواصل مع دعم شركة ماستر.');
      }
    }
  </script>
</body>
</html>
