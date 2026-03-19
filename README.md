# Mobile-covers
Bhandhilki_ Accessories<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CoverUp | Search & Shop</title>
    <style>
        body { font-family: 'Segoe UI', sans-serif; margin: 0; background: #f4f4f4; }
        header { background: #333; color: white; padding: 1rem; text-align: center; }
        
        .container { max-width: 1000px; margin: 20px auto; padding: 0 20px; }

        /* Search Bar Style */
        .search-container {
            text-align: center;
            margin-bottom: 20px;
        }

        #searchInput {
            width: 80%;
            max-width: 400px;
            padding: 12px 20px;
            border-radius: 25px;
            border: 1px solid #ccc;
            font-size: 1rem;
            outline: none;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        /* Filter Buttons */
        .filter-container { text-align: center; margin-bottom: 30px; }
        .filter-btn {
            background: white; border: 2px solid #333; padding: 8px 20px;
            margin: 5px; cursor: pointer; border-radius: 20px; font-weight: bold;
        }
        .filter-btn.active { background: #333; color: white; }

        /* Grid & Cards */
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }
        .card {
            background: white; padding: 15px; border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1); text-align: center;
        }
        .hidden { display: none !important; }

        .card img { width: 100%; height: 200px; object-fit: contain; }
        .buy-btn { background: #e67e22; color: white; border: none; padding: 10px; width: 100%; border-radius: 5px; cursor: pointer; margin-top: 10px;}
    </style>
</head>
<body>

<header><h1>CoverUp Shop</h1></header>

<div class="container">
    
    <div class="search-container">
        <input type="text" id="searchInput" onkeyup="searchProducts()" placeholder="Search for your phone model (e.g. iPhone 15)...">
    </div>

    <div class="filter-container">
        <button class="filter-btn active" onclick="filterSelection('all', this)">All</button>
        <button class="filter-btn" onclick="filterSelection('iphone', this)">iPhone</button>
        <button class="filter-btn" onclick="filterSelection('samsung', this)">Samsung</button>
    </div>

    <div class="product-grid" id="productGrid">
        <div class="card" data-category="iphone">
            <img src="https://via.placeholder.com/200?text=iPhone+15" alt="iPhone">
            <h3 class="product-title">iPhone 15 Pro Max Clear</h3>
            <p>$19.00</p>
            <button class="buy-btn" onclick="buyNow('iPhone 15 Pro Max Clear')">Buy Now</button>
        </div>

        <div class="card" data-category="samsung">
            <img src="https://via.placeholder.com/200?text=S23+Ultra" alt="Samsung">
            <h3 class="product-title">Samsung S23 Ultra Tough</h3>
            <p>$22.00</p>
            <button class="buy-btn" onclick="buyNow('Samsung S23 Ultra Tough')">Buy Now</button>
        </div>

        <div class="card" data-category="iphone">
            <img src="https://via.placeholder.com/200?text=iPhone+13" alt="iPhone">
            <h3 class="product-title">iPhone 13 Silicone Blue</h3>
            <p>$15.00</p>
            <button class="buy-btn" onclick="buyNow('iPhone 13 Silicone Blue')">Buy Now</button>
        </div>
    </div>
</div>

<script>
    // SEARCH LOGIC
    function searchProducts() {
        let input = document.getElementById('searchInput').value.toLowerCase();
        let cards = document.querySelectorAll('.card');

        cards.forEach(card => {
            let title = card.querySelector('.product-title').innerText.toLowerCase();
            if (title.includes(input)) {
                card.classList.remove('hidden');
            } else {
                card.classList.add('hidden');
            }
        });
    }

    // FILTER LOGIC
    function filterSelection(category, btnElement) {
        // Clear search input when filtering to avoid confusion
        document.getElementById('searchInput').value = "";
        
        let cards = document.querySelectorAll('.card');
        let buttons = document.querySelectorAll('.filter-btn');

        buttons.forEach(btn => btn.classList.remove('active'));
        btnElement.classList.add('active');

        cards.forEach(card => {
            const itemCategory = card.getAttribute('data-category');
            if (category === 'all' || itemCategory === category) {
                card.classList.remove('hidden');
            } else {
                card.classList.add('hidden');
            }
        });
    }

    function buyNow(productName) {
        const phoneNumber = "1234567890";
        window.open(`https://wa.me/${phoneNumber}?text=Hi, I want the ${productName}`, '_blank');
    }
</script>

</body>
</html>
