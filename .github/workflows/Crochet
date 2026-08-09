<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Crochet Shop — Handmade, Stitch by Stitch</title>

<!-- Fonts: Fraunces for handmade warmth in headings, Work Sans for clean body text -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,400;0,9..144,500;0,9..144,600;0,9..144,700;1,9..144,500&family=Work+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">

<!-- EmailJS SDK (free tier) -->
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>

<style>
  :root{
    --bg: #F6F1E8;
    --bg-soft: #EFE7D8;
    --ink: #2B241E;
    --ink-soft: #6b6154;
    --plum: #6B2545;
    --plum-dark: #4E1B33;
    --mustard: #D9A441;
    --green: #4A6741;
    --card: #FFFFFF;
    --line: #E2D8C4;
    --radius: 18px;
    --shadow: 0 10px 30px rgba(43,36,30,0.10);
  }

  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:var(--bg);
    color:var(--ink);
    font-family:'Work Sans', sans-serif;
    line-height:1.5;
    -webkit-font-smoothing:antialiased;
  }
  h1,h2,h3{
    font-family:'Fraunces', serif;
    margin:0;
    font-weight:600;
    color:var(--ink);
  }
  img{max-width:100%;display:block;}
  button{font-family:inherit;cursor:pointer;border:none;}
  a{color:inherit;}

  /* ---------- Yarn stitch divider (signature motif) ---------- */
  .stitch-divider{
    height:22px;
    width:100%;
    background-image: radial-gradient(circle at 11px 0px, transparent 9px, var(--bg) 10px);
    background-size: 22px 22px;
    background-repeat: repeat-x;
    background-position: top center;
  }
  .stitch-divider.flip{ transform: rotate(180deg); }
  .stitch-divider.on-plum{ background-image: radial-gradient(circle at 11px 0px, transparent 9px, var(--plum-dark) 10px); }

  /* ---------- Header ---------- */
  header{
    position:sticky; top:0; z-index:40;
    background:rgba(246,241,232,0.92);
    backdrop-filter:blur(6px);
    border-bottom:1px solid var(--line);
  }
  .nav-wrap{
    max-width:1100px; margin:0 auto;
    display:flex; align-items:center; justify-content:space-between;
    padding:14px 20px;
  }
  .brand{display:flex; align-items:center; gap:10px;}
  .brand-mark{
    width:38px; height:38px; border-radius:50%;
    background:conic-gradient(from 200deg, var(--mustard), var(--plum), var(--green), var(--mustard));
    flex-shrink:0;
  }
  .brand-text h1{font-size:1.25rem; letter-spacing:0.2px;}
  .brand-text span{font-size:0.72rem; color:var(--ink-soft); text-transform:uppercase; letter-spacing:1.5px;}
  nav a{
    text-decoration:none; font-weight:600; font-size:0.92rem;
    color:var(--ink); padding:8px 14px; border-radius:999px;
    transition:background 0.2s;
  }
  nav a:hover{background:var(--bg-soft);}

  /* ---------- Hero ---------- */
  .hero{
    position:relative;
    min-height:82vh;
    display:flex; align-items:flex-end;
    background:#000;
    overflow:hidden;
  }
  .hero img{
    position:absolute; inset:0; width:100%; height:100%;
    object-fit:cover; opacity:0.78;
  }
  .hero::after{
    content:"";
    position:absolute; inset:0;
    background:linear-gradient(180deg, rgba(43,36,30,0.15) 0%, rgba(43,36,30,0.15) 40%, rgba(43,36,30,0.85) 100%);
  }
  .hero-content{
    position:relative; z-index:2;
    max-width:1100px; margin:0 auto; width:100%;
    padding:0 24px 64px;
    color:#fff;
  }
  .hero-eyebrow{
    display:inline-flex; align-items:center; gap:8px;
    font-size:0.78rem; letter-spacing:2px; text-transform:uppercase;
    color:var(--mustard); font-weight:700; margin-bottom:14px;
  }
  .hero-content h2{
    font-size:clamp(2.4rem, 6vw, 4.2rem);
    color:#fff; line-height:1.03; max-width:720px;
    font-weight:600;
  }
  .hero-content h2 em{
    font-style:italic; color:var(--mustard); font-weight:500;
  }
  .hero-content p{
    max-width:480px; margin:18px 0 28px;
    color:#f1ece1; font-size:1.02rem;
  }
  .btn-primary{
    background:var(--plum); color:#fff;
    padding:15px 30px; border-radius:999px;
    font-weight:600; font-size:0.98rem;
    display:inline-flex; align-items:center; gap:10px;
    box-shadow:var(--shadow);
    transition:transform 0.2s, background 0.2s;
  }
  .btn-primary:hover{ background:var(--plum-dark); transform:translateY(-2px); }

  /* ---------- Products ---------- */
  .products-section{
    padding:64px 0 70px;
    background:var(--bg);
  }
  .section-head{
    max-width:1100px; margin:0 auto 30px; padding:0 24px;
    display:flex; align-items:flex-end; justify-content:space-between; gap:20px; flex-wrap:wrap;
  }
  .section-head .tag{
    font-size:0.75rem; letter-spacing:2px; text-transform:uppercase;
    color:var(--green); font-weight:700; margin-bottom:8px; display:block;
  }
  .section-head h3{font-size:clamp(1.7rem,3.6vw,2.4rem);}
  .section-head p{color:var(--ink-soft); max-width:380px; margin:8px 0 0; font-size:0.95rem;}

  .carousel-wrap{ position:relative; }
  .carousel{
    display:flex; gap:20px;
    overflow-x:auto; scroll-snap-type:x mandatory;
    padding:6px 24px 20px;
    max-width:1100px; margin:0 auto;
    scrollbar-width:thin; scrollbar-color:var(--plum) var(--bg-soft);
  }
  .carousel::-webkit-scrollbar{height:8px;}
  .carousel::-webkit-scrollbar-thumb{background:var(--plum); border-radius:10px;}
  .carousel::-webkit-scrollbar-track{background:var(--bg-soft); border-radius:10px;}

  .card{
    scroll-snap-align:start;
    flex:0 0 250px;
    background:var(--card);
    border-radius:var(--radius);
    overflow:hidden;
    box-shadow:var(--shadow);
    border:1px solid var(--line);
    display:flex; flex-direction:column;
  }
  .card-img{
    position:relative; height:210px; overflow:hidden;
    background:var(--bg-soft);
  }
  .card-img img{ width:100%; height:100%; object-fit:cover; transition:transform 0.4s; }
  .card:hover .card-img img{ transform:scale(1.06); }
  .card-scallop{
    height:12px; margin-top:-1px;
    background-image: radial-gradient(circle at 8px 0px, transparent 7px, var(--card) 7.5px);
    background-size: 16px 16px; background-repeat:repeat-x;
  }
  .card-body{ padding:16px 16px 18px; display:flex; flex-direction:column; gap:10px; flex:1; }
  .card-body h4{ font-family:'Fraunces', serif; font-size:1.05rem; font-weight:600; }
  .price{ color:var(--plum); font-weight:700; font-size:1.05rem; }
  .add-btn{
    margin-top:auto;
    background:var(--bg-soft); color:var(--ink);
    border:1px solid var(--line);
    padding:10px 14px; border-radius:999px;
    font-weight:600; font-size:0.86rem;
    display:flex; align-items:center; justify-content:center; gap:8px;
    transition:background 0.2s, color 0.2s;
  }
  .add-btn:hover{ background:var(--green); color:#fff; border-color:var(--green); }
  .add-btn.added{ background:var(--green); color:#fff; border-color:var(--green); }

  .carousel-nav{
    display:flex; gap:10px; justify-content:center; margin-top:6px;
  }
  .carousel-nav button{
    width:38px; height:38px; border-radius:50%;
    background:var(--card); border:1px solid var(--line);
    display:flex; align-items:center; justify-content:center;
    font-size:1rem; color:var(--plum);
    box-shadow:var(--shadow);
  }
  .carousel-nav button:hover{ background:var(--plum); color:#fff; }

  /* ---------- About strip ---------- */
  .about-strip{
    background:var(--plum-dark);
    color:#f4ece2;
    padding:50px 24px;
    text-align:center;
  }
  .about-strip .stitch-divider{margin-bottom:0;}
  .about-strip-inner{ max-width:620px; margin:0 auto; }
  .about-strip h3{ color:#fff; font-size:1.6rem; margin-bottom:12px; }
  .about-strip p{ color:#e2d3c4; font-size:0.98rem; }

  /* ---------- Footer ---------- */
  footer{
    padding:40px 24px 100px;
    text-align:center;
    color:var(--ink-soft);
    font-size:0.86rem;
  }
  footer .foot-brand{ font-family:'Fraunces', serif; color:var(--ink); font-size:1.1rem; margin-bottom:6px; }
  footer a{ text-decoration:underline; }

  /* ---------- Floating cart button ---------- */
  .fab-cart{
    position:fixed; right:22px; bottom:22px; z-index:50;
    width:60px; height:60px; border-radius:50%;
    background:var(--plum); color:#fff;
    display:flex; align-items:center; justify-content:center;
    box-shadow:0 8px 22px rgba(107,37,69,0.45);
    font-size:1.5rem;
    transition:transform 0.2s;
  }
  .fab-cart:hover{ transform:scale(1.06); }
  .cart-badge{
    position:absolute; top:-4px; right:-4px;
    background:var(--mustard); color:var(--ink);
    font-size:0.72rem; font-weight:700;
    min-width:22px; height:22px; border-radius:50%;
    display:flex; align-items:center; justify-content:center;
    border:2px solid var(--bg);
  }

  /* ---------- WhatsApp float ---------- */
  .fab-whatsapp{
    position:fixed; left:22px; bottom:22px; z-index:50;
    width:56px; height:56px; border-radius:50%;
    background:#25D366; color:#fff;
    display:flex; align-items:center; justify-content:center;
    box-shadow:0 8px 22px rgba(37,211,102,0.45);
    text-decoration:none;
  }
  .fab-whatsapp svg{ width:28px; height:28px; }
  .fab-whatsapp:hover{ transform:scale(1.06); }

  /* ---------- Cart drawer ---------- */
  .overlay{
    position:fixed; inset:0; background:rgba(43,36,30,0.45);
    z-index:60; opacity:0; pointer-events:none; transition:opacity 0.25s;
  }
  .overlay.open{ opacity:1; pointer-events:auto; }

  .drawer{
    position:fixed; top:0; right:0; height:100%;
    width:min(420px, 92vw);
    background:var(--bg);
    z-index:70;
    transform:translateX(100%);
    transition:transform 0.3s ease;
    display:flex; flex-direction:column;
    box-shadow:-14px 0 40px rgba(0,0,0,0.2);
  }
  .drawer.open{ transform:translateX(0); }
  .drawer-head{
    padding:20px 22px; border-bottom:1px solid var(--line);
    display:flex; align-items:center; justify-content:space-between;
    background:var(--bg-soft);
  }
  .drawer-head h3{ font-size:1.2rem; }
  .drawer-close{
    background:transparent; font-size:1.3rem; color:var(--ink-soft); line-height:1;
  }
  .drawer-body{ flex:1; overflow-y:auto; padding:18px 22px; }
  .empty-cart{ text-align:center; color:var(--ink-soft); padding:40px 10px; font-size:0.95rem; }

  .cart-item{
    display:flex; gap:12px; padding:12px 0; border-bottom:1px solid var(--line);
  }
  .cart-item img{ width:60px; height:60px; border-radius:10px; object-fit:cover; flex-shrink:0; }
  .cart-item-info{ flex:1; }
  .cart-item-info h5{ margin:0 0 4px; font-family:'Fraunces', serif; font-size:0.98rem; font-weight:600; }
  .cart-item-row{ display:flex; align-items:center; justify-content:space-between; gap:8px; margin-top:6px; }
  .qty-control{ display:flex; align-items:center; gap:8px; }
  .qty-control button{
    width:24px; height:24px; border-radius:50%; background:var(--bg-soft);
    border:1px solid var(--line); font-weight:700; font-size:0.85rem; color:var(--ink);
  }
  .remove-link{ font-size:0.78rem; color:var(--plum); text-decoration:underline; background:none; }

  .drawer-foot{
    border-top:1px solid var(--line);
    padding:18px 22px 22px;
    background:var(--bg-soft);
  }
  .total-row{
    display:flex; justify-content:space-between; align-items:center;
    font-weight:700; font-size:1.1rem; margin-bottom:16px;
  }
  .total-row .price{ font-size:1.2rem; }

  .field{ margin-bottom:12px; }
  .field label{ display:block; font-size:0.82rem; font-weight:600; margin-bottom:5px; color:var(--ink-soft); }
  .field input{
    width:100%; padding:11px 13px; border-radius:10px;
    border:1px solid var(--line); background:#fff;
    font-family:inherit; font-size:0.94rem; color:var(--ink);
  }
  .field input:focus{ outline:2px solid var(--green); outline-offset:1px; }

  .send-btn{
    width:100%; background:var(--green); color:#fff;
    padding:14px; border-radius:999px; font-weight:700; font-size:0.98rem;
    margin-top:6px;
    display:flex; align-items:center; justify-content:center; gap:8px;
  }
  .send-btn:disabled{ opacity:0.6; cursor:not-allowed; }
  .send-btn:hover:not(:disabled){ background:#3a5234; }
  .form-note{ font-size:0.76rem; color:var(--ink-soft); margin-top:10px; text-align:center; }
  .status-msg{ font-size:0.85rem; margin-top:10px; text-align:center; font-weight:600; }
  .status-msg.ok{ color:var(--green); }
  .status-msg.err{ color:var(--plum); }

  @media (prefers-reduced-motion: reduce){
    html{ scroll-behavior:auto; }
    *{ transition:none !important; }
  }

  @media (max-width:640px){
    .hero{ min-height:78vh; }
    .card{ flex-basis:200px; }
    .carousel-nav{ display:none; }
  }
</style>
</head>
<body>

<!-- ================= HEADER ================= -->
<header>
  <div class="nav-wrap">
    <div class="brand">
      <div class="brand-mark" aria-hidden="true"></div>
      <div class="brand-text">
        <h1>The Crochet Shop</h1>
        <span>Handmade &middot; Stitch by Stitch</span>
      </div>
    </div>
    <nav>
      <a href="#products">Shop</a>
      <a href="#about">About</a>
    </nav>
  </div>
</header>

<!-- ================= HERO ================= -->
<section class="hero">
  <img src="https://i.ibb.co/rfk7Ryvs/IMG-20260809-WA0000.jpg" alt="Handmade crochet pieces from The Crochet Shop">
  <div class="hero-content">
    <span class="hero-eyebrow">Fresh Finds, Best Prices</span>
    <h2>Every loop, <em>made by hand</em> for you</h2>
    <p>Soft, cosy, one-of-a-kind crochet pieces — made slowly, sold simply, no two exactly alike.</p>
    <a href="#products" class="btn-primary">Shop Now &#8595;</a>
  </div>
</section>
<div class="stitch-divider flip" aria-hidden="true"></div>

<!-- ================= PRODUCTS ================= -->
<section class="products-section" id="products">
  <div class="section-head">
    <div>
      <span class="tag">The Collection</span>
      <h3>Made with one hook<br>and a lot of patience</h3>
    </div>
    <p>Scroll through &mdash; tap "Add to Cart" on anything that catches your eye.</p>
  </div>

  <div class="carousel-wrap">
    <div class="carousel" id="carousel"></div>
    <div class="carousel-nav">
      <button id="scrollLeft" aria-label="Scroll left">&#8592;</button>
      <button id="scrollRight" aria-label="Scroll right">&#8594;</button>
    </div>
  </div>
</section>

<!-- ================= ABOUT STRIP ================= -->
<div class="stitch-divider on-plum" aria-hidden="true"></div>
<section class="about-strip" id="about">
  <div class="about-strip-inner">
    <h3>Small batch. Big heart.</h3>
    <p>Every piece from The Crochet Shop is made to order by hand, one stitch at a time. Message us on WhatsApp for custom colours, sizes, or a rush order &mdash; we love a good challenge.</p>
  </div>
</section>
<div class="stitch-divider on-plum flip" aria-hidden="true" style="transform:rotate(0deg);"></div>

<!-- ================= FOOTER ================= -->
<footer>
  <div class="foot-brand">The Crochet Shop</div>
  <p>Fresh Finds, Best Prices &mdash; made with love, one loop at a time.</p>
  <p>Questions? Email <a href="mailto:suhanijaiswall18@gmail.com">suhanijaiswall18@gmail.com</a></p>
</footer>

<!-- ================= FLOATING BUTTONS ================= -->
<a class="fab-whatsapp" href="https://wa.me/917238820149" target="_blank" rel="noopener" aria-label="Chat on WhatsApp">
  <svg viewBox="0 0 24 24" fill="currentColor"><path d="M17.6 6.32A7.85 7.85 0 0 0 12.05 4a7.94 7.94 0 0 0-6.87 11.88L4 20l4.24-1.11a7.9 7.9 0 0 0 3.8 0.97h0a7.94 7.94 0 0 0 7.94-7.94 7.86 7.86 0 0 0-2.38-5.6zM12.05 18.4a6.6 6.6 0 0 1-3.36-0.92l-0.24-0.14-2.5.66.67-2.44-.16-.25a6.6 6.6 0 1 1 12.26-3.4 6.6 6.6 0 0 1-6.67 6.5zm3.6-4.94c-.2-.1-1.17-.58-1.35-.64s-.31-.1-.44.1-.5.64-.62.77-.23.15-.43.05a5.4 5.4 0 0 1-1.6-.98 6 6 0 0 1-1.1-1.37c-.12-.2 0-.3.09-.4s.2-.23.29-.34a1.3 1.3 0 0 0 .2-.33.36.36 0 0 0 0-.35c-.05-.1-.44-1.06-.6-1.45-.16-.38-.32-.33-.44-.34h-.38a.72.72 0 0 0-.52.24 2.2 2.2 0 0 0-.68 1.63 3.8 3.8 0 0 0 .8 2.03 8.7 8.7 0 0 0 3.34 2.95c.47.2.83.32 1.12.41.47.15.9.13 1.24.08.38-.06 1.17-.48 1.33-.94.17-.46.17-.85.12-.94s-.18-.14-.38-.24z"/></svg>
</a>

<button class="fab-cart" id="cartFab" aria-label="Open cart">
  &#128218;
  <span class="cart-badge" id="cartBadge">0</span>
</button>

<!-- ================= CART DRAWER ================= -->
<div class="overlay" id="overlay"></div>
<aside class="drawer" id="drawer" aria-label="Shopping cart">
  <div class="drawer-head">
    <h3>Your Cart</h3>
    <button class="drawer-close" id="drawerClose" aria-label="Close cart">&times;</button>
  </div>

  <div class="drawer-body" id="cartItemsWrap">
    <div class="empty-cart" id="emptyCart">Your cart is empty. Go find something cosy 🧶</div>
  </div>

  <div class="drawer-foot" id="drawerFoot" style="display:none;">
    <div class="total-row">
      <span>Total</span>
      <span class="price" id="cartTotal">₹0</span>
    </div>

    <form id="orderForm">
      <div class="field">
        <label for="custName">Your name</label>
        <input type="text" id="custName" required placeholder="e.g. Priya Sharma">
      </div>
      <div class="field">
        <label for="custPhone">Phone number</label>
        <input type="tel" id="custPhone" required placeholder="e.g. 98765 43210">
      </div>
      <button type="submit" class="send-btn" id="sendBtn">Send Order 🧵</button>
      <div class="status-msg" id="statusMsg"></div>
      <p class="form-note">We'll email your order straight to the shop and get back to you on WhatsApp to confirm.</p>
    </form>
  </div>
</aside>

<script>
  /* ============================================================
     EmailJS setup
     ------------------------------------------------------------
     EmailJS is free (emailjs.com). To make "Send Order" actually
     deliver to suhanijaiswall18@gmail.com, sign up at emailjs.com,
     connect Gmail as your email service, then create a template
     with these variables: {{customer_name}}, {{customer_phone}},
     {{order_items}}, {{order_total}}, {{to_email}}.
     Replace the three placeholders below with your own IDs.
  ============================================================ */
  const EMAILJS_PUBLIC_KEY  = "YOUR_PUBLIC_KEY";
  const EMAILJS_SERVICE_ID  = "YOUR_SERVICE_ID";
  const EMAILJS_TEMPLATE_ID = "YOUR_TEMPLATE_ID";
  const SHOP_OWNER_EMAIL    = "suhanijaiswall18@gmail.com";

  if (window.emailjs && EMAILJS_PUBLIC_KEY !== "YOUR_PUBLIC_KEY") {
    emailjs.init({ publicKey: EMAILJS_PUBLIC_KEY });
  }

  /* ---------------- Product data ---------------- */
  const products = [
    { id: 1, name: "Granny Square Throw",     price: 1899, img: "https://i.ibb.co/08KRYVV/IMG-20260809-WA0007.jpg" },
    { id: 2, name: "Amigurumi Bunny Duo",      price: 649,  img: "https://i.ibb.co/8nbxJyYL/IMG-20260809-WA0008.jpg" },
    { id: 3, name: "Scallop Edge Coasters",    price: 399,  img: "https://i.ibb.co/wFy1SPZK/IMG-20260809-WA0004.jpg" },
    { id: 4, name: "Chunky Knit Beanie",       price: 549,  img: "https://i.ibb.co/vx5CsNYF/IMG-20260809-WA0006.jpg" },
    { id: 5, name: "Woven Flower Basket",      price: 899,  img: "https://i.ibb.co/QwLZwRd/IMG-20260809-WA0003.jpg" },
    { id: 6, name: "Mini Crochet Tote Bag",    price: 749,  img: "https://i.ibb.co/HD5P9Cbr/IMG-20260809-WA0005.jpg" },
  ];

  const carousel = document.getElementById("carousel");
  carousel.innerHTML = products.map(p => `
    <div class="card">
      <div class="card-img"><img src="${p.img}" alt="${p.name}" loading="lazy"></div>
      <div class="card-scallop"></div>
      <div class="card-body">
        <h4>${p.name}</h4>
        <span class="price">₹${p.price}</span>
        <button class="add-btn" data-id="${p.id}">+ Add to Cart</button>
      </div>
    </div>
  `).join("");

  document.getElementById("scrollLeft").onclick = () => carousel.scrollBy({ left: -280, behavior: "smooth" });
  document.getElementById("scrollRight").onclick = () => carousel.scrollBy({ left: 280, behavior: "smooth" });

  /* ---------------- Cart state (in-memory) ---------------- */
  let cart = []; // { id, name, price, img, qty }

  function addToCart(id, btn) {
    const product = products.find(p => p.id === id);
    const existing = cart.find(i => i.id === id);
    if (existing) existing.qty += 1;
    else cart.push({ ...product, qty: 1 });
    renderCart();
    if (btn) {
      btn.textContent = "✓ Added";
      btn.classList.add("added");
      setTimeout(() => { btn.textContent = "+ Add to Cart"; btn.classList.remove("added"); }, 1100);
    }
  }

  carousel.addEventListener("click", (e) => {
    const btn = e.target.closest(".add-btn");
    if (!btn) return;
    addToCart(Number(btn.dataset.id), btn);
  });

  function changeQty(id, delta) {
    const item = cart.find(i => i.id === id);
    if (!item) return;
    item.qty += delta;
    if (item.qty <= 0) cart = cart.filter(i => i.id !== id);
    renderCart();
  }

  function removeItem(id) {
    cart = cart.filter(i => i.id !== id);
    renderCart();
  }

  function renderCart() {
    const count = cart.reduce((s, i) => s + i.qty, 0);
    document.getElementById("cartBadge").textContent = count;

    const wrap = document.getElementById("emptyCart");
    const foot = document.getElementById("drawerFoot");
    const itemsWrap = document.getElementById("cartItemsWrap");

    if (cart.length === 0) {
      itemsWrap.innerHTML = `<div class="empty-cart" id="emptyCart">Your cart is empty. Go find something cosy 🧶</div>`;
      foot.style.display = "none";
      return;
    }

    foot.style.display = "block";
    itemsWrap.innerHTML = cart.map(i => `
      <div class="cart-item">
        <img src="${i.img}" alt="${i.name}">
        <div class="cart-item-info">
          <h5>${i.name}</h5>
          <div class="cart-item-row">
            <div class="qty-control">
              <button type="button" onclick="changeQty(${i.id}, -1)" aria-label="Decrease quantity">&minus;</button>
              <span>${i.qty}</span>
              <button type="button" onclick="changeQty(${i.id}, 1)" aria-label="Increase quantity">&plus;</button>
            </div>
            <span class="price">₹${i.price * i.qty}</span>
          </div>
          <button type="button" class="remove-link" onclick="removeItem(${i.id})">Remove</button>
        </div>
      </div>
    `).join("");

    const total = cart.reduce((s, i) => s + i.price * i.qty, 0);
    document.getElementById("cartTotal").textContent = "₹" + total;
  }
  // expose for inline onclick handlers
  window.changeQty = changeQty;
  window.removeItem = removeItem;

  /* ---------------- Drawer open/close ---------------- */
  const drawer = document.getElementById("drawer");
  const overlay = document.getElementById("overlay");

  function openDrawer() { drawer.classList.add("open"); overlay.classList.add("open"); }
  function closeDrawer() { drawer.classList.remove("open"); overlay.classList.remove("open"); }

  document.getElementById("cartFab").onclick = openDrawer;
  document.getElementById("drawerClose").onclick = closeDrawer;
  overlay.onclick = closeDrawer;

  /* ---------------- Send order via EmailJS ---------------- */
  document.getElementById("orderForm").addEventListener("submit", function (e) {
    e.preventDefault();
    const statusMsg = document.getElementById("statusMsg");
    const sendBtn = document.getElementById("sendBtn");
    statusMsg.textContent = "";
    statusMsg.className = "status-msg";

    if (cart.length === 0) {
      statusMsg.textContent = "Your cart is empty.";
      statusMsg.className = "status-msg err";
      return;
    }

    const name = document.getElementById("custName").value.trim();
    const phone = document.getElementById("custPhone").value.trim();
    const itemsList = cart.map(i => `${i.name} x${i.qty} — ₹${i.price * i.qty}`).join("\n");
    const total = cart.reduce((s, i) => s + i.price * i.qty, 0);

    const templateParams = {
      customer_name: name,
      customer_phone: phone,
      order_items: itemsList,
      order_total: "₹" + total,
      to_email: SHOP_OWNER_EMAIL,
    };

    if (window.emailjs && EMAILJS_PUBLIC_KEY !== "YOUR_PUBLIC_KEY") {
      sendBtn.disabled = true;
      sendBtn.textContent = "Sending…";
      emailjs.send(EMAILJS_SERVICE_ID, EMAILJS_TEMPLATE_ID, templateParams)
        .then(() => {
          statusMsg.textContent = "Order sent! We'll reach out on WhatsApp shortly. 🎉";
          statusMsg.className = "status-msg ok";
          cart = [];
          renderCart();
          document.getElementById("orderForm").reset();
        })
        .catch((err) => {
          statusMsg.textContent = "Couldn't send automatically — opening your email app instead.";
          statusMsg.className = "status-msg err";
          fallbackMailto(name, phone, itemsList, total);
        })
        .finally(() => {
          sendBtn.disabled = false;
          sendBtn.textContent = "Send Order 🧵";
        });
    } else {
      // EmailJS not configured yet — fall back to a pre-filled mailto link
      fallbackMailto(name, phone, itemsList, total);
      statusMsg.textContent = "Opening your email app to send the order…";
      statusMsg.className = "status-msg ok";
    }
  });

  function fallbackMailto(name, phone, itemsList, total) {
    const subject = encodeURIComponent("New order from " + name);
    const body = encodeURIComponent(
      `Customer Name: ${name}\nPhone Number: ${phone}\n\nItems:\n${itemsList}\n\nTotal: ₹${total}`
    );
    window.location.href = `mailto:${SHOP_OWNER_EMAIL}?subject=${subject}&body=${body}`;
  }
</script>

</body>
</html>
