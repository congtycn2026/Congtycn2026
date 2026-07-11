<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CN SERVICE TRADING COMPANY LIMITED - Secure Payment Portal</title>
    <style>
        :root {
            --bg-main: #050b14;
            --bg-card: #0c1524;
            --accent: #00f0ff;
            --accent-glow: rgba(0, 240, 255, 0.2);
            --text-main: #cbd5e1;
            --text-white: #ffffff;
            --text-muted: #64748b;
            --border: #1e293b;
            --success: #10b981;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Inter', sans-serif;
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-main);
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            padding: 20px;
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-bottom: 30px;
            border-bottom: 1px solid var(--border);
            margin-bottom: 40px;
        }

        .main-logo {
            height: 55px;
            filter: drop-shadow(0 0 10px var(--accent-glow));
        }

        .nav-links {
            display: flex;
            gap: 30px;
        }

        .nav-links a {
            color: var(--text-muted);
            text-decoration: none;
            font-weight: 500;
        }

        .nav-links a.active {
            color: var(--accent);
        }

        .lang-btn {
            background: transparent;
            border: 1px solid var(--accent);
            color: var(--accent);
            padding: 6px 12px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.85rem;
        }

        .status-badge {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            color: var(--success);
            font-size: 0.85rem;
            margin-bottom: 15px;
        }

        .status-dot {
            width: 8px;
            height: 8px;
            background-color: var(--success);
            border-radius: 50%;
            box-shadow: 0 0 8px var(--success);
        }

        h1 {
            color: var(--text-white);
            font-size: 2.2rem;
            margin-bottom: 10px;
            letter-spacing: -0.5px;
        }

        .subtitle {
            color: var(--accent);
            font-size: 0.9rem;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 40px;
        }

        .payment-box {
            max-width: 600px;
            width: 100%;
            margin: 0 auto;
        }

        .card {
            background-color: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }

        .card h2 {
            color: var(--text-white);
            font-size: 1.3rem;
            margin-bottom: 25px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            color: var(--text-muted);
            font-size: 0.85rem;
            margin-bottom: 8px;
        }

        .form-group input, .form-group select {
            width: 100%;
            background-color: rgba(5, 11, 20, 0.6);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 14px;
            color: var(--text-white);
            font-size: 1rem;
            transition: all 0.3s;
        }

        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 10px var(--accent-glow);
        }

        .submit-btn {
            width: 100%;
            background: linear-gradient(135deg, #00f0ff, #0072ff);
            color: #000;
            border: none;
            border-radius: 8px;
            padding: 16px;
            font-size: 1rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 10px;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 240, 255, 0.4);
        }

        .cards-support {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 20px;
            filter: grayscale(40%);
        }

        .cards-support img {
            height: 24px;
        }
    </style>
</head>
<body>

    <div class="container">
        <header>
            <img src="https://github.io" alt="CN Logo" class="main-logo">
            <div class="nav-links">
                <a href="#" class="active">Thanh toán</a>
                <a href="#">Thông tin công ty</a>
            </div>
            <button class="lang-btn">EN</button>
        </header>

        <div class="status-badge">
            <div class="status-dot"></div>
            Cổng thanh toán quốc tế bảo mật 3D-Secure
        </div>

        <h1>CN SERVICE TRADING COMPANY LIMITED</h1>
        <div class="subtitle">TRADING, IMPORT & EXPORT, COMMERCIAL SERVICES</div>

        <div class="payment-box">
            <div class="card">
                <h2>Khởi tạo cổng thanh toán quốc tế</h2>
                
                <div class="form-group">
                    <label for="currency">Loại tiền tệ (Currency)</label>
                    <select id="currency" onchange="toggleExchangeRate()">
                        <option value="USD">USD - Đô la Mỹ</option>
                        <option value="VND">VND - Việt Nam Đồng</option>
                    </select>
                </div>

                <div class="form-group">
                    <label id="amountLabel" for="amount">Số tiền cần chuyển (USD)</label>
                    <input type="number" id="amount" placeholder="Ví dụ: 100" oninput="calculateVND()">
                </div>

                <div id="exchangeRateGroup" class="form-group">
                    <label style="color: var(--accent);">Tạm tính quy đổi sang VND (Tỷ giá: 1 USD = 25,500 VND)</label>
                    <input type="text" id="convertedAmount" readonly style="background: rgba(255,255,255,0.05); color: #fff;" value="0 VND">
                </div>

                <div class="form-group">
                    <label for="memo">Nội dung thanh toán (Description)</label>
                    <input type="text" id="memo" placeholder="Ví dụ: THANH TOAN DON HANG 102">
                </div>

                <button class="submit-btn" onclick="processInternationalPayment()">TIẾN HÀNH THANH TOÁN (PAY NOW)</button>

                <div class="cards-support">
                    <img src="https://icons8.com" alt="Visa">
                    <img src="https://icons8.com" alt="Mastercard">
                    <img src="https://icons8.com" alt="JCB">
                </div>
            </div>
        </div>
    </div>

    <script>
        const EXCHANGE_RATE = 25500; // Cập nhật tỷ giá thực tế tại đây
        
        // ĐIỀN LINK THANH TOÁN DOANH NGHIỆP CỦA BẠN VÀO ĐÂY
        const PAYOS_LINK = "https://payos.vn"; 

        function toggleExchangeRate() {
            const currency = document.getElementById("currency").value;
            const amountLabel = document.getElementById("amountLabel");
            const exchangeRateGroup = document.getElementById("exchangeRateGroup");
            const amountInput = document.getElementById("amount");

            if (currency === "VND") {
                amountLabel.innerText = "Số tiền cần chuyển (VND)";
                amountInput.placeholder = "Ví dụ: 2500000";
                exchangeRateGroup.style.display = "none";
            } else {
                amountLabel.innerText = "Số tiền cần chuyển (USD)";
                amountInput.placeholder = "Ví dụ: 100";
                exchangeRateGroup.style.display = "block";
            }
            calculateVND();
        }

        function calculateVND() {
            const currency = document.getElementById("currency").value;
            const amount = document.getElementById("amount").value;
            const convertedInput = document.getElementById("convertedAmount");

            if (currency === "USD" && amount > 0) {
                const totalVND = amount * EXCHANGE_RATE;
                convertedInput.value = totalVND.toLocaleString('vi-VN') + " VND";
            } else {
                convertedInput.value = "0 VND";
            }
        }

        function processInternationalPayment() {
            const currency = document.getElementById("currency").value;
            const amount = document.getElementById("amount").value;
            const memo = document.getElementById("memo").value.trim();

            if (!amount || amount <= 0) {
                alert("Vui lòng nhập số tiền hợp lệ / Please enter a valid amount.");
                return;
            }

            // Tính toán số tiền cuối cùng bằng VND để gửi lên cổng thanh toán
            let finalAmountVND = currency === "USD" ? amount * EXCHANGE_RATE : amount;

            // Xử lý tạo link thanh toán động hoặc chuyển hướng đến Link thanh toán cố định của doanh nghiệp
