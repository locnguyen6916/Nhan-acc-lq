<!-- ========================================================
  Tập tin: Web Nhận Acc Liên Quân Free - iOS (Bản Full)
  Chức năng: 
    - Nhận acc thường + VIP (đã xóa yêu cầu mã)
    - Mục riêng: Thêm acc của bạn vào hệ thống
    - Mục vượt link: Mở link không bị chặn
    - Lưu toàn bộ vào localStorage
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
            padding: 10px;
        }

        .container {
            width: 100%;
            max-width: 500px;
            background: rgba(20, 20, 40, 0.92);
            border-radius: 20px;
            padding: 20px;
            box-shadow: 0 0 40px rgba(0, 150, 255, 0.3), 0 0 80px rgba(0, 100, 200, 0.1);
            border: 1px solid rgba(0, 150, 255, 0.2);
        }

        .header {
            text-align: center;
            margin-bottom: 20px;
        }

        .header h1 {
            font-size: 1.8em;
            font-weight: 900;
            background: linear-gradient(135deg, #00d4ff, #0088ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .header .subtitle {
            font-size: 0.85em;
            color: #888;
            margin-top: 5px;
        }

        /* Tabs */
        .tabs {
            display: flex;
            gap: 5px;
            margin-bottom: 15px;
            background: rgba(0,0,0,0.3);
            border-radius: 12px;
            padding: 4px;
        }

        .tab {
            flex: 1;
            padding: 10px 5px;
            text-align: center;
            border-radius: 10px;
            font-size: 0.8em;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            color: #888;
            border: none;
            background: transparent;
        }

        .tab.active {
            background: rgba(0, 150, 255, 0.3);
            color: #fff;
            box-shadow: 0 0 10px rgba(0, 150, 255, 0.3);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
            animation: fadeIn 0.3s ease;
        }

        /* Section */
        .section {
            background: rgba(30, 30, 60, 0.7);
            border-radius: 12px;
            padding: 18px;
            margin-bottom: 15px;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .section-title {
            font-size: 1em;
            font-weight: 700;
            color: #00ccff;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .input-group {
            display: flex;
            gap: 8px;
            margin-bottom: 10px;
            flex-wrap: wrap;
        }

        .input-group input, .input-group textarea {
            flex: 1;
            min-width: 120px;
            padding: 12px 15px;
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            background: rgba(0, 0, 0, 0.4);
            color: #fff;
            font-size: 0.95em;
            outline: none;
            transition: all 0.3s;
            font-family: inherit;
        }

        .input-group textarea {
            min-height: 80px;
            resize: vertical;
        }

        .input-group input:focus, .input-group textarea:focus {
            border-color: #00aaff;
            box-shadow: 0 0 15px rgba(0, 170, 255, 0.3);
        }

        .input-group input::placeholder, .input-group textarea::placeholder {
            color: #555;
        }

        .btn {
            padding: 12px 20px;
            border: none;
            border-radius: 10px;
            font-weight: 700;
            font-size: 0.9em;
            cursor: pointer;
            transition: all 0.3s;
            text-transform: uppercase;
            letter-spacing: 1px;
            width: 100%;
        }

        .btn-normal {
            background: linear-gradient(135deg, #00aaff, #0066cc);
            color: #fff;
            box-shadow: 0 4px 15px rgba(0, 150, 255, 0.4);
        }

        .btn-vip {
            background: linear-gradient(135deg, #ff0066, #cc0044);
            color: #fff;
            box-shadow: 0 4px 15px rgba(255, 0, 100, 0.4);
        }

        .btn-gold {
            background: linear-gradient(135deg, #ffaa00, #ff6600);
            color: #000;
            box-shadow: 0 4px 15px rgba(255, 150, 0, 0.4);
        }

        .btn-green {
            background: linear-gradient(135deg, #00cc66, #009944);
            color: #fff;
            box-shadow: 0 4px 15px rgba(0, 200, 100, 0.4);
        }

        .btn-red {
            background: linear-gradient(135deg, #ff3333, #cc0000);
            color: #fff;
            box-shadow: 0 4px 15px rgba(255, 50, 50, 0.4);
        }

        .btn:hover {
            transform: translateY(-2px);
            filter: brightness(1.2);
        }

        .btn-small {
            padding: 8px 12px;
            font-size: 0.75em;
            width: auto;
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
            font-size: 0.95em;
            line-height: 1.8;
            word-break: break-all;
        }

        .result-box .acc-info span {
            color: #00ff88;
            font-weight: 700;
        }

        .status {
            text-align: center;
            font-size: 0.85em;
            color: #ffaa00;
            margin-top: 8px;
            min-height: 20px;
        }

        .list-item {
            background: rgba(0,0,0,0.3);
            border-radius: 8px;
            padding: 10px;
            margin-bottom: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 8px;
            font-size: 0.85em;
        }

        .list-item .acc-detail {
            flex: 1;
            min-width: 150px;
        }

        .badge {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.7em;
            font-weight: 700;
        }

        .badge-vip { background: #ff0066; color: #fff; }
        .badge-free { background: #00aa55; color: #fff; }
        .badge-mine { background: #ffaa00; color: #000; }

        .divider {
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
            margin: 15px 0;
        }

        iframe {
            width: 100%;
            height: 500px;
            border: 1px solid rgba(255,255,255,0.1);
            border-radius: 10px;
            background: #fff;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @media (max-width: 400px) {
            .container { padding: 12px; }
            .header h1 { font-size: 1.4em; }
            .tabs { flex-wrap: wrap; }
            .tab { font-size: 0.7em; padding: 8px 4px; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1>⚔️ Nhận Acc LQ Free</h1>
            <p class="subtitle">Phiên bản iOS • Full Chức Năng</p>
        </div>

        <!-- Tabs -->
        <div class="tabs">
            <button class="tab active" onclick="chuyenTab('nhanAcc')">🎁 Nhận Acc</button>
            <button class="tab" onclick="chuyenTab('themAcc')">➕ Thêm Acc</button>
            <button class="tab" onclick="chuyenTab('vuotLink')">🔗 Vượt Link</button>
        </div>

        <!-- ==================== TAB 1: NHẬN ACC ==================== -->
        <div class="tab-content active" id="tabNhanAcc">
            <!-- Nhận Acc Thường -->
            <div class="section">
                <div class="section-title">
                    <span>🔑</span> Nhận Acc Thường <span class="badge badge-free">FREE</span>
                </div>
                <div class="input-group">
                    <input type="text" id="keyThuong" placeholder="Nhập key thường... VD: LQ-FREE-1234">
                </div>
                <button class="btn btn-normal" onclick="nhanAccThuong()">🎁 Nhận Acc Thường</button>
                <div class="status" id="statusThuong"></div>
            </div>

            <!-- Nhận Acc VIP -->
            <div class="section">
                <div class="section-title">
                    <span>👑</span> Nhận Acc VIP <span class="badge badge-vip">VIP</span>
                </div>
                <div class="input-group">
                    <input type="text" id="keyVip" placeholder="Nhập key VIP... VD: LQ-VIP-8888">
                </div>
                <button class="btn btn-vip" onclick="nhanAccVip()">💎 Nhận Acc VIP</button>
                <div class="status" id="statusVip"></div>
            </div>

            <!-- Kết quả -->
            <div class="result-box" id="resultBox">
                <div class="section-title"><span>✅</span> Thông Tin Acc Nhận Được</div>
                <div class="acc-info" id="accInfo"></div>
                <button class="btn btn-small" onclick="copyAcc()" style="margin-top:10px;">📋 Sao chép</button>
            </div>
        </div>

        <!-- ==================== TAB 2: THÊM ACC RIÊNG ==================== -->
        <div class="tab-content" id="tabThemAcc">
            <div class="section">
                <div class="section-title"><span>➕</span> Thêm Acc Của Bạn Vào Hệ Thống</div>
                <div class="input-group">
                    <input type="text" id="themKey" placeholder="Key (VD: MY-KEY-001)">
                </div>
                <div class="input-group">
                    <input type="text" id="themTaiKhoan" placeholder="Tài khoản LQ">
                </div>
                <div class="input-group">
                    <input type="text" id="themMatKhau" placeholder="Mật khẩu">
                </div>
                <div class="input-group">
                    <input type="text" id="themTuong" placeholder="Số tướng (VD: 50)">
                    <input type="text" id="themSkin" placeholder="Số skin (VD: 20)">
                </div>
                <div class="input-group">
                    <input type="text" id="themRank" placeholder="Rank (VD: Kim Cương)">
                </div>
                <div class="input-group" style="align-items:center;">
                    <label style="color:#ccc; font-size:0.9em; display:flex; align-items:center; gap:5px;">
                        <input type="checkbox" id="themVip" style="width:18px; height:18px;"> Acc VIP
                    </label>
                </div>
                <button class="btn btn-green" onclick="themAccRieng()">✅ Thêm Acc Vào Kho</button>
                <div class="status" id="statusThem"></div>
            </div>

            <!-- Danh sách acc đã thêm -->
            <div class="section">
                <div class="section-title"><span>📦</span> Kho Acc Của Bạn <span class="badge badge-mine">RIÊNG</span></div>
                <div id="danhSachAccRieng">
                    <p style="color:#555; text-align:center;">Chưa có acc nào được thêm</p>
                </div>
                <button class="btn btn-red btn-small" onclick="xoaTatCaAccRieng()" style="margin-top:10px;">🗑 Xóa Tất Cả Acc Riêng</button>
            </div>
        </div>

        <!-- ==================== TAB 3: VƯỢT LINK ==================== -->
        <div class="tab-content" id="tabVuotLink">
            <div class="section">
                <div class="section-title"><span>🔗</span> Vượt Link - Mở Trang Web Bị Chặn</div>
                <div class="input-group">
                    <input type="url" id="urlVuotLink" placeholder="Nhập URL cần vượt... (VD: https://example.com)">
                </div>
                <button class="btn btn-gold" onclick="vuotLink()">🚀 Mở Link</button>
                <div class="status" id="statusVuotLink"></div>

                <!-- Proxy iframe -->
                <div style="margin-top:15px;">
                    <p style="font-size:0.8em; color:#888; margin-bottom:8px;">
                        ⚡ Dùng proxy: 
                        <select id="proxySelect" style="background:#333; color:#fff; padding:5px; border-radius:5px;">
                            <option value="https://api.allorigins.win/raw?url=">AllOrigins</option>
                            <option value="https://corsproxy.io/?">CORS Proxy</option>
                            <option value="https://api.codetabs.com/v1/proxy?quest=">CodeTabs</option>
                            <option value="https://thingproxy.freeboard.io/fetch/">ThingProxy</option>
                        </select>
                    </p>
                    <iframe id="iframeVuotLink" src="" style="display:none;"></iframe>
                </div>
            </div>
        </div>

        <div class="divider"></div>
        <p style="text-align:center; font-size:0.7em; color:#555;">
            ⚠️ Acc demo - Web lưu dữ liệu trên máy bạn (localStorage)
        </p>
    </div>

    <script>
        // ==================== DATABASE GỐC ====================
        const DEFAULT_DB = {
            "LQ-FREE-1234": {
                taiKhoan: "lqfree_user01",
                matKhau: "Pass@Free001",
                tuong: 45,
                skin: 12,
                rank: "Kim Cương V",
                vip: false
            },
            "LQ-FREE-5678": {
                taiKhoan: "lqfree_user02",
                matKhau: "Pass@Free002",
                tuong: 52,
                skin: 18,
                rank: "Tinh Anh III",
                vip: false
            },
            "LQ-FREE-9999": {
                taiKhoan: "lqfree_pro99",
                matKhau: "Pro@Free999",
                tuong: 60,
                skin: 25,
                rank: "Cao Thủ 15 Sao",
                vip: false
            },
            "LQ-VIP-1111": {
                taiKhoan: "lqvip_legend01",
                matKhau: "Vip@Legend1",
                tuong: 95,
                skin: 78,
                rank: "Thách Đấu 50 Sao",
                vip: true
            },
            "LQ-VIP-2222": {
                taiKhoan: "lqvip_master02",
                matKhau: "Vip@Master2",
                tuong: 90,
                skin: 65,
                rank: "Thách Đấu 30 Sao",
                vip: true
            },
            "LQ-VIP-8888": {
                taiKhoan: "lqvip_god888",
                matKhau: "God@Vip888",
                tuong: 112,
                skin: 120,
                rank: "Top 1 Server",
                vip: true,
                dacBiet: "Tất cả skin giới hạn"
            }
        };

        // ==================== LOAD/SAVE ====================
        function layDatabase() {
            let db = localStorage.getItem("lq_acc_database");
            if (!db) {
                localStorage.setItem("lq_acc_database", JSON.stringify(DEFAULT_DB));
                return JSON.parse(JSON.stringify(DEFAULT_DB));
            }
            return JSON.parse(db);
        }

        function luuDatabase(db) {
            localStorage.setItem("lq_acc_database", JSON.stringify(db));
        }

        function layAccRieng() {
            let acc = localStorage.getItem("lq_acc_rieng");
            return acc ? JSON.parse(acc) : {};
        }

        function luuAccRieng(acc) {
            localStorage.setItem("lq_acc_rieng", JSON.stringify(acc));
        }

        // ==================== TAB CONTROL ====================
        function chuyenTab(tabName) {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));

            if (tabName === 'nhanAcc') {
                document.querySelectorAll('.tab')[0].classList.add('active');
                document.getElementById('tabNhanAcc').classList.add('active');
            } else if (tabName === 'themAcc') {
                document.querySelectorAll('.tab')[1].classList.add('active');
                document.getElementById('tabThemAcc').classList.add('active');
                hienThiDanhSachAccRieng();
            } else if (tabName === 'vuotLink') {
                document.querySelectorAll('.tab')[2].classList.add('active');
                document.getElementById('tabVuotLink').classList.add('active');
            }
        }

        // ==================== NHẬN ACC THƯỜNG (KHÔNG CẦN MÃ) ====================
        function nhanAccThuong() {
            const key = document.getElementById("keyThuong").value.trim().toUpperCase();
            const statusEl = document.getElementById("statusThuong");
            const resultBox = document.getElementById("resultBox");
            const accInfo = document.getElementById("accInfo");

            if (!key) {
                statusEl.textContent = "⚠️ Vui lòng nhập key thường!";
                statusEl.style.color = "#ff6600";
                return;
            }

            const db = layDatabase();
            const acc = db[key];

            if (!acc) {
                statusEl.textContent = "❌ Key không tồn tại! Thử: LQ-FREE-1234";
                statusEl.style.color = "#ff3333";
                return;
            }
            if (acc.vip) {
                statusEl.textContent = "⚠️ Key này là VIP, vui lòng dùng mục Key VIP!";
                statusEl.style.color = "#ffaa00";
                return;
            }

            hienThiKetQua(acc, false);
            statusEl.textContent = "✅ Nhận acc thành công!";
            statusEl.style.color = "#00ff88";
        }

        // ==================== NHẬN ACC VIP (KHÔNG CẦN MÃ) ====================
        function nhanAccVip() {
            const key = document.getElementById("keyVip").value.trim().toUpperCase();
            const statusEl = document.getElementById("statusVip");
            const resultBox = document.getElementById("resultBox");
            const accInfo = document.getElementById("accInfo");

            if (!key) {
                statusEl.textContent = "⚠️ Vui lòng nhập key VIP!";
                statusEl.style.color = "#ff6600";
                return;
            }

            const db = layDatabase();
            const acc = db[key];

            if (!acc) {
                statusEl.textContent = "❌ Key VIP không tồn tại! Thử: LQ-VIP-8888";
                statusEl.style.color = "#ff3333";
                return;
            }
            if (!acc.vip) {
                statusEl.textContent = "⚠️ Key này là thường, vui lòng dùng mục Key Thường!";
                statusEl.style.color = "#ffaa00";
                return;
            }

            hienThiKetQua(acc, true);
            statusEl.textContent = "✅ Nhận acc VIP thành công!";
            statusEl.style.color = "#ffcc00";
        }

        function hienThiKetQua(acc, isVip) {
            const resultBox = document.getElementById("resultBox");
            const accInfo = document.getElementById("accInfo");
            let vipHTML = isVip ? '👑 <span style="color:#ffcc00;">[VIP]</span> ' : '';
            let dacBietHTML = acc.dacBiet ? `🌟 <span>Đặc biệt:</span> ${acc.dacBiet}<br>` : '';

            accInfo.innerHTML = `
                ${vipHTML}🎮 <span>Tài khoản:</span> ${acc.taiKhoan}<br>
                🔒 <span>Mật khẩu:</span> ${acc.matKhau}<br>
                👥 <span>Số tướng:</span> ${acc.tuong}<br>
                💄 <span>Số skin:</span> ${acc.skin}<br>
                🏆 <span>Rank:</span> ${acc.rank}<br>
                ${dacBietHTML}
            `;
            resultBox.classList.add("show");
        }

        function copyAcc() {
            const text = document.getElementById("accInfo").innerText;
            navigator.clipboard.writeText(text).then(() => {
                alert("✅ Đã sao chép thông tin acc!");
            }).catch(() => {
                alert("⚠️ Vui lòng bôi đen và copy thủ công");
            });
        }

        // ==================== THÊM ACC RIÊNG ====================
        function themAccRieng() {
            const key = document.getElementById("themKey").value.trim().toUpperCase();
            const taiKhoan = document.getElementById("themTaiKhoan").value.trim();
            const matKhau = document.getElementById("themMatKhau").value.trim();
            const tuong = document.getElementById("themTuong").value.trim();
            const skin = document.getElementById("themSkin").value.trim();
            const rank = document.getElementById("themRank").value.trim();
            const isVip = document.getElementById("themVip").checked;
            const statusEl = document.getElementById("statusThem");

            if (!key || !taiKhoan || !matKhau) {
                statusEl.textContent = "⚠️ Key, Tài khoản, Mật khẩu là bắt buộc!";
                statusEl.style.color = "#ff6600";
                return;
            }

            // Thêm vào database chính
            const db = layDatabase();
            db[key] = {
                taiKhoan: taiKhoan,
                matKhau: matKhau,
                tuong: parseInt(tuong) || 0,
                skin: parseInt(skin) || 0,
                rank: rank || "Chưa xếp hạng",
                vip: isVip
            };
            luuDatabase(db);

            // Thêm vào danh sách riêng
            const accRieng = layAccRieng();
            accRieng[key] = db[key];
            luuAccRieng(accRieng);

            // Reset form
            document.getElementById("themKey").value = "";
            document.getElementById("themTaiKhoan").value = "";
            document.getElementById("themMatKhau").value = "";
            document.getElementById("themTuong").value = "";
            document.getElementById("themSkin").value = "";
            document.getElementById("themRank").value = "";
            document.getElementById("themVip").checked = false;

            statusEl.textContent = `✅ Đã thêm acc "${taiKhoan}" với key "${key}"`;
            statusEl.style.color = "#00ff88";
            hienThiDanhSachAccRieng();
        }

        function hienThiDanhSachAccRieng() {
            const container = document.getElementById("danhSachAccRieng");
            const accRieng = layAccRieng();
            const keys = Object.keys(accRieng);

            if (keys.length === 0) {
                container.innerHTML = '<p style="color:#555; text-align:center;">Chưa có acc nào được thêm</p>';
                return;
            }

            let html = "";
            keys.forEach(key => {
                const acc = accRieng[key];
                html += `
                    <div class="list-item">
                        <div class="acc-detail">
                            ${acc.vip ? '👑 ' : '🎮 '}
                            <strong>${acc.taiKhoan}</strong>
                            <span class="badge ${acc.vip ? 'badge-vip' : 'badge-free'}">${acc.vip ? 'VIP' : 'FREE'}</span>
                            <br><small style="color:#888;">Key: ${key} | Rank: ${acc.rank} | Tướng: ${acc.tuong} | Skin: ${acc.skin}</small>
                        </div>
                        <button class="btn btn-red btn-small" onclick="xoaAccRieng('${key}')">🗑 Xóa</button>
                    </div>
                `;
            });
            container.innerHTML = html;
        }

        function xoaAccRieng(key) {
            if (!confirm(`Xóa acc với key "${key}"?`)) return;

            // Xóa khỏi database chính
            const db = layDatabase();
            delete db[key];
            luuDatabase(db);

            // Xóa khỏi danh sách riêng
            const accRieng = layAccRieng();
            delete accRieng[key];
            luuAccRieng(accRieng);

            hienThiDanhSachAccRieng();
            document.getElementById("statusThem").textContent = `🗑 Đã xóa acc key: ${key}`;
            document.getElementById("statusThem").style.color = "#ff6666";
        }

        function xoaTatCaAccRieng() {
            if (!confirm("⚠️ Xóa TẤT CẢ acc riêng? Hành động này không thể hoàn tác!")) return;

            const accRieng = layAccRieng();
            const db = layDatabase();
            Object.keys(accRieng).forEach(key => delete db[key]);
            luuDatabase(db);
            luuAccRieng({});
            hienThiDanhSachAccRieng();
            document.getElementById("statusThem").textContent = "🗑 Đã xóa tất cả acc riêng!";
            document.getElementById("statusThem").style.color = "#ff6666";
        }

        // ==================== VƯỢT LINK ====================
        function vuotLink() {
            const url = document.getElementById("urlVuotLink").value.trim();
            const proxy = document.getElementById("proxySelect").value;
            const iframe = document.getElementById("iframeVuotLink");
            const statusEl = document.getElementById("statusVuotLink");

            if (!url) {
                statusEl.textContent = "⚠️ Vui lòng nhập URL!";
                statusEl.style.color = "#ff6600";
                return;
            }

            // Thêm https:// nếu thiếu
            let fullUrl = url;
            if (!url.startsWith("http://") && !url.startsWith("https://")) {
                fullUrl = "https://" + url;
            }

            const proxyUrl = proxy + encodeURIComponent(fullUrl);
            iframe.src = proxyUrl;
            iframe.style.display = "block";
            statusEl.textContent = "✅ Đang tải qua proxy: " + proxy.split("?")[0].split("/")[2];
            statusEl.style.color = "#00ff88";

            // Mở thêm tab mới nếu muốn
            // window.open(proxyUrl, "_blank");
        }

        // ==================== KHỞI TẠO ====================
        console.log("✅ Web LQ Full - Đã sẵn sàng");
        console.log("🎁 Tab Nhận Acc: Không cần mã, chỉ cần key");
        console.log("➕ Tab Thêm Acc: Thêm acc riêng của bạn");
        console.log("🔗 Tab Vượt Link: Mở link qua proxy");
        console.log("💾 Tất cả dữ liệu lưu trong localStorage");
    </script>
</body>
</html>
