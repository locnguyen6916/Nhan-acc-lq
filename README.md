<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hệ Thống Key & Tài Khoản</title>
    <style>
        :root { --primary: #4f46e5; --bg: #0f172a; --card: #1e293b; }
        body { font-family: sans-serif; background: var(--bg); color: #f1f5f9; display: flex; justify-content: center; padding: 20px; }
        .container { width: 100%; max-width: 500px; }
        .card { background: var(--card); padding: 20px; border-radius: 12px; margin-bottom: 20px; box-shadow: 0 4px 6px rgba(0,0,0,0.3); }
        input, select, textarea { width: 100%; padding: 12px; margin: 8px 0; background: #0f172a; border: 1px solid #334155; color: white; border-radius: 6px; box-sizing: border-box; }
        button { width: 100%; padding: 12px; background: var(--primary); border: none; color: white; border-radius: 6px; cursor: pointer; font-weight: bold; }
        .hidden { display: none; }
        .link-btn { background: #059669; display: block; text-align: center; text-decoration: none; color: white; padding: 12px; border-radius: 6px; }
    </style>
</head>
<body>

<div class="container">
    <div class="card">
        <h3>Vượt link lấy Key Free</h3>
        <a id="linkFreeOut" href="#" class="link-btn" target="_blank">Chưa cấu hình Link</a>
    </div>

    <div class="card">
        <h3>Nhập Key</h3>
        <input type="text" id="inputKey" placeholder="Nhập Key Free hoặc Vip...">
        <button onclick="checkKey()">Kiểm tra</button>
        <p id="result" style="margin-top: 10px;"></p>
    </div>

    <div class="card">
        <h3>Mục Admin</h3>
        <input type="password" id="adminPass" placeholder="Nhập key Admin...">
        <button onclick="accessAdmin()">Truy cập</button>

        <div id="adminPanel" class="hidden">
            <hr style="margin: 20px 0; border: 0; border-top: 1px solid #334155;">
            <h4>Thêm Acc</h4>
            <input type="text" id="newKey" placeholder="Mã Key">
            <textarea id="newAcc" placeholder="Dữ liệu Acc..."></textarea>
            <button onclick="saveAcc()" style="background: #059669;">Lưu Acc</button>
            
            <h4 style="margin-top: 20px;">Cấu hình Vượt Link</h4>
            <input type="text" id="newLink" placeholder="URL vượt link...">
            <button onclick="saveLink()" style="background: #ea580c;">Lưu Link</button>
        </div>
    </div>
</div>

<script>
    function accessAdmin() {
        if(document.getElementById('adminPass').value === "Locnguyen") {
            document.getElementById('adminPanel').classList.remove('hidden');
        } else { alert("Sai mật khẩu Admin!"); }
    }

    function saveAcc() {
        const k = document.getElementById('newKey').value;
        const a = document.getElementById('newAcc').value;
        localStorage.setItem('acc_' + k, a);
        alert("Đã lưu!");
    }

    function saveLink() {
        const l = document.getElementById('newLink').value;
        localStorage.setItem('link', l);
        document.getElementById('linkFreeOut').href = l;
        document.getElementById('linkFreeOut').innerText = "Vượt link tại đây";
        alert("Đã lưu link!");
    }

    function checkKey() {
        const k = document.getElementById('inputKey').value;
        const res = localStorage.getItem('acc_' + k);
        document.getElementById('result').innerText = res ? "Acc: " + res : "Key sai hoặc không tồn tại!";
    }

    window.onload = () => {
        const l = localStorage.getItem('link');
        if(l) { 
            document.getElementById('linkFreeOut').href = l; 
            document.getElementById('linkFreeOut').innerText = "Vượt link tại đây"; 
        }
    }
</script>
</body>
</html>
