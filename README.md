<!DOCTYPE html>
<html>
<head>
<title>AirVault</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">

<style>
body {
  margin: 0;
  font-family: 'Inter', sans-serif;
  background: linear-gradient(135deg, #e0e7ff, #f5f5f7);
  color: #1d1d1f;
}

header {
  padding: 20px;
  text-align: center;
  font-size: 1.8rem;
  font-weight: 600;
}

.products {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px,1fr));
  gap: 30px;
  padding: 40px;
}

.product {
  background: white;
  border-radius: 25px;
  padding: 20px;
  text-align: center;
  box-shadow: 0 10px 25px rgba(0,0,0,0.1);
  transition: .3s;
}

.product:hover {
  transform: translateY(-6px);
}

.product img {
  width: 180px;
}

.price {
  font-weight: 600;
  margin: 10px 0;
}

button {
  background: black;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 20px;
  cursor: pointer;
}

.cart {
  position: fixed;
  right: 20px;
  bottom: 20px;
  background: white;
  padding: 15px;
  border-radius: 15px;
  width: 250px;
}

.modal {
  display:none;
  position:fixed;
  top:0;left:0;
  width:100%;height:100%;
  background:rgba(0,0,0,0.6);
}

.modal-content {
  background:white;
  margin:5% auto;
  padding:25px;
  border-radius:20px;
  width:320px;
  text-align:center;
}

input, select, textarea {
  width: 90%;
  padding: 10px;
  margin: 5px;
  border-radius: 10px;
  border: 1px solid #ddd;
}

.review-box {
  margin: 30px;
  background: white;
  padding: 20px;
  border-radius: 20px;
}

.review {
  border-bottom: 1px solid #ddd;
  padding: 10px;
  position: relative;
}

.delete-btn {
  position: absolute;
  right: 10px;
  top: 10px;
  background: red;
  color: white;
  border: none;
  padding: 3px 8px;
  border-radius: 5px;
}
</style>
</head>

<body>

<header>AirVault</header>

<div class="products">

<div class="product">
<img src="https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MV7N2?wid=400">
<h2>AirPods Gen 2</h2>
<p>Cleaned & tested, great sound.</p>
<div class="price">$45</div>
<button onclick="addToCart('AirPods Gen 2',45)">Add</button>
</div>

<div class="product">
<img src="https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MWP22?wid=400">
<h2>AirPods Pro</h2>
<p>Refurbished with noise canceling.</p>
<div class="price">$65</div>
<button onclick="addToCart('AirPods Pro',65)">Add</button>
</div>

</div>

<!-- CART -->
<div class="cart">
<h3>Cart</h3>
<ul id="cart-items"></ul>
<p>Total: $<span id="total">0</span></p>
<button onclick="openCheckout()">Checkout</button>
</div>

<!-- CHECKOUT -->
<div class="modal" id="checkout-modal">
<div class="modal-content">

<h2>Checkout</h2>

<input id="name" placeholder="Name">
<input id="address" placeholder="Address">

<select id="delivery">
<option value="0">Free Shipping</option>
<option value="5">Standard +$5</option>
<option value="10">Express +$10</option>
</select>

<button onclick="placeOrder()">Place Order</button>
<button onclick="closeCheckout()">Cancel</button>

</div>
</div>

<!-- REVIEWS -->
<div class="review-box">
<h2>Reviews</h2>

<select id="rating">
<option>⭐</option>
<option>⭐⭐</option>
<option>⭐⭐⭐</option>
<option>⭐⭐⭐⭐</option>
<option>⭐⭐⭐⭐⭐</option>
</select>

<textarea id="review-text" placeholder="Write review..."></textarea>
<button onclick="addReview()">Submit</button>

<div id="reviews"></div>
</div>

<script>
let cart = [];

function addToCart(name, price){
  cart.push({name, price});
  updateCart();
}

function updateCart(){
  let list = document.getElementById("cart-items");
  let total = 0;
  list.innerHTML = "";

  cart.forEach(item=>{
    total += item.price;
    let li = document.createElement("li");
    li.textContent = item.name + " - $" + item.price;
    list.appendChild(li);
  });

  document.getElementById("total").innerText = total;
}

function openCheckout(){
  document.getElementById("checkout-modal").style.display="block";
}

function closeCheckout(){
  document.getElementById("checkout-modal").style.display="none";
}

function placeOrder(){
  let delivery = parseFloat(document.getElementById("delivery").value);
  let total = delivery;

  cart.forEach(i=> total+=i.price);

  alert("Order placed! Total: $" + total);

  cart=[];
  updateCart();
  closeCheckout();
}

// REVIEWS
function addReview(){
  let text = document.getElementById("review-text").value;
  let stars = document.getElementById("rating").value;

  if(!text) return alert("Write something");

  let div = document.createElement("div");
  div.className="review";
  div.innerHTML = stars + "<br>" + text +
  "<button class='delete-btn' onclick='this.parentElement.remove()'>X</button>";

  document.getElementById("reviews").prepend(div);
  document.getElementById("review-text").value="";
}
</script>

</body>
</html>
