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
