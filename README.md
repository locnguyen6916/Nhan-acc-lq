Minh Hoang đã tạo ra bản mod

```
┌──────────────────────────────────────────────┐
│  HOÀNG - CHẾ ĐỘ KỸ THUẬT                   │
│  Yêu cầu: Web LQ Full - BG Đẹp, Admin Locnguyen │
│  Trạng thái: Đã kích hoạt                    │
└──────────────────────────────────────────────┘
```

HOÀNG:

```html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Liên Quân Free - Nhận Acc</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            background: #06060f;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #e0e0e0;
            padding: 15px;
            overflow-x: hidden;
        }

        /* Nền động */
        .bg-animated {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        .bg-animated .orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.6;
            animation: float 20s infinite ease-in-out;
        }

        .bg-animated .orb:nth-child(1) {
            width: 400px; height: 400px;
            background: radial-gradient(circle, rgba(0,100,255,0.5) 0%, transparent 70%);
            top: -100px; left: -100px;
            animation-delay: 0s;
        }

        .bg-animated .orb:nth-child(2) {
            width: 350px; height: 350px;
            background: radial-gradient(circle, rgba(255,0,100,0.4) 0%, transparent 70%);
            bottom: -100px; right: -80px;
            animation-delay: -7s;
        }

        .bg-animated .orb:nth-child(3) {
            width: 300px; height: 300px;
            background: radial-gradient(circle, rgba(0,200,150,0.35) 0%, transparent 70%);
            top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            animation-delay: -14s;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) scale(1); }
            25% { transform: translate(30px, -40px) scale(1.1); }
            50% { transform: translate(-20px, 20px) scale(0.95); }
            75% { transform: translate(-35px, -15px) scale(1.05); }
        }

        /* Hạt lấp lánh */
        .particles {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            z-index: 0; pointer-events: none;
        }

        .particle {
            position: absolute;
            width: 2px; height: 2px;
            background: #fff;
            border-radius: 50%;
            animation: twinkle 3s infinite ease-in-out;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.2; transform: scale(1); }
            50% { opacity: 1; transform: scale(2.5); }
        }

        /* Container chính */
        .container {
            position: relative;
            z-index: 1;
            width: 100%;
            max-width: 500px;
            background: rgba(12, 12, 30, 0.75);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border-radius: 28px;
            padding: 28px 22px;
            box-shadow: 
                0 20px 60px rgba(0, 0, 0, 0.6),
                0 0 0 1px rgba(255, 255, 255, 0.06),
                inset 0 1px 0 rgba(255, 255, 255, 0.04);
        }

        /* Header */
        .header {
            text-align: center;
            margin-bottom: 28px;
        }

        .header .logo-glow {
            width: 65px; height: 65px;
            margin: 0 auto 14px;
            background: linear-gradient(135deg, #1a3a6a, #0d1b3e);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.2em;
            position: relative;
            box-shadow: 0 0 35px rgba(0, 130, 255, 0.3), 0 8px 25px rgba(0,0,0,0.5);
        }

        .header .logo-glow::after {
            content: '';
            position: absolute;
            inset: -2px;
            border-radius: 22px;
            background: linear-gradient(135deg, #00aaff, #0066ff, #00ccff);
            z-index: -1;
            opacity: 0.6;
        }

        .header h1 {
            font-size: 2em;
            font-weight: 900;
            letter-spacing: 3px;
            background: linear-gradient(180deg, #ffffff 0%, #88ccff 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-transform: uppercase;
        }

        .header .sub {
            font-size: 0.8em;
            color: #667;
            letter-spacing: 1.5px;
            margin-top: 2px;
        }

        .header .credit {
            font-size: 0.68em;
            color: #445;
            margin-top: 5px;
            font-style: italic;
            letter-spacing: 0.5px;
        }

        /* Tabs */
        .tabs {
            display: flex;
            gap: 5px;
            margin-bottom: 22px;
            background: rgba(255,255,255,0.02);
            border-radius: 14px;
            padding: 5px;
            border: 1px solid rgba(255,255,255,0.05);
        }

        .tab {
            flex: 1;
            padding: 11px 8px;
            text-align: center;
            border-radius: 11px;
            font-size: 0.78em;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            color: #777;
            border: none;
            background: transparent;
            letter-spacing: 0.8px;
        }

        .tab.active {
            background: rgba(0, 140, 255, 0.18);
            color: #fff;
            box-shadow: 0 0 15px rgba(0, 120, 255, 0.15);
        }

        .tab:hover { color: #aaa; }

        /* Nội dung tab */
        .tab-content { display: none; }
        .tab-content.active { display: block; animation: slideUp 0.35s ease; }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Card */
        .card {
            background: rgba(20, 20, 45, 0.55);
            border-radius: 18px;
            padding: 20px;
            margin-bottom: 16px;
            border: 1px solid rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(5px);
            transition: all 0.35s;
        }

        .card:hover {
            border-color: rgba(255, 255, 255, 0.1);
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.4);
        }

        .card-title {
            font-size: 0.95em;
            font-weight: 700;
            color: #ccddff;
            margin-bottom: 14px;
            display: flex;
            align-items: center;
            gap: 10px;
            letter-spacing: 0.5px;
        }

        .card-title .dot {
            width: 10px; height: 10px;
            border-radius: 50%;
            display: inline-block;
        }

        .dot-free { background: #00cc66; box-shadow: 0 0 12px #00cc66; }
        .dot-vip { background: #ff3366; box-shadow: 0 0 12px #ff3366; }
        .dot-link { background: #ffaa00; box-shadow: 0 0 12px #ffaa00; }
        .dot-admin { background: #9933ff; box-shadow: 0 0 12px #9933ff; }

        /* Input */
        .input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 12px;
            flex-wrap: wrap;
        }

        .input-group input,
        .input-group select,
        .input-group textarea {
            flex: 1;
            min-width: 120px;
            padding: 13px 16px;
            border: 1.5px solid rgba(255, 255, 255, 0.08);
            border-radius: 13px;
            background: rgba(0, 0, 0, 0.4);
            color: #fff;
            font-size: 0.88em;
            outline: none;
            transition: all 0.3s;
            font-family: inherit;
            letter-spacing: 0.4px;
        }

        .input-group textarea { min-height: 70px; resize: vertical; }

        .input-group input:focus,
        .input-group select:focus,
        .input-group textarea:focus {
            border-color: rgba(0, 160, 255, 0.5);
            box-shadow: 0 0 20px rgba(0, 130, 255, 0.12);
            background: rgba(0, 0, 0, 0.55);
        }

        .input-group input::placeholder,
        .input-group textarea::placeholder {
            color: #3a3a50;
            font-style: italic;
        }

        .input-group select {
            background: rgba(0, 0, 0, 0.4);
            color: #fff;
        }

        .input-group select option {
            background: #1a1a30;
            color: #fff;
        }

        /* Buttons */
        .btn {
            padding: 14px 24px;
            border: none;
            border-radius: 13px;
            font-weight: 700;
            font-size: 0.84em;
            cursor: pointer;
            transition: all 0.3s;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            width: 100%;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: -60%;
            left: -60%;
            width: 220%;
            height: 220%;
            background: radial-gradient(circle, rgba(255,255,255,0.08) 0%, transparent 60%);
            opacity: 0;
            transition: opacity 0.35s;
        }

        .btn:hover { transform: translateY(-2px); }
        .btn:hover::before { opacity: 1; }
        .btn:active { transform: translateY(0); }

        .btn-free { background: linear-gradient(135deg, #0088ff, #0055cc); color: #fff; box-shadow: 0 6px 22px rgba(0, 120, 255, 0.3); }
        .btn-vip { background: linear-gradient(135deg, #ff0055, #cc0033); color: #fff; box-shadow: 0 6px 22px rgba(255, 0, 80, 0.3); }
        .btn-gold { background: linear-gradient(135deg, #ffaa00, #ee7700); color: #000; box-shadow: 0 6px 22px rgba(255, 150, 0, 0.3); }
        .btn-green { background: linear-gradient(135deg, #00cc66, #009944); color: #fff; box-shadow: 0 6px 22px rgba(0, 200, 100, 0.3); }
        .btn-red { background: linear-gradient(135deg, #ff3333, #cc0000); color: #fff; box-shadow: 0 6px 22px rgba(255, 50, 50, 0.3); }
        .btn-purple { background: linear-gradient(135deg, #8833ff, #5500cc); color: #fff; box-shadow: 0 6px 22px rgba(130, 50, 255, 0.3); }
        .btn-outline { background: transparent; border: 2px solid rgba(255,255,255,0.18); color: #ccc; box-shadow: none; }
        .btn-sm { padding: 10px 15px; font-size: 0.7em; width: auto; letter-spacing: 1px; }

        /* Kết quả */
        .result {
            background: rgba(0, 0, 0, 0.45);
            border-radius: 15px;
            padding: 18px;
            margin-top: 12px;
            border: 1px solid rgba(0, 255, 120, 0.18);
            display: none;
            backdrop-filter: blur(5px);
        }

        .result.show { display: block; animation: slideUp 0.3s ease; }

        .result .info {
            font-size: 0.88em;
            line-height: 2;
            word-break: break-all;
        }

        .result .info span { color: #00ff88; font-weight: 700; }

        .status {
            text-align: center;
            font-size: 0.78em;
            color: #ffaa00;
            margin-top: 10px;
            min-height: 22px;
            letter-spacing: 0.5px;
        }

        /* Danh sách */
        .list-item {
            background: rgba(255,255,255,0.025);
            border-radius: 11px;
            padding: 12px;
            margin-bottom: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
            font-size: 0.8em;
            border: 1px solid rgba(255,255,255,0.04);
            transition: all 0.3s;
        }

        .list-item:hover { background: rgba(255,255,255,0.06); }

        .badge {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.66em;
            font-weight: 700;
            letter-spacing: 0.5px;
        }

        .badge-vip { background: #ff0055; color: #fff; }
        .badge-free { background: #00aa55; color: #fff; }
        .badge-admin { background: #ffaa00; color: #000; }

        .divider {
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.06), transparent);
            margin: 16px 0;
        }

        iframe {
            width: 100%;
            height: 420px;
            border: 1px solid rgba(255,255,255,0.08);
            border-radius: 14px;
            background: #fff;
            margin-top: 10px;
        }

        /* Nút toggle ẩn/hiện */
        .toggle-btn {
            background: rgba(255,255,255,0.025);
            border: 1px solid rgba(255,255,255,0.08);
            color: #aaa;
            padding: 11px 18px;
            border-radius: 11px;
            cursor: pointer;
            font-size: 0.76em;
            font-weight: 700;
            letter-spacing: 1px;
            width: 100%;
            text-align: center;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            margin-top: 10px;
        }

        .toggle-btn:hover { background: rgba(255,255,255,0.06); color: #fff; }

        .hidden-block {
            display: none;
            margin-top: 12px;
            animation: slideUp 0.3s ease;
        }

        .hidden-block.show { display: block; }

        @media (max-width: 420px) {
            .container { padding: 18px 12px; border-radius: 22px; }
            .header h1 { font-size: 1.5em; }
            .tab { font-size: 0.68em; padding: 9px 4px; }
            .btn { font-size: 0.76em; }
        }
    </style>
</head>
<body>

    <!-- Nền động -->
    <div class="bg-animated">
        <div class="orb"></div>
        <div class="orb"></div>
        <div class="orb"></div>
    </div>

    <!-- Hạt lấp lánh -->
    <div class="particles" id="particles"></div>

    <!-- Container -->
    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="logo-glow">⚔️</div>
            <h1>Liên Quân Free</h1>
            <p class="sub">Nhận Acc Miễn Phí • iOS & Android</p>
            <p class="credit">Created by Hoàng</p>
        </div>

        <!-- Tabs -->
        <div class="tabs">
            <button class="tab active" onclick="chuyenTab('nhanAcc')">🎁 Nhận Acc</button>
            <button class="tab" onclick="chuyenTab('vuotLinkFree')">🔗 Vượt Link</button>
            <button class="tab" onclick="chuyenTab('admin')">🔐 Admin</button>
        </div>

        <!-- ==================== TAB 1: NHẬN ACC ==================== -->
        <div class="tab-content active" id="tabNhanAcc">
            <!-- Free -->
            <div class="card">
                <div class="card-title"><span class="dot dot-free"></span> Nhận Acc Free <span class="badge badge-free">FREE</span></div>
                <div class="input-group">
                    <input type="text" id="keyThuong" placeholder="Nhập mã nhận acc...">
                </div>
                <button class="btn btn-free" onclick="nhanAccThuong()">🎁 Nhận Ngay</button>
                <div class="status" id="statusThuong"></div>
            </div>

            <!-- VIP -->
            <div class="card">
                <div class="card-title"><span class="dot dot-vip"></span> Nhận Acc VIP <span class="badge badge-vip">VIP</span></div>
                <div class="input-group">
                    <input type="text" id="keyVip" placeholder="Nhập mã nhận acc VIP...">
                </div>
                <button class="btn btn-vip" onclick="nhanAccVip()">💎 Nhận Ngay</button>
                <div class="status" id="statusVip"></div>
            </div>

            <!-- Kết quả -->
            <div class="result" id="resultBox">
                <div class="card-title"><span>✅</span> Thông Tin Acc</div>
                <div class="info" id="accInfo"></div>
                <button class="btn btn-outline btn-sm" onclick="copyAcc()" style="margin-top:12px;">📋 Sao Chép</button>
            </div>
        </div>

        <!-- ==================== TAB 2: VƯỢT LINK LẤY KEY FREE ==================== -->
        <div class="tab-content" id="tabVuotLinkFree">
            <div class="card">
                <div class="card-title"><span class="dot dot-link"></span> Vượt Link Lấy Key Free</div>
                <p style="font-size:0.76em; color:#667; margin-bottom:12px; text-align:center;">
                    Nhập link → Vượt → Nhận Key + Acc bên dưới
                </p>
                <div class="input-group">
                    <input type="url" id="urlVuotLinkFree" placeholder="Nhập URL cần vượt...">
                </div>
                <div class="input-group">
                    <select id="proxySelectFree">
                        <option value="https://api.allorigins.win/raw?url=">AllOrigins Proxy</option>
                        <option value="https://corsproxy.io/?">CORS Proxy</option>
                        <option value="https://api.codetabs.com/v1/proxy?quest=">CodeTabs Proxy</option>
                        <option value="https://thingproxy.freeboard.io/fetch/">ThingProxy</option>
                    </select>
                </div>
                <button class="btn btn-gold" onclick="vuotLinkFree()">🚀 Vượt Link & Nhận Key</button>
                <div class="status" id="statusVuotLinkFree"></div>
                <iframe id="iframeVuotLinkFree" src="" style="display:none;"></iframe>
            </div>

            <!-- Key + Acc -->
            <div class="result" style="display:block;">
                <div class="card-title"><span>🎮</span> Key & Acc Nhận Được</div>
                <div class="info" id="accInfoVuotLink">
                    <p style="color:#555; text-align:center;">Chưa vượt link. Nhập link và bấm nút trên.</p>
                </div>
                <button class="btn btn-outline btn-sm" onclick="copyAccVuotLink()" style="margin-top:12px;">📋 Sao Chép</button>
            </div>
        </div>

        <!-- ==================== TAB 3: ADMIN ==================== -->
        <div class="tab-content" id="tabAdmin">
            <!-- Login -->
            <div class="card" id="adminLoginSection">
                <div class="card-title"><span class="dot dot-admin"></span> Đăng Nhập Admin</div>
                <div class="input-group">
                    <input type="password" id="adminKey" placeholder="Nhập mã Admin...">
                </div>
                <button class="btn btn-purple" onclick="dangNhapAdmin()">🔓 Đăng Nhập</button>
                <div class="status" id="statusAdminLogin"></div>
            </div>

            <!-- Panel -->
            <div id="adminPanel" style="display:none;">
                <p style="text-align:center; color:#ffaa00; font-weight:700; margin-bottom:12px; letter-spacing:1px;">
                    👑 ADMIN: Locnguyen
                </p>

                <!-- TẠO KEY TỰ ĐỘNG -->
                <div class="card">
                    <div class="card-title"><span>🔑</span> Tạo Key Mới (Lin-...)</div>
                    <div class="input-group">
                        <input type="text" id="genKeySuffix" placeholder="Phần sau Lin- (VD: 123ABC)">
                    </div>
                    <p style="font-size:0.7em; color:#556; margin-bottom:8px;">
                        Key sẽ tự động có dạng: <strong style="color:#ffaa00;">Lin-</strong> + phần bạn nhập
                    </p>
                    <div class="input-group">
                        <input type="text" id="genKeyTaiKhoan" placeholder="Tài khoản LQ">
                        <input type="text" id="genKeyMatKhau" placeholder="Mật khẩu">
                    </div>
                    <div class="input-group">
                        <input type="text" id="genKeyTuong" placeholder="Số tướng">
                        <input type="text" id="genKeySkin" placeholder="Số skin">
                    </div>
                    <div class="input-group">
                        <input type="text" id="genKeyRank" placeholder="Rank">
                    </div>
                    <div class="input-group" style="align-items:center;">
                        <label style="color:#ccc; font-size:0.82em; display:flex; align-items:center; gap:6px;">
                            <input type="checkbox" id="genKeyVip" style="width:17px; height:17px;"> Acc VIP
                        </label>
                    </div>
                    <button class="btn btn-green" onclick="taoKeyMoi()">✅ Tạo Key Lin-...</button>
                    <div class="status" id="statusGenKey"></div>
                </div>

                <!-- Nút ẩn/hiện THÊM ACC -->
                <button class="toggle-btn" onclick="toggleBlock('blockThemAcc')">
                    <span>➕</span> Thêm Acc Vào Database <span id="arrowThemAcc">▼</span>
                </button>
                <div class="hidden-block" id="blockThemAcc">
                    <div class="card" style="margin-top:12px;">
                        <div class="card-title"><span>🎮</span> Thêm Acc Thủ Công</div>
                        <div class="input-group">
                            <input type="text" id="adminAccKey" placeholder="Mã key...">
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
                            <label style="color:#ccc; font-size:0.82em; display:flex; align-items:center; gap:6px;">
                                <input type="checkbox" id="adminAccVip" style="width:17px; height:17px;"> Acc VIP
                            </label>
                        </div>
                        <button class="btn btn-green" onclick="themAccAdmin()">✅ Thêm Acc</button>
                        <div class="status" id="statusAdminAcc"></div>
                    </div>
                </div>

                <!-- Nút ẩn/hiện THÊM LINK -->
                <button class="toggle-btn" style="margin-top:10px;" onclick="toggleBlock('blockThemLink')">
                    <span>🔗</span> Thêm Link Vượt <span id="arrowThemLink">▼</span>
                </button>
                <div class="hidden-block" id="blockThemLink">
                    <div class="card" style="margin-top:12px;">
                        <div class="card-title"><span>🔗</span> Thêm Link</div>
                        <div class="input-group">
                            <input type="text" id="adminLinkName" placeholder="Tên link...">
                        </div>
                        <div class="input-group">
                            <input type="url" id="adminLinkUrl" placeholder="URL...">
                        </div>
                        <button class="btn btn-gold" onclick="themLinkAdmin()">🔗 Thêm Link</button>
                        <div class="status" id="statusAdminLink"></div>
                    </div>
                    <div class="card" style="margin-top:10px;">
                        <div class="card-title"><span>📋</span> Danh Sách Link</div>
                        <div id="danhSachLinkAdmin"><p style="color:#555; text-align:center;">Chưa có link</p></div>
                    </div>
                </div>

                <button class="btn btn-red" onclick="dangXuatAdmin()" style="margin-top:14px;">🚪 Đăng Xuất</button>
            </div>
        </div>
    </div>

    <script>
        // ==================== TẠO HẠT LẤP LÁNH ====================
        (function(){
            const p = document.getElementById('particles');
            for(let i=0;i<50;i++){
                const d = document.createElement('div');
                d.className='particle';
                d.style.left=Math.random()*100+'%';
                d.style.top=Math.random()*100+'%';
                d.style.animationDelay=Math.random()*4+'s';
                d.style.animationDuration=(2+Math.random()*4)+'s';
                p.appendChild(d);
            }
        })();

        // ==================== DATABASE ====================
        const DEFAULT_DB = {
            "LQ-FREE-1234": { taiKhoan: "lqfree_user01", matKhau: "Pass@Free001", tuong: 45, skin: 12, rank: "Kim Cương V", vip: false },
            "LQ-FREE-5678": { taiKhoan: "lqfree_user02", matKhau: "Pass@Free002", tuong: 52, skin: 18, rank: "Tinh Anh III", vip: false },
            "LQ-FREE-9999": { taiKhoan: "lqfree_pro99", matKhau: "Pro@Free999", tuong: 60, skin: 25, rank: "Cao Thủ 15 Sao", vip: false },
            "LQ-VIP-1111": { taiKhoan: "lqvip_legend01", matKhau: "Vip@Legend1", tuong: 95, skin: 78, rank: "Thách Đấu 50 Sao", vip: true },
            "LQ-VIP-2222": { taiKhoan: "lqvip_master02", matKhau: "Vip@Master2", tuong: 90, skin: 65, rank: "Thách Đấu 30 Sao", vip: true },
            "LQ-VIP-8888": { taiKhoan: "lqvip_god888", matKhau: "God@Vip888", tuong: 112, skin: 120, rank: "Top 1 Server", vip: true, dacBiet: "Tất cả skin giới hạn" },
            "HOANG-VIP-9999": { taiKhoan: "hoang_pro_max", matKhau: "Hoang@Pro9999", tuong: 115, skin: 130, rank: "Thách Đấu Top 10", vip: true, dacBiet: "Key VIP riêng - Full tướng Full skin" }
        };

        const ADMIN_KEY = "Locnguyen";

        const VUOT_LINK_KEYS = [
            { key: "LQ-VUOT-001", acc: { taiKhoan: "lq_vuot_01", matKhau: "Vuot@Link01", tuong: 35, skin: 10, rank: "Vàng I", vip: false } },
            { key: "LQ-VUOT-002", acc: { taiKhoan: "lq_vuot_02", matKhau: "Vuot@Link02", tuong: 42, skin: 15, rank: "Bạch Kim III", vip: false } },
            { key: "LQ-VUOT-VIP", acc: { taiKhoan: "lq_vuot_vip", matKhau: "Vuot@Vip999", tuong: 88, skin: 60, rank: "Thách Đấu", vip: true, dacBiet: "Acc VIP từ vượt link" } }
        ];

        // ==================== LOCAL STORAGE ====================
        function layDB() {
            let d = localStorage.getItem("lq_db_v5");
            if(!d) { localStorage.setItem("lq_db_v5", JSON.stringify(DEFAULT_DB)); return JSON.parse(JSON.stringify(DEFAULT_DB)); }
            return JSON.parse(d);
        }
        function luuDB(db) { localStorage.setItem("lq_db_v5", JSON.stringify(db)); }
        function layLinks() { let l = localStorage.getItem("lq_links_v5"); return l ? JSON.parse(l) : []; }
        function luuLinks(links) { localStorage.setItem("lq_links_v5", JSON.stringify(links)); }

        // ==================== TAB ====================
        function chuyenTab(name) {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
            const map = {'nhanAcc':0,'vuotLinkFree':1,'admin':2};
            const ids = {'nhanAcc':'tabNhanAcc','vuotLinkFree':'tabVuotLinkFree','admin':'tabAdmin'};
            document.querySelectorAll('.tab')[map[name]].classList.add('active');
            document.getElementById(ids[name]).classList.add('active');
            if(name==='admin'){ kiemTraAdmin(); hienThiLinks(); }
        }

        // ==================== NHẬN ACC ====================
        function nhanAccThuong() {
            const key = document.getElementById("keyThuong").value.trim().toUpperCase();
            const s = document.getElementById("statusThuong");
            if(!key){ s.textContent="⚠️ Vui lòng nhập mã!"; s.style.color="#ff6600"; return; }
            const db = layDB(); const acc = db[key];
            if(!acc){ s.textContent="❌ Mã không tồn tại!"; s.style.color="#ff3333"; return; }
            if(acc.vip){ s.textContent="⚠️ Mã này là VIP!"; s.style.color="#ffaa00"; return; }
            hienAcc(acc,false); s.textContent="✅ Nhận acc thành công!"; s.style.color="#00ff88";
        }

        function nhanAccVip() {
            const key = document.getElementById("keyVip").value.trim().toUpperCase();
            const s = document.getElementById("statusVip");
            if(!key){ s.textContent="⚠️ Vui lòng nhập mã VIP!"; s.style.color="#ff6600"; return; }
            const db = layDB(); const acc = db[key];
            if(!acc){ s.textContent="❌ Mã VIP không tồn tại!"; s.style.color="#ff3333"; return; }
            if(!acc.vip){ s.textContent="⚠️ Mã này là Free!"; s.style.color="#ffaa00"; return; }
            hienAcc(acc,true); s.textContent="✅ Nhận acc VIP thành công!"; s.style.color="#ffcc00";
        }

        function hienAcc(acc, isVip) {
            const rb = document.getElementById("resultBox");
            const ai = document.getElementById("accInfo");
            let v = isVip ? '👑 <span style="color:#ffcc00;">[VIP]</span> ' : '';
            let db = acc.dacBiet ? `🌟 <span>Đặc biệt:</span> ${acc.dacBiet}<br>` : '';
            ai.innerHTML = `${v}🎮 <span>Tài khoản:</span> ${acc.taiKhoan}<br>🔒 <span>Mật khẩu:</span> ${acc.matKhau}<br>👥 <span>Số tướng:</span> ${acc.tuong}<br>💄 <span>Số skin:</span> ${acc.skin}<br>🏆 <span>Rank:</span> ${acc.rank}<br>${db}`;
            rb.classList.add("show");
        }

        function copyAcc() {
            const t = document.getElementById("accInfo").innerText;
            navigator.clipboard.writeText(t).then(()=>alert("✅ Đã sao chép!")).catch(()=>alert("⚠️ Bôi đen copy thủ công"));
        }

        // ==================== VƯỢT LINK FREE ====================
        function vuotLinkFree() {
            const url = document.getElementById("urlVuotLinkFree").value.trim();
            const proxy = document.getElementById("proxySelectFree").value;
            const iframe = document.getElementById("iframeVuotLinkFree");
            const s = document.getElementById("statusVuotLinkFree");
            if(!url){ s.textContent="⚠️ Nhập URL!"; s.style.color="#ff6600"; return; }
            let fu = url;
            if(!url.startsWith("http")) fu = "https://"+url;
            iframe.src = proxy + encodeURIComponent(fu);
            iframe.style.display = "block";
            s.textContent="✅ Đã vượt link! Key & Acc bên dưới...";
            s.style.color="#00ff88";
            setTimeout(()=>{
                const rd = VUOT_LINK_KEYS[Math.floor(Math.random()*VUOT_LINK_KEYS.length)];
                hienAccVuotLink(rd);
            }, 1800);
        }

        function hienAccVuotLink(data) {
            const ai = document.getElementById("accInfoVuotLink");
            const acc = data.acc;
            let v = acc.vip ? '👑 <span style="color:#ffcc00;">[VIP]</span> ' : '';
            let db = acc.dacBiet ? `🌟 <span>Đặc biệt:</span> ${acc.dacBiet}<br>` : '';
            ai.innerHTML = `🔑 <span>Key nhận được:</span> ${data.key}<br>${v}🎮 <span>Tài khoản:</span> ${acc.taiKhoan}<br>🔒 <span>Mật khẩu:</span> ${acc.matKhau}<br>👥 <span>Số tướng:</span> ${acc.tuong}<br>💄 <span>Số skin:</span> ${acc.skin}<br>🏆 <span>Rank:</span> ${acc.rank}<br>${db}`;
        }

        function copyAccVuotLink() {
            const t = document.getElementById("accInfoVuotLink").innerText;
            navigator.clipboard.writeText(t).then(()=>alert("✅ Đã sao chép!")).catch(()=>alert("⚠️ Bôi đen copy thủ công"));
        }

        // ==================== ADMIN ====================
        function dangNhapAdmin() {
            const key = document.getElementById("adminKey").value.trim();
            const s = document.getElementById("statusAdminLogin");
            if(key === ADMIN_KEY){
                sessionStorage.setItem("lq_admin_v5","true");
                document.getElementById("adminLoginSection").style.display="none";
                document.getElementById("adminPanel").style.display="block";
                s.textContent=""; hienThiLinks();
            } else { s.textContent="❌ Sai mã Admin!"; s.style.color="#ff3333"; }
        }

        function kiemTraAdmin() {
            if(sessionStorage.getItem("lq_admin_v5")==="true"){
                document.getElementById("adminLoginSection").style.display="none";
                document.getElementById("adminPanel").style.display="block";
                hienThiLinks();
            } else {
                document.getElementById("adminLoginSection").style.display="block";
                document.getElementById("adminPanel").style.display="none";
            }
        }

        function dangXuatAdmin() {
            sessionStorage.removeItem("lq_admin_v5");
            document.getElementById("adminLoginSection").style.display="block";
            document.getElementById("adminPanel").style.display="none";
            document.getElementById("adminKey").value="";
        }

        function toggleBlock(id) {
            const el = document.getElementById(id);
            el.classList.toggle("show");
            const arrowId = id==="blockThemAcc" ? "arrowThemAcc" : "arrowThemLink";
            const arrow = document.getElementById(arrowId);
            if(el.classList.contains("show")) arrow.textContent = "▲";
            else arrow.textContent = "▼";
        }

        // TẠO KEY MỚI Lin-...
        function taoKeyMoi() {
            const suffix = document.getElementById("genKeySuffix").value.trim().toUpperCase();
            const tk = document.getElementById("genKeyTaiKhoan").value.trim();
            const mk = document.getElementById("genKeyMatKhau").value.trim();
            const tuong = document.getElementById("genKeyTuong").value.trim();
            const skin = document.getElementById("genKeySkin").value.trim();
            const rank = document.getElementById("genKeyRank").value.trim();
            const vip = document.getElementById("genKeyVip").checked;
            const s = document.getElementById("statusGenKey");

            if(!suffix){ s.textContent="⚠️ Nhập phần sau Lin-!"; s.style.color="#ff6600"; return; }
            if(!tk||!mk){ s.textContent="⚠️ TK và MK là bắt buộc!"; s.style.color="#ff6600"; return; }

            const keyFull = "Lin-" + suffix;
            const db = layDB();
            if(db[keyFull]){ s.textContent="⚠️ Key này đã tồn tại!"; s.style.color="#ffaa00"; return; }

            db[keyFull] = {
                taiKhoan: tk,
                matKhau: mk,
                tuong: parseInt(tuong)||0,
                skin: parseInt(skin)||0,
                rank: rank||"Chưa xếp hạng",
                vip: vip
            };
            luuDB(db);

            ["genKeySuffix","genKeyTaiKhoan","genKeyMatKhau","genKeyTuong","genKeySkin","genKeyRank"].forEach(id=>document.getElementById(id).value="");
            document.getElementById("genKeyVip").checked=false;
            s.textContent=`✅ Đã tạo key: ${keyFull} (${vip?'VIP':'Free'})`; s.style.color="#00ff88";
        }

        // THÊM ACC THỦ CÔNG
        function themAccAdmin() {
            const key = document.getElementById("adminAccKey").value.trim().toUpperCase();
            const tk = document.getElementById("adminAccTaiKhoan").value.trim();
            const mk = document.getElementById("adminAccMatKhau").value.trim();
            const tuong = document.getElementById("adminAccTuong").value.trim();
            const skin = document.getElementById("adminAccSkin").value.trim();
            const rank = document.getElementById("adminAccRank").value.trim();
            const vip = document.getElementById("adminAccVip").checked;
            const s = document.getElementById("statusAdminAcc");
            if(!key||!tk||!mk){ s.textContent="⚠️ Key, TK, MK là bắt buộc!"; s.style.color="#ff6600"; return; }
            const db = layDB();
            db[key] = { taiKhoan:tk, matKhau:mk, tuong:parseInt(tuong)||0, skin:parseInt(skin)||0, rank:rank||"Chưa xếp hạng", vip:vip };
            luuDB(db);
            ["adminAccKey","adminAccTaiKhoan","adminAccMatKhau","adminAccTuong","adminAccSkin","adminAccRank"].forEach(id=>document.getElementById(id).value="");
            document.getElementById("adminAccVip").checked=false;
            s.textContent=`✅ Đã thêm acc "${tk}" - Key: ${key}`; s.style.color="#00ff88";
        }

        // THÊM LINK
        function themLinkAdmin() {
            const name = document.getElementById("adminLinkName").value.trim();
            const url = document.getElementById("adminLinkUrl").value.trim();
            const s = document.getElementById("statusAdminLink");
            if(!name||!url){ s.textContent="⚠️ Nhập đủ Tên và URL!"; s.style.color="#ff6600"; return; }
            let links = layLinks();
            links.push({name,url,time:new Date().toLocaleString("vi-VN")});
            luuLinks(links);
            document.getElementById("adminLinkName").value=""; document.getElementById("adminLinkUrl").value="";
            s.textContent=`✅ Đã thêm link "${name}"`; s.style.color="#00ff88";
            hienThiLinks();
        }

        function hienThiLinks() {
            const c = document.getElementById("danhSachLinkAdmin");
            const links = layLinks();
            if(links.length===0){ c.innerHTML='<p style="color:#555;text-align:center;">Chưa có link</p>'; return; }
            let h="";
            links.forEach((l,i)=>{
                h+=`<div class="list-item"><div>🔗 <strong>${l.name}</strong><br><small style="color:#888;">${l.url}</small><br><small style="color:#666;">${l.time}</small></div><div style="display:flex;gap:5px;"><button class="btn btn-free btn-sm" onclick="window.open('${l.url}','_blank')">🌐</button><button class="btn btn-red btn-sm" onclick="xoaLink(${i})">🗑</button></div></div>`;
            });
            c.innerHTML=h;
        }

        function xoaLink(i) {
            if(!confirm("Xóa link?")) return;
            let links = layLinks(); links.splice(i,1); luuLinks(links); hienThiLinks();
        }

        // ==================== INIT ====================
        kiemTraAdmin();
        console.log("✅ Web LQ - Admin: Locnguyen | Created by Hoàng");
        console.log("🔑 Tạo key: Lin- + suffix");
    </script>
</body>
</html>
```
