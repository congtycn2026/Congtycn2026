index.html<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CN SERVICE TRADING COMPANY LIMITED - Secure Payment Portal</title>
    <link href="https://googleapis.com" rel="stylesheet">
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
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Inter', sans-serif; }
        body { background-color: var(--bg-main); color: var(--text-main); display: flex; justify-content: center; align-items: center; min-height: 100vh; overflow-x: hidden; }
        .container { width: 100%; max-width: 1200px; padding: 20px; }
        header { display: flex; justify-content: space-between; align-items: center; padding-bottom: 30px; border-bottom: 1px solid var(--border); margin-bottom: 40px; }
        .main-logo { height: 55px; filter: drop-shadow(0 0 10px var(--accent-glow)); transition: transform 0.3s ease; }
        .main-logo:hover { transform: scale(1.05); }
        .nav-links a { color: var(--text-muted); text-decoration: none; margin-right: 20px; font-weight: 500; transition: color 0.3s; }
        .nav-links a.active, .nav-links a:hover { color: var(--accent); }
        #btn-lang { background: none; border: 1px solid var(--accent); color: var(--accent); padding: 5px 12px; border-radius: 6px; cursor: pointer; font-weight: 600; box-shadow: 0 0 8px var(--accent-glow); }
        .payment-grid { display: grid; grid-template-columns: 1fr 450px; gap: 40px; margin-bottom: 40px; }
        .invoice-panel { display: flex; flex-direction: column; justify-content: center; }
        .badge-status { display: inline-flex; align-items: center; background: rgba(16, 185, 129, 0.1); color: var(--success); padding: 6px 14px; border-radius: 20px; font-size: 0.85rem; font-weight: 500; width: fit-content; margin-bottom: 20px; }
        .badge-status .dot { width: 8px; height: 8px; background-color: var(--success); border-radius: 50%; margin-right: 8px; animation: pulse 2s infinite; }
        .company-title { color: var(--text-white); font-size: 2.2rem; font-weight: 700; letter-spacing: -0.5px; margin-bottom: 5px; }
        .company-sub { color: var(--accent); text-transform: uppercase; font-size: 0.85rem; font-weight: 600; letter-spacing: 1px; margin-bottom: 30px; }
        .info-table { border: 1px solid var(--border); border-radius: 12px; background: var(--bg-card); overflow: hidden; }
        .info-row { display: flex; justify-content: space-between; padding: 16px 20px; border-bottom: 1px solid var(--border); }
        .info-row:last-child { border-bottom: none; }
        .info-row .label { color: var(--text-muted); font-size: 0.9rem; }
        .info-row .value { color: var(--text-white); font-weight: 500; text-align: right; max-width: 60%; }
        .info-row .value.highlight { color: var(--accent); font-weight: 600; }
        .info-row .value a { color: var(--accent); text-decoration: none; }
        .qr-panel { display: flex; justify-content: center; }
        .qr-card { background: var(--bg-card); border: 1px solid var(--border); border-radius: 24px; padding: 30px; width: 100%; box-shadow: 0 20px 40px rgba(0,0,0,0.4); position: relative; }
        .vcb-header { display: flex; justify-content: space-between; font-weight: 700; margin-bottom: 25px; }
        .bank-name { color: var(--text-white); font-size: 1.2rem; }
        .vietqr-badge { color: #e11d48; background: rgba(225,29,72,0.1); padding: 2px 10px; border-radius: 6px; font-size: 0.8rem; }
        .qr-wrapper { background: #ffffff; padding: 15px; border-radius: 16px; display: flex; justify-content: center; margin-bottom: 20px; box-shadow: 0 0 25px rgba(0, 240, 255, 0.1); }
        .qr-wrapper img { width: 100%; max-width: 260px; height: auto; }
        .qr-instruction { text-align: center; font-size: 0.85rem; color: var(--text-muted); margin-bottom: 25px; }
        .account-details { background: var(--bg-main); border-radius: 12px; padding: 15px; margin-bottom: 25px; }
        .acc-box { margin-bottom: 12px; }
        .acc-box:last-child { margin-bottom: 0; }
        .acc-label { display: block; font-size: 0.75rem; color: var(--text-muted); text-transform: uppercase; margin-bottom: 4px; }
        .acc-value { color: var(--text-white); font-weight: 600; font-size: 1rem; }
        .copy-wrapper { display: flex; justify-content: space-between; align-items: center; }
        .btn-copy { background: rgba(0, 240, 255, 0.1); border: 1px solid rgba(0, 240, 255, 0.3); color: var(--accent); padding: 4px 10px; border-radius: 4px; font-size: 0.75rem; cursor: pointer; }
        .btn-primary, .btn-secondary { display: flex; align-items: center; justify-content: center; width: 100%; padding: 14px; border-radius: 12px; font-weight: 600; cursor: pointer; text-decoration: none; transition: all 0.2s; font-size: 0.95rem; }
        .btn-primary { background: var(--accent); color: var(--bg-main); border: none; box-shadow: 0 4px 15px var(--accent-glow); }
        .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 6px 20px var(--accent); }
        .action-footers { display: flex; gap: 15px; margin-top: 25px; }
        .btn-secondary { background: transparent; border: 1px solid var(--border); color: var(--text-main); }
        .btn-secondary:hover { background: var(--border); color: var(--text-white); }
        .text-center { text-align: center; }
        .global-footer { text-align: center; color: var(--text-muted); font-size: 0.8rem; border-top: 1px solid var(--border); padding-top: 20px; margin-top: 20px; }
        @keyframes pulse {
            0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(16, 185, 129, 0.7); }
            70% { transform: scale(1); box-shadow: 0 0 0 6px rgba(16, 185, 129, 0); }
            100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(16, 185, 129, 0); }
        }
        @media (max-width: 900px) { .payment-grid { grid-template-columns: 1fr; gap: 30px; } header { margin-bottom: 20px; } .company-title { font-size: 1.8rem; } }
        @media print { body { background: white; color: black; } .dark-theme { --bg-main: #ffffff; --bg-card: #ffffff; --text-main: #000000; --text-white: #000000; --border: #cccccc; } .no-print, .lang-switcher, .btn-copy, .nav-links { display: none !important; } .qr-card { box-shadow: none; border: 1px solid #000; } .payment-grid { grid-template-columns: 1fr; } }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo-area">
                <!-- Thay link ảnh logo của anh vào đây nếu chạy thực tế -->
                <img src="https://ibb.co" alt="CN Logo" class="main-logo">
            </div>
            <nav class="nav-links">
                <a href="#" class="active" data-vi="Thanh toán" data-en="Payment">Thanh toán</a>
                <a href="#company-info" data-vi="Thông tin công ty" data-en="Company Info">Thông tin công ty</a>
            </nav>
            <div class="lang-switcher">
                <button id="btn-lang" onclick="toggleLanguage()">EN</button>
            </div>
        </header>

        <main class="payment-grid">
            <section class="invoice-panel" id="company-info">
                <div class="badge-status">
                    <span class="dot"></span> <span data-vi="Cổng thanh toán bảo mật HTTPS" data-en="Secure HTTPS Payment Gateway">Cổng thanh toán bảo mật HTTPS</span>
                </div>
                
                <h1 class="company-title">CN SERVICE TRADING COMPANY LIMITED</h1>
                <p class="company-sub">Trading, Import & Export, Commercial Services</p>

                <div class="info-table">
                    <div class="info-row">
                        <span class="label" data-vi="Mã số doanh nghiệp" data-en="Business Reg No.">Mã số doanh nghiệp</span>
                        <span class="value highlight">0110922550</span>
                    </div>
                    <div class="info-row">
                        <span class="label" data-vi="Đại diện pháp luật" data-en="Legal Representative">Đại diện pháp luật</span>
                        <span class="value">NGUYEN CHINH (Director)</span>
                    </div>
                    <div class="info-row">
                        <span class="label" data-vi="Vốn điều lệ" data-en="Charter Capital">Vốn điều lệ</span>
                        <span class="value">2,000,000,000 VND</span>
                    </div>
                    <div class="info-row">
                        <span class="label" data-vi="Địa chỉ trụ sở" data-en="Registered Address">Địa chỉ trụ sở</span>
                        <span class="value">90/61 Pho Tram, Long Bien, Hanoi, Vietnam</span>
                    </div>
                    <div class="info-row">
                        <span class="label" data-vi="Email liên hệ" data-en="Official Email">Email liên hệ</span>
                        <span class="value"><a href="mailto:nc0982650007@gmail.com">nc0982650007@gmail.com</a></span>
                    </div>
                    <div class="info-row">
                        <span class="label" data-vi="Điện thoại" data-en="Telephone">Điện thoại</span>
                        <span class="value">+84 982 650 007</span>
                    </div>
                </div>

                <div class="action-footers no-print">
                    <button class="btn-secondary" onclick="window.print()">
                        📊 <span data-vi="In hóa đơn này" data-en="Print Invoice">In hóa đơn này</span>
                    </button>
