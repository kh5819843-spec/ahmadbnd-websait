<!DOCTYPE html>
<html lang="fa">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AHAMD.BND | وب‌سایت شخصی</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>👋 سلام! من Ahamd BND هستم</h1>
    <p>طراح وب از بندرعباس | عاشق گرافیک و خلاقیت</p>
  </header>

  <section id="about">
    <h2>درباره من</h2>
    <p>
      من احمد هستم، توسعه‌دهنده و طراح وب با تمرکز بر طراحی تاریک و مدرن.  
      علاقه‌مند به پروژه‌های خلاقانه و تجربه‌های کاربری خاص.
    </p>
  </section>

  <section id="social">
    <h2>شبکه‌های اجتماعی</h2>
    <ul>
      <li><a href="https://github.ahmad-websayte67.com" target="_blank">صفحه GitHub من</a></li>
    </ul>
  </section>

  <section id="contact">
    <h2>ارتباط با من</h2>
    <form id="contactForm">
      <label for="name">نام:</label>
      <input type="text" id="name" name="name" required>

      <label for="email">ایمیل:</label>
      <input type="email" id="email" name="email" required>

      <label for="message">پیام:</label>
      <textarea id="message" name="message" rows="5" required></textarea>

      <button type="submit">ارسال پیام</button>
    </form>
    <p id="status"></p>
  </section>

  <footer>
    <p>© 2025 Ahamd BND | ساخته‌شده با ❤️</p>
  </footer>

  <!-- 📦 EmailJS -->
  <script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
  <script>
    // 🧩  EmailJS
    emailjs.init("kh5819843@gmail.com"); // Public Key 

    const form = document.getElementById("contactForm");
    const status = document.getElementById("status");

    form.addEventListener("submit", function (e) {
      e.preventDefault();
      status.textContent = "در حال ارسال...";

      // ارسال پیام از طریق سرویس تستی
      emailjs.send("service_test123", "template_test123", {
        from_name: form.name.value,
        from_email: form.email.value,
        message: form.message.value,
      })
      .then(() => {
        status.textContent = "✅ پیام با موفقیت ارسال شد!";
        form.reset();
      }, (error) => {
        console.error(error);
        status.textContent = "❌ خطا در ارسال پیام. لطفاً دوباره تلاش کنید.";
      });
    });
  </script>
</body>
</html>
