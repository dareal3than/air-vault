<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AirVault - Tested AirPods</title>
  
  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600&display=swap" rel="stylesheet">

  <style>
    /* General Styles */
    body {
      font-family: 'Montserrat', sans-serif;
      background: #f5f5f5 url('https://www.transparenttextures.com/patterns/diagonal-noise.png');
      background-size: cover;
      margin: 0;
      padding: 0;
      color: #333;
    }

    /* Header */
    header {
      background: linear-gradient(90deg, #1e1e1e, #000000);
      color: white;
      padding: 25px 0;
      text-align: center;
    }
    header h1 {
      margin: 0;
      font-size: 2.5rem;
    }
    header p {
      margin: 5px 0 0 0;
      font-size: 1.1rem;
      color: #ccc;
    }

    /* Products Grid */
    .products {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin: 30px 20px;
    }

    /* Product Card */
    .product {
      background: white;
      width: 300px;
      margin: 15px;
      border-radius: 15px;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
      padding: 20px;
      text-align: center;
      transition: transform 0.3s, box-shadow 0.3s;
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
    .product h2 {
      margin: 10px 0;
      font-size: 1.3rem;
    }
    .product p {
      font-size: 1rem;
      margin: 5px 0 15px 0;
    }

    /* Buttons */
    .product button {
      background: black;
      color: white;
      border: none;
      padding: 10px 25px;
      border-radius: 5px;
      cursor: pointer;
      font-size: 1rem;
      transition: background 0.3s, transform 0.2s;
    }
    .product button:hover {
      background: #1e1e1e;
      transform: scale(1.05);
    }

    /* Footer */
    footer {
      text-align: center;
      padding: 25px 0;
      background: #222;
      color: #ccc;
      margin-top: 30px;
    }
    footer a {
      color: #1e90ff;
      text-decoration: none;
    }

    /* Responsive */
    @media (max-width: 650px) {
      .products {
        flex-direction: column;
        align-items: center;
      }
      .product {
        width: 90%;
      }
    }

  </style>
</head>
<body>

  <!-- Header -->
  <header>
    <h1>AirVault</h1>
    <p>Tested & Cleaned AirPods | DM to Buy</p>
  </header>

  <!-- Products -->
  <div class="products">
    <div class="product">
      <img src="https://via.placeholder.com/150" alt="AirPods Gen 2" loading="lazy">
      <h2>AirPods Gen 2</h2>
      <p>$65 – Cleaned & Tested</p>
      <button onclick="window.location.href='https://instagram.com/Dareal3than_'" aria-label="DM AirVault on Instagram to buy AirPods Gen 2">
        DM to Buy
      </button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/150" alt="AirPods Pro" loading="lazy">
      <h2>AirPods Pro</h2>
      <p>$95 – Refurbished & Tested</p>
      <button onclick="window.location.href='https://instagram.com/Dareal3than_'" aria-label="DM AirVault on Instagram to buy AirPods Pro">
        DM to Buy
      </button>
    </div>
  </div>

  <!-- Footer -->
  <footer>
    <p>Follow us on <a href="https://instagram.com/Dareal3than_" target="_blank">Instagram @AirVault</a></p>
  </footer>

</body>
</html>
