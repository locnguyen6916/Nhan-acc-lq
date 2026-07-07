<!-- ========================================================
  Web Nhận Acc Liên Quân Free - iOS (Bản Hoàn Chỉnh)
  CRE: Theo yêu cầu
  - Xóa chữ "VD" trong placeholder key free và vip
  - Vượt link xong hiện acc ngay bên dưới
  - Thêm key VIP riêng cho bạn
  - Xóa dòng "Acc demo"
  - Thêm Credit tên bạn
  ======================================================== -->

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nhận Acc Liên Quân Free - iOS</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

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

        .credit {
            text-align: center;
            font-size: 0.75em;
            color: #666;
            margin-top: 2px;
            font-style: italic;
        }

        .tabs {
            display: flex;
            gap: 5px;
            margin-bottom: 15px;
            background: rgba(0,0,0,0.3);
            border-radius: 12px;
            padding: 4px;
            flex-wrap: wrap;
        }

        .tab {
            flex: 1;
            min-width: 60px;
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

        .input-group input, .input-group textarea, .input-group select {
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

        .input-group textarea { min-height: 80px; resize: vertical; }
        .input-group input:focus, .input-group textarea:focus, .input-group select:focus {
            border-color: #00aaff;
            box-shadow: 0 0 15px rgba(0, 170, 255, 0.3);
        }
        .input-group input::placeholder, .input-group textarea::placeholder { color: #555; }

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

        .btn-normal { background: linear-gradient(135deg, #00aaff, #0066cc); color: #fff; box-shadow: 0 4px 15px rgba(0, 150, 255, 0.4); }
        .btn-vip { background: linear-gradient(135deg, #ff0066, #cc0044); color: #fff; box-shadow: 0 4px 15px rgba(255, 0, 100, 0.4); }
        .btn-gold { background: linear-gradient(135deg, #ffaa00, #ff6600); color: #000; box-shadow: 0 4px 15px rgba(255, 150, 0, 0.4); }
        .btn-green { background: linear-gradient(135deg, #00cc66, #009944); color: #fff; box-shadow: 0 4px 15px rgba(0, 200, 100, 0.4); }
        .btn-red { background: linear-gradient(135deg, #ff3333, #cc0000); color: #fff; box-shadow: 0 4px 15px rgba(255, 50, 50, 0.4); }
        .btn-purple { background: linear-gradient(135deg, #9933ff, #6600cc); color: #fff; box-shadow: 0 4px 15px rgba(150, 50, 255, 0.4); }
        .btn:hover { transform: translateY(-2px); filter: brightness(1.2); }
        .btn-small { padding: 8px 12px; font-size: 0.75em; width: auto; }

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
        .badge-admin { background: #ffaa00; color: #000; }

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
            .tab { font-size: 0.7em; padding: 8px 4px; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1>⚔️ Nhận Acc LQ Free</h1>
            <p class="subtitle">Phiên bản iOS • Cập nhật mới nhất</p>
            <p class="credit">Created by Hoàng</p>
        </div>

        <!-- Tabs -->
        <div class="tabs">
            <button class="tab active" onclick="chuyenTab('nhanAcc')">🎁 Nhận Acc</button>
            <button class="tab" onclick="chuyenTab('themAcc')">➕ Thêm Acc</button>
            <button class="tab" onclick="chuyenTab('vuotLink')">🔗 Vượt Link</button>
            <button class="tab" onclick="chuyenTab('admin')">🔐 Admin</button>
        </div>

        <!-- ==================== TAB 1: NHẬN ACC ==================== -->
        <div class="tab-content active" id="tabNhanAcc">
            <div class="section">
                <div class="section-title"><span>🔑</span> Nhận Acc Thường <span class="badge badge-free">FREE</span></div>
                <div class="input-group">
                    <input type="text" id="keyThuong" placeholder="Nhập key thường...">
                </div>
                <button class="btn btn-normal" onclick="nhanAccThuong()">🎁 Nhận Acc Thường</button>
                <div class="status" id="statusThuong"></div>
            </div>

            <div class="section">
                <div class="section-title"><span>👑</span> Nhận Acc VIP <span class="badge badge-vip">VIP</span></div>
                <div class="input-group">
                    <input type="text" id="keyVip" placeholder="Nhập key VIP...">
                </div>
                <button class="btn btn-vip" onclick="nhanAccVip()">💎 Nhận Acc VIP</button>
                <div class="status" id="statusVip"></div>
            </div>

            <div class="result-box" id="resultBox">
                <div class="section-title"><span>✅</span> Thông Tin Acc Nhận Được</div>
                <div class="acc-info" id="accInfo"></div>
                <button class="btn btn-small" onclick="copyAcc()" style="margin-top:10px;">📋 Sao chép</button>
            </div>
        </div>

        <!-- ==================== TAB 2: THÊM ACC ==================== -->
        <div class="tab-content" id="tabThemAcc">
            <div class="section">
                <div class="section-title"><span>➕</span> Thêm Acc Của Bạn</div>
                <div class="input-group">
                    <input type="text" id="themKey" placeholder="Key...">
                </div>
                <div class="input-group">
                    <input type="text" id="themTaiKhoan" placeholder="Tài khoản LQ">
                    <input type="text" id="themMatKhau" placeholder="Mật khẩu">
                </div>
                <div class="input-group">
                    <input type="text" id="themTuong" placeholder="Số tướng">
                    <input type="text" id="themSkin" placeholder="Số skin">
                </div>
                <div class="input-group">
                    <input type="text" id="themRank" placeholder="Rank">
                </div>
                <div class="input-group" style="align-items:center;">
                    <label style="color:#ccc; font-size:0.9em; display:flex; align-items:center; gap:5px;">
                        <input type="checkbox" id="themVip" style="width:18px; height:18px;"> Acc VIP
                    </label>
                </div>
                <button class="btn btn-green" onclick="themAccRieng()">✅ Thêm Acc Vào Kho</button>
                <div class="status" id="statusThem"></div>
            </div>

            <div class="section">
                <div class="section-title"><span>📦</span> Kho Acc Của Bạn</div>
                <div id="danhSachAccRieng">
                    <p style="color:#555; text-align:center;">Chưa có acc nào được thêm</p>
                </div>
                <button class="btn btn-red btn-small" onclick="xoaTatCaAccRieng()" style="margin-top:10px;">🗑 Xóa Tất Cả Acc Riêng</button>
            </div>
        </div>

        <!-- ==================== TAB 3: VƯỢT LINK ==================== -->
        <div class="tab-content" id="tabVuotLink">
            <div class="section">
                <div class="section-title"><span>🔗</span> Vượt Link - Nhận Acc Ngay</div>
                <p style="font-size:0.8em; color:#888; margin-bottom:10px;">
                    Nhập link cần vượt, bấm Mở Link, acc sẽ hiện bên dưới
                </p>
                <div class="input-group">
                    <input type="url" id="urlVuotLink" placeholder="Nhập URL cần vượt...">
                </div>
                <div class="input-group">
                    <select id="proxySelect" style="flex:1; padding:12px; background:#333; color:#fff; border-radius:10px; border:1px solid rgba(255,255,255,0.1);">
                        <option value="https://api.allorigins.win/raw?url=">AllOrigins Proxy</option>
                        <option value="https://corsproxy.io/?">CORS Proxy</option>
                        <option value="https://api.codetabs.com/v1/proxy?quest=">CodeTabs Proxy</option>
                        <option value="https://thingproxy.freeboard.io/fetch/">ThingProxy</option>
                    </select>
                </div>
                <button class="btn btn-gold" onclick="vuotLink()">🚀 Mở Link</button>
                <div class="status" id="statusVuotLink"></div>
                <iframe id="iframeVuotLink" src="" style="display:none; margin-top:10px;"></iframe>
            </div>

            <!-- Acc hiện sau khi vượt link -->
            <div class="result-box" id="resultBoxVuotLink">
                <div class="section-title"><span>🎮</span> Acc Nhận Được Sau Khi Vượt Link</div>
                <div class="acc-info" id="accInfoVuotLink">
                    <p style="color:#888;">Đang chờ vượt link...</p>
                </div>
                <button class="btn btn-small" onclick="copyAccVuotLink()" style="margin-top:10px;">📋 Sao chép</button>
            </div>
        </div>

        <!-- ==================== TAB 4: ADMIN ==================== -->
        <div class="tab-content" id="tabAdmin">
            <div class="section" id="adminLoginSection">
                <div class="section-title"><span>🔐</span> Đăng Nhập Admin <span class="badge badge-admin">ADMIN</span></div>
                <div class="input-group">
                    <input type="password" id="adminKey" placeholder="Nhập key Admin...">
                </div>
                <button class="btn btn-purple" onclick="dangNhapAdmin()">🔓 Đăng Nhập</button>
                <div class="status" id="statusAdminLogin"></div>
            </div>

            <div id="adminPanel" style="display:none;">
                <div class="section">
                    <div class="section-title"><span>⚙️</span> Quản Lý Link Vượt</div>
                    <div class="input-group">
                        <input type="text" id="adminLinkName" placeholder="Tên link...">
                    </div>
                    <div class="input-group">
                        <input type="url" id="adminLinkUrl" placeholder="URL đầy đủ...">
                    </div>
                    <button class="btn btn-gold" onclick="themLinkVaoHeThong()">🔗 Thêm Link</button>
                    <div class="status" id="statusAdminLink"></div>
                </div>

                <div class="section">
                    <div class="section-title"><span>🎮</span> Thêm Acc Sau Khi Vượt Link</div>
                    <div class="input-group">
                        <input type="text" id="adminAccKey" placeholder="Key acc...">
                    </div>
                    <div class="input-group">
                        <input type="text" id="adminAccTaiKhoan" placeholder="Tài khoản">
                        <input type="text" id="adminAccMatKhau" placeholder="Mật khẩu">
                    </div>
                    <div class="input-group">
                        <input type="text" id="adminAccTuong" placeholder="Số tướng">
                        <input type="text" id="adminAccSkin" placeholder="Số skin">
                    </div>
                    <div class="input-group">
                        <input type="text" id="adminAccRank" placeholder="Rank">
                    </div>
                    <div class="input-group" style="align-items:center;">
                        <label style="color:#ccc; font-size:0.9em; display:flex; align-items:center; gap:5px;">
                            <input type="checkbox" id="adminAccVip" style="width:18px; height:18px;"> Acc VIP
                        </label>
                    </div>
                    <button class="btn btn-green" onclick="themAccSauKhiVuot()">✅ Thêm Acc Vào Database</button>
                    <div class="status" id="statusAdminAcc"></div>
                </div>

                <div class="section">
                    <div class="section-title"><span>📋</span> Danh Sách Link Đã Thêm</div>
                    <div id="danhSachLinkAdmin">
                        <p style="color:#555; text-align:center;">Chưa có link nào</p>
                    </div>
                </div>

                <button class="btn btn-red" onclick="dangXuatAdmin()" style="margin-top:10px;">🚪 Đăng Xuất Admin</button>
            </div>
        </div>
    </div>

    <script>
        // ==================== DATABASE GỐC ====================
        const DEFAULT_DB = {
            "LQ-FREE-1234": { taiKhoan: "lqfree_user01", matKhau: "Pass@Free001", tuong: 45, skin: 12, rank: "Kim Cương V", vip: false },
            "LQ-FREE-5678": { taiKhoan: "lqfree_user02", matKhau: "Pass@Free002", tuong: 52, skin: 18, rank: "Tinh Anh III", vip: false },
            "LQ-FREE-9999": { taiKhoan: "lqfree_pro99", matKhau: "Pro@Free999", tuong: 60, skin: 25, rank: "Cao Thủ 15 Sao", vip: false },
            "LQ-VIP-1111": { taiKhoan: "lqvip_legend01", matKhau: "Vip@Legend1", tuong: 95, skin: 78, rank: "Thách Đấu 50 Sao", vip: true },
            "LQ-VIP-2222": { taiKhoan: "lqvip_master02", matKhau: "Vip@Master2", tuong: 90, skin: 65, rank: "Thách Đấu 30 Sao", vip: true },
            "LQ-VIP-8888": { taiKhoan: "lqvip_god888", matKhau: "God@Vip888", tuong: 112, skin: 120, rank: "Top 1 Server", vip: true, dacBiet: "Tất cả skin giới hạn" },
            // KEY VIP RIÊNG CHO BẠN
            "HOANG-VIP-9999": { taiKhoan: "hoang_pro_max", matKhau: "Hoang@Pro9999", tuong: 115, skin: 130, rank: "Thách Đấu Top 10", vip: true, dacBiet: "Key VIP riêng của Hoàng - Full tướng Full skin" }
        };

        const ADMIN_KEY = "adminlq2026@@";

        // Danh sách acc ảo hiện ra sau khi vượt link
        const VUOT_LINK_ACC = [
            { taiKhoan: "lq_vuotlink_01", matKhau: "Vuot@Link001", tuong: 35, skin: 10, rank: "Vàng I", vip: false },
            { taiKhoan: "lq_vuotlink_02", matKhau: "Vuot@Link002", tuong: 42, skin: 15, rank: "Bạch Kim III", vip: false },
            { taiKhoan: "lq_vuotlink_vip", matKhau: "Vuot@Vip999", tuong: 88, skin: 60, rank: "Thách Đấu", vip: true, dacBiet: "Acc từ vượt link VIP" }
        ];

        // ==================== LOAD/SAVE ====================
        function layDatabase() {
            let db = localStorage.getItem("lq_acc_db_v3");
            if (!db) { localStorage.setItem("lq_acc_db_v3", JSON.stringify(DEFAULT_DB)); return JSON.parse(JSON.stringify(DEFAULT_DB)); }
            return JSON.parse(db);
        }
        function luuDatabase(db) { localStorage.setItem("lq_acc_db_v3", JSON.stringify(db)); }
        function layAccRieng() { let acc = localStorage.getItem("lq_acc_rieng_v3"); return acc ? JSON.parse(acc) : {}; }
        function luuAccRieng(acc) { localStorage.setItem("lq_acc_rieng_v3", JSON.stringify(acc)); }
        function layLinkAdmin() { let links = localStorage.getItem("lq_admin_links_v3"); return links ? JSON.parse(links) : []; }
        function luuLinkAdmin(links) { localStorage.setItem("lq_admin_links_v3", JSON.stringify(links)); }

        // ==================== TAB CONTROL ====================
        function chuyenTab(tabName) {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
            const tabMap = { 'nhanAcc': 0, 'themAcc': 1, 'vuotLink': 2, 'admin': 3 };
            const contentMap = { 'nhanAcc': 'tabNhanAcc', 'themAcc': 'tabThemAcc', 'vuotLink': 'tabVuotLink', 'admin': 'tabAdmin' };
            document.querySelectorAll('.tab')[tabMap[tabName]].classList.add('active');
            document.getElementById(contentMap[tabName]).classList.add('active');
            if (tabName === 'themAcc') hienThiDanhSachAccRieng();
            if (tabName === 'admin') { kiemTraAdminDangNhap(); hienThiDanhSachLinkAdmin(); }
            if (tabName === 'vuotLink') { document.getElementById("resultBoxVuotLink").classList.add("show"); }
        }

        // ==================== NHẬN ACC ====================
        function nhanAccThuong() {
            const key = document.getElementById("keyThuong").value.trim().toUpperCase();
            const statusEl = document.getElementById("statusThuong");
            if (!key) { statusEl.textContent = "⚠️ Vui lòng nhập key!"; statusEl.style.color = "#ff6600"; return; }
            const db = layDatabase();
            const acc = db[key];
            if (!acc) { statusEl.textContent = "❌ Key không tồn tại!"; statusEl.style.color = "#ff3333"; return; }
            if (acc.vip) { statusEl.textContent = "⚠️ Key này là VIP, dùng mục Key VIP!"; statusEl.style.color = "#ffaa00"; return; }
            hienThiKetQua(acc, false);
            statusEl.textContent = "✅ Nhận acc thành công!"; statusEl.style.color = "#00ff88";
        }

        function nhanAccVip() {
            const key = document.getElementById("keyVip").value.trim().toUpperCase();
            const statusEl = document.getElementById("statusVip");
            if (!key) { statusEl.textContent = "⚠️ Vui lòng nhập key VIP!"; statusEl.style.color = "#ff6600"; return; }
            const db = layDatabase();
            const acc = db[key];
            if (!acc) { statusEl.textContent = "❌ Key VIP không tồn tại!"; statusEl.style.color = "#ff3333"; return; }
            if (!acc.vip) { statusEl.textContent = "⚠️ Key này là thường, dùng mục Key Thường!"; statusEl.style.color = "#ffaa00"; return; }
            hienThiKetQua(acc, true);
            statusEl.textContent = "✅ Nhận acc VIP thành công!"; statusEl.style.color = "#ffcc00";
        }

        function hienThiKetQua(acc, isVip) {
            const resultBox = document.getElementById("resultBox");
            const accInfo = document.getElementById("accInfo");
            let vipHTML = isVip ? '👑 <span style="color:#ffcc00;">[VIP]</span> ' : '';
            let dacBietHTML = acc.dacBiet ? `🌟 <span>Đặc biệt:</span> ${acc.dacBiet}<br>` : '';
            accInfo.innerHTML = `${vipHTML}🎮 <span>Tài khoản:</span> ${acc.taiKhoan}<br>🔒 <span>Mật khẩu:</span> ${acc.matKhau}<br>👥 <span>Số tướng:</span> ${acc.tuong}<br>💄 <span>Số skin:</span> ${acc.skin}<br>🏆 <span>Rank:</span> ${acc.rank}<br>${dacBietHTML}`;
            resultBox.classList.add("show");
        }

        function copyAcc() {
            const text = document.getElementById("accInfo").innerText;
            navigator.clipboard.writeText(text).then(() => alert("✅ Đã sao chép!")).catch(() => alert("⚠️ Bôi đen và copy thủ công"));
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
            if (!key || !taiKhoan || !matKhau) { statusEl.textContent = "⚠️ Key, Tài khoản, Mật khẩu là bắt buộc!"; statusEl.style.color = "#ff6600"; return; }
            const db = layDatabase();
            db[key] = { taiKhoan, matKhau, tuong: parseInt(tuong) || 0, skin: parseInt(skin) || 0, rank: rank || "Chưa xếp hạng", vip: isVip };
            luuDatabase(db);
            const accRieng = layAccRieng(); accRieng[key] = db[key]; luuAccRieng(accRieng);
            ["themKey","themTaiKhoan","themMatKhau","themTuong","themSkin","themRank"].forEach(id => document.getElementById(id).value = "");
            document.getElementById("themVip").checked = false;
            statusEl.textContent = `✅ Đã thêm acc "${taiKhoan}" với key "${key}"`; statusEl.style.color = "#00ff88";
            hienThiDanhSachAccRieng();
        }

        function hienThiDanhSachAccRieng() {
            const container = document.getElementById("danhSachAccRieng");
            const accRieng = layAccRieng();
            const keys = Object.keys(accRieng);
            if (keys.length === 0) { container.innerHTML = '<p style="color:#555; text-align:center;">Chưa có acc nào được thêm</p>'; return; }
            let html = "";
            keys.forEach(key => {
                const acc = accRieng[key];
                html += `<div class="list-item"><div class="acc-detail">${acc.vip ? '👑 ' : '🎮 '}<strong>${acc.taiKhoan}</strong><span class="badge ${acc.vip ? 'badge-vip' : 'badge-free'}">${acc.vip ? 'VIP' : 'FREE'}</span><br><small style="color:#888;">Key: ${key} | Rank: ${acc.rank} | Tướng: ${acc.tuong} | Skin: ${acc.skin}</small></div><button class="btn btn-red btn-small" onclick="xoaAccRieng('${key}')">🗑 Xóa</button></div>`;
            });
            container.innerHTML = html;
        }

        function xoaAccRieng(key) {
            if (!confirm(`Xóa acc với key "${key}"?`)) return;
            const db = layDatabase(); delete db[key]; luuDatabase(db);
            const accRieng = layAccRieng(); delete accRieng[key]; luuAccRieng(accRieng);
            hienThiDanhSachAccRieng();
            document.getElementById("statusThem").textContent = `🗑 Đã xóa acc key: ${key}`; document.getElementById("statusThem").style.color = "#ff6666";
        }

        function xoaTatCaAccRieng() {
            if (!confirm("⚠️ Xóa TẤT CẢ acc riêng?")) return;
            const accRieng = layAccRieng(); const db = layDatabase();
            Object.keys(accRieng).forEach(key => delete db[key]);
            luuDatabase(db); luuAccRieng({}); hienThiDanhSachAccRieng();
            document.getElementById("statusThem").textContent = "🗑 Đã xóa tất cả acc riêng!"; document.getElementById("statusThem").style.color = "#ff6666";
        }

        // ==================== VƯỢT LINK + HIỆN ACC ====================
        function vuotLink() {
            const url = document.getElementById("urlVuotLink").value.trim();
            const proxy = document.getElementById("proxySelect").value;
            const iframe = document.getElementById("iframeVuotLink");
            const statusEl = document.getElementById("statusVuotLink");

            if (!url) { statusEl.textContent = "⚠️ Vui lòng nhập URL!"; statusEl.style.color = "#ff6600"; return; }

            let fullUrl = url;
            if (!url.startsWith("http://") && !url.startsWith("https://")) fullUrl = "https://" + url;

            const proxyUrl = proxy + encodeURIComponent(fullUrl);
            iframe.src = proxyUrl;
            iframe.style.display = "block";
            statusEl.textContent = "✅ Đã vượt link! Acc hiện bên dưới...";
            statusEl.style.color = "#00ff88";

            // Tự động hiện acc ngẫu nhiên sau khi vượt link
            setTimeout(() => {
                const accNgauNhien = VUOT_LINK_ACC[Math.floor(Math.random() * VUOT_LINK_ACC.length)];
                hienThiKetQuaVuotLink(accNgauNhien);
            }, 1500);
        }

        function hienThiKetQuaVuotLink(acc) {
            const resultBox = document.getElementById("resultBoxVuotLink");
            const accInfo = document.getElementById("accInfoVuotLink");
            let vipHTML = acc.vip ? '👑 <span style="color:#ffcc00;">[VIP]</span> ' : '';
            let dacBietHTML = acc.dacBiet ? `🌟 <span>Đặc biệt:</span> ${acc.dacBiet}<br>` : '';
            accInfo.innerHTML = `${vipHTML}🎮 <span>Tài khoản:</span> ${acc.taiKhoan}<br>🔒 <span>Mật khẩu:</span> ${acc.matKhau}<br>👥 <span>Số tướng:</span> ${acc.tuong}<br>💄 <span>Số skin:</span> ${acc.skin}<br>🏆 <span>Rank:</span> ${acc.rank}<br>${dacBietHTML}`;
            resultBox.classList.add("show");
        }

        function copyAccVuotLink() {
            const text = document.getElementById("accInfoVuotLink").innerText;
            navigator.clipboard.writeText(text).then(() => alert("✅ Đã sao chép!")).catch(() => alert("⚠️ Bôi đen và copy thủ công"));
        }

        // ==================== ADMIN ====================
        function dangNhapAdmin() {
            const key = document.getElementById("adminKey").value.trim();
            const statusEl = document.getElementById("statusAdminLogin");
            if (key === ADMIN_KEY) {
                sessionStorage.setItem("lq_admin_logged_v3", "true");
                document.getElementById("adminLoginSection").style.display = "none";
                document.getElementById("adminPanel").style.display = "block";
                statusEl.textContent = "";
                hienThiDanhSachLinkAdmin();
            } else { statusEl.textContent = "❌ Key Admin không đúng!"; statusEl.style.color = "#ff3333"; }
        }

        function kiemTraAdminDangNhap() {
            const logged = sessionStorage.getItem("lq_admin_logged_v3");
            if (logged === "true") {
                document.getElementById("adminLoginSection").style.display = "none";
                document.getElementById("adminPanel").style.display = "block";
            } else {
                document.getElementById("adminLoginSection").style.display = "block";
                document.getElementById("adminPanel").style.display = "none";
            }
        }

        function dangXuatAdmin() {
            sessionStorage.removeItem("lq_admin_logged_v3");
            document.getElementById("adminLoginSection").style.display = "block";
            document.getElementById("adminPanel").style.display = "none";
            document.getElementById("adminKey").value = "";
        }

        function themLinkVaoHeThong() {
            const name = document.getElementById("adminLinkName").value.trim();
            const url = document.getElementById("adminLinkUrl").value.trim();
            const statusEl = document.getElementById("statusAdminLink");
            if (!name || !url) { statusEl.textContent = "⚠️ Vui lòng nhập đầy đủ Tên và URL!"; statusEl.style.color = "#ff6600"; return; }
            let links = layLinkAdmin();
            links.push({ name, url, thoiGian: new Date().toLocaleString("vi-VN") });
            luuLinkAdmin(links);
            document.getElementById("adminLinkName").value = ""; document.getElementById("adminLinkUrl").value = "";
            statusEl.textContent = `✅ Đã thêm link "${name}"`; statusEl.style.color = "#00ff88";
            hienThiDanhSachLinkAdmin();
        }

        function hienThiDanhSachLinkAdmin() {
            const container = document.getElementById("danhSachLinkAdmin");
            const links = layLinkAdmin();
            if (links.length === 0) { container.innerHTML = '<p style="color:#555; text-align:center;">Chưa có link nào</p>'; return; }
            let html = "";
            links.forEach((link, index) => {
                html += `<div class="list-item"><div class="acc-detail">🔗 <strong>${link.name}</strong><br><small style="color:#888;">${link.url}</small><br><small style="color:#666;">Thêm lúc: ${link.thoiGian}</small></div><div style="display:flex; gap:5px;"><button class="btn btn-normal btn-small" onclick="window.open('${link.url}', '_blank')">🌐 Mở</button><button class="btn btn-red btn-small" onclick="xoaLinkAdmin(${index})">🗑</button></div></div>`;
            });
            container.innerHTML = html;
        }

        function xoaLinkAdmin(index) {
            if (!confirm("Xóa link này?")) return;
            let links = layLinkAdmin(); links.splice(index, 1); luuLinkAdmin(links); hienThiDanhSachLinkAdmin();
        }

        function themAccSauKhiVuot() {
            const key = document.getElementById("adminAccKey").value.trim().toUpperCase();
            const taiKhoan = document.getElementById("adminAccTaiKhoan").value.trim();
            const matKhau = document.getElementById("adminAccMatKhau").value.trim();
            const tuong = document.getElementById("adminAccTuong").value.trim();
            const skin = document.getElementById("adminAccSkin").value.trim();
            const rank = document.getElementById("adminAccRank").value.trim();
            const isVip = document.getElementById("adminAccVip").checked;
            const statusEl = document.getElementById("statusAdminAcc");
            if (!key || !taiKhoan || !matKhau) { statusEl.textContent = "⚠️ Key, Tài khoản, Mật khẩu là bắt buộc!"; statusEl.style.color = "#ff6600"; return; }
            const db = layDatabase();
            db[key] = { taiKhoan, matKhau, tuong: parseInt(tuong) || 0, skin: parseInt(skin) || 0, rank: rank || "Chưa xếp hạng", vip: isVip };
            luuDatabase(db);
            const accRieng = layAccRieng(); accRieng[key] = db[key]; luuAccRieng(accRieng);
            ["adminAccKey","adminAccTaiKhoan","adminAccMatKhau","adminAccTuong","adminAccSkin","adminAccRank"].forEach(id => document.getElementById(id).value = "");
            document.getElementById("adminAccVip").checked = false;
            statusEl.textContent = `✅ Đã thêm acc "${taiKhoan}" vào database! Key: ${key}`; statusEl.style.color = "#00ff88";
        }

        // ==================== KHỞI TẠO ====================
        kiemTraAdminDangNhap();
        document.getElementById("resultBoxVuotLink").classList.add("show");
        console.log("✅ Web LQ Hoàn Chỉnh - Created by Hoàng");
        console.log("👑 Key VIP riêng: HOANG-VIP-9999");
        console.log("🔐 Admin key: " + ADMIN_KEY);
    </script>
</body>
</html>
