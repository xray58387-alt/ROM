html = r'''<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ROM — Real Orders More | متجرك الذكي</title>
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
:root{--bg:#000;--bg-soft:#f5f5f7;--text:#1d1d1f;--text-soft:#86868b;--accent:#0071e3;--accent-hover:#0077ed;--radius:18px;--max:1200px;--danger:#ff375f;--success:#34c759}
html{scroll-behavior:smooth}
body{font-family:"SF Pro Display","Segoe UI",Tahoma,Arial,sans-serif;background:var(--bg);color:var(--text);-webkit-font-smoothing:antialiased;overflow-x:hidden}
a{text-decoration:none;color:inherit}
button{font-family:inherit;cursor:pointer;border:none;background:none}
img{max-width:100%;display:block}
input,select,textarea{font-family:inherit}

/* NAVBAR */
nav{position:fixed;top:0;right:0;left:0;z-index:1000;backdrop-filter:saturate(180%) blur(20px);background:rgba(0,0,0,.8);height:52px;display:flex;align-items:center;justify-content:center}
.nav-inner{display:flex;align-items:center;gap:34px;max-width:var(--max);width:100%;padding:0 22px}
.logo{font-size:19px;font-weight:900;background:linear-gradient(135deg,#7d7aff,#0071e3);-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent;letter-spacing:.5px}
.nav-links{display:flex;gap:30px;list-style:none}
.nav-links a{color:#d6d6da;font-size:13px;transition:color .2s}
.nav-links a:hover{color:#fff}
.nav-icons{display:flex;gap:18px;align-items:center;margin-right:auto}
.nav-icon{color:#fff;font-size:17px;position:relative;transition:transform .2s}
.nav-icon:hover{transform:scale(1.1)}
.cart-badge{position:absolute;top:-7px;right:-8px;background:var(--accent);color:#fff;font-size:10px;font-weight:700;width:16px;height:16px;border-radius:50%;display:flex;align-items:center;justify-content:center;transform:scale(0);transition:transform .25s cubic-bezier(.68,-0.55,.27,1.55)}
.cart-badge.show{transform:scale(1)}
.search-bar{display:none;position:fixed;top:52px;right:0;left:0;z-index:999;background:#1d1d1f;padding:14px;text-align:center;box-shadow:0 10px 30px rgba(0,0,0,.4)}
.search-bar input{width:min(600px,90%);padding:10px 18px;border-radius:10px;border:none;font-size:14px;outline:none}
.hamburger{display:none;color:#fff;font-size:22px}

/* HERO */
.hero{min-height:92vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:110px 20px 60px;background:radial-gradient(ellipse at 50% 0%,#1a1a2e 0%,#000 60%)}
.hero h1{font-size:clamp(42px,7vw,84px);font-weight:800;letter-spacing:-2px;line-height:1.1;background:linear-gradient(180deg,#fff 30%,#7d7aff);-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
.hero p{color:#a1a1a6;font-size:clamp(16px,2.2vw,22px);margin:20px 0 34px;max-width:640px}
.btn{display:inline-block;padding:13px 30px;border-radius:980px;font-size:16px;font-weight:600;transition:all .25s}
.btn-primary{background:var(--accent);color:#fff}
.btn-primary:hover{background:var(--accent-hover);transform:translateY(-2px);box-shadow:0 8px 25px rgba(0,113,227,.4)}
.btn-ghost{color:var(--accent);border:1px solid var(--accent)}
.btn-ghost:hover{background:var(--accent);color:#fff}
.btn-danger{background:var(--danger);color:#fff;padding:9px 18px;border-radius:980px;font-size:13px;font-weight:600}
.btn-danger:hover{background:#d9264c}
.btn-small{padding:8px 16px;font-size:13px;border-radius:980px}
.hero-btns{display:flex;gap:16px;flex-wrap:wrap;justify-content:center}
.hero-visual{margin-top:50px;width:min(700px,90%);height:340px;background:linear-gradient(135deg,#2b2b4d,#0071e3 50%,#7d7aff);border-radius:30px;position:relative;overflow:hidden;box-shadow:0 40px 100px rgba(0,113,227,.3);animation:float 6s ease-in-out infinite;display:flex;align-items:center;justify-content:center;font-size:90px}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-15px)}}

section{padding:80px 20px}
.container{max-width:var(--max);margin:0 auto}
.section-title{font-size:clamp(30px,4.5vw,52px);font-weight:800;text-align:center;margin-bottom:10px;letter-spacing:-1px}
.section-sub{text-align:center;color:var(--text-soft);font-size:17px;margin-bottom:48px}

/* GRID */
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(270px,1fr));gap:24px}
.card{background:var(--bg-soft);border-radius:var(--radius);padding:30px 24px;text-align:center;transition:transform .35s cubic-bezier(.2,.8,.2,1),box-shadow .35s;cursor:pointer;position:relative;overflow:hidden}
.card:hover{transform:translateY(-8px);box-shadow:0 20px 50px rgba(0,0,0,.12)}
.card .emoji{font-size:72px;margin-bottom:18px;transition:transform .35s}
.card:hover .emoji{transform:scale(1.15) rotate(-5deg)}
.card h3{font-size:19px;font-weight:700;margin-bottom:6px}
.card .cat-tag{font-size:12px;color:var(--accent);font-weight:600;margin-bottom:8px;display:block}
.card p{color:var(--text-soft);font-size:14px;margin-bottom:14px;line-height:1.6;min-height:44px}
.stars{color:#ff9500;font-size:14px;margin-bottom:10px;letter-spacing:2px}
.price{font-size:22px;font-weight:800}
.price small{font-size:13px;color:var(--text-soft);font-weight:400}
.card .actions{display:flex;gap:10px;margin-top:18px}
.btn-add{flex:1;background:var(--accent);color:#fff;padding:11px;border-radius:980px;font-size:14px;font-weight:600;transition:all .2s}
.btn-add:hover{background:#000}
.btn-view{padding:11px 16px;border:1px solid #d2d2d7;border-radius:980px;font-size:14px;transition:all .2s}
.btn-view:hover{border-color:var(--text)}
.new-badge{position:absolute;top:16px;right:16px;background:linear-gradient(135deg,#ff375f,#ff9500);color:#fff;font-size:11px;font-weight:700;padding:5px 12px;border-radius:980px}
.sale-badge{position:absolute;top:16px;left:16px;background:var(--success);color:#fff;font-size:11px;font-weight:700;padding:5px 12px;border-radius:980px}
.old-price{text-decoration:line-through;color:var(--text-soft);font-size:14px;font-weight:400;margin-right:6px}

/* BAND */
.band{background:var(--bg-soft)}
.band-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(230px,1fr));gap:24px}
.band-card{background:#fff;border-radius:var(--radius);padding:36px 24px;text-align:center;transition:transform .3s}
.band-card:hover{transform:translateY(-6px)}
.band-card .ic{font-size:44px;margin-bottom:16px}
.band-card h4{font-size:17px;margin-bottom:8px}
.band-card p{color:var(--text-soft);font-size:14px;line-height:1.7}

.filters{display:flex;gap:12px;justify-content:center;flex-wrap:wrap;margin-bottom:44px}
.chip{padding:9px 22px;border-radius:980px;border:1px solid #d2d2d7;font-size:14px;transition:all .2s;background:#fff}
.chip:hover{border-color:var(--text)}
.chip.active{background:var(--text);color:#fff;border-color:var(--text)}

/* DRAWER */
.overlay{position:fixed;inset:0;background:rgba(0,0,0,.4);z-index:1100;opacity:0;pointer-events:none;transition:opacity .3s}
.overlay.open{opacity:1;pointer-events:auto}
.drawer{position:fixed;top:0;left:0;bottom:0;width:min(420px,92vw);background:#fff;z-index:1200;transform:translateX(-105%);transition:transform .4s cubic-bezier(.2,.8,.2,1);display:flex;flex-direction:column;box-shadow:20px 0 60px rgba(0,0,0,.2)}
.drawer.open{transform:translateX(0)}
.drawer-head{padding:22px 24px;border-bottom:1px solid #eee;display:flex;justify-content:space-between;align-items:center}
.drawer-head h3{font-size:20px}
.drawer-close{font-size:24px;color:var(--text-soft)}
.cart-items{flex:1;overflow-y:auto;padding:20px 24px}
.cart-item{display:flex;gap:14px;align-items:center;padding:14px 0;border-bottom:1px solid #f0f0f0}
.ci-emoji{font-size:38px;width:56px;height:56px;background:var(--bg-soft);border-radius:14px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.ci-info{flex:1}
.ci-info h5{font-size:15px}
.ci-info .ci-price{color:var(--text-soft);font-size:13px}
.qty{display:flex;align-items:center;gap:10px}
.qty button{width:26px;height:26px;border:1px solid #d2d2d7;border-radius:50%;font-size:15px;display:flex;align-items:center;justify-content:center;transition:all .2s}
.qty button:hover{background:var(--text);color:#fff}
.ci-del{color:var(--danger);font-size:18px;transition:transform .2s}
.ci-del:hover{transform:scale(1.2)}
.empty-cart{text-align:center;padding:60px 20px;color:var(--text-soft)}
.empty-cart .big{font-size:60px;margin-bottom:16px}
.drawer-foot{padding:22px 24px;border-top:1px solid #eee}
.total-row{display:flex;justify-content:space-between;font-size:18px;font-weight:700;margin-bottom:16px}
.checkout-btn{width:100%;background:var(--accent);color:#fff;padding:15px;border-radius:14px;font-size:16px;font-weight:700;transition:all .2s}
.checkout-btn:hover{background:#000}
.checkout-btn:disabled{background:#d2d2d7;cursor:not-allowed}

/* MODAL */
.modal{position:fixed;inset:0;z-index:1300;display:flex;align-items:center;justify-content:center;padding:20px;opacity:0;pointer-events:none;transition:opacity .3s}
.modal.open{opacity:1;pointer-events:auto}
.modal-bg{position:absolute;inset:0;background:rgba(0,0,0,.5);backdrop-filter:blur(6px)}
.modal-box{position:relative;background:#fff;border-radius:24px;max-width:640px;width:100%;max-height:88vh;overflow-y:auto;padding:40px;transform:scale(.92);transition:transform .35s}
.modal.open .modal-box{transform:scale(1)}
.modal-close{position:absolute;top:18px;left:18px;font-size:24px;color:var(--text-soft);width:36px;height:36px;border-radius:50%;background:var(--bg-soft);display:flex;align-items:center;justify-content:center;z-index:2}
.modal-emoji{font-size:100px;text-align:center;margin-bottom:20px}
.modal-box h2{text-align:center;font-size:28px;margin-bottom:8px}
.m-price{text-align:center;font-size:26px;font-weight:800;color:var(--accent);margin-bottom:14px}
.m-desc{color:var(--text-soft);text-align:center;line-height:1.8;margin-bottom:24px;font-size:15px}
.spec-list{background:var(--bg-soft);border-radius:14px;padding:18px 24px;margin-bottom:26px}
.spec-list li{display:flex;justify-content:space-between;padding:9px 0;font-size:14px;border-bottom:1px solid #e5e5ea;list-style:none}
.spec-list li:last-child{border:none}

/* TOAST */
.toast{position:fixed;bottom:30px;right:50%;transform:translate(50%,100px);background:#1d1d1f;color:#fff;padding:14px 28px;border-radius:980px;font-size:14px;z-index:1400;transition:transform .4s cubic-bezier(.2,.8,.2,1);display:flex;align-items:center;gap:10px;box-shadow:0 10px 30px rgba(0,0,0,.3)}
.toast.show{transform:translate(50%,0)}
.toast.success{background:var(--success)}
.toast.error{background:var(--danger)}

/* FOOTER */
footer{background:#f5f5f7;padding:60px 20px 30px;border-top:1px solid #d2d2d7}
.footer-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:34px;max-width:var(--max);margin:0 auto 40px}
.footer-grid h5{font-size:14px;margin-bottom:14px}
.footer-grid a{display:block;color:var(--text-soft);font-size:13px;margin-bottom:9px;transition:color .2s}
.footer-grid a:hover{color:var(--text)}
.footer-bottom{text-align:center;color:var(--text-soft);font-size:12px;border-top:1px solid #d2d2d7;padding-top:22px;max-width:var(--max);margin:0 auto}

/* FORMS */
.form-group{margin-bottom:16px}
.form-group label{display:block;font-size:13px;font-weight:600;margin-bottom:6px}
.form-group input,.form-group select,.form-group textarea{width:100%;padding:12px 16px;border:1px solid #d2d2d7;border-radius:12px;font-size:14px;outline:none;transition:border .2s;background:#fff}
.form-group input:focus,.form-group select:focus,.form-group textarea:focus{border-color:var(--accent)}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.form-error{color:var(--danger);font-size:12px;margin-top:4px;display:none}
.form-group.invalid input{border-color:var(--danger)}
.form-group.invalid .form-error{display:block}

/* PAYMENT */
.pay-methods{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:22px}
.pay-method{border:2px solid #d2d2d7;border-radius:14px;padding:14px 8px;text-align:center;font-size:13px;font-weight:700;transition:all .2s;background:#fff}
.pay-method .pi{font-size:26px;display:block;margin-bottom:6px}
.pay-method.active{border-color:var(--accent);background:#f0f7ff}
.card-preview{background:linear-gradient(135deg,#1a1a2e,#2b2b4d);border-radius:18px;padding:22px;color:#fff;margin-bottom:20px;font-family:monospace;min-height:140px;display:flex;flex-direction:column;justify-content:space-between}
.card-preview .num{font-size:20px;letter-spacing:3px}
.card-preview .row{display:flex;justify-content:space-between;font-size:13px;color:#a1a1a6}
.spinner{display:inline-block;width:18px;height:18px;border:3px solid rgba(255,255,255,.3);border-top-color:#fff;border-radius:50%;animation:spin .7s linear infinite;vertical-align:middle;margin-left:8px}
@keyframes spin{to{transform:rotate(360deg)}}
.secure-note{display:flex;align-items:center;justify-content:center;gap:6px;color:var(--text-soft);font-size:12px;margin-top:14px}

/* ============ ADMIN ============ */
.admin-layout{display:grid;grid-template-columns:230px 1fr;min-height:100vh}
.admin-side{background:#1d1d1f;color:#fff;padding:26px 18px;position:sticky;top:0;height:100vh}
.admin-side .logo{font-size:22px;margin-bottom:36px;display:block;text-align:center}
.admin-nav a{display:flex;gap:10px;align-items:center;padding:12px 14px;border-radius:12px;color:#a1a1a6;font-size:14px;margin-bottom:6px;transition:all .2s}
.admin-nav a:hover{background:#2c2c2e;color:#fff}
.admin-nav a.active{background:var(--accent);color:#fff}
.admin-main{background:var(--bg-soft);padding:32px;overflow-y:auto}
.admin-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:28px}
.admin-top h2{font-size:26px;font-weight:800}
.stats-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:18px;margin-bottom:30px}
.stat-card{background:#fff;border-radius:var(--radius);padding:24px;box-shadow:0 2px 12px rgba(0,0,0,.05)}
.stat-card .si{font-size:30px;margin-bottom:10px}
.stat-card .sv{font-size:28px;font-weight:800}
.stat-card .sl{color:var(--text-soft);font-size:13px;margin-top:4px}
.admin-table{width:100%;background:#fff;border-radius:var(--radius);overflow:hidden;border-collapse:collapse;box-shadow:0 2px 12px rgba(0,0,0,.05)}
.admin-table th{background:#fafafa;padding:14px;font-size:13px;color:var(--text-soft);text-align:right;border-bottom:2px solid #f0f0f0}
.admin-table td{padding:14px;font-size:14px;border-bottom:1px solid #f5f5f7;vertical-align:middle}
.admin-table tr:hover td{background:#fafafa}
.admin-table .pe{font-size:28px}
.status-pill{padding:4px 14px;border-radius:980px;font-size:12px;font-weight:700;display:inline-block}
.status-new{background:#e8f0fe;color:var(--accent)}
.status-shipped{background:#fff4e5;color:#ff9500}
.status-done{background:#e8f9ee;color:var(--success)}
.status-cancel{background:#ffe8ec;color:var(--danger)}
.admin-actions{display:flex;gap:8px}
.icon-btn{width:34px;height:34px;border-radius:10px;background:var(--bg-soft);display:inline-flex;align-items:center;justify-content:center;font-size:15px;transition:all .2s}
.icon-btn:hover{background:#e5e5ea}
.icon-btn.danger:hover{background:#ffe8ec}
.admin-login{min-height:100vh;display:flex;align-items:center;justify-content:center;background:radial-gradient(ellipse at 50% 0%,#1a1a2e 0%,#000 60%)}
.login-box{background:#fff;border-radius:24px;padding:44px;width:min(400px,92vw);box-shadow:0 40px 100px rgba(0,0,0,.5)}
.login-box .logo{font-size:32px;text-align:center;display:block;margin-bottom:8px}
.login-box p{text-align:center;color:var(--text-soft);font-size:13px;margin-bottom:26px}
.login-hint{background:var(--bg-soft);border-radius:12px;padding:12px;text-align:center;font-size:12px;color:var(--text-soft);margin-top:16px}
.hidden{display:none!important}
.admin-mobile-bar{display:none}

@media(max-width:860px){
  .admin-layout{grid-template-columns:1fr}
  .admin-side{position:fixed;z-index:900;right:-250px;transition:right .3s;width:230px}
  .admin-side.open{right:0}
  .admin-mobile-bar{display:flex;position:sticky;top:0;z-index:800;background:#1d1d1f;color:#fff;padding:14px 20px;align-items:center;gap:14px}
  .admin-main{padding:20px}
  .pay-methods{grid-template-columns:1fr}
  .form-row{grid-template-columns:1fr}
}
@media(max-width:768px){
  .nav-links{display:none}
  .hamburger{display:block}
  .nav-links.mobile-open{display:flex;position:fixed;top:52px;right:0;left:0;background:rgba(0,0,0,.95);flex-direction:column;padding:24px;gap:20px;z-index:998}
}
.reveal{opacity:0;transform:translateY(30px);transition:opacity .7s,transform .7s}
.reveal.visible{opacity:1;transform:translateY(0)}
</style>
</head>
<body>

<!-- ============ STORE VIEW ============ -->
<div id="storeView">
<nav>
  <div class="nav-inner">
    <a href="#" class="logo">ROM</a>
    <ul class="nav-links" id="navLinks">
      <li><a href="#home">الرئيسية</a></li>
      <li><a href="#products">المنتجات</a></li>
      <li><a href="#features">المميزات</a></li>
      <li><a href="#contact">تواصل</a></li>
    </ul>
    <div class="nav-icons">
      <button class="nav-icon" onclick="toggleSearch()" title="بحث">🔍</button>
      <button class="nav-icon" onclick="toggleCart(true)" title="السلة">🛒<span class="cart-badge" id="cartBadge">0</span></button>
      <button class="hamburger" onclick="document.getElementById('navLinks').classList.toggle('mobile-open')">☰</button>
    </div>
  </div>
</nav>
<div class="search-bar" id="searchBar">
  <input type="text" id="searchInput" placeholder="ابحث عن منتج..." oninput="renderProducts()">
</div>

<header class="hero" id="home">
  <h1>المستقبل بين يديك.</h1>
  <p>اكتشف أحدث الأجهزة والإلكترونيات بأفضل الأسعار. جودة عالمية، توصيل سريع، وضمان حقيقي.</p>
  <div class="hero-btns">
    <a href="#products" class="btn btn-primary">تسوق الآن</a>
    <a href="#features" class="btn btn-ghost">تعرف على المميزات</a>
  </div>
  <div class="hero-visual">🎧⌚💻</div>
</header>

<section id="products">
  <div class="container">
    <h2 class="section-title reveal">تسوق حسب الفئة</h2>
    <p class="section-sub reveal">اختر ما يناسبك من تشكيلتنا الواسعة</p>
    <div class="filters reveal" id="filters"></div>
    <div class="grid" id="productGrid"></div>
  </div>
</section>

<section id="features" class="band">
  <div class="container">
    <h2 class="section-title reveal">لماذا تختارنا؟</h2>
    <p class="section-sub reveal">نلتزم بتقديم أفضل تجربة تسوق</p>
    <div class="band-grid">
      <div class="band-card reveal"><div class="ic">🚚</div><h4>شحن سريع مجاني</h4><p>توصيل خلال 24-48 ساعة لجميع المدن دون رسوم إضافية.</p></div>
      <div class="band-card reveal"><div class="ic">🛡️</div><h4>ضمان سنتان</h4><p>ضمان شامل على جميع المنتجات مع إمكانية الاستبدال.</p></div>
      <div class="band-card reveal"><div class="ic">💳</div><h4>دفع آمن</h4><p>ادفع بأمان عبر مدى، Apple Pay، أو البطاقات البنكية.</p></div>
      <div class="band-card reveal"><div class="ic">🔄</div><h4>إرجاع مجاني</h4><p>غير راضٍ عن المنتج؟ أرجعه مجاناً خلال 30 يوماً.</p></div>
    </div>
  </div>
</section>

<footer id="contact">
  <div class="footer-grid">
    <div>
      <h5 style="font-size:18px;font-weight:900;background:linear-gradient(135deg,#7d7aff,#0071e3);-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent">ROM</h5>
      <p style="color:var(--text-soft);font-size:13px;line-height:1.7;margin-bottom:10px">Real Orders More.<br>طلبات حقيقية، مبيعات أكثر.</p>
    </div>
    <div><h5>تسوق</h5><a href="#products">الهواتف الذكية</a><a href="#products">اللابتوبات</a><a href="#products">السماعات</a><a href="#products">الساعات</a></div>
    <div><h5>خدمة العملاء</h5><a href="#">تتبع الطلب</a><a href="#">الشحن والتوصيل</a><a href="#">الإرجاع والاستبدال</a><a href="#">الأسئلة الشائعة</a></div>
    <div><h5>عن المتجر</h5><a href="#">من نحن</a><a href="#">الأخبار</a><a href="#" onclick="showAdminLogin();return false;">لوحة التحكم 🔐</a></div>
  </div>
  <div class="footer-bottom"><b style="color:var(--text)">ROM</b> — Real Orders More.<br>© 2026 ROM. جميع الحقوق محفوظة. | صُنع بشغف 🖤</div>
</footer>
</div>

<!-- ============ ADMIN LOGIN VIEW ============ -->
<div id="adminLoginView" class="admin-login hidden">
  <div class="login-box">
    <span class="logo">ROM</span>
    <p>لوحة تحكم المتجر — Real Orders More</p>
    <form onsubmit="adminLogin(event)">
      <div class="form-group"><label>اسم المستخدم</label><input id="adminUser" required placeholder="admin" autocomplete="username"></div>
      <div class="form-group"><label>كلمة المرور</label><input id="adminPass" type="password" required placeholder="••••••••" autocomplete="current-password"></div>
      <button class="btn btn-primary" style="width:100%;text-align:center">تسجيل الدخول 🔐</button>
    </form>
    <div class="login-hint">للتجربة: المستخدم <b>admin</b> — كلمة المرور <b>rom2026</b></div>
    <p style="text-align:center;margin-top:14px"><a href="#" onclick="showStore();return false;" style="color:var(--accent);font-size:13px">← العودة للمتجر</a></p>
  </div>
</div>

<!-- ============ ADMIN PANEL VIEW ============ -->
<div id="adminView" class="hidden">
  <div class="admin-mobile-bar"><button class="nav-icon" onclick="document.getElementById('adminSide').classList.toggle('open')">☰</button><b>ROM لوحة التحكم</b></div>
  <div class="admin-layout">
    <aside class="admin-side" id="adminSide">
      <span class="logo">ROM</span>
      <nav class="admin-nav">
        <a href="#" class="active" data-tab="dashboard" onclick="adminTab('dashboard',this)">📊 لوحة المعلومات</a>
        <a href="#" data-tab="products" onclick="adminTab('products',this)">📦 المنتجات</a>
        <a href="#" data-tab="orders" onclick="adminTab('orders',this)">🧾 الطلبات</a>
        <a href="#" onclick="showStore();return false;">🛍️ عرض المتجر</a>
        <a href="#" onclick="adminLogout();return false;">🚪 تسجيل الخروج</a>
      </nav>
    </aside>
    <main class="admin-main">
      <!-- DASHBOARD -->
      <div id="tab-dashboard">
        <div class="admin-top"><h2>لوحة المعلومات</h2><span style="color:var(--text-soft);font-size:13px" id="todayDate"></span></div>
        <div class="stats-grid" id="statsGrid"></div>
        <h3 style="margin-bottom:14px;font-size:18px">أحدث الطلبات</h3>
        <div style="overflow-x:auto"><table class="admin-table"><thead><tr><th>رقم الطلب</th><th>العميل</th><th>الإجمالي</th><th>الحالة</th><th>التاريخ</th></tr></thead><tbody id="recentOrders"></tbody></table></div>
      </div>
      <!-- PRODUCTS -->
      <div id="tab-products" class="hidden">
        <div class="admin-top">
          <h2>إدارة المنتجات</h2>
          <button class="btn btn-primary btn-small" onclick="openProductForm()">+ إضافة منتج</button>
        </div>
        <div style="overflow-x:auto"><table class="admin-table"><thead><tr><th></th><th>المنتج</th><th>الفئة</th><th>السعر</th><th>المخزون</th><th>الحالة</th><th>إجراءات</th></tr></thead><tbody id="adminProducts"></tbody></table></div>
      </div>
      <!-- ORDERS -->
      <div id="tab-orders" class="hidden">
        <div class="admin-top"><h2>الطلبات</h2></div>
        <div style="overflow-x:auto"><table class="admin-table"><thead><tr><th>رقم الطلب</th><th>العميل</th><th>الجوال</th><th>المدينة</th><th>المنتجات</th><th>الإجمالي</th><th>الدفع</th><th>الحالة</th><th>إجراءات</th></tr></thead><tbody id="adminOrders"></tbody></table></div>
      </div>
    </main>
  </div>
</div>

<!-- CART DRAWER -->
<div class="overlay" id="overlay" onclick="toggleCart(false)"></div>
<aside class="drawer" id="cartDrawer">
  <div class="drawer-head"><h3>🛍️ سلة التسوق</h3><button class="drawer-close" onclick="toggleCart(false)">✕</button></div>
  <div class="cart-items" id="cartItems"></div>
  <div class="drawer-foot">
    <div class="total-row"><span>الإجمالي</span><span id="cartTotal">0 ر.س</span></div>
    <button class="checkout-btn" id="checkoutBtn" onclick="startCheckout()">إتمام الشراء 💳</button>
  </div>
</aside>

<!-- MODAL -->
<div class="modal" id="productModal">
  <div class="modal-bg" onclick="closeModal()"></div>
  <div class="modal-box" id="modalBox"></div>
</div>

<div class="toast" id="toast"></div>

<script>
/* ============================================================
   ROM — Real Orders More
   قاعدة البيانات (Database Layer) — localStorage
============================================================ */
const DB = {
  get(key, fallback){ try{ const v = localStorage.getItem('rom_'+key); return v ? JSON.parse(v) : fallback; }catch(e){ return fallback; } },
  set(key, val){ localStorage.setItem('rom_'+key, JSON.stringify(val)); }
};

const DEFAULT_PRODUCTS = [
  {id:1, name:"آيفون 17 برو ماكس", cat:"هواتف", price:5299, oldPrice:null, stock:25, emoji:"📱", isNew:true, rating:5, desc:"شريحة A19 Pro، كاميرا 48MP، شاشة ProMotion 120Hz، وتصميم من التيتانيوم.", specs:{"الشاشة":"6.9 بوصة OLED","التخزين":"256GB","الكاميرا":"48MP ثلاثية","البطارية":"30 ساعة"}},
  {id:2, name:"ماك بوك برو 16", cat:"لابتوبات", price:9499, oldPrice:null, stock:12, emoji:"💻", isNew:true, rating:5, desc:"شريحة M5 Pro مع ذاكرة 36GB وشاشة Liquid Retina XDR مذهلة.", specs:{"المعالج":"M5 Pro","الذاكرة":"36GB","التخزين":"512GB SSD","البطارية":"22 ساعة"}},
  {id:3, name:"سماعات AirPods Max", cat:"سماعات", price:1999, oldPrice:2499, stock:40, emoji:"🎧", isNew:false, rating:4, desc:"إلغاء ضوضاء نشط، صوت فضائي، وبطارية تدوم حتى 20 ساعة.", specs:{"إلغاء الضوضاء":"نشط","البطارية":"20 ساعة","الاتصال":"Bluetooth 5.3","الوزن":"385 جم"}},
  {id:4, name:"ساعة Apple Watch Ultra 3", cat:"ساعات", price:3299, oldPrice:null, stock:18, emoji:"⌚", isNew:true, rating:5, desc:"مصنوعة من التيتانيوم، مقاومة للماء حتى 100 متر، وبطارية 72 ساعة.", specs:{"المعالج":"S11","البطارية":"72 ساعة","المقاومة":"100 متر","GPS":"مزدوج التردد"}},
  {id:5, name:"آيباد برو 13 بوصة", cat:"هواتف", price:4599, oldPrice:4999, stock:15, emoji:"📲", isNew:false, rating:4, desc:"أنحف آيباد على الإطلاق مع شريحة M5 وشاشة Ultra Retina XDR.", specs:{"الشاشة":"13 بوصة XDR","المعالج":"M5","التخزين":"256GB","القلم":"مدعوم"}},
  {id:6, name:"سماعات AirPods Pro 3", cat:"سماعات", price:949, oldPrice:null, stock:60, emoji:"🎵", isNew:false, rating:4, desc:"إلغاء ضوضاء مضاعف، وضع الشفافية التكيفية، وصوت مخصص.", specs:{"إلغاء الضوضاء":"2x أقوى","البطارية":"30 ساعة","الشحن":"MagSafe","الصندوق":"USB-C"}},
  {id:7, name:"آيفون 16", cat:"هواتف", price:3699, oldPrice:null, stock:30, emoji:"📱", isNew:false, rating:5, desc:"التوازن المثالي بين الأداء والسعر مع شريحة A18.", specs:{"الشاشة":"6.1 بوصة","المعالج":"A18","الكاميرا":"48MP","البطارية":"27 ساعة"}},
  {id:8, name:"ماك بوك Air 15", cat:"لابتوبات", price:5899, oldPrice:null, stock:20, emoji:"💻", isNew:false, rating:4, desc:"أخف وأنحف ماك بوك مع شريحة M4 وألوان مبهجة.", specs:{"المعالج":"M4","الذاكرة":"16GB","التخزين":"512GB","الوزن":"1.51 كجم"}},
  {id:9, name:"ساعة Apple Watch SE", cat:"ساعات", price:1249, oldPrice:1399, stock:35, emoji:"⌚", isNew:false, rating:4, desc:"ساعة ذكية مثالية للمبتدئين مع تتبع الصحة واللياقة.", specs:{"المعالج":"S9","البطارية":"18 ساعة","المقاومة":"50 متر","المقاسات":"40/44mm"}},
  {id:10, name:"سماعات Beats Studio Pro", cat:"سماعات", price:1349, oldPrice:null, stock:22, emoji:"🎶", isNew:false, rating:4, desc:"صوت احترافي مع إلغاء ضوضاء وتشغيل 40 ساعة.", specs:{"البطارية":"40 ساعة","الشحن":"USB-C","الكودك":"Lossless","الألوان":"4 خيارات"}},
  {id:11, name:"آيباد ميني 7", cat:"هواتف", price:2099, oldPrice:null, stock:28, emoji:"📲", isNew:true, rating:5, desc:"قوة A17 Pro بحجم الجيب، مثالي للقراءة والرسم.", specs:{"الشاشة":"8.3 بوصة","المعالج":"A17 Pro","القلم":"Apple Pencil Pro","الوزن":"297 جم"}},
  {id:12, name:"ماك ستوديو", cat:"لابتوبات", price:12499, oldPrice:null, stock:8, emoji:"🖥️", isNew:true, rating:5, desc:"وحش الأداء الإبداعي مع شريحة M5 Ultra للمحترفين.", specs:{"المعالج":"M5 Ultra","الذاكرة":"96GB","التخزين":"1TB SSD","المنافذ":"12 منفذ"}},
];
const CATS = ["الكل","هواتف","لابتوبات","سماعات","ساعات"];
const ADMIN_CRED = {user:"admin", pass:"rom2026"};

/* تهيئة قاعدة البيانات */
let PRODUCTS = DB.get('products', null);
if(!PRODUCTS){ PRODUCTS = DEFAULT_PRODUCTS; DB.set('products', PRODUCTS); }
let cart = DB.get('cart', []);
let activeCat = "الكل";

/* ================= VIEWS ================= */
function showStore(){ hideAllViews(); document.getElementById('storeView').classList.remove('hidden'); renderProducts(); renderFilters(); window.scrollTo(0,0); }
function showAdminLogin(){ hideAllViews(); document.getElementById('adminLoginView').classList.remove('hidden'); }
function showAdminPanel(){ hideAllViews(); document.getElementById('adminView').classList.remove('hidden'); renderAdmin(); }
function hideAllViews(){ ['storeView','adminLoginView','adminView'].forEach(id=>document.getElementById(id).classList.add('hidden')); }

/* ================= AUTH ================= */
function adminLogin(e){
  e.preventDefault();
  const u = document.getElementById('adminUser').value.trim();
  const p = document.getElementById('adminPass').value;
  if(u===ADMIN_CRED.user && p===ADMIN_CRED.pass){
    sessionStorage.setItem('rom_admin','1');
    showAdminPanel(); showToast('✅ مرحباً بك في لوحة التحكم','success');
  } else showToast('❌ بيانات الدخول غير صحيحة','error');
}
function adminLogout(){ sessionStorage.removeItem('rom_admin'); showStore(); }

/* ================= ADMIN TABS ================= */
function adminTab(tab, el){
  ['dashboard','products','orders'].forEach(t=>document.getElementById('tab-'+t).classList.add('hidden'));
  document.getElementById('tab-'+tab).classList.remove('hidden');
  document.querySelectorAll('.admin-nav a[data-tab]').forEach(a=>a.classList.remove('active'));
  el.classList.add('active');
  document.getElementById('adminSide').classList.remove('open');
}

function renderAdmin(){
  const orders = DB.get('orders', []);
  const revenue = orders.filter(o=>o.status!=='ملغي').reduce((s,o)=>s+o.total,0);
  const lowStock = PRODUCTS.filter(p=>p.stock<10).length;
  document.getElementById('todayDate').textContent = new Date().toLocaleDateString('ar-SA',{weekday:'long',year:'numeric',month:'long',day:'numeric'});
  document.getElementById('statsGrid').innerHTML = `
    <div class="stat-card"><div class="si">🧾</div><div class="sv">${orders.length}</div><div class="sl">إجمالي الطلبات</div></div>
    <div class="stat-card"><div class="si">💰</div><div class="sv">${revenue.toLocaleString()} <small style="font-size:14px">ر.س</small></div><div class="sl">إجمالي المبيعات</div></div>
    <div class="stat-card"><div class="si">📦</div><div class="sv">${PRODUCTS.length}</div><div class="sl">عدد المنتجات</div></div>
    <div class="stat-card"><div class="si">⚠️</div><div class="sv" style="color:${lowStock?'var(--danger)':'inherit'}">${lowStock}</div><div class="sl">منتجات مخزون منخفض</div></div>`;
  document.getElementById('recentOrders').innerHTML = orders.length ? orders.slice(-5).reverse().map(o=>`
    <tr><td><b>#${o.id}</b></td><td>${o.customer.name}</td><td>${o.total.toLocaleString()} ر.س</td><td>${statusPill(o.status)}</td><td style="color:var(--text-soft);font-size:12px">${o.date}</td></tr>`).join('')
    : '<tr><td colspan="5" style="text-align:center;color:var(--text-soft);padding:30px">لا توجد طلبات بعد</td></tr>';
  renderAdminProducts();
  renderAdminOrders();
}

function statusPill(s){
  const map = {"جديد":"status-new","تم الشحن":"status-shipped","مكتمل":"status-done","ملغي":"status-cancel"};
  return `<span class="status-pill ${map[s]||'status-new'}">${s}</span>`;
}

function renderAdminProducts(){
  document.getElementById('adminProducts').innerHTML = PRODUCTS.map(p=>`
    <tr>
      <td><span class="pe">${p.emoji}</span></td>
      <td><b>${p.name}</b>${p.isNew?' <span class="new-badge" style="position:static;display:inline-block">جديد</span>':''}</td>
      <td>${p.cat}</td>
      <td><b>${p.price.toLocaleString()}</b> ر.س${p.oldPrice?`<br><small style="text-decoration:line-through;color:var(--text-soft)">${p.oldPrice.toLocaleString()}</small>`:''}</td>
      <td style="color:${p.stock<10?'var(--danger)':'inherit'};font-weight:${p.stock<10?'700':'400'}">${p.stock}</td>
      <td>${statusPill(p.stock>0?'مكتمل':'ملغي').replace('مكتمل','متوفر').replace('ملغي','نفد')}</td>
      <td><div class="admin-actions">
        <button class="icon-btn" onclick="openProductForm(${p.id})" title="تعديل">✏️</button>
        <button class="icon-btn danger" onclick="deleteProduct(${p.id})" title="حذف">🗑</button>
      </div></td>
    </tr>`).join('');
}

function renderAdminOrders(){
  const orders = DB.get('orders', []);
  document.getElementById('adminOrders').innerHTML = orders.length ? orders.slice().reverse().map(o=>`
    <tr>
      <td><b>#${o.id}</b></td>
      <td>${o.customer.name}</td>
      <td style="direction:ltr;text-align:right">${o.customer.phone}</td>
      <td>${o.customer.city}</td>
      <td>${o.items.map(i=>`${i.emoji}×${i.qty}`).join(' ')}</td>
      <td><b>${o.total.toLocaleString()}</b> ر.س</td>
      <td>${o.payment}</td>
      <td>${statusPill(o.status)}</td>
      <td><div class="admin-actions">
        ${o.status==='جديد'?`<button class="icon-btn" onclick="updateOrder(${o.id},'تم الشحن')" title="شحن">🚚</button>`:''}
        ${o.status==='تم الشحن'?`<button class="icon-btn" onclick="updateOrder(${o.id},'مكتمل')" title="إكمال">✅</button>`:''}
        ${o.status!=='ملغي'&&o.status!=='مكتمل'?`<button class="icon-btn danger" onclick="updateOrder(${o.id},'ملغي')" title="إلغاء">✕</button>`:''}
      </div></td>
    </tr>`).join('')
    : '<tr><td colspan="9" style="text-align:center;color:var(--text-soft);padding:30px">لا توجد طلبات بعد — الطلبات الجديدة ستظهر هنا</td></tr>';
}

function updateOrder(id, status){
  const orders = DB.get('orders', []);
  const o = orders.find(x=>x.id===id);
  if(o){ o.status = status; DB.set('orders', orders); renderAdmin(); showToast(`تم تحديث الطلب #${id} → ${status}`,'success'); }
}

/* ================= PRODUCT CRUD ================= */
function openProductForm(id){
  const p = id ? PRODUCTS.find(x=>x.id===id) : null;
  document.getElementById('modalBox').innerHTML = `
    <button class="modal-close" onclick="closeModal()">✕</button>
    <h2>${p?'✏️ تعديل منتج':'➕ إضافة منتج جديد'}</h2>
    <form onsubmit="saveProduct(event,${p?p.id:'null'})" style="margin-top:20px">
      <div class="form-group"><label>اسم المنتج *</label><input id="fName" required value="${p?p.name:''}"></div>
      <div class="form-row">
        <div class="form-group"><label>الفئة *</label><select id="fCat">${CATS.slice(1).map(c=>`<option ${p&&p.cat===c?'selected':''}>${c}</option>`).join('')}</select></div>
        <div class="form-group"><label>الأيقونة (Emoji)</label><input id="fEmoji" value="${p?p.emoji:'📦'}" maxlength="4"></div>
      </div>
      <div class="form-row">
        <div class="form-group"><label>السعر (ر.س) *</label><input id="fPrice" type="number" min="1" required value="${p?p.price:''}"></div>
        <div class="form-group"><label>السعر قبل الخصم</label><input id="fOld" type="number" min="0" value="${p&&p.oldPrice?p.oldPrice:''}"></div>
      </div>
      <div class="form-row">
        <div class="form-group"><label>المخزون *</label><input id="fStock" type="number" min="0" required value="${p?p.stock:20}"></div>
        <div class="form-group"><label>التقييم (1-5)</label><input id="fRating" type="number" min="1" max="5" value="${p?p.rating:5}"></div>
      </div>
      <div class="form-group"><label>الوصف</label><textarea id="fDesc" rows="3">${p?p.desc:''}</textarea></div>
      <div class="form-group"><label style="display:flex;align-items:center;gap:8px"><input type="checkbox" id="fNew" style="width:auto" ${p&&p.isNew?'checked':''}> منتج جديد (شارة)</label></div>
      <button class="btn btn-primary" style="width:100%;text-align:center">${p?'حفظ التعديلات 💾':'إضافة المنتج ➕'}</button>
    </form>`;
  document.getElementById('productModal').classList.add('open');
}

function saveProduct(e, id){
  e.preventDefault();
  const data = {
    name: document.getElementById('fName').value.trim(),
    cat: document.getElementById('fCat').value,
    emoji: document.getElementById('fEmoji').value || '📦',
    price: +document.getElementById('fPrice').value,
    oldPrice: +document.getElementById('fOld').value || null,
    stock: +document.getElementById('fStock').value,
    rating: Math.min(5,Math.max(1,+document.getElementById('fRating').value||5)),
    desc: document.getElementById('fDesc').value.trim(),
    isNew: document.getElementById('fNew').checked,
  };
  if(id){
    const i = PRODUCTS.findIndex(x=>x.id===id);
    PRODUCTS[i] = {...PRODUCTS[i], ...data};
  } else {
    data.id = Math.max(0,...PRODUCTS.map(p=>p.id))+1;
    data.specs = {"الضمان":"سنتان","التوصيل":"مجاني"};
    PRODUCTS.push(data);
  }
  DB.set('products', PRODUCTS);
  closeModal(); renderAdmin(); renderProducts(); renderFilters();
  showToast(id?'✅ تم حفظ التعديلات':'✅ تمت إضافة المنتج','success');
}

function deleteProduct(id){
  if(!confirm('هل أنت متأكد من حذف هذا المنتج؟')) return;
  PRODUCTS = PRODUCTS.filter(p=>p.id!==id);
  DB.set('products', PRODUCTS);
  cart = cart.filter(i=>i.id!==id); saveCart();
  renderAdmin(); renderProducts();
  showToast('🗑 تم حذف المنتج','success');
}

/* ================= STORE RENDER ================= */
function renderFilters(){
  document.getElementById('filters').innerHTML = CATS.map(c=>
    `<button class="chip ${c===activeCat?'active':''}" onclick="setCat('${c}')">${c}</button>`).join('');
}
function setCat(c){ activeCat=c; renderFilters(); renderProducts(); }
function starStr(n){ return "★".repeat(n)+"☆".repeat(5-n); }

function renderProducts(){
  const q = (document.getElementById('searchInput').value||'').trim();
  const list = PRODUCTS.filter(p =>
    (activeCat==="الكل"||p.cat===activeCat) &&
    (!q || p.name.includes(q)||(p.desc||'').includes(q)||p.cat.includes(q))
  );
  document.getElementById('productGrid').innerHTML = list.length ? list.map(p=>`
    <div class="card reveal visible" onclick="openProduct(${p.id})">
      ${p.isNew?'<span class="new-badge">جديد</span>':''}
      ${p.oldPrice?`<span class="sale-badge">خصم ${Math.round((1-p.price/p.oldPrice)*100)}%</span>`:''}
      <div class="emoji">${p.emoji}</div>
      <span class="cat-tag">${p.cat}</span>
      <h3>${p.name}</h3>
      <p>${p.desc||''}</p>
      <div class="stars">${starStr(p.rating)}</div>
      <div class="price">${p.oldPrice?`<span class="old-price">${p.oldPrice.toLocaleString()}</span>`:''}${p.price.toLocaleString()} <small>ر.س</small></div>
      ${p.stock<=0?'<button class="btn-add" style="background:#d2d2d7;cursor:not-allowed;margin-top:18px;width:100%">نفد المخزون</button>':`
      <div class="actions">
        <button class="btn-add" onclick="event.stopPropagation();addToCart(${p.id})">أضف للسلة</button>
        <button class="btn-view" onclick="event.stopPropagation();openProduct(${p.id})">عرض</button>
      </div>`}
    </div>`).join('')
  : '<p style="grid-column:1/-1;text-align:center;color:#86868b;font-size:18px;padding:40px">لا توجد نتائج مطابقة 😕</p>';
}

/* ================= CART ================= */
function saveCart(){ DB.set('cart', cart); updateCartUI(); }

function addToCart(id){
  const p = PRODUCTS.find(x=>x.id===id);
  if(!p || p.stock<=0){ showToast('⚠️ نفد المخزون','error'); return; }
  const item = cart.find(i=>i.id===id);
  const inCart = item ? item.qty : 0;
  if(inCart+1 > p.stock){ showToast(`⚠️ المتوفر فقط ${p.stock} قطعة`,'error'); return; }
  if(item) item.qty++;
  else cart.push({id:p.id, name:p.name, price:p.price, emoji:p.emoji, qty:1});
  saveCart(); showToast('✅ تمت الإضافة إلى السلة','success');
}
function changeQty(id,d){
  const item = cart.find(i=>i.id===id);
  if(!item) return;
  const p = PRODUCTS.find(x=>x.id===id);
  if(d>0 && p && item.qty+1 > p.stock){ showToast(`⚠️ المتوفر فقط ${p.stock} قطعة`,'error'); return; }
  item.qty += d;
  if(item.qty<=0) cart = cart.filter(i=>i.id!==id);
  saveCart();
}
function removeItem(id){ cart = cart.filter(i=>i.id!==id); saveCart(); }

function updateCartUI(){
  const count = cart.reduce((s,i)=>s+i.qty,0);
  const badge = document.getElementById('cartBadge');
  badge.textContent = count; badge.classList.toggle('show', count>0);
  const box = document.getElementById('cartItems');
  box.innerHTML = !cart.length
    ? `<div class="empty-cart"><div class="big">🛒</div><h4>سلتك فارغة</h4><p>ابدأ التسوق الآن واملأها بأفضل المنتجات</p></div>`
    : cart.map(i=>`
      <div class="cart-item">
        <div class="ci-emoji">${i.emoji}</div>
        <div class="ci-info"><h5>${i.name}</h5><span class="ci-price">${i.price.toLocaleString()} ر.س</span></div>
        <div class="qty"><button onclick="changeQty(${i.id},1)">+</button><span>${i.qty}</span><button onclick="changeQty(${i.id},-1)">−</button></div>
        <button class="ci-del" onclick="removeItem(${i.id})">🗑</button>
      </div>`).join('');
  document.getElementById('cartTotal').textContent = cart.reduce((s,i)=>s+i.price*i.qty,0).toLocaleString()+' ر.س';
  document.getElementById('checkoutBtn').disabled = !cart.length;
}
function toggleCart(open){
  document.getElementById('cartDrawer').classList.toggle('open',open);
  document.getElementById('overlay').classList.toggle('open',open);
}
function toggleSearch(){
  const bar = document.getElementById('searchBar');
  bar.style.display = bar.style.display==='block'?'none':'block';
  if(bar.style.display==='block') document.getElementById('searchInput').focus();
}

/* ================= PRODUCT MODAL ================= */
function openProduct(id){
  const p = PRODUCTS.find(x=>x.id===id);
  if(!p) return;
  document.getElementById('modalBox').innerHTML = `
    <button class="modal-close" onclick="closeModal()">✕</button>
    <div class="modal-emoji">${p.emoji}</div>
    <h2>${p.name}</h2>
    <div class="m-price">${p.oldPrice?`<span class="old-price">${p.oldPrice.toLocaleString()} ر.س</span> `:''}${p.price.toLocaleString()} ر.س</div>
    <div class="stars" style="text-align:center;margin-bottom:18px">${starStr(p.rating)}</div>
    <p class="m-desc">${p.desc||''}</p>
    <ul class="spec-list">${Object.entries(p.specs||{}).map(([k,v])=>`<li><span>${k}</span><b>${v}</b></li>`).join('')}<li><span>المتوفر</span><b style="color:${p.stock<10?'var(--danger)':'inherit'}">${p.stock} قطعة</b></li></ul>
    ${p.stock>0
      ? `<button class="btn btn-primary" style="width:100%;text-align:center" onclick="addToCart(${p.id})">أضف إلى السلة 🛒</button>`
      : `<button class="btn" style="width:100%;text-align:center;background:#d2d2d7;color:#fff;cursor:not-allowed">نفد المخزون</button>`}`;
  document.getElementById('productModal').classList.add('open');
}
function closeModal(){ document.getElementById('productModal').classList.remove('open'); }

/* ============================================================
   💳 بوابة الدفع — Checkout Flow
============================================================ */
let checkoutData = {};

function startCheckout(){
  if(!cart.length) return;
  toggleCart(false);
  const total = cart.reduce((s,i)=>s+i.price*i.qty,0);
  checkoutData = {total};
  document.getElementById('modalBox').innerHTML = `
    <button class="modal-close" onclick="closeModal()">✕</button>
    <h2>🧾 إتمام الطلب</h2>
    <p class="m-desc">الإجمالي: <b style="color:var(--accent);font-size:20px">${total.toLocaleString()} ر.س</b> — شامل الشحن المجاني 🚚</p>
    <form onsubmit="submitCustomerInfo(event)">
      <div class="form-group"><label>الاسم الكامل *</label><input id="cName" required placeholder="محمد أحمد"></div>
      <div class="form-row">
        <div class="form-group"><label>رقم الجوال *</label><input id="cPhone" required placeholder="05xxxxxxxx" pattern="[0-9+]{9,}"></div>
        <div class="form-group"><label>المدينة *</label><input id="cCity" required placeholder="الرياض"></div>
      </div>
      <div class="form-group"><label>العنوان *</label><input id="cAddr" required placeholder="الحي، الشارع، رقم المبنى"></div>
      <button class="btn btn-primary" style="width:100%;text-align:center">المتابعة للدفع 💳</button>
    </form>`;
  document.getElementById('productModal').classList.add('open');
}

function submitCustomerInfo(e){
  e.preventDefault();
  checkoutData.customer = {
    name: document.getElementById('cName').value.trim(),
    phone: document.getElementById('cPhone').value.trim(),
    city: document.getElementById('cCity').value.trim(),
    addr: document.getElementById('cAddr').value.trim()
  };
  renderPaymentStep();
}

function renderPaymentStep(){
  document.getElementById('modalBox').innerHTML = `
    <button class="modal-close" onclick="startCheckout();event.stopPropagation();">→</button>
    <h2>💳 اختر وسيلة الدفع</h2>
    <p class="m-desc">المبلغ: <b style="color:var(--accent);font-size:20px">${checkoutData.total.toLocaleString()} ر.س</b></p>
    <div class="pay-methods" id="payMethods">
      <button type="button" class="pay-method" data-pay="مدى" onclick="selectPay(this)"><span class="pi">💳</span>مدى</button>
      <button type="button" class="pay-method" data-pay="Apple Pay" onclick="selectPay(this)"><span class="pi"></span>Apple Pay</button>
      <button type="button" class="pay-method" data-pay="بطاقة بنكية" onclick="selectPay(this)"><span class="pi">💳</span>فيزا / ماستر</button>
    </div>
    <div id="payForm"></div>`;
}

function selectPay(el){
  document.querySelectorAll('.pay-method').forEach(b=>b.classList.remove('active'));
  el.classList.add('active');
  checkoutData.payment = el.dataset.pay;
  const form = document.getElementById('payForm');
  if(el.dataset.pay === 'Apple Pay'){
    form.innerHTML = `<button class="btn btn-primary" style="width:100%;text-align:center;background:#000" onclick="processPayment(this)"> ادفع الآن — ${checkoutData.total.toLocaleString()} ر.س</button>`;
  } else {
    form.innerHTML = `
      <div class="card-preview" id="cardPreview">
        <div style="font-size:13px;color:#a1a1a6">ROM PAY</div>
        <div class="num" id="pvNum">•••• •••• •••• ••••</div>
        <div class="row"><span id="pvName">اسم حامل البطاقة</span><span id="pvExp">MM/YY</span></div>
      </div>
      <form onsubmit="processPaymentForm(event)">
        <div class="form-group"><label>رقم البطاقة *</label><input id="cardNum" required inputmode="numeric" maxlength="19" placeholder="0000 0000 0000 0000" oninput="formatCardNum(this)"></div>
        <div class="form-row">
          <div class="form-group"><label>تاريخ الانتهاء *</label><input id="cardExp" required maxlength="5" placeholder="MM/YY" oninput="formatExp(this)"></div>
          <div class="form-group"><label>CVV *</label><input id="cardCvv" required type="password" inputmode="numeric" maxlength="3" placeholder="•••"></div>
        </div>
        <div class="form-group"><label>اسم حامل البطاقة *</label><input id="cardName" required placeholder="MOHAMMED AHMED" oninput="document.getElementById('pvName').textContent=this.value||'اسم حامل البطاقة'"></div>
        <button class="btn btn-primary" style="width:100%;text-align:center">ادفع ${checkoutData.total.toLocaleString()} ر.س 🔒</button>
      </form>
      <div class="secure-note">🔒 دفع مشفر وآمن 100% — بروتوكول SSL</div>`;
  }
}

function formatCardNum(el){
  let v = el.value.replace(/\D/g,'').slice(0,16);
  el.value = v.replace(/(.{4})/g,'$1 ').trim();
  document.getElementById('pvNum').textContent = el.value || '•••• •••• •••• ••••';
}
function formatExp(el){
  let v = el.value.replace(/\D/g,'').slice(0,4);
  if(v.length>2) v = v.slice(0,2)+'/'+v.slice(2);
  el.value = v;
  document.getElementById('pvExp').textContent = v || 'MM/YY';
}

function processPaymentForm(e){
  e.preventDefault();
  const num = document.getElementById('cardNum').value.replace(/\s/g,'');
  const exp = document.getElementById('cardExp').value;
  const cvv = document.getElementById('cardCvv').value;
  if(num.length !== 16){ showToast('❌ رقم البطاقة يجب أن يكون 16 رقماً','error'); return; }
  if(!/^\d{2}\/\d{2}$/.test(exp)){ showToast('❌ تاريخ الانتهاء غير صحيح (MM/YY)','error'); return; }
  const [m] = exp.split('/').map(Number);
  if(m<1||m>12){ showToast('❌ شهر غير صحيح','error'); return; }
  if(cvv.length !== 3){ showToast('❌ رمز CVV يجب أن يكون 3 أرقام','error'); return; }
  processPayment(e.target.querySelector('button[type=submit],button.btn'));
}

function processPayment(btn){
  btn.disabled = true;
  btn.innerHTML = 'جاري معالجة الدفع... <span class="spinner"></span>';
  setTimeout(()=>{ btn.innerHTML = 'جاري التحقق من البنك... <span class="spinner"></span>'; }, 1200);
  setTimeout(()=>{
    /* خصم المخزون */
    cart.forEach(i=>{ const p=PRODUCTS.find(x=>x.id===i.id); if(p) p.stock=Math.max(0,p.stock-i.qty); });
    DB.set('products', PRODUCTS);
    /* حفظ الطلب في قاعدة البيانات */
    const orders = DB.get('orders', []);
    const order = {
      id: Math.floor(100000+Math.random()*900000),
      date: new Date().toLocaleString('ar-SA'),
      customer: checkoutData.customer,
      items: cart.map(i=>({id:i.id,name:i.name,price:i.price,qty:i.qty,emoji:i.emoji})),
      total: checkoutData.total,
      payment: checkoutData.payment,
      status: 'جديد'
    };
    orders.push(order); DB.set('orders', orders);
    cart = []; saveCart();
    document.getElementById('modalBox').innerHTML = `
      <div class="modal-emoji">🎉</div>
      <h2>تم الدفع بنجاح!</h2>
      <p class="m-desc">رقم الطلب: <b style="color:var(--accent)">#${order.id}</b><br>وسيلة الدفع: ${order.payment}<br>سنتواصل معك قريباً لتأكيد التوصيل 📦</p>
      <button class="btn btn-primary" style="width:100%;text-align:center" onclick="closeModal()">متابعة التسوق 🛍️</button>`;
  }, 2600);
}

/* ================= TOAST ================= */
let toastTimer;
function showToast(msg, type){
  const t = document.getElementById('toast');
  t.textContent = msg; t.className = 'toast show'+(type?' '+type:'');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(()=>t.classList.remove('show'),2500);
}

/* ================= SCROLL ANIMATION ================= */
const obs = new IntersectionObserver(es=>es.forEach(e=>{ if(e.isIntersecting) e.target.classList.add('visible'); }),{threshold:.12});
document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));
document.querySelectorAll('#navLinks a').forEach(a=>a.addEventListener('click',()=>document.getElementById('navLinks').classList.remove('mobile-open')));

/* ================= INIT ================= */
renderFilters(); renderProducts(); updateCartUI();
if(sessionStorage.getItem('rom_admin')==='1') showAdminPanel();
</script>
</body>
</html>

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ROM — Real Orders More | متجرك الذكي</title>
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
:root{--bg:#000;--bg-soft:#f5f5f7;--text:#1d1d1f;--text-soft:#86868b;--accent:#0071e3;--accent-hover:#0077ed;--radius:18px;--max:1200px;--danger:#ff375f;--success:#34c759}
html{scroll-behavior:smooth}
body{font-family:"SF Pro Display","Segoe UI",Tahoma,Arial,sans-serif;background:var(--bg);color:var(--text);-webkit-font-smoothing:antialiased;overflow-x:hidden}
a{text-decoration:none;color:inherit}
button{font-family:inherit;cursor:pointer;border:none;background:none}
img{max-width:100%;display:block}
input,select,textarea{font-family:inherit}

/* NAVBAR */
nav{position:fixed;top:0;right:0;left:0;z-index:1000;backdrop-filter:saturate(180%) blur(20px);background:rgba(0,0,0,.8);height:52px;display:flex;align-items:center;justify-content:center}
.nav-inner{display:flex;align-items:center;gap:34px;max-width:var(--max);width:100%;padding:0 22px}
.logo{font-size:19px;font-weight:900;background:linear-gradient(135deg,#7d7aff,#0071e3);-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent;letter-spacing:.5px}
.nav-links{display:flex;gap:30px;list-style:none}
.nav-links a{color:#d6d6da;font-size:13px;transition:color .2s}
.nav-links a:hover{color:#fff}
.nav-icons{display:flex;gap:18px;align-items:center;margin-right:auto}
.nav-icon{color:#fff;font-size:17px;position:relative;transition:transform .2s}
.nav-icon:hover{transform:scale(1.1)}
.cart-badge{position:absolute;top:-7px;right:-8px;background:var(--accent);color:#fff;font-size:10px;font-weight:700;width:16px;height:16px;border-radius:50%;display:flex;align-items:center;justify-content:center;transform:scale(0);transition:transform .25s cubic-bezier(.68,-0.55,.27,1.55)}
.cart-badge.show{transform:scale(1)}
.search-bar{display:none;position:fixed;top:52px;right:0;left:0;z-index:999;background:#1d1d1f;padding:14px;text-align:center;box-shadow:0 10px 30px rgba(0,0,0,.4)}
.search-bar input{width:min(600px,90%);padding:10px 18px;border-radius:10px;border:none;font-size:14px;outline:none}
.hamburger{display:none;color:#fff;font-size:22px}

/* HERO */
.hero{min-height:92vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:110px 20px 60px;background:radial-gradient(ellipse at 50% 0%,#1a1a2e 0%,#000 60%)}
.hero h1{font-size:clamp(42px,7vw,84px);font-weight:800;letter-spacing:-2px;line-height:1.1;background:linear-gradient(180deg,#fff 30%,#7d7aff);-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
.hero p{color:#a1a1a6;font-size:clamp(16px,2.2vw,22px);margin:20px 0 34px;max-width:640px}
.btn{display:inline-block;padding:13px 30px;border-radius:980px;font-size:16px;font-weight:600;transition:all .25s}
.btn-primary{background:var(--accent);color:#fff}
.btn-primary:hover{background:var(--accent-hover);transform:translateY(-2px);box-shadow:0 8px 25px rgba(0,113,227,.4)}
.btn-ghost{color:var(--accent);border:1px solid var(--accent)}
.btn-ghost:hover{background:var(--accent);color:#fff}
.btn-danger{background:var(--danger);color:#fff;padding:9px 18px;border-radius:980px;font-size:13px;font-weight:600}
.btn-danger:hover{background:#d9264c}
.btn-small{padding:8px 16px;font-size:13px;border-radius:980px}
.hero-btns{display:flex;gap:16px;flex-wrap:wrap;justify-content:center}
.hero-visual{margin-top:50px;width:min(700px,90%);height:340px;background:linear-gradient(135deg,#2b2b4d,#0071e3 50%,#7d7aff);border-radius:30px;position:relative;overflow:hidden;box-shadow:0 40px 100px rgba(0,113,227,.3);animation:float 6s ease-in-out infinite;display:flex;align-items:center;justify-content:center;font-size:90px}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-15px)}}

section{padding:80px 20px}
.container{max-width:var(--max);margin:0 auto}
.section-title{font-size:clamp(30px,4.5vw,52px);font-weight:800;text-align:center;margin-bottom:10px;letter-spacing:-1px}
.section-sub{text-align:center;color:var(--text-soft);font-size:17px;margin-bottom:48px}

/* GRID */
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(270px,1fr));gap:24px}
.card{background:var(--bg-soft);border-radius:var(--radius);padding:30px 24px;text-align:center;transition:transform .35s cubic-bezier(.2,.8,.2,1),box-shadow .35s;cursor:pointer;position:relative;overflow:hidden}
.card:hover{transform:translateY(-8px);box-shadow:0 20px 50px rgba(0,0,0,.12)}
.card .emoji{font-size:72px;margin-bottom:18px;transition:transform .35s}
.card:hover .emoji{transform:scale(1.15) rotate(-5deg)}
.card h3{font-size:19px;font-weight:700;margin-bottom:6px}
.card .cat-tag{font-size:12px;color:var(--accent);font-weight:600;margin-bottom:8px;display:block}
.card p{color:var(--text-soft);font-size:14px;margin-bottom:14px;line-height:1.6;min-height:44px}
.stars{color:#ff9500;font-size:14px;margin-bottom:10px;letter-spacing:2px}
.price{font-size:22px;font-weight:800}
.price small{font-size:13px;color:var(--text-soft);font-weight:400}
.card .actions{display:flex;gap:10px;margin-top:18px}
.btn-add{flex:1;background:var(--accent);color:#fff;padding:11px;border-radius:980px;font-size:14px;font-weight:600;transition:all .2s}
.btn-add:hover{background:#000}
.btn-view{padding:11px 16px;border:1px solid #d2d2d7;border-radius:980px;font-size:14px;transition:all .2s}
.btn-view:hover{border-color:var(--text)}
.new-badge{position:absolute;top:16px;right:16px;background:linear-gradient(135deg,#ff375f,#ff9500);color:#fff;font-size:11px;font-weight:700;padding:5px 12px;border-radius:980px}
.sale-badge{position:absolute;top:16px;left:16px;background:var(--success);color:#fff;font-size:11px;font-weight:700;padding:5px 12px;border-radius:980px}
.old-price{text-decoration:line-through;color:var(--text-soft);font-size:14px;font-weight:400;margin-right:6px}

/* BAND */
.band{background:var(--bg-soft)}
.band-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(230px,1fr));gap:24px}
.band-card{background:#fff;border-radius:var(--radius);padding:36px 24px;text-align:center;transition:transform .3s}
.band-card:hover{transform:translateY(-6px)}
.band-card .ic{font-size:44px;margin-bottom:16px}
.band-card h4{font-size:17px;margin-bottom:8px}
.band-card p{color:var(--text-soft);font-size:14px;line-height:1.7}

.filters{display:flex;gap:12px;justify-content:center;flex-wrap:wrap;margin-bottom:44px}
.chip{padding:9px 22px;border-radius:980px;border:1px solid #d2d2d7;font-size:14px;transition:all .2s;background:#fff}
.chip:hover{border-color:var(--text)}
.chip.active{background:var(--text);color:#fff;border-color:var(--text)}

/* DRAWER */
.overlay{position:fixed;inset:0;background:rgba(0,0,0,.4);z-index:1100;opacity:0;pointer-events:none;transition:opacity .3s}
.overlay.open{opacity:1;pointer-events:auto}
.drawer{position:fixed;top:0;left:0;bottom:0;width:min(420px,92vw);background:#fff;z-index:1200;transform:translateX(-105%);transition:transform .4s cubic-bezier(.2,.8,.2,1);display:flex;flex-direction:column;box-shadow:20px 0 60px rgba(0,0,0,.2)}
.drawer.open{transform:translateX(0)}
.drawer-head{padding:22px 24px;border-bottom:1px solid #eee;display:flex;justify-content:space-between;align-items:center}
.drawer-head h3{font-size:20px}
.drawer-close{font-size:24px;color:var(--text-soft)}
.cart-items{flex:1;overflow-y:auto;padding:20px 24px}
.cart-item{display:flex;gap:14px;align-items:center;padding:14px 0;border-bottom:1px solid #f0f0f0}
.ci-emoji{font-size:38px;width:56px;height:56px;background:var(--bg-soft);border-radius:14px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.ci-info{flex:1}
.ci-info h5{font-size:15px}
.ci-info .ci-price{color:var(--text-soft);font-size:13px}
.qty{display:flex;align-items:center;gap:10px}
.qty button{width:26px;height:26px;border:1px solid #d2d2d7;border-radius:50%;font-size:15px;display:flex;align-items:center;justify-content:center;transition:all .2s}
.qty button:hover{background:var(--text);color:#fff}
.ci-del{color:var(--danger);font-size:18px;transition:transform .2s}
.ci-del:hover{transform:scale(1.2)}
.empty-cart{text-align:center;padding:60px 20px;color:var(--text-soft)}
.empty-cart .big{font-size:60px;margin-bottom:16px}
.drawer-foot{padding:22px 24px;border-top:1px solid #eee}
.total-row{display:flex;justify-content:space-between;font-size:18px;font-weight:700;margin-bottom:16px}
.checkout-btn{width:100%;background:var(--accent);color:#fff;padding:15px;border-radius:14px;font-size:16px;font-weight:700;transition:all .2s}
.checkout-btn:hover{background:#000}
.checkout-btn:disabled{background:#d2d2d7;cursor:not-allowed}

/* MODAL */
.modal{position:fixed;inset:0;z-index:1300;display:flex;align-items:center;justify-content:center;padding:20px;opacity:0;pointer-events:none;transition:opacity .3s}
.modal.open{opacity:1;pointer-events:auto}
.modal-bg{position:absolute;inset:0;background:rgba(0,0,0,.5);backdrop-filter:blur(6px)}
.modal-box{position:relative;background:#fff;border-radius:24px;max-width:640px;width:100%;max-height:88vh;overflow-y:auto;padding:40px;transform:scale(.92);transition:transform .35s}
.modal.open .modal-box{transform:scale(1)}
.modal-close{position:absolute;top:18px;left:18px;font-size:24px;color:var(--text-soft);width:36px;height:36px;border-radius:50%;background:var(--bg-soft);display:flex;align-items:center;justify-content:center;z-index:2}
.modal-emoji{font-size:100px;text-align:center;margin-bottom:20px}
.modal-box h2{text-align:center;font-size:28px;margin-bottom:8px}
.m-price{text-align:center;font-size:26px;font-weight:800;color:var(--accent);margin-bottom:14px}
.m-desc{color:var(--text-soft);text-align:center;line-height:1.8;margin-bottom:24px;font-size:15px}
.spec-list{background:var(--bg-soft);border-radius:14px;padding:18px 24px;margin-bottom:26px}
.spec-list li{display:flex;justify-content:space-between;padding:9px 0;font-size:14px;border-bottom:1px solid #e5e5ea;list-style:none}
.spec-list li:last-child{border:none}

/* TOAST */
.toast{position:fixed;bottom:30px;right:50%;transform:translate(50%,100px);background:#1d1d1f;color:#fff;padding:14px 28px;border-radius:980px;font-size:14px;z-index:1400;transition:transform .4s cubic-bezier(.2,.8,.2,1);display:flex;align-items:center;gap:10px;box-shadow:0 10px 30px rgba(0,0,0,.3)}
.toast.show{transform:translate(50%,0)}
.toast.success{background:var(--success)}
.toast.error{background:var(--danger)}

/* FOOTER */
footer{background:#f5f5f7;padding:60px 20px 30px;border-top:1px solid #d2d2d7}
.footer-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:34px;max-width:var(--max);margin:0 auto 40px}
.footer-grid h5{font-size:14px;margin-bottom:14px}
.footer-grid a{display:block;color:var(--text-soft);font-size:13px;margin-bottom:9px;transition:color .2s}
.footer-grid a:hover{color:var(--text)}
.footer-bottom{text-align:center;color:var(--text-soft);font-size:12px;border-top:1px solid #d2d2d7;padding-top:22px;max-width:var(--max);margin:0 auto}

/* FORMS */
.form-group{margin-bottom:16px}
.form-group label{display:block;font-size:13px;font-weight:600;margin-bottom:6px}
.form-group input,.form-group select,.form-group textarea{width:100%;padding:12px 16px;border:1px solid #d2d2d7;border-radius:12px;font-size:14px;outline:none;transition:border .2s;background:#fff}
.form-group input:focus,.form-group select:focus,.form-group textarea:focus{border-color:var(--accent)}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:14px}
.form-error{color:var(--danger);font-size:12px;margin-top:4px;display:none}
.form-group.invalid input{border-color:var(--danger)}
.form-group.invalid .form-error{display:block}

/* PAYMENT */
.pay-methods{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:22px}
.pay-method{border:2px solid #d2d2d7;border-radius:14px;padding:14px 8px;text-align:center;font-size:13px;font-weight:700;transition:all .2s;background:#fff}
.pay-method .pi{font-size:26px;display:block;margin-bottom:6px}
.pay-method.active{border-color:var(--accent);background:#f0f7ff}
.card-preview{background:linear-gradient(135deg,#1a1a2e,#2b2b4d);border-radius:18px;padding:22px;color:#fff;margin-bottom:20px;font-family:monospace;min-height:140px;display:flex;flex-direction:column;justify-content:space-between}
.card-preview .num{font-size:20px;letter-spacing:3px}
.card-preview .row{display:flex;justify-content:space-between;font-size:13px;color:#a1a1a6}
.spinner{display:inline-block;width:18px;height:18px;border:3px solid rgba(255,255,255,.3);border-top-color:#fff;border-radius:50%;animation:spin .7s linear infinite;vertical-align:middle;margin-left:8px}
@keyframes spin{to{transform:rotate(360deg)}}
.secure-note{display:flex;align-items:center;justify-content:center;gap:6px;color:var(--text-soft);font-size:12px;margin-top:14px}

/* ============ ADMIN ============ */
.admin-layout{display:grid;grid-template-columns:230px 1fr;min-height:100vh}
.admin-side{background:#1d1d1f;color:#fff;padding:26px 18px;position:sticky;top:0;height:100vh}
.admin-side .logo{font-size:22px;margin-bottom:36px;display:block;text-align:center}
.admin-nav a{display:flex;gap:10px;align-items:center;padding:12px 14px;border-radius:12px;color:#a1a1a6;font-size:14px;margin-bottom:6px;transition:all .2s}
.admin-nav a:hover{background:#2c2c2e;color:#fff}
.admin-nav a.active{background:var(--accent);color:#fff}
.admin-main{background:var(--bg-soft);padding:32px;overflow-y:auto}
.admin-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:28px}
.admin-top h2{font-size:26px;font-weight:800}
.stats-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:18px;margin-bottom:30px}
.stat-card{background:#fff;border-radius:var(--radius);padding:24px;box-shadow:0 2px 12px rgba(0,0,0,.05)}
.stat-card .si{font-size:30px;margin-bottom:10px}
.stat-card .sv{font-size:28px;font-weight:800}
.stat-card .sl{color:var(--text-soft);font-size:13px;margin-top:4px}
.admin-table{width:100%;background:#fff;border-radius:var(--radius);overflow:hidden;border-collapse:collapse;box-shadow:0 2px 12px rgba(0,0,0,.05)}
.admin-table th{background:#fafafa;padding:14px;font-size:13px;color:var(--text-soft);text-align:right;border-bottom:2px solid #f0f0f0}
.admin-table td{padding:14px;font-size:14px;border-bottom:1px solid #f5f5f7;vertical-align:middle}
.admin-table tr:hover td{background:#fafafa}
.admin-table .pe{font-size:28px}
.status-pill{padding:4px 14px;border-radius:980px;font-size:12px;font-weight:700;display:inline-block}
.status-new{background:#e8f0fe;color:var(--accent)}
.status-shipped{background:#fff4e5;color:#ff9500}
.status-done{background:#e8f9ee;color:var(--success)}
.status-cancel{background:#ffe8ec;color:var(--danger)}
.admin-actions{dis
