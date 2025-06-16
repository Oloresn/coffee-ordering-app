<!DOCTYPE html>
<html lang="en" >
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Coffee Ordering Mobile App</title>

  <!-- Material Icons -->
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet" />

  <style>
    /* Reset and box-sizing */
    *, *::before, *::after {
      box-sizing: border-box;
    }
    body {
      margin: 0;
      background-color: var(--bg);
      color: var(--text);
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
      Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      min-height: 100vh;
      display: grid;
      grid-template-rows: var(--header-height) 1fr auto;
      grid-template-columns: 1fr;
      overflow: hidden;
      --color-bg-light: #fff9f4;
      --color-bg-dark: #1e1e1e;
      --color-text-light: #3c2f2f;
      --color-text-dark: #eee7e2;
      --color-primary: #7b3f00;
      --color-secondary: #c18d53;
      --color-muted-light: #a38e79;
      --color-muted-dark: #6f675f;
      --radius: 14px;
      --header-height: 64px;
      --sidebar-width: 260px;
      --shadow-glass-light: rgba(255, 255, 255, 0.6);
      --shadow-glass-dark: rgba(20,20,20,0.8);
      --transition-fast: 0.25s cubic-bezier(0.4,0,0.2,1);
    }
    [data-theme="light"] {
      --bg: var(--color-bg-light);
      --text: var(--color-text-light);
      --muted: var(--color-muted-light);
      --shadow-glass: var(--shadow-glass-light);
    }
    [data-theme="dark"] {
      --bg: var(--color-bg-dark);
      --text: var(--color-text-dark);
      --muted: var(--color-muted-dark);
      --shadow-glass: var(--shadow-glass-dark);
    }

    /* Scrollbar styling */
    ::-webkit-scrollbar {
      width: 12px;
      height: 12px;
    }
    ::-webkit-scrollbar-track {
      background: transparent;
    }
    ::-webkit-scrollbar-thumb {
      background-color: var(--muted);
      border-radius: var(--radius);
      border: 3px solid transparent;
      background-clip: content-box;
    }

    /* Header */
    header {
      grid-row: 1;
      position: sticky;
      top: 0;
      height: var(--header-height);
      backdrop-filter: saturate(180%) blur(15px);
      background: rgba(255 249 244 / 0.75);
      box-shadow: 0 2px 8px var(--shadow-glass);
      padding: 0 20px;
      display: flex;
      align-items: center;
      gap: 12px;
      color: var(--color-primary);
      user-select: none;
      z-index: 1000;
      transition: background var(--transition-fast);
    }
    [data-theme="dark"] header {
      background: rgba(30 30 30 / 0.85);
      color: var(--color-secondary);
    }
    header .logo {
      font-weight: 900;
      font-size: 24px;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      flex-shrink: 0;
    }
    header .nav-spacer {
      flex-grow: 1;
    }
    header button.theme-toggle {
      background: none;
      border: none;
      cursor: pointer;
      color: inherit;
      font-size: 26px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: var(--radius);
      padding: 8px;
      transition: background-color var(--transition-fast);
    }
    header button.theme-toggle:hover,
    header button.theme-toggle:focus {
      background: var(--color-secondary);
      color: var(--color-bg-dark);
      outline: none;
    }

    /* Sidebar */
    nav.sidebar {
      grid-row: 2;
      position: fixed;
      top: var(--header-height);
      bottom: 0;
      left: 0;
      width: var(--sidebar-width);
      background: var(--bg);
      box-shadow: inset -1px 0 0 var(--muted);
      font-weight: 700;
      padding-top: 16px;
      display: flex;
      flex-direction: column;
      gap: 6px;
      overflow-y: auto;
      -webkit-overflow-scrolling: touch;
      transition: transform 0.3s ease;
      z-index: 1000;
      /* Glass morphism */
      backdrop-filter: saturate(180%) blur(15px);
    }
    nav.sidebar.mobile-hidden {
      transform: translateX(-280px);
    }
    nav.sidebar ul {
      padding: 0 12px 12px;
      margin: 0;
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    nav.sidebar li {
      cursor: pointer;
      padding: 10px 18px;
      border-radius: var(--radius);
      display: flex;
      align-items: center;
      gap: 16px;
      color: var(--color-primary);
      transition: background-color var(--transition-fast);
      user-select: none;
      font-size: 18px;
    }
    [data-theme="dark"] nav.sidebar li {
      color: var(--color-secondary);
    }
    nav.sidebar li:hover,
    nav.sidebar li[data-selected="true"],
    nav.sidebar li:focus-visible {
      background: var(--color-secondary);
      color: var(--color-bg-dark);
      outline: none;
    }
    nav.sidebar li .material-icons-outlined {
      flex-shrink: 0;
      font-size: 24px;
    }
    /* Sidebar toggle button for mobile */
    button.sidebar-toggle {
      position: fixed;
      top: calc(var(--header-height)/2);
      left: 0;
      width: 40px;
      height: 40px;
      background: var(--bg);
      border-radius: 0 14px 14px 0;
      box-shadow: 2px 2px 12px var(--shadow-glass);
      border: none;
      cursor: pointer;
      z-index: 1050;
      display: none;
      align-items: center;
      justify-content: center;
      color: var(--color-primary);
      transition: background-color var(--transition-fast);
    }
    button.sidebar-toggle:hover,
    button.sidebar-toggle:focus {
      background: var(--color-secondary);
      color: var(--color-bg-dark);
      outline: none;
    }

    /* Main Content */
    main.content {
      grid-row: 2;
      margin-left: var(--sidebar-width);
      padding: 20px 24px 80px;
      height: calc(100vh - var(--header-height));
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      gap: 32px;
      background: var(--bg);
      transition: margin-left 0.3s ease;
    }
    main.content.fullwidth {
      margin-left: 0;
    }
    main h2 {
      font-weight: 800;
      font-size: 22px;
      margin-bottom: 8px;
      color: var(--color-primary);
    }

    /* Coffee Category List */
    .category-list {
      display: flex;
      gap: 16px;
      overflow-x: auto;
      padding-bottom: 12px;
      scroll-padding-inline: 12px;
    }
    .category-item {
      background: var(--color-secondary);
      color: var(--color-bg-dark);
      font-weight: 700;
      padding: 8px 16px;
      border-radius: var(--radius);
      box-shadow: 0 4px 12px rgba(123, 63, 0, 0.3);
      cursor: pointer;
      white-space: nowrap;
      user-select: none;
      transition: background-color var(--transition-fast);
      flex-shrink: 0;
      display: flex;
      align-items: center;
      gap: 6px;
      font-size: 16px;
    }
    .category-item[data-selected="true"], .category-item:hover, .category-item:focus-visible {
      background: var(--color-primary);
      color: var(--color-bg-light);
      outline: none;
    }
    .category-item .material-icons {
      font-size: 20px;
    }

    /* Coffee List */
    .coffee-list {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
      gap: 20px;
    }
    .coffee-card {
      background: var(--bg);
      border-radius: var(--radius);
      box-shadow: 0 6px 14px rgba(123, 63, 0, 0.15);
      display: flex;
      flex-direction: column;
      overflow: hidden;
      transition: box-shadow var(--transition-fast);
      user-select: none;
    }
    .coffee-card:focus-within, .coffee-card:hover {
      box-shadow: 0 10px 26px rgba(123, 63, 0, 0.4);
      outline: none;
    }
    .coffee-image {
      width: 100%;
      height: 160px;
      object-fit: cover;
      background-color: var(--color-muted-light);
    }
    .coffee-content {
      padding: 12px 16px;
      flex-grow: 1;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .coffee-title {
      font-weight: 700;
      font-size: 18px;
      color: var(--color-primary);
      margin: 0;
      user-select: text;
    }
    .coffee-desc {
      font-size: 14px;
      color: var(--muted);
      flex-grow: 1;
      user-select: text;
    }
    .coffee-price {
      font-weight: 700;
      font-size: 16px;
      color: var(--color-secondary);
    }
    .coffee-actions {
      display: flex;
      justify-content: flex-end;
      gap: 12px;
      padding-top: 8px;
    }
    .coffee-actions button {
      background-color: var(--color-primary);
      color: var(--color-bg-light);
      border: none;
      border-radius: 24px;
      padding: 8px 16px;
      font-weight: 700;
      cursor: pointer;
      transition: background-color var(--transition-fast);
      user-select: none;
      font-size: 14px;
      display: flex;
      align-items: center;
      gap: 6px;
    }
    .coffee-actions button:hover,
    .coffee-actions button:focus {
      background-color: var(--color-secondary);
      outline: none;
    }
    .coffee-actions .material-icons {
      font-size: 18px;
    }
    /* Disabled button */
    button:disabled {
      background-color: var(--muted);
      cursor: default;
      color: var(--bg);
    }

    /* Cart Section */
    #cart-section {
      background: var(--bg);
      padding: 16px 20px;
      border-radius: var(--radius);
      box-shadow: 0 6px 14px rgba(123, 63, 0, 0.15);
      max-width: 500px;
      width: 100%;
      margin: 0 auto;
    }
    #cart-section h2 {
      text-align: center;
      margin-bottom: 16px;
      color: var(--color-primary);
    }
    .cart-items {
      max-height: 260px;
      overflow-y: auto;
      margin-bottom: 16px;
      border-top: 1px solid var(--muted);
      border-bottom: 1px solid var(--muted);
    }
    .cart-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 12px 0;
      border-bottom: 1px solid var(--muted);
      user-select: none;
    }
    .cart-item:last-child {
      border-bottom: none;
    }
    .cart-item .title {
      font-weight: 700;
      font-size: 16px;
      color: var(--color-primary);
      flex: 1;
      user-select: text;
    }
    .cart-item .quantity-controls {
      display: flex;
      align-items: center;
      gap: 12px;
      user-select: none;
    }
    .quantity-btn {
      border: none;
      background: var(--color-primary);
      color: var(--color-bg-light);
      border-radius: 50%;
      width: 28px;
      height: 28px;
      font-size: 20px;
      line-height: 20px;
      cursor: pointer;
      user-select: none;
      transition: background-color var(--transition-fast);
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .quantity-btn:disabled {
      background: var(--muted);
      cursor: default;
    }
    .quantity-btn:hover:not(:disabled),
    .quantity-btn:focus:not(:disabled) {
      background: var(--color-secondary);
      outline: none;
    }
    .quantity-display {
      min-width: 24px;
      text-align: center;
      font-size: 16px;
      user-select: text;
    }
    .cart-item .remove-btn {
      background: none;
      border: none;
      color: var(--color-error);
      cursor: pointer;
      font-size: 20px;
      transition: color var(--transition-fast);
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .cart-item .remove-btn:hover,
    .cart-item .remove-btn:focus {
      color: #a32e2e;
      outline: none;
    }
    #cart-total {
      font-weight: 800;
      font-size: 18px;
      text-align: right;
      margin-top: 12px;
      color: var(--color-secondary);
    }
    #checkout-btn {
      margin-top: 12px;
      width: 100%;
      padding: 12px;
      font-size: 18px;
      font-weight: 700;
    }

    /* Checkout Modal */
    .modal {
      position: fixed;
      inset: 0;
      background: rgba(30,30,30,0.75);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 2000;
      padding: 16px;
    }
    .modal-content {
      background: var(--bg);
      border-radius: var(--radius);
      width: 100%;
      max-width: 400px;
      box-shadow: 0 10px 30px rgba(123, 63, 0, 0.7);
      padding: 24px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      position: relative;
    }
    .modal-close-btn {
      position: absolute;
      top: 10px;
      right: 10px;
      border: none;
      background: none;
      color: var(--color-primary);
      font-size: 24px;
      cursor: pointer;
      transition: color var(--transition-fast);
    }
    .modal-close-btn:hover,
    .modal-close-btn:focus {
      color: var(--color-secondary);
      outline: none;
    }
    .modal-content h3 {
      margin-top: 0;
      text-align: center;
      color: var(--color-primary);
    }
    .modal-content form {
      display: flex;
      flex-direction: column;
      gap: 14px;
    }
    .modal-content label {
      font-weight: 600;
      font-size: 15px;
      color: var(--color-primary);
    }
    .modal-content input[type="text"],
    .modal-content input[type="email"],
    .modal-content textarea {
      padding: 10px 12px;
      border-radius: var(--radius);
      border: 1.5px solid var(--muted);
      background: var(--bg);
      color: var(--text);
      font-size: 14px;
      transition: border-color var(--transition-fast);
      resize: vertical;
    }
    .modal-content input[type="text"]:focus,
    .modal-content input[type="email"]:focus,
    .modal-content textarea:focus {
      border-color: var(--color-primary);
      outline: none;
      box-shadow: 0 0 10px var(--color-primary);
    }
    .modal-content .field-error {
      color: var(--color-error);
      font-size: 13px;
      font-weight: 700;
      margin-top: -8px;
      margin-bottom: 4px;
    }
    .modal-content button.submit-btn {
      background-color: var(--color-primary);
      color: var(--bg);
      padding: 12px;
      font-weight: 700;
      border: none;
      cursor: pointer;
      border-radius: var(--radius);
      font-size: 18px;
      transition: background-color var(--transition-fast);
    }
    .modal-content button.submit-btn:hover,
    .modal-content button.submit-btn:focus {
      background-color: var(--color-secondary);
      outline: none;
    }

    /* Toast container */
    #toast-container {
      position: fixed;
      top: var(--header-height);
      right: 20px;
      max-width: 320px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      z-index: 2500;
      pointer-events: none;
    }
    .toast {
      pointer-events: auto;
      background: var(--bg);
      color: var(--color-primary);
      padding: 12px 20px;
      border-radius: var(--radius);
      box-shadow: 0 6px 14px rgba(123, 63, 0, 0.3);
      display: flex;
      align-items: center;
      gap: 16px;
      font-weight: 700;
      animation: slideInRight 0.3s ease forwards;
      user-select: none;
    }
    .toast.success {
      border-left: 4px solid var(--color-secondary);
      color: var(--color-secondary);
    }
    .toast.error {
      border-left: 4px solid #bb1e0a;
      color: #bb1e0a;
    }
    .toast .material-icons {
      font-size: 24px;
    }
    .toast button.close-btn {
      background: none;
      border: none;
      color: inherit;
      font-weight: 700;
      font-size: 18px;
      margin-left: auto;
      cursor: pointer;
      padding: 0;
      line-height: 0;
      transition: color var(--transition-fast);
      border-radius: var(--radius);
      outline-offset: 2px;
    }
    .toast button.close-btn:hover,
    .toast button.close-btn:focus {
      color: var(--color-primary);
      outline: none;
    }

    @keyframes slideInRight {
      from {
        opacity: 0;
        transform: translateX(40px);
      }
      to {
        opacity: 1;
        transform: translateX(0);
      }
    }

    /* Responsive */
    @media (max-width: 767px) {
      nav.sidebar {
        top: 0;
        height: 100vh;
        transform: translateX(-280px);
        box-shadow: 6px 0 20px rgba(0,0,0,0.4);
        width: 280px;
      }
      nav.sidebar.mobile-visible {
        transform: translateX(0);
      }
      main.content {
        margin-left: 0;
        padding-bottom: 80px;
      }
      button.sidebar-toggle {
        display: flex;
      }
    }
    @media (min-width: 768px) {
      button.sidebar-toggle {
        display: none;
      }
      nav.sidebar {
        transform: translateX(0) !important;
      }
    }
  </style>
</head>
<body data-theme="light">

  <header role="banner" aria-label="Application header">
    <button class="sidebar-toggle" aria-label="Toggle menu navigation" aria-controls="sidebar" aria-expanded="false">
      <span class="material-icons">menu</span>
    </button>
    <span class="logo" tabindex="0">CoffeeHub</span>
    <div class="nav-spacer"></div>
    <button class="theme-toggle" aria-label="Toggle color theme" title="Toggle color theme">
      <span class="material-icons" aria-hidden="true">dark_mode</span>
    </button>
  </header>

  <nav id="sidebar" role="navigation" aria-label="Coffee categories and navigation" class="sidebar mobile-hidden">
    <ul id="category-list" tabindex="0">
      <!-- Categories inserted by JS -->
    </ul>
  </nav>

  <main class="content" role="main" tabindex="0" aria-live="polite" aria-atomic="true">
    <section aria-label="Coffee products" id="coffees-section">
      <h2>Our Coffees</h2>
      <div id="coffee-list" class="coffee-list" tabindex="0">
        <!-- Coffee products inserted by JS -->
      </div>
    </section>

    <section aria-label="Cart summary" id="cart-section" tabindex="0">
      <h2>Your Cart</h2>
      <div class="cart-items" id="cart-items" tabindex="0" aria-live="polite" aria-relevant="additions removals">
        <!-- Cart items inserted by JS -->
      </div>
      <div id="cart-total">Total: $0.00</div>
      <button id="checkout-btn" disabled>Checkout</button>
    </section>
  </main>

  <!-- Checkout Modal -->
  <div id="checkout-modal" class="modal" role="dialog" aria-modal="true" aria-hidden="true" aria-labelledby="checkout-title" tabindex="-1" style="display:none">
    <div class="modal-content">
      <button class="modal-close-btn" aria-label="Close checkout form">
        <span class="material-icons">close</span>
      </button>
      <h3 id="checkout-title">Complete Your Order</h3>
      <form id="checkout-form" novalidate>
        <label for="cust-name">Name</label>
        <input type="text" id="cust-name" name="name" autocomplete="name" required aria-required="true" />
        <div class="field-error" id="name-error" aria-live="assertive"></div>

        <label for="cust-email">Email</label>
        <input type="email" id="cust-email" name="email" autocomplete="email" required aria-required="true" />
        <div class="field-error" id="email-error" aria-live="assertive"></div>

        <label for="cust-address">Address</label>
        <textarea id="cust-address" name="address" rows="3" autocomplete="street-address" required aria-required="true"></textarea>
        <div class="field-error" id="address-error" aria-live="assertive"></div>

        <button type="submit" class="submit-btn">Place Order</button>
      </form>
    </div>
  </div>

  <!-- Toast notifications container -->
  <div id="toast-container" role="region" aria-live="assertive" aria-atomic="false"></div>

  <script>
    (() => {
      const COFFEE_CATEGORIES = [
        { id: 'c1', name: 'Espresso', icon: 'local_cafe' },
        { id: 'c2', name: 'Latte', icon: 'free_breakfast' },
        { id: 'c3', name: 'Cold Brew', icon: 'icecream' },
        { id: 'c4', name: 'Specialty', icon: 'emoji_food_beverage' }
      ];
      const COFFEE_PRODUCTS = [
        {
          id: 'p1',
          title: "Classic Espresso",
          description: "Strong and bold shot of pure espresso.",
          category: 'c1',
          price: 2.85,
          image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/b06d8ee3-0301-4f5a-82d5-fd053625201f.png",
          alt: "Close-up of classic Espresso coffee shot in a small cup"
        },
        {
          id: 'p2',
          title: "Vanilla Latte",
          description: "Smooth latte with vanilla syrup and rich foam.",
          category: 'c2',
          price: 4.50,
          image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/fd12c8fd-9a32-4dba-9361-697b50a8bc7a.png",
          alt: "A cup of vanilla latte with frothy milk and vanilla drizzle"
        },
        {
          id: 'p3',
          title: "Iced Cold Brew",
          description: "Refreshing cold brew coffee served over ice.",
          category: 'c3',
          price: 3.95,
          image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/d4b742e3-6ec6-4b3f-9bc6-66a220aaada8.png",
          alt: "Tall glass of iced cold brew coffee with ice cubes"
        },
        {
          id: 'p4',
          title: "Mocha Deluxe",
          description: "Delicious blend of espresso, chocolate, and steamed milk.",
          category: 'c4',
          price: 5.20,
          image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/ec2013c7-1873-4a80-b012-157fd6c64e3f.png",
          alt: "Cup of mocha deluxe coffee with chocolate drizzle on top"
        },
        {
          id: 'p5',
          title: "Caramel Macchiato",
          description: "Rich espresso layered with steamed milk and caramel sauce.",
          category: 'c2',
          price: 4.75,
          image: "https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/8638f8b8-a104-43d0-8968-383cd90c56ca.png",
          alt: "Cup of caramel macchiato coffee with caramel drizzle on top"
        }
      ];

      let currentTheme = 'light';
      const bodyEl = document.body;
      const categoryListEl = document.getElementById('category-list');
      const coffeeListEl = document.getElementById('coffee-list');
      const cartItemsEl = document.getElementById('cart-items');
      const cartTotalEl = document.getElementById('cart-total');
      const checkoutBtn = document.getElementById('checkout-btn');
      const checkoutModal = document.getElementById('checkout-modal');
      const checkoutForm = document.getElementById('checkout-form');
      const toastContainer = document.getElementById('toast-container');
      const headerThemeToggleBtn = document.querySelector('button.theme-toggle');
      const sidebarToggleBtn = document.querySelector('button.sidebar-toggle');
      const sidebarNav = document.getElementById('sidebar');

      let cart = {};
      let selectedCategory = null;

      function init() {
        renderCategories();
        renderCoffees();
        renderCart();
        applyTheme(currentTheme);

        headerThemeToggleBtn.addEventListener('click', toggleTheme);
        sidebarToggleBtn.addEventListener('click', toggleSidebar);

        checkoutBtn.addEventListener('click', openCheckoutModal);

        checkoutForm.addEventListener('submit', handleCheckoutSubmit);

        window.addEventListener('keydown', e => {
          if (e.key === 'Escape' && checkoutModal.style.display === 'flex') {
            closeCheckoutModal();
          }
        });

        const closeModalBtn = checkoutModal.querySelector('.modal-close-btn');
        closeModalBtn.addEventListener('click', closeCheckoutModal);

        document.addEventListener('click', e => {
          if (window.innerWidth <= 767 && sidebarNav.classList.contains('mobile-visible')) {
            if (!sidebarNav.contains(e.target) && !sidebarToggleBtn.contains(e.target)) {
              sidebarNav.classList.remove('mobile-visible');
              sidebarToggleBtn.setAttribute('aria-expanded', 'false');
            }
          }
        });
      }

      function renderCategories() {
        categoryListEl.innerHTML = '';
        const allItem = document.createElement('li');
        allItem.textContent = 'All Coffees';
        allItem.className = 'category-item';
        allItem.setAttribute('tabindex', '0');
        allItem.dataset.selected = selectedCategory === null ? 'true' : 'false';
        allItem.addEventListener('click', () => selectCategory(null));
        allItem.addEventListener('keydown', e => {
          if (e.key === 'Enter' || e.key === ' ') {
            e.preventDefault();
            selectCategory(null);
          }
        });
        categoryListEl.appendChild(allItem);

        COFFEE_CATEGORIES.forEach(cat => {
          const li = document.createElement('li');
          li.className = 'category-item';
          li.dataset.selected = selectedCategory === cat.id ? 'true' : 'false';
          li.setAttribute('tabindex', '0');
          li.innerHTML = `<span class="material-icons">${cat.icon}</span>${cat.name}`;
          li.addEventListener('click', () => selectCategory(cat.id));
          li.addEventListener('keydown', e => {
            if (e.key === 'Enter' || e.key === ' ') {
              e.preventDefault();
              selectCategory(cat.id);
            }
          });
          categoryListEl.appendChild(li);
        });
      }

      function selectCategory(catId) {
        if (catId === selectedCategory) return;
        selectedCategory = catId;
        renderCategories();
        renderCoffees();
      }

      function renderCoffees() {
        coffeeListEl.innerHTML = '';
        let filtered = COFFEE_PRODUCTS;
        if (selectedCategory) {
          filtered = COFFEE_PRODUCTS.filter(p => p.category === selectedCategory);
        }
        if (filtered.length === 0) {
          coffeeListEl.textContent = 'No coffees in this category.';
          return;
        }
        filtered.forEach(coffee => {
          const card = document.createElement('article');
          card.className = 'coffee-card';
          card.setAttribute('tabindex', '0');
          card.setAttribute('aria-label', `${coffee.title}, price $${coffee.price.toFixed(2)}`);

          const img = document.createElement('img');
          img.className = 'coffee-image';
          img.src = coffee.image;
          img.alt = coffee.alt || coffee.title;
          img.loading = 'lazy';
          card.appendChild(img);

          const contentDiv = document.createElement('div');
          contentDiv.className = 'coffee-content';

          const titleEl = document.createElement('h3');
          titleEl.className = 'coffee-title';
          titleEl.textContent = coffee.title;
          contentDiv.appendChild(titleEl);

          const descEl = document.createElement('p');
          descEl.className = 'coffee-desc';
          descEl.textContent = coffee.description;
          contentDiv.appendChild(descEl);

          const priceEl = document.createElement('div');
          priceEl.className = 'coffee-price';
          priceEl.textContent = `$${coffee.price.toFixed(2)}`;
          contentDiv.appendChild(priceEl);

          const actionsDiv = document.createElement('div');
          actionsDiv.className = 'coffee-actions';

          const addBtn = document.createElement('button');
          addBtn.type = 'button';
          addBtn.innerHTML = '<span class="material-icons">add_shopping_cart</span> Add';
          addBtn.setAttribute('aria-label', `Add ${coffee.title} to cart`);
          addBtn.addEventListener('click', () => addToCart(coffee.id));
          actionsDiv.appendChild(addBtn);

          contentDiv.appendChild(actionsDiv);

          card.appendChild(contentDiv);

          coffeeListEl.appendChild(card);
        });
      }

      function addToCart(productId) {
        if (!cart[productId]) {
          cart[productId] = 1;
        } else {
          cart[productId]++;
        }
        renderCart();
        showToast("Added coffee to cart.", {type:"success"});
      }

      function renderCart() {
        cartItemsEl.innerHTML = '';
        const productIds = Object.keys(cart);
        if (productIds.length === 0) {
          cartItemsEl.textContent = "Your cart is empty.";
          cartTotalEl.textContent = "Total: $0.00";
          checkoutBtn.disabled = true;
          return;
        }

        let total = 0;
        productIds.forEach(pid => {
          const qty = cart[pid];
          const prod = COFFEE_PRODUCTS.find(p => p.id === pid);
          if (!prod) return;
          total += prod.price * qty;

          const itemDiv = document.createElement('div');
          itemDiv.className = 'cart-item';
          itemDiv.tabIndex = 0;
          itemDiv.setAttribute('aria-label', `${prod.title}, quantity ${qty}`);

          const titleSpan = document.createElement('span');
          titleSpan.className = 'title';
          titleSpan.textContent = prod.title;
          itemDiv.appendChild(titleSpan);

          const controlsDiv = document.createElement('div');
          controlsDiv.className = 'quantity-controls';

          const decBtn = document.createElement('button');
          decBtn.className = 'quantity-btn';
          decBtn.setAttribute('aria-label', `Decrease quantity of ${prod.title}`);
          decBtn.innerHTML = '<span class="material-icons">remove</span>';
          decBtn.disabled = qty <= 1;
          decBtn.addEventListener('click', () => {
            if (cart[pid] > 1) {
              cart[pid]--;
              renderCart();
            }
          });
          controlsDiv.appendChild(decBtn);

          const qtyDisplay = document.createElement('span');
          qtyDisplay.className = 'quantity-display';
          qtyDisplay.textContent = qty;
          qtyDisplay.setAttribute('aria-live', 'polite');
          qtyDisplay.setAttribute('aria-atomic', 'true');
          controlsDiv.appendChild(qtyDisplay);

          const incBtn = document.createElement('button');
          incBtn.className = 'quantity-btn';
          incBtn.setAttribute('aria-label', `Increase quantity of ${prod.title}`);
          incBtn.innerHTML = '<span class="material-icons">add</span>';
          incBtn.addEventListener('click', () => {
            cart[pid]++;
            renderCart();
          });
          controlsDiv.appendChild(incBtn);

          const removeBtn = document.createElement('button');
          removeBtn.className = 'remove-btn';
          removeBtn.setAttribute('aria-label', `Remove ${prod.title} from cart`);
          removeBtn.innerHTML = '<span class="material-icons">delete</span>';
          removeBtn.addEventListener('click', () => {
            delete cart[pid];
            renderCart();
            showToast(`Removed ${prod.title} from cart.`, {type:'warning'});
          });
          controlsDiv.appendChild(removeBtn);

          itemDiv.appendChild(controlsDiv);

          cartItemsEl.appendChild(itemDiv);
        });

        cartTotalEl.textContent = `Total: $${total.toFixed(2)}`;
        checkoutBtn.disabled = productIds.length === 0;
      }

      function toggleSidebar() {
        const isVisible = sidebarNav.classList.contains('mobile-visible');
        if (isVisible) {
          sidebarNav.classList.remove('mobile-visible');
          sidebarToggleBtn.setAttribute('aria-expanded', 'false');
        } else {
          sidebarNav.classList.add('mobile-visible');
          sidebarToggleBtn.setAttribute('aria-expanded', 'true');
          const firstCategory = categoryListEl.querySelector('li');
          if (firstCategory) firstCategory.focus();
        }
      }

      function applyTheme(theme) {
        currentTheme = theme;
        bodyEl.setAttribute('data-theme', theme);
        if (theme === 'dark') {
          headerThemeToggleBtn.querySelector('span').textContent = 'light_mode';
          headerThemeToggleBtn.setAttribute('aria-label', 'Switch to light theme');
        } else {
          headerThemeToggleBtn.querySelector('span').textContent = 'dark_mode';
          headerThemeToggleBtn.setAttribute('aria-label', 'Switch to dark theme');
        }
      }

      function toggleTheme() {
        const newTheme = currentTheme === 'light' ? 'dark' : 'light';
        applyTheme(newTheme);
        showToast(`Switched to ${newTheme} theme.`, {type:'success'});
      }

      function openCheckoutModal() {
        if (Object.keys(cart).length === 0) {
          showToast("Your cart is empty. Add coffee before checkout.", {type:'error'});
          return;
        }
        checkoutModal.style.display = 'flex';
        checkoutModal.setAttribute('aria-hidden', 'false');
        checkoutForm.elements[0]?.focus();
      }

      function closeCheckoutModal() {
        checkoutModal.style.display = 'none';
        checkoutModal.setAttribute('aria-hidden', 'true');
        checkoutBtn.focus();
        clearCheckoutForm();
      }

      function validateEmail(email) {
        return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
      }

      function handleCheckoutSubmit(e) {
        e.preventDefault();
        const nameInput = checkoutForm.elements['name'];
        const emailInput = checkoutForm.elements['email'];
        const addressInput = checkoutForm.elements['address'];

        const nameError = document.getElementById('name-error');
        const emailError = document.getElementById('email-error');
        const addressError = document.getElementById('address-error');

        nameError.textContent = '';
        emailError.textContent = '';
        addressError.textContent = '';

        let valid = true;

        if (!nameInput.value.trim()) {
          nameError.textContent = 'Name is required.';
          valid = false;
        }
        if (!emailInput.value.trim()) {
          emailError.textContent = 'Email is required.';
          valid = false;
        } else if (!validateEmail(emailInput.value.trim())) {
          emailError.textContent = 'Invalid email address.';
          valid = false;
        }
        if (!addressInput.value.trim()) {
          addressError.textContent = 'Address is required.';
          valid = false;
        }

        if (!valid) return;

        showToast('Processing your order...', {type: 'info', duration: 2000});
        setTimeout(() => {
          showToast('Order placed successfully. Thank you!', {type:'success'});
          cart = {};
          renderCart();
          closeCheckoutModal();
        }, 2000);
      }

      function clearCheckoutForm() {
        checkoutForm.reset();
        document.getElementById('name-error').textContent = '';
        document.getElementById('email-error').textContent = '';
        document.getElementById('address-error').textContent = '';
      }

      function showToast(message, {type='info', duration=4000} = {}) {
        const toast = document.createElement('div');
        toast.className = `toast ${type}`;
        const icon = document.createElement('span');
        icon.className = 'material-icons';
        switch(type) {
          case 'success': icon.textContent = 'check_circle'; break;
          case 'error': icon.textContent = 'error'; break;
          case 'warning': icon.textContent = 'warning'; break;
          case 'info': 
          default: icon.textContent = 'info'; break;
        }
        toast.appendChild(icon);

        const msg = document.createElement('div');
        msg.className = 'message';
        msg.textContent = message;
        toast.appendChild(msg);

        const closeBtn = document.createElement('button');
        closeBtn.className = 'close-btn';
        closeBtn.setAttribute('aria-label', 'Close notification');
        closeBtn.innerHTML = '&times;';
        closeBtn.addEventListener('click', () => {
          toast.remove();
        });
        toast.appendChild(closeBtn);

        toastContainer.appendChild(toast);

        setTimeout(() => {
          toast.style.opacity = '0';
          toast.style.transform = 'translateX(40px)';
          setTimeout(() => toast.remove(), 350);
        }, duration);
      }

      document.addEventListener('DOMContentLoaded', () => {
        init();
      });
    })();
  </script>
</body>
</html>

