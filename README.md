<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hệ Thống Key & Tài Khoản</title>
    <style>
        :root { --primary: #6366f1; --accent: #8b5cf6; --bg: #0f172a; --card: #1e293b; }
        body { 
            font-family: 'Segoe UI', sans-serif; 
            background: linear-gradient(135deg, #0f172a 0%, #1e1b4b 100%); 
            color: #f8fafc; min-height: 100vh; display: flex; justify-content: center; padding: 20px; 
        }
        .container { width: 100%; max-width: 500px; }
        .card { background: rgba(30, 41, 59, 0.7); backdrop-filter: blur(10px); padding: 25px; border-radius: 16px; margin-bottom: 20px; border: 1px solid rgba(255,255,255,0.1); }
        input, textarea { width: 100%; padding: 12px; margin: 8px 0; background: #0f172a; border: 1px solid #475569; color: white; border-radius: 8px; box-sizing: border-box; }
        button { width: 100%; padding: 12px; background: var(--primary); border: none; color: white; border-radius: 8px; cursor: pointer; font-weight: bold; transition: 0.3s; }
        button:hover { background: var(--accent); }
        .hidden { display: none; }
        .zalo-btn { background: #0ea5e9; text-decoration: none; display: block; text-align: center; padding: 12px; border-radius: 8px; color: white; margin-top: 10px; }
    </style>
</head>
<body>

<div class="container">
    <div class="card">
        <h3>Vượt link lấy Key Free</h3>
        <a id="linkFreeOut" href="#" class="zalo-btn" target="_blank">Vượt link tại đây</a>
    </div>

    <div class="card">
        <h3>Kích hoạt hệ thống</h3>
        <input type="text" id="inputKey" placeholder="Nhập Key...">
        <button onclick="checkKey()">Kiểm tra Key</button>
        <p id="result" style="text-align: center; margin-top: 10px;"></p>
    </div>

    <div class="card">
        <h3>Mục Admin</h3>
        <input type="password" id="adminPass" placeholder="Key Admin...">
        <button onclick="accessAdmin()">Truy cập</button>

        <div id="adminPanel" class="hidden">
            <button onclick="toggleTools()" style="background:#475569; margin: 10px 0;">Ẩn/Hiện Công cụ</button>
            <div id="adminTools">
                <hr>
                <h4>Thêm Acc</h4>
                <input type="text" id="newKey" placeholder="Mã Key">
                <textarea id="newAcc" placeholder="Dữ liệu Acc..."></textarea>
                <button onclick="saveAcc()" style="background: #059669;">Lưu Acc</button>
                
                <h4 style="margin-top: 15px;">Vượt Link</h4>
                <input type="text" id="newLink" placeholder="URL vượt link...">
                <button onclick="saveLink()" style="background: #ea580c;">Lưu Link</button>
            </div>
        </div>
    </div>

    <div class="card">
        <h3>Mua Key VIP</h3>
        <a href="https://zalo.me/037332056" class="zalo-btn">Liên hệ Zalo: 037332056</a>
    </div>
</div>

<script>
    function accessAdmin() {
        if(document.getElementById('adminPass').value === "Locnguyen") {
            document.getElementById('adminPanel').classList.remove('hidden');
        } else { alert("Sai mật khẩu!"); }
    }

    function toggleTools() {
        const tools = document.getElementById('adminTools');
        tools.style.display = tools.style.display === 'none' ? 'block' : 'none';
    }

    function saveAcc() {
        localStorage.setItem('acc_' + document.getElementById('newKey').value, document.getElementById('newAcc').value);
        alert("Đã lưu!");
    }

    function saveLink() {
        const l = document.getElementById('newLink').value;
        localStorage.setItem('link', l);
        document.getElementById('linkFreeOut').href = l;
        alert("Đã lưu!");
    }

    function checkKey() {
        const res = localStorage.getItem('acc_' + document.getElementById('inputKey').value);
        document.getElementById('result').innerText = res ? "Acc: " + res : "Key sai!";
    }

    window.onload = () => {
        const l = localStorage.getItem('link');
        if(l) document.getElementById('linkFreeOut').href = l;
    }
</script>
</body>
</html>
