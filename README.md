<!DOCTYPE html>
<html>
<head>
  <title>AirVault</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">

  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: 'Inter', sans-serif;
      background: #f5f5f7;
      color: #1d1d1f;
    }

    /* NAVBAR */
    header {
      position: sticky;
      top: 0;
      backdrop-filter: blur(10px);
      background: rgba(255,255,255,0.7);
      padding: 15px 30px;
      font-weight: 600;
      font-size: 1.5rem;
      border-bottom: 1px solid #ddd;
    }

    /* PRODUCTS */
    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 30px;
      padding: 60px;
    }

    .product {
      background: white;
      border-radius: 24px;
      padding: 25px;
      text-align: center;
      box-shadow: 0 10px 25px rgba(0,0,0,0.08);
      transition: 0.3s;
    }

    .product:hover {
      transform: translateY(-8px) scale(1.02);
    }

    .product img {
      width: 180px;
      margin-bottom: 20px;
    }

    .price {
      font-size: 1.2rem;
      font-weight: 600;
      margin: 10px 0;
    }

    button {
      background: black;
      color: white;
      border: none;
      padding: 12px 22px;
      border-radius: 30px;
      cursor: pointer;
      font-size: 0.95rem;
      transition: 0.2s;
    }

    button:hover {
      opacity: 0.85;
    }

    /* CART */
    .cart {
      position: fixed;
      right: 20px;
      bottom: 20px;
      background: white;
      padding: 20px;
      border-radius: 20px;
      width: 260px;
      box-shadow: 0 15px 30px rgba(0,0,0,0.15);
    }

    .cart h3 {
      margin-top: 0;
    }

    /* MODAL */
    .modal {
      display: none;
      position: fixed;
      top:0; left:0;
      width:100%; height:100%;
      background: rgba(0,0,0,0.6);
      backdrop-filter: blur(5px);
    }

    .modal-content {
      background: white;
      margin: 5% auto;
      padding: 30px;
      border-radius: 25px;
      width: 350px;
      text-align: center;
      animation: fadeIn 0.3s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px);}
      to { opacity: 1; transform: translateY(0);}
    }

    .carousel img {
      width: 200px;
      margin: 10px 0;
    }

    .arrow {
      cursor: pointer;
      font-size: 24px;
      margin: 10px;
    }
  </style>
</head>

<body>

<header>AirVault</header>

<div class="products">

  <div class="product">
    <img src="https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MV7N2?wid=400">
    <h2>AirPods Gen 2</h2>
    <p>Reliable, clean sound with seamless Apple connection.</p>
    <div class="price">$65</div>
    <button onclick="openModal('AirPods Gen 2',65,'Cleaned & Tested',['https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MV7N2?wid=400','https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MV7N2_AV2?wid=400'])">View</button>
  </div>

  <div class="product">
    <img src="https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MWP22?wid=400">
    <h2>AirPods Pro</h2>
    <p>Noise cancellation with premium immersive audio.</p>
    <div class="price">$95</div>
    <button onclick="openModal('AirPods Pro',95,'Refurbished Pro with ANC',['https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MWP22?wid=400','https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MWP22_AV2?wid=400'])">View</button>
  </div>

</div>

<!-- CART -->
<div class="cart">
  <h3>Cart</h3>
  <ul id="cart-items"></ul>
  <p>Total: $<span id="total">0</span></p>
</div>

<!-- MODAL -->
<div class="modal" id="modal">
  <div class="modal-content">
    <div>
      <span class="arrow" onclick="prev()">⬅</span>
      <img id="modal-img">
      <span class="arrow" onclick="next()">➡</span>
    </div>

    <h2 id="name"></h2>
    <p id="desc"></p>
    <div class="price">$<span id="price"></span></div>

    <button onclick="addToCart()">Add to Cart</button><br><br>
    <button onclick="closeModal()">Close</button>
  </div>
</div>

<script>
let cart = [];
let current = {};
let imgs = [];
let i = 0;

function openModal(name, price, desc, images) {
  current = {name, price};
  imgs = images;
  i = 0;

  document.getElementById("name").innerText = name;
  document.getElementById("desc").innerText = desc;
  document.getElementById("price").innerText = price;
  document.getElementById("modal-img").src = imgs[0];

  document.getElementById("modal").style.display = "block";
}

function closeModal() {
  document.getElementById("modal").style.display = "none";
}

function next() {
  i = (i+1)%imgs.length;
  document.getElementById("modal-img").src = imgs[i];
}

function prev() {
  i = (i-1+imgs.length)%imgs.length;
  document.getElementById("modal-img").src = imgs[i];
}

function addToCart() {
  cart.push(current);
  updateCart();
  closeModal();
}

function updateCart() {
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
</script>

</body>
</html>
