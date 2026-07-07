<!-- ========================================================
  Tập tin: Web Nhận Acc Liên Quân Free - iOS
  Nền tảng: HTML/CSS/JS thuần (chạy trên mọi trình duyệt)
  Chức năng: Nhập key thường, key VIP, mã nhận acc
  Dữ liệu: Lưu trong localStorage + danh sách acc ảo
  ======================================================== -->

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nhận Acc Liên Quân Free - iOS</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0a0a1a 0%, #1a1a3e 50%, #0d0d2b 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #e0e0e0;
        }

        .container {
            width: 95%;
            max-width: 480px;
            background: rgba(20, 20, 40, 0.9);
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 0 40px rgba(0, 150, 255, 0.3), 0 0 80px rgba(0, 100, 200, 0.1);
            border: 1px solid rgba(0, 150, 255, 0.2);
        }

        .header {
            text-align: center;
            margin-bottom: 25px;
        }

        .header h1 {
            font-size: 2em;
            font-weight: 900;
            background: linear-gradient(135deg, #00d4ff, #0088ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .header .subtitle {
            font-size: 0.9em;
            color: #888;
            margin-top: 5px;
        }

        .section {
            background: rgba(30, 30, 60, 0.7);
            border-radius: 12px;
            padding: 18px;
            margin-bottom: 18px;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .section-title {
            font-size: 1.1em;
            font-weight: 700;
            color: #00ccff;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .section-title .icon {
            font-size: 1.3em;
        }

        .input-group {
            display: flex;
            gap: 8px;
            margin-bottom: 10px;
        }

        .input-group input {
            flex: 1;
            padding: 12px 15px;
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            background: rgba(0, 0, 0, 0.4);
            color: #fff;
            font-size: 1em;
            outline: none;
            transition: all 0.3s;
        }

        .input-group input:focus {
            border-color: #00aaff;
            box-shadow: 0 0 15px rgba(0, 170, 255, 0.3);
        }

        .input-group input::placeholder {
            color: #555;
        }

        .btn {
            padding: 12px 20px;
            border: none;
            border-radius: 10px;
            font-weight: 700;
            font-size: 0.95em;
            cursor: pointer;
            transition: all 0.3s;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .btn-gold {
            background: linear-gradient(135deg, #ffaa00, #ff6600);
            color: #000;
            width: 100%;
            box-shadow: 0 4px 15px rgba(255, 150, 0, 0.4);
        }

        .btn-gold:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 25px rgba(255, 150, 0, 0.6);
        }

        .btn-vip {
            background: linear-gradient(135deg, #ff0066, #cc0044);
            color: #fff;
            width: 100%;
            box-shadow: 0 4px 15px rgba(255, 0, 100, 0.4);
        }

        .btn-vip:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 25px rgba(255, 0, 100, 0.6);
        }

        .btn-normal {
            background: linear-gradient(135deg, #00aaff, #0066cc);
            color: #fff;
            width: 100%;
            box-shadow: 0 4px 15px rgba(0, 150, 255, 0.4);
        }

        .btn-normal:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 25px rgba(0, 150, 255, 0.6);
        }

        .btn-small {
            padding: 10px 15px;
            font-size: 0.85em;
            white-space: nowrap;
        }

        .result-box {
            background: rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            padding: 15px;
            margin-top: 10px;
            border: 1px solid rgba(0, 255, 100, 0.3);
            display: none;
        }

        .result-box.show {
            display: block;
            animation: fadeIn 0.3s ease;
        }

        .result-box .acc-info {
            font-size: 1em;
            line-height: 1.8;
            word-break: break-all;
        }

        .result-box .acc-info span {
            color: #00ff88;
            font-weight: 700;
        }

        .copy-btn {
            margin-top: 10px;
            padding: 8px 15px;
            background: #333;
            color: #fff;
            border: 1px solid #555;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.85em;
            transition: all 0.3s;
        }

        .copy-btn:hover {
            background: #444;
        }

        .status {
            text-align: center;
            font-size: 0.85em;
            color: #ffaa00;
            margin-top: 8px;
            min-height: 20px;
        }

        .divider {
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
            margin: 15px 0;
        }

        .badge {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.75em;
            font-weight: 700;
            margin-left: 5px;
        }

        .badge-vip {
            background: #ff0066;
            color: #fff;
        }

        .badge-free {
            background: #00aa55;
            color: #fff;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @media (max-width: 400px) {
            .container {
                padding: 15px;
            }
            .header h1 {
                font-size: 1.5em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1>⚔️ Nhận Acc LQ Free</h1>
            <p class="subtitle">Phiên bản iOS • Cập nhật 2026</p>
        </div>

        <!-- Mục 1: Nhập Key Thường -->
        <div class="section">
            <div class="section-title">
                <span class="icon">🔑</span> Nhập Key Thường
                <span class="badge badge-free">FREE</span>
            </div>
            <div class="input-group">
                <input type="text" id="keyThuong" placeholder="Nhập key thường... VD: LQ-FREE-XXXX">
            </div>
            <div class="input-group">
                <input type="text" id="maNhan" placeholder="Nhập mã nhận acc... VD: ACC-XXXX">
            </div>
            <button class="btn btn-normal" onclick="nhanAccThuong()">
                🎁 Nhận Acc Thường
            </button>
            <div class="status" id="statusThuong"></div>
        </div>

        <!-- Mục 2: Nhập Key VIP -->
        <div class="section">
            <div class="section-title">
                <span class="icon">👑</span> Nhập Key VIP
                <span class="badge badge-vip">VIP</span>
            </div>
            <div class="input-group">
                <input type="text" id="keyVip" placeholder="Nhập key VIP... VD: LQ-VIP-XXXX">
            </div>
            <div class="input-group">
                <input type="text" id="maNhanVip" placeholder="Nhập mã VIP... VD: VIP-XXXX">
            </div>
            <button class="btn btn-vip" onclick="nhanAccVip()">
                💎 Nhận Acc VIP
            </button>
            <div class="status" id="statusVip"></div>
        </div>

        <!-- Kết quả -->
        <div class="result-box" id="resultBox">
            <div class="section-title">
                <span class="icon">✅</span> Thông Tin Acc
            </div>
            <div class="acc-info" id="accInfo"></div>
            <button class="copy-btn" onclick="copyAcc()">📋 Sao chép thông tin</button>
        </div>

        <div class="divider"></div>
        <p style="text-align:center; font-size:0.75em; color:#555;">
            ⚠️ Tool chỉ mang tính chất minh họa - Acc demo
        </p>
    </div>

    <script>
        // ==================== DATABASE ACC ẢO ====================
        const accDatabase = {
            // Key thường -> Acc thường
            "LQ-FREE-1234": {
                taiKhoan: "lqfree_user01",
                matKhau: "Pass@Free001",
                tuong: 45,
                skin: 12,
                rank: "Kim Cương V",
                server: "iOS - Việt Nam"
            },
            "LQ-FREE-5678": {
                taiKhoan: "lqfree_user02",
                matKhau: "Pass@Free002",
                tuong: 52,
                skin: 18,
                rank: "Tinh Anh III",
                server: "iOS - Việt Nam"
            },
            "LQ-FREE-9999": {
                taiKhoan: "lqfree_pro99",
                matKhau: "Pro@Free999",
                tuong: 60,
                skin: 25,
                rank: "Cao Thủ 15 Sao",
                server: "iOS - Việt Nam"
            },

            // Key VIP -> Acc VIP
            "LQ-VIP-1111": {
                taiKhoan: "lqvip_legend01",
                matKhau: "Vip@Legend1",
                tuong: 95,
                skin: 78,
                rank: "Thách Đấu 50 Sao",
                server: "iOS - Việt Nam",
                vip: true
            },
            "LQ-VIP-2222": {
                taiKhoan: "lqvip_master02",
                matKhau: "Vip@Master2",
                tuong: 90,
                skin: 65,
                rank: "Thách Đấu 30 Sao",
                server: "iOS - Việt Nam",
                vip: true
            },
            "LQ-VIP-8888": {
                taiKhoan: "lqvip_god888",
                matKhau: "God@Vip888",
                tuong: 112,
                skin: 120,
                rank: "Top 1 Server",
                server: "iOS - Việt Nam",
                vip: true,
                dacBiet: "Tất cả skin giới hạn"
            }
        };

        // ==================== HÀM KIỂM TRA MÃ ====================
        function kiemTraMa(ma) {
            const maHopLe = ["ACC-FREE", "ACC-VIP", "ACC-LQ", "ACC-2026", "VIP-FREE"];
            return maHopLe.some(m => ma.toUpperCase().startsWith(m));
        }

        // ==================== NHẬN ACC THƯỜNG ====================
        function nhanAccThuong() {
            const keyThuong = document.getElementById("keyThuong").value.trim();
            const maNhan = document.getElementById("maNhan").value.trim();
            const statusEl = document.getElementById("statusThuong");
            const resultBox = document.getElementById("resultBox");
            const accInfo = document.getElementById("accInfo");

            // Validate
            if (!keyThuong) {
                statusEl.textContent = "⚠️ Vui lòng nhập key thường!";
                statusEl.style.color = "#ff6600";
                return;
            }
            if (!maNhan) {
                statusEl.textContent = "⚠️ Vui lòng nhập mã nhận acc!";
                statusEl.style.color = "#ff6600";
                return;
            }
            if (!kiemTraMa(maNhan)) {
                statusEl.textContent = "❌ Mã nhận acc không hợp lệ! (Gợi ý: ACC-FREE, ACC-2026)";
                statusEl.style.color = "#ff3333";
                return;
            }

            // Tìm acc
            const acc = accDatabase[keyThuong.toUpperCase()];
            if (!acc) {
                statusEl.textContent = "❌ Key thường không tồn tại trong hệ thống!";
                statusEl.style.color = "#ff3333";
                return;
            }
            if (acc.vip) {
                statusEl.textContent = "⚠️ Key này thuộc VIP, vui lòng dùng mục Key VIP!";
                statusEl.style.color = "#ffaa00";
                return;
            }

            // Hiển thị kết quả
            accInfo.innerHTML = `
                🎮 <span>Tài khoản:</span> ${acc.taiKhoan}<br>
                🔒 <span>Mật khẩu:</span> ${acc.matKhau}<br>
                👥 <span>Số tướng:</span> ${acc.tuong}<br>
                💄 <span>Số skin:</span> ${acc.skin}<br>
                🏆 <span>Rank:</span> ${acc.rank}<br>
                📱 <span>Server:</span> ${acc.server}
            `;
            resultBox.classList.add("show");
            statusEl.textContent = "✅ Nhận acc thành công!";
            statusEl.style.color = "#00ff88";

            // Lưu lịch sử
            luuLichSu(keyThuong, acc, false);
        }

        // ==================== NHẬN ACC VIP ====================
        function nhanAccVip() {
            const keyVip = document.getElementById("keyVip").value.trim();
            const maNhanVip = document.getElementById("maNhanVip").value.trim();
            const statusEl = document.getElementById("statusVip");
            const resultBox = document.getElementById("resultBox");
            const accInfo = document.getElementById("accInfo");

            // Validate
            if (!keyVip) {
                statusEl.textContent = "⚠️ Vui lòng nhập key VIP!";
                statusEl.style.color = "#ff6600";
                return;
            }
            if (!maNhanVip) {
                statusEl.textContent = "⚠️ Vui lòng nhập mã VIP!";
                statusEl.style.color = "#ff6600";
                return;
            }
            if (!maNhanVip.toUpperCase().startsWith("VIP-")) {
                statusEl.textContent = "❌ Mã VIP không hợp lệ! (Phải bắt đầu bằng VIP-)";
                statusEl.style.color = "#ff3333";
                return;
            }

            // Tìm acc
            const acc = accDatabase[keyVip.toUpperCase()];
            if (!acc) {
                statusEl.textContent = "❌ Key VIP không tồn tại trong hệ thống!";
                statusEl.style.color = "#ff3333";
                return;
            }
            if (!acc.vip) {
                statusEl.textContent = "⚠️ Key này là key thường, vui lòng dùng mục Key Thường!";
                statusEl.style.color = "#ffaa00";
                return;
            }

            // Hiển thị kết quả
            let dacBietHTML = acc.dacBiet ? `🌟 <span>Đặc biệt:</span> ${acc.dacBiet}<br>` : "";
            accInfo.innerHTML = `
                👑 <span style="color:#ffcc00;">[VIP]</span> <span>Tài khoản:</span> ${acc.taiKhoan}<br>
                🔒 <span>Mật khẩu:</span> ${acc.matKhau}<br>
                👥 <span>Số tướng:</span> ${acc.tuong}<br>
                💄 <span>Số skin:</span> ${acc.skin}<br>
                🏆 <span>Rank:</span> ${acc.rank}<br>
                📱 <span>Server:</span> ${acc.server}<br>
                ${dacBietHTML}
            `;
            resultBox.classList.add("show");
            statusEl.textContent = "✅ Nhận acc VIP thành công!";
            statusEl.style.color = "#ffcc00";

            // Lưu lịch sử
            luuLichSu(keyVip, acc, true);
        }

        // ==================== SAO CHÉP ====================
        function copyAcc() {
            const accInfo = document.getElementById("accInfo");
            const text = accInfo.innerText;
            navigator.clipboard.writeText(text).then(() => {
                alert("✅ Đã sao chép thông tin acc vào clipboard!");
            }).catch(() => {
                alert("❌ Lỗi sao chép. Vui lòng bôi đen và copy thủ công.");
            });
        }

        // ==================== LƯU LỊCH SỬ ====================
        function luuLichSu(key, acc, isVip) {
            let lichSu = JSON.parse(localStorage.getItem("lq_history") || "[]");
            lichSu.unshift({
                key: key,
                acc: acc.taiKhoan,
                rank: acc.rank,
                vip: isVip,
                thoiGian: new Date().toLocaleString("vi-VN")
            });
            // Giới hạn 20 mục
            if (lichSu.length > 20) lichSu = lichSu.slice(0, 20);
            localStorage.setItem("lq_history", JSON.stringify(lichSu));
        }

        // ==================== KHỞI TẠO ====================
        console.log("✅ Web Nhận Acc LQ Free iOS đã sẵn sàng");
        console.log("🔑 Key thường demo: LQ-FREE-1234, LQ-FREE-5678, LQ-FREE-9999");
        console.log("👑 Key VIP demo: LQ-VIP-1111, LQ-VIP-2222, LQ-VIP-8888");
        console.log("📋 Mã nhận hợp lệ: ACC-FREE, ACC-VIP, ACC-2026, VIP-FREE");
    </script>
</body>
</html>
