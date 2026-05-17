<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HM BOX - Quet Ma QR</title>
    <script src="https://unpkg.com/html5-qrcode"></script>
    <style>
        body { font-family: 'Segoe UI', Roboto, Arial, sans-serif; background-color: #f4f6f9; margin: 0; padding: 0; display: flex; flex-direction: column; align-items: center; color: #333; }
        .header { background-color: #1a252f; color: white; width: 100%; text-align: center; padding: 20px 0; box-shadow: 0 2px 10px rgba(0,0,0,0.1); }
        .header h1 { margin: 0; font-size: 24px; letter-spacing: 1px; }
        .header p { margin: 5px 0 0 0; font-size: 14px; opacity: 0.8; }
        .container { width: 90%; max-width: 450px; margin-top: 30px; background: white; padding: 20px; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); text-align: center; }
        #reader { width: 100% !important; border: none !important; border-radius: 8px; overflow: hidden; }
        #reader button { background-color: #3498db; color: white; border: none; padding: 12px 20px; font-size: 16px; font-weight: bold; border-radius: 6px; cursor: pointer; margin: 10px 0; }
        .result-box { margin-top: 20px; padding: 15px; background-color: #e8f8f5; border: 1px solid #2ecc71; border-radius: 8px; display: none; word-wrap: break-word; }
        .result-box h3 { margin: 0 0 5px 0; color: #27ae60; }
        .footer { margin-top: 40px; font-size: 12px; color: #7f8c8d; }
    </style>
</head>
<body>
    <div class="header">
        <h1>HM BOX SYSTEM</h1>
        <p>He thong Quet Ma QR Dat Hang & Check-in</p>
    </div>
    <div class="container">
        <p style="font-weight: 500; margin-bottom: 15px;">Vui long dua ma QR vao khung camera ben duoi</p>
        <div id="reader"></div>
        <div id="result" class="result-box">
            <h3>Quet Thanh Cong!</h3>
            <p id="result-text"></p>
        </div>
    </div>
    <div class="footer"> &copy; 2026 HM Box - Chiba Tokyo </div>
    <script>
        function onScanSuccess(decodedText, decodedResult) {
            html5QrcodeScanner.clear();
            document.getElementById('result').style.display = 'block';
            document.getElementById('result-text').innerText = "Data: " + decodedText;
            if (decodedText.startsWith("http://") || decodedText.startsWith("https://")) {
                setTimeout(function() { window.location.href = decodedText; }, 2000);
            }
        }
        let html5QrcodeScanner = new Html5QrcodeScanner("reader", { fps: 10, qrbox: 250 });
        html5QrcodeScanner.render(onScanSuccess);
    </script>
</body>
</html>
