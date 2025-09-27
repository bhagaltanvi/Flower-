<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Flower World — Flowers, Gifts & Booking</title>

  <!-- ====== Styles (Single-file for simplicity) ====== -->
  <style>
    :root{
      --accent:#E84A5F;
      --accent-2:#FFB86B;
      --bg:#fffaf6;
      --muted:#666;
      --card-shadow: 0 8px 20px rgba(0,0,0,0.08);
      --glass: rgba(255,255,255,0.6);
      --max-width: 1200px;
      --radius:14px;
      --transition: 300ms cubic-bezier(.22,.9,.36,1);
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      /* background-image: url(back.jpg);
      background-repeat: no-repeat;
      background-size: cover; */
      font-family: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background: radial-gradient(circle at 10% 10%, #fffaf0 0%, #f6f2f9 40%, #f1f7fb 100%);
      color:#222;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      background-color: pink;
      line-height:1.5;
    }

    a{color:inherit; text-decoration:none}

    /* Layout */
    .container{
      width:calc(100% - 40px);
      max-width:var(--max-width);
      margin:0 auto;
      padding:30px 0;
    }

    header{
      position:sticky;
      top:0;
      z-index:999;
      backdrop-filter: blur(6px);
      background: linear-gradient(180deg, rgba(255,255,255,0.75), rgba(255,255,255,0.5));
      border-bottom: 1px solid rgba(0,0,0,0.04);
    }
    .nav-bar{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:16px;
      padding:10px 20px;
      max-width:var(--max-width);
      margin:0 auto;
      background-color: pink;
    }
    .brand{
      display:flex; align-items:center; gap:12px;
    }
    .logo{
      width:52px;height:52px;border-radius:12px;
      background:linear-gradient(135deg,var(--accent),var(--accent-2));
      display:flex;align-items:center;justify-content:center;color:white;font-weight:700;
      box-shadow: 0 6px 18px rgba(232,74,95,0.18);
      transform:translateZ(0);
    }
    .brand h1{font-size:18px;margin:0}
    nav ul{display:flex;gap:18px;list-style:none;margin:0;padding:0;align-items:center}
    nav ul li a{padding:8px 12px;border-radius:10px;transition:var(--transition); font-weight:600; color:var(--muted)}
    nav ul li a:hover{color:var(--accent); background:rgba(232,74,95,0.06)}

    .cta{
      display:flex; gap:10px; align-items:center;
    }
    .btn{
      background:var(--accent);
      color:white;padding:10px 14px;border-radius:10px;border:none;cursor:pointer;
      font-weight:700; box-shadow: 0 8px 20px rgba(232,74,95,0.12);
      transition:transform 220ms ease, box-shadow 220ms ease;
    }
    .btn:hover{transform:translateY(-3px)}
    .secondary{
      background:transparent;border:1px solid rgba(0,0,0,0.06); color:var(--muted); font-weight:600;padding:8px 12px;border-radius:10px;
    }

    /* Hero */
    .hero{
      display:grid;
      grid-template-columns: 1fr 420px;
      gap:28px;
      align-items:center;
      padding:42px 20px;
      max-width:var(--max-width);
      margin:30px auto;
      background-color: pink;
    }
    .hero-card{
      background:linear-gradient(180deg, rgba(255,255,255,0.85), rgba(255,255,255,0.9));
      border-radius:18px;
      padding:28px;
      box-shadow: var(--card-shadow);
      transform:translateY(0);
      transition:var(--transition);
    }
    .hero-card:hover{transform:translateY(-6px)}
    .hero h2{font-size:36px;margin:0 0 12px 0}
    .hero p{color:var(--muted); margin-bottom:18px}

    .hero-features{display:flex; gap:12px; flex-wrap:wrap}
    .feature{
      background:var(--glass);
      padding:10px 12px;border-radius:10px;font-weight:600;color:var(--muted);
      box-shadow: 0 2px 10px rgba(0,0,0,0.04); backdrop-filter: blur(4px);
    }

    /* Search & quick booking mini */
    .hero-side{
      padding:18px;
    }
    .search{
      display:flex; gap:10px; align-items:center;
      background-color: pink;
      margin-bottom:14px;
    }
    .search input, .search select{
      padding:12px; border-radius:10px; border:1px solid rgba(0,0,0,0.06); flex:1; font-size:14px;
      transition:box-shadow 200ms;
    }
    .search input:focus, .search select:focus{box-shadow: 0 8px 20px rgba(232,74,95,0.08); outline:none; border-color:var(--accent)}
    .quick-book{background:linear-gradient(135deg,var(--accent),var(--accent-2)); color:pink;padding:12px;border-radius:10px;text-align:center;font-weight:700}

    /* Sections */
    section{padding:40px 0}
    .section-title{display:flex;align-items:center;gap:12px;margin-bottom:18px}
    .section-title h3{margin:0;font-size:24px}
    .section-sub{color:var(--muted); font-size:14px}

    /* Cards / Services */
    .services-grid{display:grid; grid-template-columns:repeat(3, 1fr); gap:18px}
    .service-card{background:pink;border-radius:12px;padding:18px; box-shadow:var(--card-shadow); transition:transform 350ms var(--transition);}
    .service-card:hover{transform:translateY(-8px)}
    .service-card h4{margin:8px 0}

    /* Shop */
    .products-grid{display:grid; grid-template-columns:repeat(4,1fr); gap:18px}
    .product{
      background:pink;border-radius:12px;padding:10px; overflow:hidden; box-shadow:var(--card-shadow);
      display:flex; flex-direction:column; gap:10px; transition:transform 280ms;
    }
    .product img{width:100%; height:180px; object-fit:cover; border-radius:8px}
    .product .info{padding:8px 6px; flex:1}
    .price{font-weight:800;color:var(--accent); font-size:18px}
    .product .actions{display:flex; gap:8px}
    .add-btn{flex:1; padding:10px;border-radius:10px;background:var(--accent);color:pink;border:none;cursor:pointer}
    .fav{padding:8px;border-radius:10px;border:1px solid rgba(0,0,0,0.06); background:transparent}

    /* Cart floating */
    .cart-floating{
      position:fixed; right:18px; bottom:18px; z-index:999;
    }
    .cart-floating button{
      background:linear-gradient(135deg,var(--accent),#c83b51); color:pink; border:none;padding:12px 16px;border-radius:12px; box-shadow:0 10px 30px rgba(232,74,95,0.18);
      cursor:pointer;font-weight:800;
    }

    /* Booking form / Contact */
    .form-card{background:pink;border-radius:12px;padding:20px; box-shadow:var(--card-shadow);}
    .form-row{display:flex; gap:12px; margin-bottom:12px}
    .form-row .col{flex:1}
    input[type="text"], input[type="email"], input[type="tel"], input[type="date"], select, textarea{
      width:100%; padding:12px;border-radius:10px;border:1px solid rgba(0,0,0,0.06); font-size:14px;
    }
    textarea{min-height:120px; resize:vertical}

    /* Gallery */
    .gallery-grid{display:grid; grid-template-columns: repeat(4,1fr); gap:10px}
    .gallery-grid img{width:100%; height:160px; object-fit:cover; border-radius:10px; cursor:pointer; transition: transform 240ms ease}
    .gallery-grid img:hover{transform:scale(1.04)}

    /* Lightbox */
    .lightbox{
      position:fixed; inset:0; display:none; align-items:center; justify-content:center; background:rgba(0,0,0,0.6); z-index:2000;
    }
    .lightbox.active{display:flex}
    .lightbox img{max-width:90%; max-height:80%; border-radius:12px; box-shadow:0 20px 60px rgba(0,0,0,0.5)}

    /* Footer */
    footer{padding:26px 0; background:linear-gradient(180deg, pink, rgba(0,0,0,0.01)); margin-top:40px}
    .footer-grid{display:flex; gap:20px; justify-content:space-between; align-items:flex-start; flex-wrap:wrap}
    .small{font-size:13px;color:var(--muted)}

    /* Responsive */
    @media (max-width:1000px){
      .hero{grid-template-columns:1fr; padding:18px; gap:16px}
      .products-grid{grid-template-columns:repeat(2,1fr)}
      .gallery-grid{grid-template-columns:repeat(3,1fr)}
      .services-grid{grid-template-columns:repeat(2,1fr)}
    }
    @media (max-width:700px){
      nav ul{display:none}
      .hamburger{display:block; cursor:pointer}
      .products-grid{grid-template-columns:1fr}
      .gallery-grid{grid-template-columns:repeat(2,1fr)}
      .brand h1{font-size:16px}
      .hero h2{font-size:28px}
    }

    /* Mobile nav overlay */
    .mobile-nav{
      position:fixed; inset:0; background:rgba(0,0,0,0.4); display:none; z-index:999;
      align-items:center; justify-content:center;
    }
    .mobile-nav.active{display:flex}
    .mobile-panel{background:palevioletred; padding:24px;border-radius:12px; width:90%; max-width:420px}
    .mobile-panel ul{display:flex; flex-direction:column; gap:12px; list-style:none; padding:0; margin:0}

    /* subtle animations */
    .fade-up{opacity:0; transform:translateY(10px); transition:opacity 500ms, transform 500ms}
    .fade-up.visible{opacity:1; transform:translateY(0)}
  </style>
</head>
<body background="back.jpg">

  <!-- HEADER / NAV -->
  <header>
    <div class="nav-bar">
      <div class="brand">
        <div class="logo">FW</div>
        <div>
          <h1>Flower World</h1>
          <div class="small">Fresh blooms • Same day delivery</div>
        </div>
      </div>

      <nav>
        <ul>
          <li><a href="#home" data-link="home">Home</a></li>
          <li><a href="#about" data-link="about">About</a></li>
          <li><a href="#services" data-link="services">Services</a></li>
          <li><a href="#shop" data-link="shop">Shop</a></li>
          <li><a href="#gallery" data-link="gallery">Gallery</a></li>
          <li><a href="#booking" data-link="booking">Booking</a></li>
          <li><a href="#contact" data-link="contact">Contact</a></li>
        </ul>
      </nav>

      <div class="cta">
        <button class="secondary" id="view-cart-btn">Cart (<span id="cart-count">0</span>)</button>
        <button class="btn" id="book-now-cta">Book Now</button>
        <div class="hamburger" style="display:none; margin-left:8px;">
          <svg id="hamb" xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="#333" stroke-width="2"><path d="M3 12h18M3 6h18M3 18h18"/></svg>
        </div>
      </div>
    </div>
  </header>

  <!-- Mobile nav -->
  <div class="mobile-nav" id="mobileNav">
    <div class="mobile-panel">
      <button id="closeMobile" style="float:right;border:none;background:transparent;font-size:18px;cursor:pointer">✕</button>
      <ul>
        <li><a href="#home" data-link="home" class="mobile-link">Home</a></li>
        <li><a href="#about" data-link="about" class="mobile-link">About</a></li>
        <li><a href="#services" data-link="services" class="mobile-link">Services</a></li>
        <li><a href="#shop" data-link="shop" class="mobile-link">Shop</a></li>
        <li><a href="#gallery" data-link="gallery" class="mobile-link">Gallery</a></li>
        <li><a href="#booking" data-link="booking" class="mobile-link">Booking</a></li>
        <li><a href="#contact" data-link="contact" class="mobile-link">Contact</a></li>
      </ul>
    </div>
  </div>

  <!-- MAIN CONTENT -->
  <main>

    <!-- HERO -->
    <div class="hero" id="home">
      <div class="hero-card">
        <h2>Beautiful flowers delivered fast — <span style="color:var(--accent)">same day</span> in your city</h2>
        <p>Gifts, Bouquets, Event decoration, Corporate orders. Freshness guaranteed. Customize bouquets and book online.</p>

        <div class="hero-features">
          <div class="feature">Free delivery above ₹999</div>
          <div class="feature">24/7 Support</div>
          <div class="feature">Money-back guarantee</div>
          <div class="feature">Custom arrangements</div>
        </div>

        <div style="margin-top:18px; display:flex; gap:10px;">
          <button class="btn" onclick="scrollToSection('shop')">Shop Flowers</button>
          <button class="secondary" onclick="scrollToSection('gallery')">View Gallery</button>
        </div>

        <div style="margin-top:18px; color:var(--muted); font-size:14px">
          Popular: <strong>Roses</strong>, <strong>Lilies</strong>, <strong>Orchids</strong>, <strong>Anniversary Bouquets</strong>.
        </div>
      </div>

      <!-- right side quick card -->
      <div class="hero-card hero-side">
        <div style="margin-bottom:12px">
          <div style="font-weight:800; font-size:16px; margin-bottom:6px">Quick Search</div>
          <div class="search">
            <input id="searchInput" placeholder="Type flower name, occasion..." />
            <select id="filterOccasion">
              <option value="">Occasion</option>
              <option>Birthday</option>
              <option>Anniversary</option>
              <option>Wedding</option>
              <option>Sympathy</option>
            </select>
          </div>
          <button class="btn" onclick="searchProducts()">Search</button>
        </div>

        <div style="margin-top:18px">
          <div style="font-weight:800; margin-bottom:8px">Quick Booking</div>
          <div style="font-size:13px; color:var(--muted); margin-bottom:8px">Book a delivery slot in minutes</div>
          <div style="display:flex; gap:8px; margin-bottom:8px">
            <input type="date" id="bookDate" style="flex:1" />
            <input type="time" id="bookTime" style="flex:1" />
          </div>
          <button class="quick-book" onclick="prefillBooking()">Reserve Slot</button>
        </div>
      </div>
    </div>

    <!-- ABOUT -->
    <section id="about" class="container fade-up">
      <div class="section-title">
        <h3>About Flower World</h3>
      </div>
      <div style="display:flex; gap:20px; align-items:center; flex-wrap:wrap;">
        <div style="flex:1; min-width:260px">
          <div class="form-card">
            <h4>हमारी कहानी</h4>
            <p class="small">Flower World 2010 में शुरू हुआ — हमारा मकसद है हर छोटे और बड़े मौके को फूलों से खास बनाना। हम ताजी डिलीवरी, आकर्षक arrangements, और कस्टम ऑर्डर देते हैं।</p>
            <ul style="margin-top:10px; color:var(--muted)">
              <li>Local farms से direct sourcing</li>
              <li>Experienced florists</li>
              <li>Same day delivery in major cities</li>
            </ul>
          </div>
        </div>

        <div style="flex:1; min-width:260px">
          <div style="display:grid; gap:10px; grid-template-columns:repeat(2,1fr)">
            <img src="webroses5.jpg" style="width:100%; height:150px; object-fit:cover; border-radius:12px" alt="flowers"/>
            <img src="webroses8.jpg" style="width:100%; height:150px; object-fit:cover; border-radius:12px" alt="bouquet"/>
            <img src="webroses6.jpg" style="width:100%; height:150px; object-fit:cover; border-radius:12px" alt="florist"/>
            <img src="webrosese4.jpg" style="width:100%; height:150px; object-fit:cover; border-radius:12px" alt="gift"/>
          </div>
        </div>
      </div>
    </section>

    <!-- SERVICES -->
    <section id="services" class="container fade-up">
      <div class="section-title">
        <h3>Our Services</h3>
        <div class="section-sub">Event decoration, Corporate gifting, Custom bouquets and more</div>
      </div>

      <div class="services-grid">
        <div class="service-card">
          <h4>Event Decoration</h4>
          <p class="small">Weddings, birthdays, corporate events — full floral decor & installation.</p>
        </div>
        <div class="service-card">
          <h4>Custom Bouquets</h4>
          <p class="small">Design your bouquet — choose flowers, wrap style and card message.</p>
        </div>
        <div class="service-card">
          <h4>Corporate Gifting</h4>
          <p class="small">Bulk orders and corporate accounts — recurring deliveries available.</p>
        </div>
        <div class="service-card">
          <h4>Subscription</h4>
          <p class="small">Weekly/Monthly fresh flowers delivered to homes and offices.</p>
        </div>
        <div class="service-card">
          <h4>Same Day Delivery</h4>
          <p class="small">Order before cut-off and we deliver same day in many cities.</p>
        </div>
        <div class="service-card">
          <h4>Workshops</h4>
          <p class="small">Flower arranging workshops for groups and corporates.</p>
        </div>
      </div>
    </section>

    <!-- SHOP -->
    <section id="shop" class="container fade-up">
      <div class="section-title">
        <h3>Shop — Popular Arrangements</h3>
        <div class="section-sub">Click Add to Cart to build your order. Cart persists locally.</div>
      </div>

      <!-- products -->
      <div id="products" class="products-grid" style="margin-bottom:18px">
        <!-- Products inserted via JS -->
      </div>

      <div style="margin-top:18px; display:flex; justify-content:center;">
        <button class="btn" onclick="loadMoreProducts()">Load more</button>
      </div>
    </section>

    <!-- GALLERY -->
    <section id="gallery" class="container fade-up">
      <div class="section-title">
        <h3>Gallery</h3>
        <div class="section-sub">Our recent events & flower art</div>
      </div>

      <div class="gallery-grid" id="galleryGrid">
        <!-- images via JS -->
      </div>
    </section>

    <!-- Booking -->
    <section id="booking" class="container fade-up">
      <div class="section-title"><h3>Booking / Delivery</h3><div class="section-sub">Reserve a slot or request custom arrangement</div></div>

      <div style="display:flex; gap:18px; flex-wrap:wrap;">
        <div style="flex:1; min-width:300px">
          <div class="form-card">
            <h4>Book a Delivery</h4>
            <div class="form-row">
              <div class="col"><input id="custName" type="text" placeholder="Your name" /></div>
              <div class="col"><input id="custPhone" type="tel" placeholder="Phone" /></div>
            </div>
            <div class="form-row">
              <div class="col"><input id="custEmail" type="email" placeholder="Email" /></div>
              <div class="col"><input id="deliverDate" type="date" /></div>
            </div>
            <div class="form-row">
              <div class="col"><input id="deliverTime" type="time" /></div>
              <div class="col">
                <select id="deliverType">
                  <option value="">Select type</option>
                  <option value="standard">Standard Delivery</option>
                  <option value="same-day">Same Day</option>
                  <option value="event">Event Setup</option>
                </select>
              </div>
            </div>
            <div style="margin-bottom:12px">
              <textarea id="deliverNote" placeholder="Notes for florist (message to include, directions...)"></textarea>
            </div>
            <div style="display:flex; gap:10px">
              <button class="btn" onclick="submitBooking()">Submit Booking</button>
              <button class="secondary" onclick="clearBooking()">Clear</button>
            </div>
            <div id="bookingStatus" style="margin-top:10px;color:green;font-weight:700"></div>
          </div>
        </div>

        <div style="flex:1; min-width:300px">
          <div class="form-card">
            <h4>Why book with us?</h4>
            <ul class="small" style="color:var(--muted)">
              <li>Realtime tracking of your delivery</li>
              <li>Pre-check call from the florist</li>
              <li>Easy reschedule & refunds</li>
            </ul>

            <div style="margin-top:12px;">
              <h4 style="margin-bottom:8px">Popular combos</h4>
              <div style="display:flex; gap:10px; flex-wrap:wrap">
                <div style="background:#fff4f6;padding:10px;border-radius:10px">Roses + Teddy</div>
                <div style="background:#fff9ec;padding:10px;border-radius:10px">Anniversary Special</div>
                <div style="background:#f3fff6;padding:10px;border-radius:10px">Premium Orchids</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact" class="container fade-up">
      <div class="section-title"><h3>Contact Us</h3><div class="section-sub">We are here to help — call or message</div></div>

      <div style="display:flex; gap:18px; flex-wrap:wrap;">
        <div style="flex:1; min-width:300px">
          <div class="form-card">
            <h4>Send a message</h4>
            <div class="form-row"><div class="col"><input id="msgName" placeholder="Name" /></div><div class="col"><input id="msgEmail" placeholder="Email" /></div></div>
            <div style="margin-bottom:12px"><textarea id="msgText" placeholder="Your message"></textarea></div>
            <div style="display:flex; gap:10px"><button class="btn" onclick="sendMessage()">Send Message</button><button class="secondary" onclick="clearMessage()">Clear</button></div>
            <div id="msgStatus" style="margin-top:10px;color:green;font-weight:700"></div>
          </div>
        </div>

        <div style="flex:1; min-width:300px">
          <div class="form-card">
            <h4>Visit / Call</h4>
            <p class="small">Flower World HQ<br/>123 Flower Lane, YourCity</p>
            <p style="margin-top:8px"><strong>Phone:</strong> +91 98765 43210<br/><strong>Email:</strong> hello@flowerworld.example</p>
            <div style="margin-top:12px">
              <iframe title="map" style="width:100%; min-height:180px; border-radius:12px; border:0"
                src="https://maps.google.com/maps?q=flower%20shop&t=&z=13&ie=UTF8&iwloc=&output=embed"></iframe>
            </div>
          </div>
        </div>
      </div>

    </section>

  </main>

  <!-- Lightbox -->
  <div class="lightbox" id="lightbox">
    <img id="lightboxImg" src="" alt=""/>
  </div>

  <!-- Cart Floating -->
  <div class="cart-floating" id="cartFloat">
    <button onclick="openCart()">🛒 View Cart (<span id="cartFloatCount">0</span>)</button>
  </div>

  <!-- Cart Modal (simple) -->
  <div id="cartModal" style="position:fixed; right:20px; bottom:80px; width:340px; background:white; border-radius:12px; box-shadow:0 30px 80px rgba(0,0,0,0.2); padding:12px; display:none; z-index:3000">
    <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:10px">
      <strong>Your Cart</strong>
      <button onclick="closeCart()" style="border:none;background:transparent;cursor:pointer">✕</button>
    </div>
    <div id="cartItems" style="max-height:300px; overflow:auto; gap:8px; display:flex; flex-direction:column"></div>
    <div style="display:flex; gap:8px; margin-top:10px; align-items:center; justify-content:space-between">
      <div><strong>Total:</strong> ₹<span id="cartTotal">0</span></div>
      <div style="display:flex; gap:8px">
        <button class="secondary" onclick="clearCart()">Clear</button>
        <button class="btn" onclick="checkout()">Checkout</button>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <footer>
    <div class="container">
      <div class="footer-grid">
        <div>
          <h4>Flower World</h4>
          <div class="small">Freshness guaranteed • Delivery across major cities</div>
        </div>
        <div class="small">© 2025 Flower World — All rights reserved</div>
        <div>
          <div class="small">Follow us:</div>
          <div style="display:flex; gap:8px; margin-top:6px">
            <a class="small" href="#">Instagram</a>
            <a class="small" href="#">Facebook</a>
            <a class="small" href="#">X</a>
          </div>
        </div>
      </div>
    </div>
  </footer>

  <!-- ====== JavaScript ====== -->
  <script>
    /* ===== Sample product data ===== */
    const PRODUCTS = [
      { id: 'p1', title:'Red Roses Bouquet', price:799, img:'webroses5.jpg' },
      { id: 'p2', title:'Pastel Mixed Bouquet', price:999, img:'webrosese4.jpg' },
      { id: 'p3', title:'Orchid Premium', price:1299, img:'webroses7.jpg' },
      { id: 'p4', title:'Sunflower Delight', price:599, img:'webrosee1.jpg' },
      { id: 'p5', title:'Anniversary Special', price:1499, img:'webroses6.jpg' },
      { id: 'p6', title:'Mixed Seasonal', price:699, img:'webroses2.jpg' },
      { id: 'p7', title:'Sympathy Wreath', price:2199, img:'webrosese3.jpg' },
      { id: 'p8', title:'Mini Gift Hamper', price:499, img:'webroses8.jpg' }
      // { id: 'p9', title:'Mixed Seasonal', price:699, img:'https://source.unsplash.com/600x400/?flower,bouquet' },
      // { id: 'p10', title:'Sympathy Wreath', price:2199, img:'https://source.unsplash.com/600x400/?wreath,flowers' },
    ];
    let productsToShow = 6;

    /* ===== Cart using localStorage ===== */
    const CART_KEY = 'flower_cart_v1';
    let cart = JSON.parse(localStorage.getItem(CART_KEY) || '{}');

    function saveCart(){ localStorage.setItem(CART_KEY, JSON.stringify(cart)); updateCartUI(); }

    function addToCart(id){
      if(!cart[id]) cart[id]=0;
      cart[id] += 1;
      saveCart();
      animateAdd(id);
    }

    function removeFromCart(id){
      if(cart[id]) { delete cart[id]; saveCart(); }
    }

    function changeQty(id, delta){
      if(!cart[id]) return;
      cart[id] += delta;
      if(cart[id] <= 0) delete cart[id];
      saveCart();
    }

    function cartCount(){
      return Object.values(cart).reduce((s,n)=>s+n,0);
    }

    function cartTotal(){
      let total=0;
      for(let id in cart){
        const p = PRODUCTS.find(x=>x.id===id);
        if(p) total += p.price * cart[id];
      }
      return total;
    }

    function updateCartUI(){
      document.getElementById('cart-count').innerText = cartCount();
      document.getElementById('cartFloatCount').innerText = cartCount();
      document.getElementById('cartTotal').innerText = cartTotal();
      const container = document.getElementById('cartItems');
      container.innerHTML = '';
      if(cartCount()===0){
        container.innerHTML = '<div class="small">Cart is empty</div>';
        return;
      }
      for(let id in cart){
        const p = PRODUCTS.find(x=>x.id===id);
        if(!p) continue;
        const row = document.createElement('div');
        row.style.display='flex';
        row.style.alignItems='center';
        row.style.justifyContent='space-between';
        row.style.gap='8px';
        row.innerHTML = `
          <div style="display:flex; gap:12px; align-items:center">
            <img src="${p.img}" style="width:60px; height:44px; object-fit:cover; border-radius:8px" />
            <div>
              <div style="font-weight:700">${p.title}</div>
              <div class="small">₹${p.price} x ${cart[id]}</div>
            </div>
          </div>
          <div style="display:flex; gap:6px; align-items:center">
            <button class="secondary" onclick="changeQty('${id}', -1)">-</button>
            <button class="secondary" onclick="changeQty('${id}', 1)">+</button>
            <button class="secondary" onclick="removeFromCart('${id}')">Remove</button>
          </div>
        `;
        container.appendChild(row);
      }
    }

    /* ===== Render products and gallery ===== */
    function renderProducts(){
      const el = document.getElementById('products');
      el.innerHTML = '';
      PRODUCTS.slice(0, productsToShow).forEach(p=>{
        const card = document.createElement('div');
        card.className='product fade-up';
        card.innerHTML = `
          <img src="${p.img}" alt="${p.title}" />
          <div class="info">
            <div style="display:flex; justify-content:space-between; align-items:center">
              <h4 style="margin:0">${p.title}</h4>
              <div class="price">₹${p.price}</div>
            </div>
            <p class="small">Freshly arranged by our florists. Free card message included.</p>
          </div>
          <div class="actions" style="padding:0 6px 12px 6px;">
            <button class="add-btn" onclick="addToCart('${p.id}')">Add to Cart</button>
            <button class="fav secondary" onclick="previewProduct('${p.id}')">Quick view</button>
          </div>
        `;
        el.appendChild(card);
      });
      revealOnScroll(); updateCartUI();
    }

    function loadMoreProducts(){
      productsToShow = Math.min(PRODUCTS.length, productsToShow + 4);
      renderProducts();
    }

    /* Gallery */
    const GALLERY = [
      'shop4.jpg',
      'shop5.jpg',
      'shop6.jpg',
      'shop7.jpg',
      'shop8.jpg',
      'shop9.jpg',
      'shop10.jpg',
      'shop11.jpg'
    ];
    function renderGallery(){
      const grid = document.getElementById('galleryGrid');
      grid.innerHTML = '';
      GALLERY.forEach((src, i) => {
        const img = document.createElement('img');
        img.src = src;
        img.alt = 'Gallery image';
        img.addEventListener('click',()=>openLightbox(src));
        grid.appendChild(img);
      });
    }

    /* Lightbox */
    function openLightbox(src){ document.getElementById('lightboxImg').src = src; document.getElementById('lightbox').classList.add('active'); }
    function closeLightbox(){ document.getElementById('lightbox').classList.remove('active'); }

    document.getElementById('lightbox').addEventListener('click', closeLightbox);

    /* Quick preview */
    function previewProduct(id){
      const p = PRODUCTS.find(x=>x.id===id);
      if(!p) return;
      openLightbox(p.img);
    }

    /* Search */
    function searchProducts(){
      const q = document.getElementById('searchInput').value.toLowerCase();
      const occ = document.getElementById('filterOccasion').value.toLowerCase();
      if(!q && !occ){ renderProducts(); return; }
      const filtered = PRODUCTS.filter(p => p.title.toLowerCase().includes(q) || (occ && p.title.toLowerCase().includes(occ)));
      const el = document.getElementById('products');
      el.innerHTML = '';
      filtered.forEach(p=>{
        const card = document.createElement('div');
        card.className='product';
        card.innerHTML = `<img src="${p.img}" alt="${p.title}"><div class="info"><div style="display:flex;justify-content:space-between"><h4>${p.title}</h4><div class="price">₹${p.price}</div></div><p class="small">Fresh bouquet</p></div><div class="actions" style="padding:0 6px 12px 6px;"><button class="add-btn" onclick="addToCart('${p.id}')">Add to Cart</button><button class="fav secondary" onclick="previewProduct('${p.id}')">Quick view</button></div>`;
        el.appendChild(card);
      });
    }

    /* Booking form handling (local mock) */
    function prefillBooking(){
      const d = document.getElementById('bookDate').value || new Date().toISOString().slice(0,10);
      document.getElementById('deliverDate').value = d;
      document.getElementById('deliverTime').value = document.getElementById('bookTime').value || '12:00';
      document.getElementById('bookingStatus').innerText = 'Slot prefilling done. Please complete details and submit.';
      window.scrollTo({top:document.getElementById('booking').offsetTop - 80, behavior:'smooth'});
    }

    function submitBooking(){
      const name = document.getElementById('custName').value.trim();
      const phone = document.getElementById('custPhone').value.trim();
      const date = document.getElementById('deliverDate').value;
      if(!name || !phone || !date){ alert('कृपया नाम, फोन और तारीख भरें'); return; }
      // Simulate success
      document.getElementById('bookingStatus').innerText = 'Booking successful! Confirmation sent to your phone/email.';
      // reset lightly
      setTimeout(()=>{ document.getElementById('bookingStatus').innerText = ''; }, 5500);
    }
    function clearBooking(){
      ['custName','custPhone','custEmail','deliverDate','deliverTime','deliverNote'].forEach(id=>document.getElementById(id).value='');
      document.getElementById('bookingStatus').innerText = '';
    }

    /* Contact message */
    function sendMessage(){
      const name = document.getElementById('msgName').value.trim();
      const email = document.getElementById('msgEmail').value.trim();
      const text = document.getElementById('msgText').value.trim();
      if(!name || !email || !text){ alert('Please fill out all Fields'); return; }
      document.getElementById('msgStatus').innerText = 'Message sent! We will reply soon.';
      setTimeout(()=>{ document.getElementById('msgStatus').innerText = ''; }, 5000);
    }
    function clearMessage(){ ['msgName','msgEmail','msgText'].forEach(id=>document.getElementById(id).value=''); document.getElementById('msgStatus').innerText=''; }

    /* Cart modal open/close */
    function openCart(){ document.getElementById('cartModal').style.display='block'; updateCartUI(); }
    function closeCart(){ document.getElementById('cartModal').style.display='none'; }
    function clearCart(){ cart = {}; saveCart(); }
    function checkout(){
      if(cartCount()===0){ alert('Cart is empty'); return; }
      alert('Checkout simulated. Thank you! Order confirmed.');
      cart = {}; saveCart();
      closeCart();
    }

    /* small animation for add to cart (pulse) */
    function animateAdd(id){
      const el = document.querySelector(`.product img[src*="${id ? '' : ''}"]`);
      // simple notification
      const c = document.createElement('div');
      c.style.position='fixed'; c.style.right='20px'; c.style.bottom='20px';
      c.style.background='var(--accent)'; c.style.color='white'; c.style.padding='8px 12px'; c.style.borderRadius='10px';
      c.style.boxShadow='0 10px 30px rgba(232,74,95,0.18)'; c.innerText = 'Added to cart';
      document.body.appendChild(c);
      setTimeout(()=>c.style.opacity=0,1200);
      setTimeout(()=>document.body.removeChild(c),1700);
    }

    /* Smooth scrolling helper */
    function scrollToSection(id){
      const el = document.getElementById(id);
      if(!el) return;
      window.scrollTo({ top: el.offsetTop - 70, behavior: 'smooth' });
    }

    /* Navigation links */
    document.querySelectorAll('a[data-link]').forEach(a=>{
      a.addEventListener('click', function(e){
        e.preventDefault();
        const id = this.getAttribute('data-link');
        scrollToSection(id);
      });
    });

    /* Mobile nav toggles */
    document.querySelector('.hamburger').addEventListener('click', ()=>document.getElementById('mobileNav').classList.add('active'));
    document.getElementById('closeMobile').addEventListener('click', ()=>document.getElementById('mobileNav').classList.remove('active'));
    document.querySelectorAll('.mobile-link').forEach(a=>a.addEventListener('click', (e)=>{ document.getElementById('mobileNav').classList.remove('active'); }));

    /* Show/hide hamburger based on width */
    function adaptNav(){
      const hamb = document.querySelector('.hamburger');
      const navul = document.querySelector('nav ul');
      if(window.innerWidth <= 700){ hamb.style.display='block'; navul.style.display='none'; } else{ hamb.style.display='none'; navul.style.display='flex'; }
    }
    window.addEventListener('resize', adaptNav);
    adaptNav();

    /* Reveal on scroll */
    function revealOnScroll(){
      document.querySelectorAll('.fade-up').forEach(el=>{
        const rect = el.getBoundingClientRect();
        if(rect.top < window.innerHeight - 60){
          el.classList.add('visible');
        }
      });
      document.querySelectorAll('.product.fade-up').forEach((el,i)=>{
        setTimeout(()=>el.classList.add('visible'), 80*i);
      });
    }
    window.addEventListener('scroll', revealOnScroll);

    /* Light initializations */
    renderProducts();
    renderGallery();
    updateCartUI();
    revealOnScroll();

    /* click outside cart to close */
    window.addEventListener('click', (e)=>{
      const modal = document.getElementById('cartModal');
      if(modal.style.display==='block' && !modal.contains(e.target) && !e.target.closest('.cart-floating')){ closeCart(); }
    });

    /* small keyboard support */
    window.addEventListener('keydown', (e)=>{ if(e.key==='Escape'){ closeLightbox(); closeCart(); document.getElementById('mobileNav').classList.remove('active'); } });

  </script>
</body>
</html>
