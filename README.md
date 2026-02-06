# Next-Look28
<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Python Book Store</title>
    <style>
        body { font-family: 'Segoe UI', Arial, sans-serif; background:#f4f4f4; display: flex; justify-content: center; padding-top: 50px; margin: 0; }
        .container { background:#fff; padding:25px; width:90%; max-width:320px; border-radius:15px; box-shadow: 0px 8px 20px rgba(0,0,0,0.15); text-align: center; }
        h2 { color: #2c3e50; margin-bottom: 10px; font-size: 22px; }
        .price-tag { font-size: 28px; color: #27ae60; font-weight: bold; margin-bottom: 20px; }
        input { width: 100%; padding: 12px; margin: 10px 0; border: 1px solid #ddd; border-radius: 8px; box-sizing: border-box; font-size: 16px; }
        
        .pay-btn { 
            background:#3498db; 
            color:white; 
            border:none; 
            padding: 15px;
            width: 100%;
            border-radius: 8px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 10px;
            transition: 0.3s;
        }
        .pay-btn:active { background: #2980b9; transform: scale(0.95); }
        
        .info-text { margin-top:15px; font-size: 13px; color: #666; line-height: 1.5; }
        .upi-icons { margin-top: 15px; opacity: 0.6; font-size: 12px; }
    </style>
</head>
<body>

<div class="container">
    <h2>Python Basics Book</h2>
    <div class="price-tag">₹199</div>

    <input type="text" id="custName" placeholder="Aapka Naam" required>
    <input type="email" id="custEmail" placeholder="Email Address" required>

    <button onclick="payNow()" class="pay-btn">Pay Now</button>

    <p class="info-text">
        <b>Note:</b> Button dabaate hi aapke phone ke UPI apps open ho jayenge. Payment ke baad hum aapko email par book bhej denge.
    </p>
    
    <div class="upi-icons">Accepted: GPay, PhonePe, Paytm, BHIM</div>
</div>

<script>
function payNow() {
    const name = document.getElementById('custName').value;
    const email = document.getElementById('custEmail').value;

    // Check if fields are empty
    if(name.trim() === "" || email.trim() === "") {
        alert("Kripya Naam aur Email bharein!");
        return;
    }

    // --- UPI Configuration ---
    const upiId = "nxtloook@ybl"; 
    const amount = "199";
    const note = encodeURIComponent("Python Book - " + name);
    const merchantName = encodeURIComponent("Python Store");

    // Creating the UPI Deep Link
    const upiUrl = `upi://pay?pa=${upiId}&pn=${merchantName}&am=${amount}&cu=INR&tn=${note}`;

    // Redirecting to UPI App
    window.location.href = upiUrl;
}
</script>

</body>
</html>
