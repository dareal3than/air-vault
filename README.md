<!DOCTYPE html>
<html>
<head>
  <title>AirVault</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&display=swap" rel="stylesheet">

  <style>
    body {
      font-family: 'Montserrat', sans-serif;
      margin: 0;
      background: #f5f5f7;
      color: #1d1d1f;
    }

    header {
      background: white;
      padding: 20px;
      text-align: center;
      font-size: 1.8rem;
      font-weight: 600;
      box-shadow: 0 2px 5px rgba(0,0,0,0.05);
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 25px;
      padding: 40px;
    }

    .product {
      background: white;
      border-radius: 18px;
      padding: 20px;
      text-align: center;
      box-shadow: 0 8px 20px rgba(0,0,0,0.08);
      transition: 0.3s;
    }

    .product:hover {
      transform: translateY(-5px);
    }

    .product img {
      width: 150px;
      margin-bottom: 15px;
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
      border-radius: 12px;
      width: 250px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    }

    /* MODAL */
    .modal {
      display: none;
      position: fixed;
      top:0; left:0;
      width:100%; height:100%;
      background: rgba(0,0,0,0.6);
    }

    .modal-content {
      background: white;
      margin: 5% auto;
      padding: 25px;
      border-radius: 20px;
      width: 320px;
      text-align: center;
    }

    .carousel img {
      width: 180px;
      margin: 10px;
    }

    .arrow {
      cursor: pointer;
      font-size: 22px;
      padding: 10px;
    }
  </style>
</head>

<body>

<header>AirVault</header>

<div class="products">

  <div class="product">
    <img src="https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MV7N2?wid=400&hei=400&fmt=jpeg">
    <h2>AirPods Gen 2</h2>
    <p>Cleaned, tested, and ready to use. Reliable battery and smooth Bluetooth connection.</p>
    <p><strong>$65</strong></p>
    <button onclick="openModal('AirPods Gen 2',65,'Cleaned & Tested AirPods with great sound quality',['https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MV7N2?wid=400','https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MV7N2_AV2?wid=400'])">View</button>
  </div>

  <div class="product">
    <img src="https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MWP22?wid=400&hei=400&fmt=jpeg">
    <h2>AirPods Pro</h2>
    <p>Refurbished premium AirPods with noise cancellation and immersive sound.</p>
    <p><strong>$95</strong></p>
    <button onclick="openModal('AirPods Pro',95,'Refurbished AirPods Pro with ANC',['https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MWP22?wid=400','https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MWP22_AV2?wid=400'])">View</button>
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
    <p>$<span id="price"></span></p>

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
