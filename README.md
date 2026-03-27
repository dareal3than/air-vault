<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dareal3than Store - AirPods & Clothing</title>
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&family=Lora&display=swap" rel="stylesheet">
<style>
/* ===== GENERAL STYLES ===== */
body {
  font-family: 'Montserrat', sans-serif;
  background: #f0f2f5;
  margin: 0;
  padding: 0;
  color: #333;
}
a { color: #1e90ff; text-decoration: none; }

/* ===== HERO BANNER ===== */
.hero {
  background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.3)), url('https://images.unsplash.com/photo-1606813909455-3d09fdb1d7b1?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwxMTc3M3wwfDF8c2VhcmNofDF8fGFpcnBvZHN8ZW58MHx8fHwxNjg5Mjc3NjY4&ixlib=rb-4.0.3&q=80&w=1080') no-repeat center center;
  background-size: cover;
  text-align: center;
  padding: 80px 20px;
  color: white;
}
.hero h1 { font-size: 3rem; margin-bottom: 10px; }
.hero p { font-size: 1.2rem; }

/* ===== HEADER ===== */
header {
  background: #111;
  color: white;
  padding: 15px 0;
  text-align: center;
  font-family: 'Montserrat', sans-serif;
}
header h1 { margin: 0; font-size: 2rem; }
header p { margin: 5px 0 0 0; color: #ccc; font-size: 1rem; }

/* ===== PRODUCTS GRID ===== */
.products {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 30px 20px;
}
.product {
  background: white;
  width: 280px;
  margin: 15px;
  border-radius: 15px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  padding: 20px;
  text-align: center;
  transition: transform 0.3s, box-shadow 0.3s;
  cursor: pointer;
}
.product:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.2);
}
.product img {
  width: 150px;
  margin-bottom: 15px;
  border-radius: 15px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
.product h2 { margin: 10px 0; font-size: 1.3rem; }
.product p { font-size: 1rem; margin: 5px 0 15px 0; }
.product button {
  background: black; color: white; border: none; padding: 10px 25px;
  border-radius: 5px; cursor: pointer; font-size: 1rem;
  transition: background 0.3s, transform 0.2s;
}
.product button:hover { background: #1e1e1e; transform: scale(1.05); }

/* ===== MODAL ===== */
.modal {
  display: none; 
  position: fixed; 
  z-index: 1000; 
  left: 0;
  top: 0;
  width: 100%; 
  height: 100%; 
  overflow: auto;
  background-color: rgba(0,0,0,0.7);
}
.modal-content {
  background-color: #fff;
  margin: 5% auto; 
  padding: 20px;
  border-radius: 15px;
  max-width: 550px;
  text-align: center;
  position: relative;
}
.close-modal {
  position: absolute;
  top: 10px; right: 15px;
  font-size: 1.5rem;
  font-weight: bold;
  cursor: pointer;
  color: #333;
}
.close-modal:hover { color: black; }

/* ===== CAROUSEL ===== */
.carousel-container {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 15px;
}
.carousel-container img {
  width: 80px;
  margin: 0 5px;
  border-radius: 10px;
  border: 2px solid transparent;
  cursor: pointer;
  transition: border 0.3s;
}
.carousel-container img.selected { border-color: #1e90ff; }
.carousel-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  font-size: 2rem;
  background: rgba(255,255,255,0.8);
  border-radius: 50%;
  width: 35px; height: 35px;
  line-height: 35px;
  text-align: center;
  cursor: pointer;
}
.carousel-arrow:hover { background: rgba(255,255,255,1); }
.carousel-left { left: -45px; }
.carousel-right { right: -45px; }

/* ===== CART ===== */
.cart {
  max-width: 800px;
  margin: 20px auto;
  background: #fff;
  border-radius: 12px;
  padding: 15px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  position: relative;
}
.cart h2 { text-align: center; margin-bottom: 10px; }
.cart-items { list-style: none; padding: 0; margin: 0; }
.cart-items li { padding: 10px 0; border-bottom: 1px solid #ddd; display: flex; justify-content: space-between; flex-direction: column; }
.cart-items li:last-child { border-bottom: none; }
.cart-items button {
  background: #ff4d4d; color: white; border: none; padding: 5px 10px; border-radius: 5px; margin-top: 5px;
  cursor: pointer;
}
.cart-items button:hover { background: #ff1a1a; }
.clear-cart {
  margin-top: 10px;
  background: red;
  color: white;
  border: none;
  padding: 8px 15px;
  border-radius: 5px;
  cursor: pointer;
}
.clear-cart:hover { background: darkred; }

/* ===== DELIVERY OPTIONS ===== */
.delivery-options {
  margin: 10px 0;
}
.delivery-options select {
  padding: 8px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

/* ===== REVIEWS ===== */
.reviews {
  max-width: 800px;
  margin: 40px auto;
  padding: 20px;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
.reviews h2 { text-align: center; font-size: 2rem; margin-bottom: 20px; }
.review { border-bottom: 1px solid #ddd; padding: 10px 0; position: relative; }
.review:last-child { border-bottom: none; }
.review p { margin: 5px 0; }
.review strong { font-weight: 600; }
.delete-btn {
  position: absolute;
  top: 10px; right: 10px;
  background: #ff4d4d;
  color: white;
  border: none;
  padding: 3px 8px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 0.8rem;
}
.delete-btn:hover { background: #ff1a1a; }

/* Review Form */
.review-form { margin-top: 20px; text-align: center; }
.review-form input, .review-form textarea, .review-form select {
  width: 80%;
  max-width: 400px;
  padding: 8px;
  margin: 5px 0;
  border-radius: 5px;
  border: 1px solid #ccc;
  font-size: 1rem;
}
.review-form button {
  margin-top: 10px;
  padding: 10px 20px;
  font-size: 1rem;
  border: none;
  border-radius: 5px;
  background: black;
  color: white;
  cursor: pointer;
}
.review-form button:hover { background: #1e1e1e; }

/* ===== FOOTER ===== */
footer {
  text-align: center;
  padding: 20px 0;
  background: #222;
  color: #ccc;
  margin-top: 30px;
}
</style>
</head>
<body>

<!-- HERO BANNER -->
<div class="hero">
  <h1>Dareal3than Store</h1>
  <p>Tested AirPods & Trendy Clothing – DM to Buy!</p>
</div>

<!-- HEADER -->
<header>
  <h1>Dareal3than Store</h1>
  <p>Shop AirPods & Clothing | Fast Delivery</p>
</header>

<!-- PRODUCTS -->
<div class="products">
  <div class="product" onclick="openModal('AirPods Gen 2', 65, 'The AirPods 2nd generation features improved sound quality, seamless connectivity, and a new H1 chip for enhanced performance and battery life.', [
    'https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/MV7N2?wid=200&hei=200&fmt=jpeg&qlt=95&.v=1591634795000',
    'https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/MV7N2?wid=400&hei=400&fmt=jpeg&qlt=95&.v=1591634795000'
  ])">
    <img src="https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/MV7N2?wid=200&hei=200&fmt=jpeg&qlt=95&.v=1591634795000" alt="AirPods Gen 2">
    <h2>AirPods Gen 2</h2>
    <p>$65 – Cleaned & Tested</p>
    <button onclick="window.location.href='https://instagram.com/dareal3than_'; event.stopPropagation()">DM to Buy</button>
  </div>

  <div class="product" onclick="openModal('AirPods Pro', 95, 'AirPods Pro are premium wireless in-ear headphones featuring active noise cancellation, transparency mode, and advanced health and audio features.', [
    'https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/MWP22?wid=200&hei=200&fmt=jpeg&qlt=95&.v=1591634795000',
    'https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/MWP22?wid=400&hei=400&fmt=jpeg&qlt=95&.v=1591634795000'
  ])">
    <img src="https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/MWP22?wid=200&hei=200&fmt=jpeg&qlt=95&.v=1591634795000" alt="AirPods Pro">
    <h2>AirPods Pro</h2>
    <p>$95 – Refurbished & Tested</p>
    <button onclick="window.location.href='https://instagram.com/dareal3than_'; event.stopPropagation()">DM to Buy</button>
  </div>
</div>

<!-- MODAL -->
<div id="product-modal" class="modal">
  <div class="modal-content">
    <span class="close-modal" onclick="closeModal()">&times;</span>
    <h2 id="modal-name"></h2>
    <div class="carousel-container">
      <span class="carousel-arrow carousel-left" onclick="prevImage()">&#10094;</span>
      <img id="modal-main-img" src="" alt="">
      <span class="carousel-arrow carousel-right" onclick="nextImage()">&#10095;</span>
    </div>
    <div class="carousel-thumbnails" id="modal-carousel"></div>
    <p id="modal-description"></p>
    <p><strong>Price: $<span id="modal-price"></span></strong></p>
    <div class="delivery-options">
      <label for="delivery">Choose Delivery Option:</label>
      <select id="delivery">
        <option value="Pickup">Pickup</option>
        <option value="Standard">Standard Delivery</option>
        <option value="Express">Express Delivery</option>
      </select>
    </div>
    <button onclick="addToCartFromModal()">Add to Cart</button>
  </div>
</div>

<!-- CART -->
<div class="cart">
  <h2>Shopping Cart</h2>
  <ul class="cart-items" id="cart-items"></ul>
  <p>Total: $<span id="cart-total">0</span></p>
  <button class="clear-cart" onclick="clearCart()">Clear Cart</button>
</div>

<!-- REVIEWS -->
<div class="reviews">
  <h2>Customer Reviews</h2>
  <div id="review-list"></div>
  <div class="review-form">
    <h3>Submit Your Review</h3>
    <input type="text" id="reviewer-name" placeholder="Your Name" required><br>
    <select id="review-stars" required>
      <option value="">Select Rating</option>
      <option value="⭐">⭐</option>
      <option value="⭐⭐">⭐⭐</option>
      <option value="⭐⭐⭐">⭐⭐⭐</option>
      <option value="⭐⭐⭐⭐">⭐⭐⭐⭐</option>
      <option value="⭐⭐⭐⭐⭐">⭐⭐⭐⭐⭐</option>
    </select><br>
    <textarea id="review-text" placeholder="Your review..." rows="3" required></textarea><br>
    <button onclick="addReview()">Submit Review</button>
  </div>
</div>

<footer>
  <p>Follow us on <a href="https://instagram.com/dareal3than_" target="_blank">Instagram @dareal3than_</a></p>
</footer>

<script>
/* ===== CART LOGIC ===== */
let cart = [];
let modalProduct = {};
let modalImages = [];
let currentImageIndex = 0;

function openModal(name, price, description, images) {
  modalProduct = {name, price, description};
  modalImages = images;
  currentImageIndex = 0;

  document.getElementById('modal-name').textContent = name;
  document.getElementById('modal-price').textContent = price;
  document.getElementById('modal-description').textContent = description;
  document.getElementById('modal-main-img').src = modalImages[0];

  buildThumbnails();
  document.getElementById('product-modal').style.display = 'block';
}

function buildThumbnails() {
  const carousel = document.getElementById('modal-carousel');
  carousel.innerHTML = '';
  modalImages.forEach((img, index) => {
    const thumb = document.createElement('img');
    thumb.src = img;
    thumb.className = index === 0 ? 'selected' : '';
    thumb.onclick = () => { currentImageIndex = index; updateMainImage(); };
    carousel.appendChild(thumb);
  });
}

function updateMainImage() {
  document.getElementById('modal-main-img').src = modalImages[currentImageIndex];
  document.querySelectorAll('#modal-carousel img').forEach((img, i) => {
    img.classList.toggle('selected', i === currentImageIndex);
  });
}

function nextImage() { currentImageIndex = (currentImageIndex + 1) % modalImages.length; updateMainImage(); }
function prevImage() { currentImageIndex = (currentImageIndex - 1 + modalImages.length) % modalImages.length; updateMainImage(); }
function closeModal() { document.getElementById('product-modal').style.display = 'none'; }

function addToCartFromModal() {
  const delivery = document.getElementById('delivery').value;
  cart.push({...modalProduct, delivery});
  updateCart();
  closeModal();
}

function updateCart() {
  const cartItems = document.getElementById('cart-items');
  cartItems.innerHTML = '';
  let total = 0;
  cart.forEach((item, index) => {
    total += item.price;
    const li = document.createElement('li');
    li.innerHTML = `<strong>${item.name}</strong> - $${item.price}<br>${item.description}<br>Delivery: ${item.delivery} <button onclick="removeItem(${index})">Remove</button>`;
    cartItems.appendChild(li);
  });
  document.getElementById('cart-total').textContent = total;
}

function removeItem(index) { cart.splice(index, 1); updateCart(); }
function clearCart() { cart = []; updateCart(); }

/* ===== REVIEWS ===== */
function addReview() {
  const name = document.getElementById('reviewer-name').value.trim();
  const stars = document.getElementById('review-stars').value;
  const text = document.getElementById('review-text').value.trim();
  if (!name || !stars || !text) { alert('Please fill in all fields.'); return; }

  const reviewList = document.getElementById('review-list');
  const reviewDiv = document.createElement('div');
  reviewDiv.className = 'review';
  reviewDiv.innerHTML = `<p><strong>${name}</strong> ${stars}</p><p>"${text}"</p><button class="delete-btn" onclick="deleteReview(this)">Delete</button>`;
  reviewList.prepend(reviewDiv);

  document.getElementById('reviewer-name').value = '';
  document.getElementById('review-stars').value =
