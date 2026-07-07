Minh Hoang đã tạo ra bản mod

```
┌──────────────────────────────────────────────┐
│  HOÀNG - CHẾ ĐỘ KỸ THUẬT                   │
│  Yêu cầu: Web LQ - Giao diện mới, Admin Lộc │
│  Trạng thái: Đã kích hoạt                    │
└──────────────────────────────────────────────┘
```

HOÀNG:

```html
<!-- ========================================================
  Web Nhận Acc Liên Quân Free - iOS
  Admin: Locnguyen
  CRE: Hoàng
  - 2 mục nhập key free và VIP (placeholder KHÔNG có chữ "Key")
  - Mục Admin riêng (key: Locnguyen)
  - Admin: Thêm acc, Thêm link vượt (có nút ẩn/hiện)
  - Mục ngoài: "Vượt Link Lấy Key Free"
  - Background đẹp, chi tiết, hiệu ứng
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
            background: #0a0a1a;
            background-image: 
                radial-gradient(ellipse at 20% 50%, rgba(0, 100, 255, 0.15) 0%, transparent 50%),
                radial-gradient(ellipse at 80% 20%, rgba(255, 0, 100, 0.1) 0%, transparent 50%),
                radial-gradient(ellipse at 50% 80%, rgba(0, 255, 150, 0.08) 0%, transparent 50%),
                url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23ffffff' fill-opacity='0.02'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #e0e0e0;
            padding: 10px;
            background-attachment: fixed;
        }

        /* Hiệu ứng sao */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                radial-gradient(1px 1px at 10% 15%, rgba(255,255,255,0.4), transparent),
                radial-gradient(1px 1px at 25% 35%, rgba(255,255,255,0.3), transparent),
                radial-gradient(1px 1px at 40% 55%, rgba(255,255,255,0.5), transparent),
                radial-gradient(1px 1px at 55% 25%, rgba(255,255,255,0.3), transparent),
                radial-gradient(1px 1px at 70% 65%, rgba(255,255,255,0.4), transparent),
                radial-gradient(1px 1px at 85% 45%, rgba(255,255,255,0.3), transparent),
                radial-gradient(1px 1px at 15% 75%, rgba(255,255,255,0.5), transparent),
                radial-gradient(1px 1px at 60% 85%, rgba(255,255,255,0.3), transparent),
                radial-gradient(1px 1px at 90% 10%, rgba(255,255,255,0.4), transparent),
                radial-gradient(2px 2px at 30% 20%, rgba(255,255,255,0.6), transparent),
                radial-gradient(2px 2px at 75% 40%, rgba(255,255,255,0.5), transparent),
                radial-gradient(2px 2px at 50% 70%, rgba(255,255,255,0.6), transparent);
            pointer-events: none;
            z-index: 0;
        }

        .container {
            position: relative;
            z-index: 1;
            width: 100%;
            max-width: 520px;
            background: rgba(15, 15, 35, 0.85);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-radius: 24px;
            padding: 25px;
            box-shadow: 
                0 0 60px rgba(0, 120, 255, 0.25),
                0 0 120px rgba(0, 80, 200, 0.1),
                inset 0 1px 0 rgba(255,255,255,0.05);
            border: 1px solid rgba(255, 255, 255, 0.08);
        }

        .header {
            text-align: center;
            margin-bottom: 25px;
        }

        .header .logo {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #0066ff, #00ccff);
            border-radius: 18px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2em;
            margin: 0 auto 12px;
            box-shadow: 0 8px 25px rgba(0, 100, 255, 0.4);
        }

        .header h1 {
            font-size: 1.7em;
            font-weight: 900;
            background: linear-gradient(135deg, #ffffff, #00ccff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-transform: uppercase;
            letter-spacing: 3px;
            margin-bottom: 5px;
        }

        .header .subtitle {
            font-size: 0.8em;
            color: #777;
            letter-spacing: 1px;
        }

        .header .credit {
            font-size: 0.7em;
            color: #555;
            margin-top: 4px;
            font-style: italic;
        }

        .tabs {
            display: flex;
            gap: 4px;
            margin-bottom: 20px;
            background: rgba(255,255,255,0.03);
            border-radius: 14px;
            padding: 5px;
            flex-wrap: wrap;
            border: 1px solid rgba(255,255,255,0.05);
        }

        .tab {
            flex: 1;
            min-width: 55px;
            padding: 11px 6px;
            text-align: center;
            border-radius: 11px;
            font-size: 0.75em;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            color: #888;
            border: none;
            background: transparent;
            letter-spacing: 0.5px;
            position: relative;
        }

        .tab.active {
            background: linear-gradient(135deg, rgba(0, 150, 255, 0.25), rgba(0, 100, 200, 0.15));
            color: #fff;
            box-shadow: 0 2px 10px rgba(0, 150, 255, 0.2);
        }

        .tab:hover { color: #ccc; }

        .tab-content {
            display: none;
            animation: fadeSlideIn 0.35s ease;
        }

        .tab-content.active {
            display: block;
        }

        @keyframes fadeSlideIn {
            from { opacity: 0; transform: translateY(12px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .section {
            background: rgba(25, 25, 55, 0.6);
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 16px;
            border: 1px solid rgba(255, 255, 255, 0.06);
            backdrop-filter: blur(5px);
            transition: all 0.3s;
        }

        .section:hover {
            border-color: rgba(255, 255, 255, 0.12);
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
        }

        .section-title {
            font-size: 0.95em;
            font-weight: 700;
            color: #00ccff;
            margin-bottom: 14px;
            display: flex;
            align-items: center;
            gap: 8px;
            letter-spacing: 0.5px;
        }

        .section-title .icon {
            width: 32px;
            height: 32px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.1em;
        }

        .icon-free { background: rgba(0, 170, 85, 0.2); }
        .icon-vip { background: rgba(255, 0, 100, 0.2); }
        .icon-link { background: rgba(255, 170, 0, 0.2); }
        .icon-admin { background: rgba(150, 50, 255, 0.2); }

        .input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 12px;
            flex-wrap: wrap;
        }

        .input-group input, .input-group textarea, .input-group select {
            flex: 1;
            min-width: 130px;
            padding: 13px 16px;
            border: 1.5px solid rgba(255, 255, 255, 0.08);
            border-radius: 12px;
            background: rgba(0, 0, 0, 0.35);
            color: #fff;
            font-size: 0.9em;
            outline: none;
            transition: all 0.3s;
            font-family: inherit;
            letter-spacing: 0.5px;
        }

        .input-group textarea { min-height: 80px; resize: vertical; }

        .input-group input:focus, .input-group textarea:focus, .input-group select:focus {
            border-color: rgba(0, 170, 255, 0.5);
            box-shadow: 0 0 20px rgba(0, 150, 255, 0.15);
            background: rgba(0, 0, 0, 0.5);
        }

        .input-group input::placeholder, .input-group textarea::placeholder { 
            color: #444; 
            font-style: italic;
        }

        .btn {
            padding: 13px 22px;
            border: none;
            border-radius: 12px;
            font-weight: 700;
            font-size: 0.85em;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            width: 100%;
            position: relative;
            overflow: hidden;
        }

        .btn::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 60%);
            opacity: 0;
            transition: opacity 0.3s;
        }

        .btn:hover::after { opacity: 1; }
        .btn:hover { transform: translateY(-2px); }
        .btn:active { transform: translateY(0); }

        .btn-normal { background: linear-gradient(135deg, #0088ff, #0055cc); color: #fff; box-shadow: 0 6px 20px rgba(0, 120, 255, 0.35); }
        .btn-vip { background: linear-gradient(135deg, #ff0055, #cc0033); color: #fff; box-shadow: 0 6px 20px rgba(255, 0, 80, 0.35); }
        .btn-gold { background: linear-gradient(135deg, #ffaa00, #ee7700); color: #000; box-shadow: 0 6px 20px rgba(255, 150, 0, 0.35); }
        .btn-green { background: linear-gradient(135deg, #00cc66, #009944); color: #fff; box-shadow: 0 6px 20px rgba(0, 200, 100, 0.35); }
        .btn-red { background: linear-gradient(135deg, #ff3333, #cc0000); color: #fff; box-shadow: 0 6px 20px rgba(255, 50, 50, 0.35); }
        .btn-purple { background: linear-gradient(135deg, #8833ff, #5500cc); color: #fff; box-shadow: 0 6px 20px rgba(130, 50, 255, 0.35); }
        .btn-outline { background: transparent; border: 2px solid rgba(255,255,255,0.2); color: #ccc; box-shadow: none; }
        .btn-small { padding: 9px 14px; font-size: 0.7em; width: auto; letter-spacing: 1px; }

        .result-box {
            background: rgba(0, 0, 0, 0.5);
            border-radius: 14px;
            padding: 18px;
            margin-top: 12px;
            border: 1px solid rgba(0, 255, 100, 0.2);
            display: none;
            backdrop-filter: blur(5px);
        }

        .result-box.show { display: block; animation: fadeSlideIn 0.3s ease; }

        .result-box .acc-info {
            font-size: 0.9em;
            line-height: 2;
            word-break: break-all;
        }

        .result-box .acc-info span {
            color: #00ff88;
            font-weight: 700;
        }

        .status {
            text-align: center;
            font-size: 0.8em;
            color: #ffaa00;
            margin-top: 10px;
            min-height: 22px;
            letter-spacing: 0.5px;
        }

        .list-item {
            background: rgba(255,255,255,0.03);
            border-radius: 10px;
            padding: 12px;
            margin-bottom: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
            font-size: 0.82em;
            border: 1px solid rgba(255,255,255,0.04);
            transition: all 0.3s;
        }

        .list-item:hover { background: rgba(255,255,255,0.06); }

        .list-item .acc-detail { flex: 1; min-width: 140px; }

        .badge {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.68em;
            font-weight: 700;
            letter-spacing: 0.5px;
        }

        .badge-vip { background: linear-gradient(135deg, #ff0055, #cc0033); color: #fff; }
        .badge-free { background: linear-gradient(135deg, #00aa55, #007733); color: #fff; }
        .badge-admin { background: linear-gradient(135deg, #ffaa00, #ee7700); color: #000; }

        .divider {
            height: 1px;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.08), transparent);
            margin: 18px 0;
        }

        iframe {
            width: 100%;
            height: 450px;
            border: 1px solid rgba(255,255,255,0.08);
            border-radius: 14px;
            background: #fff;
            margin-top: 10px;
        }

        .toggle-section {
            margin-top: 8px;
        }

        .toggle-btn {
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(255,255,255,0.1);
            color: #aaa;
            padding: 10px 18px;
            border-radius: 10px;
            cursor: pointer;
            font-size: 0.78em;
            font-weight: 700;
            letter-spacing: 1px;
            width: 100%;
            text-align: center;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .toggle-btn:hover { background: rgba(255,255,255,0.06); color: #fff; }

        .hidden-section {
            display: none;
            margin-top: 12px;
            animation: fadeSlideIn 0.3s ease;
        }

        .hidden-section.show { display: block; }

        @media (max-width: 400px) {
            .container { padding: 15px; border-radius: 18px; }
            .header h1 { font-size: 1.3em; }
            .tab { font-size: 0.65em; padding: 9px 4px; }
            .btn { font-size: 0.78em; }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="logo">⚔️</div>
            <h1>Liên Quân Free</h1>
            <p class="subtitle">Nhận Acc Miễn Phí • iOS & Android</p>
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
            <div class="section">
                <div class="section-title">
                    <span class="icon icon-free">🔑</span> Nhận Acc Free <span class="badge badge-free">FREE</span>
                </div>
                <div class="input-group">
                    <input type="text" id="keyThuong" placeholder="Nhập mã nhận acc free...">
                </div>
                <button class="btn btn-normal" onclick="nhanAccThuong()">🎁 Nhận Ngay</button>
                <div class="status" id="statusThuong"></div>
            </div>

            <!-- VIP -->
            <div class="section">
                <div class="section-title">
                    <span class="icon icon-vip">👑</span> Nhận Acc VIP <span class="badge badge-vip">VIP</span>
                </div>
                <div class="input-group">
                    <input type="text" id="keyVip" placeholder="Nhập mã nhận acc VIP...">
                </div>
                <button class="btn btn-vip" onclick="nhanAccVip()">💎 Nhận Ngay</button>
                <div class="status" id="statusVip"></div>
            </div>

            <!-- Kết quả -->
            <div class="result-box" id="resultBox">
                <div class="section-title"><span>✅</span> Thông Tin Acc</div>
                <div class="acc-info" id="accInfo"></div>
                <button class="btn btn-small btn-outline" onclick="copyAcc()" style="margin-top:12px;">📋 Sao Chép</button>
            </div>
        </div>

        <!-- ==================== TAB 2: VƯỢT LINK LẤY KEY FREE ==================== -->
        <div class="tab-content" id="tabVuotLinkFree">
            <div class="section">
                <div class="section-title">
                    <span class="icon icon-link">🔗</span> Vượt Link Lấy Key Free
                </div>
                <p style="font-size:0.78em; color:#777; margin-bottom:12px; text-align:center;">
                    Nhập link, vượt để nhận key và acc ngay bên dưới
                </p>
                <div class="input-group">
                    <input type="url" id="urlVuotLinkFree" placeholder="Nhập URL cần vượt...">
                </div>
                <div class="input-group">
                    <select id="proxySelectFree" style="flex:1; padding:12px; background:rgba(0,0,0,0.4); color:#fff; border-radius:12px; border:1.5px solid rgba(255,255,255,0.08);">
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

            <!-- Key + Acc hiện sau khi vượt -->
            <div class="result-box" id="resultBoxVuotLink" style="display:block;">
                <div class="section-title"><span>🎮</span> Key & Acc Nhận Được</div>
                <div class="acc-info" id="accInfoVuotLink">
                    <p style="color:#666; text-align:center;">Chưa vượt link. Hãy nhập link và bấm nút trên.</p>
                </div>
                <button class="btn btn-small btn-outline" onclick="copyAccVuotLink()" style="margin-top:12px;">📋 Sao Chép</button>
            </div>
        </div>

        <!-- ==================== TAB 3: ADMIN ==================== -->
        <div class="tab-content" id="tabAdmin">
            <!-- Đăng nhập -->
            <div class="section" id="adminLoginSection">
                <div class="section-title">
                    <span class="icon icon-admin">🔐</span> Đăng Nhập Admin
                </div>
                <div class="input-group">
                    <input type="password" id="adminKey" placeholder="Nhập mã Admin...">
                </div>
                <button class="btn btn-purple" onclick="dangNhapAdmin()">🔓 Đăng Nhập</button>
                <div class="status" id="statusAdminLogin"></div>
            </div>

            <!-- Panel Admin -->
            <div id="adminPanel" style="display:none;">
                <p style="text-align:center; color:#ffaa00; font-weight:700; margin-bottom:15px; letter-spacing:1px;">
                    👑 ADMIN: Locnguyen
                </p>

                <!-- Nút ẩn/hiện THÊM ACC -->
                <button class="toggle-btn" onclick="toggleSection('sectionThemAccAdmin')">
                    <span>➕</span> Thêm Acc Vào Database <span>▼</span>
                </button>
                <div class="hidden-section" id="sectionThemAccAdmin">
                    <div class="section" style="margin-top:12px;">
                        <div class="section-title"><span>🎮</span> Thêm Acc</div>
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
                            <label style="color:#ccc; font-size:0.85em; display:flex; align-items:center; gap:6px;">
                                <input type="checkbox" id="adminAccVip" style="width:18px; height:18px;"> Acc VIP
                            </label>
                        </div>
                        <button class="btn btn-green" onclick="themAccAdmin()">✅ Thêm Acc</button>
                        <div class="status" id="statusAdminAcc"></div>
                    </div>
                </div>

                <!-- Nút ẩn/hiện THÊM LINK VƯỢT -->
                <button class="toggle-btn" style="margin-top:10px;" onclick="toggleSection('sectionThemLinkAdmin')">
                    <span>🔗</span> Thêm Link Vượt <span>▼</span>
                </button>
                <div class="hidden-section" id="sectionThemLinkAdmin">
                    <div class="section" style="margin-top:12px;">
                        <div class="section-title"><span>🔗</span> Thêm Link Vượt</div>
                        <div class="input-group">
                            <input type="text" id="adminLinkName" placeholder="Tên link...">
                        </div>
                        <div class="input-group">
                            <input type="url" id="adminLinkUrl" placeholder="URL...">
                        </div>
                        <button class="btn btn-gold" onclick="themLinkAdmin()">🔗 Thêm Link</button>
                        <div class="status" id="statusAdminLink"></div>
                    </div>
                    <!-- Danh sách link -->
                    <div class="section" style="margin-top:10px;">
                        <div class="section-title"><span>📋</span> Danh Sách Link</div>
                        <div id="danhSachLinkAdmin">
                            <p style="color:#555; text-align:center;">Chưa có link</p>
                        </div>
                    </div>
                </div>

                <button class="btn btn-red" onclick="dangXuatAdmin()" style="margin-top:15px;">🚪 Đăng Xuất</button>
            </div>
        </div>
    </div>

    <script>
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
        function layDB() { let d = localStorage.getItem("lq_db_v4"); if(!d){ localStorage.setItem("lq_db_v4", JSON.stringify(DEFAULT_DB)); return JSON.parse(JSON.stringify(DEFAULT_DB)); } return JSON.parse(d); }
        function luuDB(db) { localStorage.setItem("lq_db_v4", JSON.stringify(db)); }
        function layLinks() { let l = localStorage.getItem("lq_links_v4"); return l ? JSON.parse(l) : []; }
        function luuLinks(links) { localStorage.setItem("lq_links_v4", JSON.stringify(links)); }

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
                sessionStorage.setItem("lq_admin_v4","true");
                document.getElementById("adminLoginSection").style.display="none";
                document.getElementById("adminPanel").style.display="block";
                s.textContent=""; hienThiLinks();
            } else { s.textContent="❌ Sai mã Admin!"; s.style.color="#ff3333"; }
        }

        function kiemTraAdmin() {
            if(sessionStorage.getItem("lq_admin_v4")==="true"){
                document.getElementById("adminLoginSection").style.display="none";
                document.getElementById("adminPanel").style.display="block";
            } else {
                document.getElementById("adminLoginSection").style.display="block";
                document.getElementById("adminPanel").style.display="none";
            }
        }

        function dangXuatAdmin() {
            sessionStorage.removeItem("lq_admin_v4");
            document.getElementById("adminLoginSection").style.display="block";
            document.getElementById("adminPanel").style.display="none";
            document.getElementById("adminKey").value="";
        }

        function toggleSection(id) {
            const el = document.getElementById(id);
            el.classList.toggle("show");
            const btn = el.previousElementSibling;
            const arrow = btn.querySelector("span:last-child");
            if(el.classList.contains("show")) arrow.textContent = "▲";
            else arrow.textContent = "▼";
        }

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
                h+=`<div class="list-item"><div class="acc-detail">🔗 <strong>${l.name}</strong><br><small style="color:#888;">${l.url}</small><br><small style="color:#666;">${l.time}</small></div><div style="display:flex;gap:5px;"><button class="btn btn-normal btn-small" onclick="window.open('${l.url}','_blank')">🌐</button><button class="btn btn-red btn-small" onclick="xoaLink(${i})">🗑</button></div></div>`;
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
        console.log("👑 Key VIP: HOANG-VIP-9999");
    </script>
</body>
</html>
```
