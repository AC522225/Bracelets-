<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Beads & Besties</title>
  <style>
    body {
      margin: 0;
      font-family: 'Georgia', serif;
      background-color: #fff;
      color: #111;
    }
    header {
      background-color: #f7f7f7;
      padding: 40px 20px;
      text-align: center;
      border-bottom: 1px solid #eee;
    }
    nav {
      text-align: center;
      padding: 10px;
      background-color: #fff;
      border-bottom: 1px solid #eee;
    }
    nav a {
      margin: 0 15px;
      text-decoration: none;
      color: #333;
      font-weight: 600;
      font-size: 1.1em;
    }
    nav a:hover {
      text-decoration: underline;
    }
    header h1 {
      margin: 0;
      font-size: 3em;
      color: #111;
      font-weight: 600;
    }
    header p {
      font-size: 1.2em;
      color: #444;
    }
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 30px;
      padding: 40px;
      max-width: 1200px;
      margin: auto;
    }
    .item {
      background-color: #fafafa;
      border: 1px solid #ddd;
      border-radius: 12px;
      padding: 20px;
      text-align: center;
      transition: box-shadow 0.3s;
    }
    .item:hover {
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    }
    .item img {
      width: 100%;
      height: auto;
      border-radius: 10px;
    }
    .item h2[contenteditable] {
      margin-top: 15px;
      font-size: 1.5em;
      font-weight: 600;
      cursor: text;
    }
    .price {
      font-size: 1.1em;
      color: #666;
      margin: 10px 0;
    }
    .buy-btn, .apple-pay-btn {
      display: block;
      width: 100%;
      margin: 10px 0;
      padding: 12px;
      font-size: 1em;
      border-radius: 6px;
      border: none;
      cursor: pointer;
    }
    .buy-btn {
      background-color: #111;
      color: white;
    }
    .buy-btn:hover {
      background-color: #444;
    }
    .apple-pay-btn {
      background-color: black;
      color: white;
      font-weight: bold;
      font-family: -apple-system, BlinkMacSystemFont, sans-serif;
    }
    .apple-pay-btn::before {
      content: "\f8ff Pay";
      font-family: sans-serif;
      margin-right: 8px;
    }
    input[type="file"] {
      display: block;
      margin: 10px auto;
    }
    .about {
      max-width: 800px;
      margin: 60px auto;
      padding: 0 20px;
      font-size: 1.2em;
      line-height: 1.8;
      color: #333;
    }
  </style>
</head>
<body>
  <header>
    <h1 contenteditable="true">Beads & Besties</h1>
    <p contenteditable="true">Timeless handmade jewelry for every moment ✨</p>
  </header>

  <nav>
    <a href="#shop">Shop</a>
    <a href="#about">Our Story</a>
  </nav>

  <section id="shop" class="gallery">
    <div class="item">
      <img src="images/bracelet1.jpg" alt="Colorful Bracelet" class="editable-img">
      <input type="file" accept="image/*">
      <h2 contenteditable="true">Sunshine Vibes Bracelet</h2>
      <div class="price">$12.00</div>
      <button class="buy-btn" onclick="buy(this.previousElementSibling.previousElementSibling.innerText, 12)">Buy Now</button>
      <button class="apple-pay-btn" onclick="fakeApplePay(this.previousElementSibling.previousElementSibling.innerText)"></button>
    </div>
    <div class="item">
      <img src="images/bracelet2.jpg" alt="Blue & Pink Bracelet" class="editable-img">
      <input type="file" accept="image/*">
      <h2 contenteditable="true">BFF Mix Earrings</h2>
      <div class="price">$14.00</div>
      <button class="buy-btn" onclick="buy(this.previousElementSibling.previousElementSibling.innerText, 14)">Buy Now</button>
      <button class="apple-pay-btn" onclick="fakeApplePay(this.previousElementSibling.previousElementSibling.innerText)"></button>
    </div>
    <div class="item">
      <img src="images/bracelet3.jpg" alt="Beaded Bracelet" class="editable-img">
      <input type="file" accept="image/*">
      <h2 contenteditable="true">Lucky Charms Earrings</h2>
      <div class="price">$10.00</div>
      <button class="buy-btn" onclick="buy(this.previousElementSibling.previousElementSibling.innerText, 10)">Buy Now</button>
      <button class="apple-pay-btn" onclick="fakeApplePay(this.previousElementSibling.previousElementSibling.innerText)"></button>
    </div>
  </section>

  <section id="about" class="about">
    <h2>Our Story</h2>
    <p contenteditable="true">
      Beads & Besties began as a boutique jewelry line inspired by friendship, creativity, and modern femininity. From beaded bracelets to elegant earrings, our collections are designed to empower and adorn. Every piece is handcrafted with intention, celebrating individuality and timeless style.
    </p>
  </section>

  <script>
    document.querySelectorAll('input[type="file"]').forEach((input, index) => {
      input.addEventListener('change', function(e) {
        const file = e.target.files[0];
        if (file) {
          const reader = new FileReader();
          reader.onload = function(event) {
            document.querySelectorAll('.editable-img')[index].src = event.target.result;
          };
          reader.readAsDataURL(file);
        }
      });
    });

    function buy(itemName, price) {
      alert(`Thank you for choosing "${itemName}"! You will be redirected to checkout.`);
      window.location.href = 'https://buy.stripe.com/test_dummy_checkout';
    }

    function fakeApplePay(itemName) {
      alert(`Apple Pay clicked for "${itemName}". (This is a demo button!)`);
    }
  </script>
</body>
</html>
