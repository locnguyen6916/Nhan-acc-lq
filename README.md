<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Hệ Thống Quản Trị Key</title>
    <style>
        body { font-family: 'Segoe UI', sans-serif; background: #0f172a; color: #f1f5f9; display: flex; justify-content: center; padding: 20px; }
        .wrapper { width: 100%; max-width: 600px; }
        .card { background: #1e293b; padding: 20px; border-radius: 12px; margin-bottom: 20px; box-shadow: 0 4px 6px rgba(0,0,0,0.3); }
        input, textarea { width: 100%; padding: 12px; margin: 8px 0; background: #0f172a; border: 1px solid #334155; color: white; border-radius: 6px; box-sizing: border-box; }
        button { width: 100%; padding: 12px; background: #4f46e5; border: none; color: white; border-radius: 6px; cursor: pointer; font-weight: bold; }
        button:hover { background: #4338ca; }
        .hidden { display: none; }
        #adminPanel { border: 2px dashed #ef4444; }
        .link-section { text-align: center; margin-bottom: 20px; }
    </style>
</head>
<body>

<div class="wrapper">
    <div class="card link-section">
        <h3>Vượt link lấy Key Free</h3>
        <a id="publicLink" href="#" style="color: #22d3ee; font-weight: bold;">Chưa có cấu hình Link</a>
    </div>

    <div class="card">
        <h3>Kích hoạt hệ thống</h3>
        <input type="text" id="userKey" placeholder="Nhập Key Free hoặc Vip...">
        <button onclick="validateKey()">Kiểm tra Key</button>
        <p id="output" style="margin-top: 15px; color: #10b981;"></p>
    </div>

    <div class="card" id="adminPanel">
        <h3 style="color: #ef4444;">Mục của Admin</h3>
        <input type="password" id="adminKey" placeholder="Nhập Key Admin...">
        <button onclick="accessAdmin()">Truy cập Admin</button>

        <div id="adminTools" class="hidden">
            <hr style="border: 0; border-top: 1px solid #334155; margin: 20px 0;">
            <input type="text" id="targetKey" placeholder="Key (Free/Vip)">
            <textarea id="targetAcc" placeholder="Tài khoản trả về..."></textarea>
            <button onclick="saveAccount()" style="background: #059669;">Lưu Acc</button>
            
            <h4 style="margin-top: 20px;">Cấu hình Link vượt</h4>
            <input type="text" id="linkInput" placeholder="Nhập đường dẫn URL...">
            <button onclick="saveLink()" style="background: #ea580c;">Lưu Link</button>
        </div>
    </div>
</div>

<script>
    const ADMIN_KEY = "Locnguyen151110";

    function validateKey() {
        const key = document.getElementById('userKey').value;
        const db = JSON.parse(localStorage.getItem('database') || '{}');
        document.getElementById('output').innerText = db[key] ? "Tài khoản: " + db[key] : "Key không tồn tại!";
    }

    function accessAdmin() {
        if (document.getElementById('adminKey').value === ADMIN_KEY) {
            document.getElementById('adminTools').classList.remove('hidden');
        } else {
            alert("Key Admin sai!");
        }
    }

    function saveAccount() {
        const key = document.getElementById('targetKey').value;
        const acc = document.getElementById('targetAcc').value;
        const db = JSON.parse(localStorage.getItem('database') || '{}');
        db[key] = acc;
        localStorage.setItem('database', JSON.stringify(db));
        alert("Đã lưu Acc!");
    }

    function saveLink() {
        const url = document.getElementById('linkInput').value;
        localStorage.setItem('publicLink', url);
        updatePublicLink(url);
    }

    function updatePublicLink(url) {
        const link = document.getElementById('publicLink');
        link.href = url;
        link.innerText = "Bấm vào đây để lấy Key Free";
    }

    window.onload = () => {
        const url = localStorage.getItem('publicLink');
        if (url) updatePublicLink(url);
    };
</script>
</body>
</html>
