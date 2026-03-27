<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AirVault - Tested AirPods & More</title>

<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&display=swap" rel="stylesheet">

<style>
body {
  font-family: 'Montserrat', sans-serif;
  background: #f5f5f5 url('https://www.transparenttextures.com/patterns/diagonal-noise.png');
  background-size: cover;
  margin: 0;
  padding: 0;
  color: #333;
}
a { color: #1e90ff; text-decoration: none; }

header {
  background: linear-gradient(90deg, #1e1e1e, #000000);
  color: white;
  padding: 25px 0;
  text-align: center;
}
header h1 { margin: 0; font-size: 2.5rem; }
header p { margin: 5px 0 0 0; font-size: 1.1rem; color: #ccc; }

.products {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 30px 20px;
}
.product {
  background: white;
  width: 300px;
  margin: 15px;
  border-radius: 15px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  padding: 20px;
  text-align: center;
  transition: transform 0.3s, box-shadow 0.3s;
  cursor: pointer;
}
.product:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 15px rgba(0,0,0,0.2);
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

/* Cart */
.cart {
  max-width: 800px;
  margin: 20px auto;
  background: #fff;
  border-radius: 12px;
  padding: 15px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}
.cart h2 { text-align: center; margin-bottom: 10px; }
.cart-items { list-style: none; padding: 0; margin: 0; }
.cart-items li { padding: 10px 0; border-bottom: 1px solid #ddd; display: flex; justify-content: space-between; }
.cart-items li:last-child { border-bottom: none; }
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

/* Reviews */
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

footer {
  text-align: center;
  padding: 25px 0;
  background: #222;
  color: #ccc;
  margin-top: 30px;
}

@media (max-width: 650px) {
  .products { flex-direction: column; align-items: center; }
  .product { width: 90%; }
}
</style>
</head>
<body>

<header>
  <h1>AirVault</h1>
  <p>Tested & Cleaned AirPods | DM to Buy</p>
</header>

<div class="products">
  <div class="product" onclick="addToCart('AirPods Gen 2', 65)">
    <img src="https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/MV7N2?wid=200&hei=200&fmt=jpeg&qlt=95&.v=1591634795000" alt="AirPods Gen 2">
    <h2>AirPods Gen 2</h2>
    <p>$65 – Cleaned & Tested</p>
    <button onclick="window.location.href='https://instagram.com/dareal3than_'; event.stopPropagation()">DM to Buy</button>
  </div>
  <div class="product" onclick="addToCart('AirPods Pro', 95)">
    <img src="https://store.storeimages.cdn-apple.com/4668/as-images.apple.com/is/MWP22?wid=200&hei=200&fmt=jpeg&qlt=95&.v=1591634795000" alt="AirPods Pro">
    <h2>AirPods Pro</h2>
    <p>$95 – Refurbished & Tested</p>
    <button onclick="window.location.href='https://instagram.com/dareal3than_'; event.stopPropagation()">DM to Buy</button>
  </div>
</div>

<!-- CART -->
<div class="cart">
  <h2>Shopping Cart</h2>
  <ul class="cart-items" id="cart-items">
    <!-- Cart items appear here -->
  </ul>
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
let cart = [];

function addToCart(name, price) {
  cart.push({name, price});
  updateCart();
}

function updateCart() {
  const cartItems = document.getElementById('cart-items');
  cartItems.innerHTML = '';
  let total = 0;
  cart.forEach((item, index) => {
    total += item.price;
    const li = document.createElement('li');
    li.innerHTML = `${item.name} - $${item.price} <button onclick="removeItem(${index})">Remove</button>`;
    cartItems.appendChild(li);
  });
  document.getElementById('cart-total').textContent = total;
}

function removeItem(index) {
  cart.splice(index, 1);
  updateCart();
}

function clearCart() {
  cart = [];
  updateCart();
}

// Reviews
function addReview() {
  const name = document.getElementById('reviewer-name').value.trim();
  const stars = document.getElementById('review-stars').value;
  const text = document.getElementById('review-text').value.trim();

  if (!name || !stars || !text) {
    alert('Please fill in all fields.');
    return;
  }

  const reviewList = document.getElementById('review-list');
  const reviewDiv = document.createElement('div');
  reviewDiv.className = 'review';
  reviewDiv.innerHTML = `
    <p><strong>${name}</strong> ${stars}</p>
    <p>"${text}"</p>
    <button class="delete-btn" onclick="deleteReview(this)">Delete</button>
  `;

  reviewList.prepend(reviewDiv);
  document.getElementById('reviewer-name').value = '';
  document.getElementById('review-stars').value = '';
  document.getElementById('review-text').value = '';
}

function deleteReview(button) {
  const review = button.parentElement;
  review.remove();
}
</script>

</body>
</html>
