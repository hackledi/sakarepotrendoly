<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trendyol Giriş Yap</title>
    <style>
        /* Genel Sayfa Ayarları */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }

        /* Giriş Konteyneri */
        .login-container {
            width: 300px;
            padding: 20px;
            background-color: #ffffff;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            text-align: center;
            border: 1px solid #ddd;
        }

        .login-container h2 {
            font-size: 20px;
            color: #333;
            margin-bottom: 30px;
        }

        .input-field {
            width: 100%;
            padding: 12px;
            margin-bottom: 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 14px;
        }

        .login-button {
            width: 100%;
            padding: 12px;
            background-color: #ff8c00;
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .login-button:hover {
            background-color: #e87c00;
        }

        .login-button:disabled {
            background-color: #ddd;
            cursor: not-allowed;
        }

        /* Yükleme Simgesi */
        .spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #3498db;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            animation: spin 2s linear infinite;
            margin: 20px auto;
            display: none;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .footer-links {
            margin-top: 20px;
            font-size: 12px;
            color: #555;
        }

        .footer-links a {
            text-decoration: none;
            color: #ff8c00;
        }

        /* Hata Mesajı */
        .error-message {
            color: red;
            font-size: 14px;
            margin-top: 10px;
        }

        /* Başarı Mesajı */
        .success-message {
            color: green;
            font-size: 14px;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <div class="login-container">
        <h2>Hesabınıza Giriş Yapın</h2>
        <input type="email" class="input-field" placeholder="E-posta adresiniz" id="email">
        <input type="password" class="input-field" placeholder="Şifreniz" id="password">
        <button class="login-button" onclick="showSpinner()">Giriş Yap</button>
        <div class="spinner" id="spinner"></div>

        <div class="footer-links">
            <p><a href="#">Şifremi unuttum</a></p>
            <p><a href="#">Üye olmadan devam et</a></p>
        </div>

        <!-- Hata ve Başarı Mesajları -->
        <div id="message" class="error-message"></div>
        <div id="successMessage" class="success-message"></div>
    </div>

    <script>
        function showSpinner() {
            var spinner = document.getElementById("spinner");
            var loginButton = document.querySelector(".login-button");
            var messageDiv = document.getElementById("message");
            var successMessageDiv = document.getElementById("successMessage");

            // Yükleme simgesini göster
            spinner.style.display = "block";
            loginButton.disabled = true; // Butonu devre dışı bırak
            messageDiv.textContent = ""; // Önceki mesajları temizle
            successMessageDiv.textContent = ""; // Önceki başarı mesajlarını temizle

            // 2 saniye sonra, gerçek giriş kontrolünü simüle et
            setTimeout(function() {
                // Burada şifre kontrolü yapıyoruz (gerçek kontrol değil)
                var email = document.getElementById("email").value;
                var password = document.getElementById("password").value;

                // Sahte giriş doğrulama (email ve şifre kontrolü)
                if (email === "test@example.com" && password === "1234") {
                    successMessageDiv.textContent = "Giriş başarılı!";
                    messageDiv.textContent = ""; // Hata mesajını temizle
                } else {
                    messageDiv.textContent = "Yanlış e-posta veya şifre!";
                    successMessageDiv.textContent = ""; // Başarı mesajını temizle
                }

                // Yükleme simgesini gizle ve butonu tekrar aktif yap
                spinner.style.display = "none";
                loginButton.disabled = false;
            }, 2000); // 2 saniye
        }
    </script>

</body>
</html>
