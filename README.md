<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{{ page_title }}</title>
  <link rel="stylesheet" href="{{ 'styles.css' | asset_url }}">
</head>
<body>
  <header class="header">
    <div class="container">
      <h1 class="logo">{{ shop.name }}</h1>
      <nav class="nav">
        <ul>
          <li><a href="/">Home</a></li>
          <li><a href="/collections/all">Shop</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <main class="main">
    <div class="container">
      <article class="product">
        <div class="product-images" id="product-gallery">
          {% for image in product.images %}
            <img src="{{ image.src | img_url: '600x600' }}" alt="{{ product.title }}">
          {% endfor %}
        </div>
        <div class="product-details">
          <h2 class="product-title">{{ product.title }}</h2>
          <p class="product-description">{{ product.description }}</p>
          <p class="product-price">$ {{ product.price }}</p>
          <form action="/cart/add" method="post" class="product-form">
            <input type="hidden" name="id" value="{{ product.variants.first.id }}">
            <button type="submit" class="add-to-cart-btn">Add to Cart</button>
          </form>
        </div>
      </article>

      <section class="additional-info">
        <h2>Additional Information</h2>
        <p>This is where you can add more details about your product or any other relevant information.</p>
      </section>
    </div>
  </main>

  <footer class="footer">
    <div class="container">
      <p class="copyright">&copy; {{ 'now' | date: '%Y' }} {{ shop.name }}</p>
    </div>
  </footer>

  <script src="{{ 'main.js' | asset_url }}"></script>
</body>
</html>
