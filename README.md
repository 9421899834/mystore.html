# mystore.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E-Commerce Website</title>
    <link rel="stylesheet" href="styles.css"> <!-- External CSS -->
</head>
<body>
    <header>
        <div class="logo">Store Logo</div>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#shop">Shop</a></li>
                <li><a href="#categories">Categories</a></li>
                <li><a href="#account">Account</a></li>
            </ul>
        </nav>
        <div class="search-cart">
            <input type="text" placeholder="Search products...">
            <button>Cart (0)</button>
        </div>
    </header>

    <main>
        <section id="home">
            <div class="hero">Hero Banner</div>
            <div class="featured-products">Featured Products</div>
        </section>

        <section id="shop">
            <div class="filters">Filters</div>
            <div class="product-grid">Product Listings</div>
        </section>

        <section id="product-detail" style="display:none;">
            <div class="product-images">Images</div>
            <div class="product-info">Details</div>
        </section>

        <section id="cart" style="display:none;">
            <div class="cart-items">Items</div>
            <div class="cart-total">Total</div>
        </section>

        <section id="checkout" style="display:none;">
            <form>Checkout Form</form>
        </section>

        <section id="account" style="display:none;">
            <div class="profile">User Profile</div>
        </section>
    </main>

    <footer>
        <div class="links">Policies & Links</div>
        <div class="social">Social Media</div>
    </footer>

    <script src="script.js"></script> <!-- External JS -->
</body>
</html>
/* Updated styles for better look and feel */
* { margin: 0; padding: 0; box-sizing: border-box; }
body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; line-height: 1.6; color: #333; background: linear-gradient(135deg, #f4f4f4 0%, #e9ecef 100%); }
header { background: linear-gradient(90deg, #333 0%, #555 100%); color: #fff; padding: 1rem; text-align: center; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
nav { background: #444; padding: 0.5rem; }
nav ul { list-style: none; display: flex; justify-content: center; }
nav ul li { margin: 0 1rem; }
nav ul li a { color: #fff; text-decoration: none; transition: color 0.3s; }
nav ul li a:hover { color: #28a745; }
main { padding: 2rem; max-width: 1200px; margin: 0 auto; }
.products { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1.5rem; }
.product { background: #fff; border: 1px solid #ddd; padding: 1.5rem; text-align: center; border-radius: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); transition: transform 0.3s, box-shadow 0.3s; }
.product:hover { transform: translateY(-5px); box-shadow: 0 8px 16px rgba(0,0,0,0.2); }
.product img { max-width: 100%; height: 200px; object-fit: cover; border-radius: 5px; }
.product h3 { margin: 0.5rem 0; font-weight: bold; }
.product p { margin: 0.5rem 0; }
button { background: linear-gradient(45deg, #28a745, #20c997); color: #fff; border: none; padding: 0.75rem 1.5rem; cursor: pointer; border-radius: 25px; transition: background 0.3s, transform 0.2s; font-weight: bold; }
button:hover { background: linear-gradient(45deg, #218838, #17a2b8); transform: scale(1.05); }
.cart { position: fixed; right: 0; top: 0; width: 350px; height: 100%; background: #fff; border-left: 1px solid #ddd; padding: 1rem; overflow-y: auto; transform: translateX(100%); transition: transform 0.3s ease; box-shadow: -2px 0 10px rgba(0,0,0,0.1); }
.cart.open { transform: translateX(0); }
.cart-item { display: flex; justify-content: space-between; margin-bottom: 1rem; padding: 0.5rem; background: #f8f9fa; border-radius: 5px; }
.modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); justify-content: center; align-items: center; animation: fadeIn 0.3s; }
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
.modal-content { background: #fff; padding: 2rem; border-radius: 10px; max-width: 500px; width: 90%; box-shadow: 0 10px 30px rgba(0,0,0,0.3); }
.checkout { display: none; }
footer { background: #333; color: #fff; text-align: center; padding: 1rem; margin-top: 2rem; }
@media (max-width: 768px) { .cart { width: 100%; } .products { grid-template-columns: 1fr; } }



const express = require('express');
const bodyParser = require('body-parser');
const app = express();
const port = 3000;

// Middleware
app.use(bodyParser.json());
app.use(express.static('.')); // Serve static files

// In-memory storage for demo (use a DB in production)
let orders = [];

// Handle order submission
app.post('/submit-order', (req, res) => {
    const { quantity, name, email, address } = req.body;
    const total = (quantity * 10.00).toFixed(2);
    orders.push({ quantity, name, email, address, total });
    res.json({ message: `Order submitted! Total: $${total}. We'll process it soon.` });
});

app.listen(port, () => console.log(`Server running on http://localhost:${port}`));
