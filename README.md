<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hệ Thống Quản Lý Key & Tài Khoản</title>
    <style>
        :root {
            --primary-color: #4f46e5;
            --secondary-color: #06b6d4;
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --text-color: #f8fafc;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .container {
            width: 100%;
            max-width: 800px;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }

        h2 {
            margin-top: 0;
            border-bottom: 2px solid #334155;
            padding-bottom: 10px;
            color: var(--secondary-color);
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        input[type="text"], select, textarea {
            width: 100%;
            padding: 10px;
            border-radius: 4px;
            border: 1px solid #475569;
            background-color: #0f172a;
            color: var(--text-color);
            box-sizing: border-box;
        }

        button {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.2s;
        }

        button:hover {
            background-color: #4338ca;
        }

        .btn-link {
            background-color: #10b981;
            display: inline-block;
            text-decoration: none;
            color: white;
            padding: 10px 20px;
            border-radius: 4px;
            font-weight: bold;
            text-align: center;
        }

        .btn-link:hover {
            background-color: #059669;
        }

        .result-box {
            margin-top: 15px;
            padding: 15px;
            background-color: #020617;
            border-left: 4px solid var(--secondary-color);
            border-radius: 4px;
            display: none;
            white-space: pre-wrap;
        }

        .admin-panel {
            border: 2px dashed #dc2626;
        }

        .grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }

        th, td {
            border: 1px solid #475569;
            padding: 8px;
            text-align: left;
        }

        th {
            background-color: #334155;
        }
    </style>
</head>
<body>

<div class="container">

    <div class="card">
        <h2>Nhận Key Miễn Phí</h2>
        <p>Bấm vào nút bên dưới để vượt link rút gọn và nhận Key Free hệ thống.</p>
        <a href="https://example.com/bypass-link" target="_blank" class="btn-link">Vượt Link Lấy Key Free</a>
    </div>

    <div class="card">
        <h2>Kích Hoạt Hệ Thống</h2>
        <div class="grid">
            <div>
                <h3>Nhập Key FREE</h3>
                <div class="form-group">
                    <label for="keyFreeInput">Mã Key:</label>
                    <input type="text" id="keyFreeInput" placeholder="Nhập mã key free tại đây...">
                </div>
                <button onclick="verifyKey('free')">Kiểm Tra Key Free</button>
                <div id="resultFree" class="result-box"></div>
            </div>

            <div>
                <h3>Nhập Key VIP</h3>
                <div class="form-group">
                    <label for="keyVipInput">Mã Key:</label>
                    <input type="text" id="keyVipInput" placeholder="Nhập mã key vip tại đây...">
                </div>
                <button onclick="verifyKey('vip')">Kiểm Tra Key VIP</button>
                <div id="resultVip" class="result-box"></div>
            </div>
        </div>
    </div>

    <div class="card admin-panel">
        <h2>Mục của Admin (Quản Lý Hệ Thống)</h2>
        
        <div class="grid">
            <div>
                <h3>Cấu Hình Thêm Key & Tài Khoản</h3>
                <div class="form-group">
                    <label for="adminKeyType">Loại Key:</label>
                    <select id="adminKeyType">
                        <option value="free">Free</option>
                        <option value="vip">Vip</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="adminKeyString">Mã Key Cần Thêm:</label>
                    <input type="text" id="adminKeyString" placeholder="Ví dụ: FREE_123XYZ hoặc VIP_999AAA">
                </div>
                <div class="form-group">
                    <label for="adminAccData">Dữ Liệu Xuất Ra (Tài khoản / Thông tin):</label>
                    <textarea id="adminAccData" rows="3" placeholder="Username:Password hoặc nội dung phần thưởng..."></textarea>
                </div>
                <button onclick="addKeyConfig()">Lưu Cấu Hình</button>
            </div>

            <div>
                <h3>Danh Sách Key Đang Có</h3>
                <div style="max-height: 250px; overflow-y: auto;">
                    <table>
                        <thead>
                            <tr>
                                <th>Loại</th>
                                <th>Key</th>
                                <th>Dữ liệu Acc</th>
                            </tr>
                        </thead>
                        <tbody id="keyListTable">
                            </tbody>
                    </table>
                </div>
                <button onclick="clearDatabase()" style="background-color: #dc2626; margin-top: 10px;">Xóa Toàn Bộ Dữ Liệu</button>
            </div>
        </div>
    </div>

</div>

<script>
    // Khởi tạo cơ sở dữ liệu tạm thời bằng localStorage nếu chưa có
    if (!localStorage.getItem('keyStorage')) {
        const defaultData = {
            free: {},
            vip: {}
        };
        localStorage.setItem('keyStorage', JSON.stringify(defaultData));
    }

    // Hàm load dữ liệu lên bảng admin
    function loadAdminTable() {
        const storage = JSON.parse(localStorage.getItem('keyStorage'));
        const tableBody = document.getElementById('keyListTable');
        tableBody.innerHTML = '';

        // Đọc key free
        for (const [key, acc] of Object.entries(storage.free)) {
            const row = `<tr><td><span style="color:#10b981">Free</span></td><td>${key}</td><td>${acc}</td></tr>`;
            tableBody.innerHTML += row;
        }

        // Đọc key vip
        for (const [key, acc] of Object.entries(storage.vip)) {
            const row = `<tr><td><span style="color:#06b6d4">Vip</span></td><td>${key}</td><td>${acc}</td></tr>`;
            tableBody.innerHTML += row;
        }
    }

    // Hàm xử lý khi admin thêm cấu hình mới
    function addKeyConfig() {
        const type = document.getElementById('adminKeyType').value;
        const key = document.getElementById('adminKeyString').value.trim();
        const accData = document.getElementById('adminAccData').value.trim();

        if (!key || !accData) {
            alert('Vui lòng nhập đầy đủ mã Key và dữ liệu Tài Khoản!');
            return;
        }

        const storage = JSON.parse(localStorage.getItem('keyStorage'));
        storage[type][key] = accData;

        localStorage.setItem('keyStorage', JSON.stringify(storage));
        alert('Đã thêm cấu hình thành công!');
        
        // Reset form
        document.getElementById('adminKeyString').value = '';
        document.getElementById('adminAccData').value = '';
        
        loadAdminTable();
    }

    // Hàm xác thực key khi người dùng nhập vào hệ thống
    function verifyKey(type) {
        const inputId = type === 'free' ? 'keyFreeInput' : 'keyVipInput';
        const resultId = type === 'free' ? 'resultFree' : 'resultVip';
        
        const inputKey = document.getElementById(inputId).value.trim();
        const resultBox = document.getElementById(resultId);

        if (!inputKey) {
            resultBox.style.display = 'block';
            resultBox.style.color = '#ef4444';
            resultBox.innerHTML = 'Lỗi: Vui lòng không để trống ô nhập key.';
            return;
        }

        const storage = JSON.parse(localStorage.getItem('keyStorage'));
        
        // Kiểm tra xem key có tồn tại trong nhóm tương ứng (free/vip) không
        if (storage[type] && storage[type][inputKey]) {
            resultBox.style.display = 'block';
            resultBox.style.color = '#10b981';
            resultBox.innerHTML = `<strong>Kích hoạt thành công!</strong>\nTài khoản của bạn:\n${storage[type][inputKey]}`;
        } else {
            resultBox.style.display = 'block';
            resultBox.style.color = '#ef4444';
            resultBox.innerHTML = `Lỗi: Mã Key ${type.toUpperCase()} không chính xác hoặc đã hết hạn.`;
        }
    }

    // Hàm xóa sạch database để làm mới môi trường test
    function clearDatabase() {
        if (confirm('Bạn có chắc chắn muốn xóa toàn bộ Key và Tài khoản không?')) {
            const defaultData = { free: {}, vip: {} };
            localStorage.setItem('keyStorage', JSON.stringify(defaultData));
            loadAdminTable();
        }
    }

    // Tự động load bảng admin khi mở trang web
    window.onload = loadAdminTable;
</script>

</body>
</html>
