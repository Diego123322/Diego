<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Chic modas</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
  <style>
    body
{
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Inter', sans-serif;
    }

    body {
      background-color: #000000;
      color: #333;
    }

    header {
      background-color: #0d6efd;
      color: white;
      padding: 20px 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
    }

    header h1 {
      font-size: 1.8rem;
    }

    .search-filter {
      display: flex;
      gap: 10px;
      margin-top: 10px;
      flex-wrap: wrap;
    }

    .search-filter input,
    .search-filter select {
      padding: 8px 12px;
      border-radius: 6px;
      border: none;
      outline: none;
    }

    .container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 30px;
      max-width: 1300px;
      margin: auto;
    }

    .product {
      background-color: white;
      border-radius: 15px;
      padding: 20px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
      text-align: center;
      transition: transform 0.3s;
    }

    .product:hover {
      transform: translateY(-5px);
    }

    .product img {
      max-width: 100%;
      height: auto;
      border-radius: 10px;
    }

    .product h3 {
      margin: 15px 0 10px;
    }

    .product p {
      color: #666;
      font-size: 0.95rem;
    }

    .product button {
      background-color: #198754;
      color: white;
      border: none;
      padding: 10px 16px;
      margin-top: 10px;
      border-radius: 6px;
      cursor: pointer;
      font-weight: bold;
    }

    .product button:hover {
      background-color: #157347;
    }

    .cart {
      position: fixed;
      top: 20px;
      right: 20px;
      background-color: white;
      border: 1px solid #ddd;
      padding: 15px;
      border-radius: 10px;
      width: 250px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }

    .cart h4 {
      margin-bottom: 10px;
    }

    .cart ul {
      list-style: none;
      padding: 0;
      max-height: 200px;
      overflow-y: auto;
    }

    .cart ul li {
      margin-bottom: 6px;
    }

    @media (max-width: 768px) {
      .cart {
        position: static;
        margin: 20px auto;
      }
    }
  </style>
</head>
<body>
  <header>
    <div>
      <h1>Loja Moderna</h1>
      <div class="search-filter">
        <input type="text" id="searchInput" placeholder="Buscar produto..." oninput="filterProducts()">
        <select id="filterSelect" onchange="filterProducts()">
          <option value="">Todos</option>
          <option value="promo">Promoções</option>
        </select>
      </div>
    </div>
    <div class="cart" id="cart">
      <h4>Carrinho</h4>
      <ul id="cartItems"></ul>
    </div>
  </header>

  <div class="container" id="productList">
    <div class="product" data-name="camiseta" data-category="promo">
      <img src="https://via.placeholder.com/250x150" alt="Produto 1">
      <h3>Camiseta</h3>
      <p>Linda camiseta de algodão.</p>
      <button onclick="addToCart('Camiseta')">Adicionar ao Carrinho</button>
    </div>
    <div class="product" data-name="tenis" data-category="">
      <img src="https://via.placeholder.com/250x150" alt="Produto 2">
      <h3>Tênis</h3>
      <p>Super confortável e estiloso.</p>
      <button onclick="addToCart('Tênis')">Adicionar ao Carrinho</button>
    </div>
    <div class="product" data-name="mochila" data-category="promo">
      <img src="https://via.placeholder.com/250x150" alt="Produto 3">
      <h3>Mochila</h3>
      <p>Espaçosa e resistente.</p>
      <button onclick="addToCart('Mochila')">Adicionar ao Carrinho</button>
    </div>
  </div>

  <script>
    const cartItems = document.getElementById('cartItems');

    function addToCart(itemName) {
      const li = document.createElement('li');
      li.textContent = itemName;
      cartItems.appendChild(li);
    }

    function filterProducts() {
      const searchValue = document.getElementById('searchInput').value.toLowerCase();
      const filterValue = document.getElementById('filterSelect').value;
      const products = document.querySelectorAll('.product');

      products.forEach(product => {
        const name = product.getAttribute('data-name');
        const category = product.getAttribute('data-category');

        const matchesSearch = name.includes(searchValue);
        const matchesFilter = filterValue === '' || category === filterValue;

        if (matchesSearch && matchesFilter) {
          product.style.display = 'block';
        } else {
          product.style.display = 'none';
        }
      });
    }
  </script>
</body>
</html>
