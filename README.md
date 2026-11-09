# AZIZ-GAS-SHOP
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>অনলাইন প্রোডাক্ট ক্যাটালগ ও অর্ডার</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <header>
        <h1>আমাদের পণ্যসমূহ</h1>
        <p>পছন্দের পণ্যটি বেছে নিন এবং সহজেই অর্ডার করুন</p>
    </header>

    <!-- প্রোডাক্ট ক্যাটালগ সেকশন -->
    <main class="catalog">
        <!-- প্রোডাক্ট ১ -->
        <div class="product-card">
            <img src="https://via.placeholder.com/250x150" alt="প্রোডাক্ট ছবি">
            <h3>১২ কেজি এলপিজি গ্যাস সিলিন্ডার</h3>
            <p class="price">মূল্য: ১,৪৫০ টাকা</p>
            <button onclick="selectProduct('১২ কেজি এলপিজি গ্যাস সিলিন্ডার', 1450)">অর্ডার করুন</button>
        </div>

        <!-- প্রোডাক্ট ২ -->
        <div class="product-card">
            <img src="https://via.placeholder.com/250x150" alt="প্রোডাক্ট ছবি">
            <h3>স্মার্ট মাল্টি-পোর্ট ইউএসবি হাব</h3>
            <p class="price">মূল্য: ৮৫০ টাকা</p>
            <button onclick="selectProduct('স্মার্ট মাল্টি-পোর্ট ইউএসবি হাব', 850)">অর্ডার করুন</button>
        </div>
    </main>

    <!-- অর্ডার ফর্ম সেকশন -->
    <section class="order-section" id="orderFormSection">
        <h2>অর্ডার কনফার্ম করুন</h2>
        <form id="orderForm" onsubmit="submitOrder(event)">
            <div class="form-group">
                <label for="productName">নির্বাচিত পণ্য:</label>
                <input type="text" id="productName" readonly>
            </div>
            <div class="form-group">
                <label for="customerName">আপনার নাম:</label>
                <input type="text" id="customerName" placeholder="আপনার সম্পূর্ণ নাম লিখুন" required>
            </div>
            <div class="form-group">
                <label for="customerPhone">মোবাইল নম্বর:</label>
                <input type="tel" id="customerPhone" placeholder="০১৭xxxxxxxx" required>
            </div>
            <div class="form-group">
                <label for="customerAddress">ডেলিভারি ঠিকানা:</label>
                <textarea id="customerAddress" rows="3" placeholder="পূর্ণাঙ্গ ঠিকানা ও এলাকা লিখুন" required></textarea>
            </div>
            <button type="submit" class="submit-btn">অর্ডার কনফার্ম করুন</button>
        </form>
    </section>

    <!-- সফল মেসেজ দেখানোর জন্য -->
    <div id="successMessage" class="hidden">
        <h3>🎉 আপনার অর্ডারটি সফলভাবে গ্রহণ করা হয়েছে!</h3>
        <p>খুব শীঘ্রই আমাদের প্রতিনিধি আপনার সাথে যোগাযোগ করবেন।</p>
    </div>

    <script src="script.js"></script>
</body>
</html>
body {
    font-family: 'Arial', sans-serif;
    background-color: #f4f7f6;
    margin: 0;
    padding: 20px;
    color: #333;
}

header {
    text-align: center;
    margin-bottom: 30px;
}

header h1 {
    color: #2c3e50;
    margin-bottom: 5px;
}

.catalog {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
    margin-bottom: 40px;
}

.product-card {
    background: #ffffff;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    width: 280px;
    padding: 15px;
    text-align: center;
}

.product-card img {
    width: 100%;
    border-radius: 6px;
}

.product-card h3 {
    font-size: 18px;
    margin: 15px 0 10px;
}

.price {
    color: #e74c3c;
    font-weight: bold;
    font-size: 16px;
    margin-bottom: 15px;
}

.product-card button, .submit-btn {
    background-color: #27ae60;
    color: white;
    border: none;
    padding: 10px 15px;
    border-radius: 5px;
    cursor: pointer;
    font-size: 15px;
    width: 100%;
}

.product-card button:hover, .submit-btn:hover {
    background-color: #219653;
}

.order-section {
    background: #ffffff;
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.order-section h2 {
    text-align: center;
    margin-bottom: 20px;
    font-size: 22px;
}

.form-group {
    margin-bottom: 15px;
}

.form-group label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

.form-group input, .form-group textarea {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.hidden {
    display: none;
    text-align: center;
    background: #d4edda;
    color: #155724;
    padding: 20px;
    border-radius: 8px;
    max-width: 400px;
    margin: 20px auto;
}
// পণ্যের "অর্ডার করুন" বাটনে ক্লিক করলে পণ্য সিলেক্ট হয়ে ফর্মে চলে আসবে
function selectProduct(productName, productPrice) {
    const productInput = document.getElementById('selectedProduct');
    productInput.value = `${productName} - ${productPrice} টাকা`;
    
    // স্ক্রিনটি স্বয়ংক্রিয়ভাবে অর্ডার ফর্মের দিকে স্ক্রোল করে নিয়ে যাবে
    document.getElementById('orderSection').scrollIntoView({ behavior: 'smooth' });
}

// অর্ডার ফর্ম সাবমিট করার পর হোয়াটসঅ্যাপে পাঠানোর ফাংশন
function handleOrder(event) {
    event.preventDefault(); // পেজ রিলোড হওয়া বন্ধ করবে

    const selectedProduct = document.getElementById('selectedProduct').value;
    
    if (!selectedProduct) {
        alert('দয়া করে প্রথমে ক্যাটালগ থেকে একটি পণ্য সিলেক্ট করুন।');
        return;
    }

    const customerName = document.getElementById('customerName').value;
    const customerPhone = document.getElementById('customerPhone').value;
    const customerAddress = document.getElementById('customerAddress').value;

    // আপনার হোয়াটসঅ্যাপ নম্বর এখানে দিন (অবশ্যই দেশের কোড সহ দিতে হবে, যেমন বাংলাদেশের জন্য +880 হলে শুধু 880 লিখতে হবে)
    const whatsappNumber = "8801700000000"; // উদাহরণ: 88017XXXXXXXX বা আপনার পার্সোনাল/বিজনেস হোয়াটসঅ্যাপ নম্বর

    // হোয়াটসঅ্যাপে পাঠানোর জন্য মেসেজ ফরম্যাট তৈরি
    const message = `🛍️ *নতুন অর্ডার এসেছে!*\n\n` +
                    `📦 *পণ্য:* ${selectedProduct}\n` +
                    `👤 *নাম:* ${customerName}\n` +
                    `📞 *মোবাইল:* ${customerPhone}\n` +
                    `🏠 *ঠিকানা:* ${customerAddress}`;

    // মেসেজটিকে URL-এ রূপান্তর করা
    const encodedMessage = encodeURIComponent(message);
    const whatsappURL = `https://wa.me/${whatsappNumber}?text=${encodedMessage}`;

    // ফর্ম লুকিয়ে সফল মেসেজ দেখাবে
    document.getElementById('orderForm').style.display = 'none';
    document.getElementById('successMessage').style.display = 'block';

    // ১.৫ সেকেন্ড পর স্বয়ংক্রিয়ভাবে গ্রাহককে হোয়াটসঅ্যাপে রিডাইরেক্ট করবে
    setTimeout(() => {
        window.open(whatsappURL, '_blank');
    }, 1500);
}
