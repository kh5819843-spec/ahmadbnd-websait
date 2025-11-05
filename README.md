<!DOCTYPE html>
<html lang="fa">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>فرم تماس با ما</title>

  <!-- ✅ EmailJS Browser CDN جدید -->
  <script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>

  <style>
    body {
      font-family: sans-serif;
      direction: rtl;
      background: #f5f5f5;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    form {
      background: white;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
      width: 320px;
    }

    input, textarea, button {
      width: 100%;
      margin-top: 10px;
      padding: 10px;
      border: 1px solid #ccc; /* ✅ اصلاح شد */
      border-radius: 8px;
      font-size: 14px;
    }

    button {
      background: #28a745;
      color: white;
      border: none;
      cursor: pointer;
      font-weight: bold;
      transition: 0.3s;
    }

    button:hover {
      background: #218838;
    }

    #status {
      margin-top: 10px;
      font-size: 14px;
      text-align: center;
    }
  </style>
</head>
<body>

  <form id="contact-form">
    <h3>فرم تماس با ما</h3>
    <input type="text" name="name" placeholder="نام شما" required>
    <input type="email" name="email" placeholder="ایمیل شما" required>
    <textarea name="message" placeholder="پیام شما..." rows="5" required></textarea>
    <button type="submit">ارسال پیام</button>
    <div id="status"></div>
  </form>

  <script>
    // 🔹 مقداردهی اولیه EmailJS با کلید عمومی شما
    (function() {
      emailjs.init({
        publicKey: "HZWtwr83vTE7CCcv6", // Public Key شما
      });
    })();

    const form = document.getElementById("contact-form");
    const status = document.getElementById("status");

    // 🔹 ارسال فرم
    form.addEventListener("submit", function(event) {
      event.preventDefault();

      emailjs.send("43qNH8mXDjEkEe9Ospp9T", "YOUR_TEMPLATE_ID", {
        from_name: form.name.value,
        from_email: form.email.value,
        message: form.message.value,
      })
      .then(() => {
        status.textContent = "✅ پیام با موفقیت ارسال شد!";
        form.reset();
      }, (error) => {
        console.error(error);
        status.textContent = "❌ خطا در ارسال. لطفاً دوباره تلاش کنید.";
      });
    });
  </script>

</body>
</html>
