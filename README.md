<!DOCTYPE html>
<html>
<head>
  <title>AirVault</title>
  <style>
    body { font-family: Arial; text-align: center; }

    .product { margin: 20px; }

    .checkout-btn {
      background: green;
      color: white;
      padding: 12px;
      border: none;
      cursor: pointer;
      border-radius: 8px;
    }

    #admin-login, #admin-dashboard {
      margin-top: 30px;
    }
  </style>
</head>
<body>

<h1>AirVault</h1>

<!-- PRODUCTS -->
<div class="product">
  <h2>AirPods Gen 2</h2>
  <p>$65</p>
  <button onclick="addToCart('AirPods Gen 2', 65)">Add to Cart</button>
</div>

<div class="product">
  <h2>AirPods Pro</h2>
  <p>$95</p>
  <button onclick="addToCart('AirPods Pro', 95)">Add to Cart</button>
</div>

<!-- CART -->
<h2>Cart</h2>
<ul id="cart-items"></ul>
<p>Total: $<span id="cart-total">0</span></p>

<!-- CUSTOMER FORM -->
<h3>Shipping Info</h3>
<input id="cust-name" placeholder="Full Name"><br>
<input id="cust-address" placeholder="Address"><br>
<input id="cust-city" placeholder="City"><br>
<input id="cust-zip" placeholder="ZIP"><br>

<!-- DELIVERY -->
<h3>Delivery</h3>
<select id="delivery-option">
  <option value="0">Free (5–7 days) - $0</option>
  <option value="5">Standard (3–5 days) - $5</option>
  <option value="10">Express (1–2 days) - $10</option>
</select>

<br><br>
<button class="checkout-btn" onclick="checkout()">Checkout</button>

<!-- ADMIN LOGIN -->
<div id="admin-login" style="display:none;">
  <h2>Admin Login</h2>
  <input type="password" id="admin-password">
  <button onclick="loginAdmin()">Login</button>
</div>

<!-- ADMIN DASHBOARD -->
<div id="admin-dashboard" style="display:none;">
  <h2>Sales Dashboard</h2>
  <p>Total: $<span id="total-revenue">0</span></p>
  <ul id="sales-list"></ul>
  <button onclick="logoutAdmin()">Logout</button>
</div>

<script>
// CART
let cart = [];
let sales = JSON.parse(localStorage.getItem("sales")) || [];

// ADD TO CART
function addToCart(name, price) {
  cart.push({name, price});
  updateCart();
}

// UPDATE CART
function updateCart() {
  const list = document.getElementById("cart-items");
  const totalEl = document.getElementById("cart-total");

  list.innerHTML = "";
  let total = 0;

  cart.forEach(item => {
    total += item.price;
    const li = document.createElement("li");
    li.textContent = item.name + " - $" + item.price;
    list.appendChild(li);
  });

  totalEl.textContent = total;
}

// CHECKOUT
function checkout() {
  if (cart.length === 0) return alert("Cart is empty");

  const name = document.getElementById("cust-name").value;
  const address = document.getElementById("cust-address").value;
  const city = document.getElementById("cust-city").value;
  const zip = document.getElementById("cust-zip").value;

  if (!name || !address || !city || !zip) {
    return alert("Fill all fields");
  }

  const delivery = parseFloat(document.getElementById("delivery-option").value);

  let total = delivery;
  cart.forEach(i => total += i.price);

  const order = { name, address, city, zip, items: cart, total };

  localStorage.setItem("lastOrder", JSON.stringify(order));
  sales.push(order);
  localStorage.setItem("sales", JSON.stringify(sales));

  cart = [];
  updateCart();

  window.location.href = "confirmation.html";
}

// ADMIN LOGIN
function loginAdmin() {
  const pass = document.getElementById("admin-password").value;

  if (pass === "airvault123") {
    document.getElementById("admin-login").style.display = "none";
    document.getElementById("admin-dashboard").style.display = "block";
    updateSalesDashboard();
  } else {
    alert("Wrong password");
  }
}

function logoutAdmin() {
  document.getElementById("admin-login").style.display = "block";
  document.getElementById("admin-dashboard").style.display = "none";
}

// SHOW ADMIN ONLY WITH ?admin=true
if (window.location.search === "?admin=true") {
  document.getElementById("admin-login").style.display = "block";
}

// SALES DASHBOARD
function updateSalesDashboard() {
  const list = document.getElementById("sales-list");
  const totalEl = document.getElementById("total-revenue");

  list.innerHTML = "";
  let total = 0;

  sales.forEach(order => {
    total += order.total;

    const li = document.createElement("li");
    li.textContent = order.name + " - $" + order.total;
    list.appendChild(li);
  });

  totalEl.textContent = total;
}
</script>

</body>
</html>
