<!doctype html>
<html lang="pt-BR" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Geladinhos da Vovó 🍦</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&amp;display=swap" rel="stylesheet">
  <script>
tailwind.config = {
  theme: {
    extend: {
      fontFamily: { nunito: ['Nunito', 'sans-serif'] },
      colors: {
        rose: { 50:'#fff1f2',100:'#ffe4e6',200:'#fecdd3',300:'#fda4af',400:'#fb7185',500:'#f43f5e',600:'#e11d48' },
        grape: { 50:'#faf5ff',100:'#f3e8ff',200:'#e9d5ff',300:'#d8b4fe',400:'#c084fc',500:'#a855f7',600:'#9333ea' },
        cream: { 50:'#fffbf0',100:'#fff3d6' }
      }
    }
  }
}
</script>
  <style>
html, body { height: 100%; margin: 0; }
* { font-family: 'Nunito', sans-serif; }
.card-pop { transition: transform 0.2s, box-shadow 0.2s; }
.card-pop:hover { transform: translateY(-4px); box-shadow: 0 12px 32px rgba(244,63,94,0.15); }
.btn-bounce { transition: transform 0.1s; }
.btn-bounce:active { transform: scale(0.9); }
.drawer-overlay { transition: opacity 0.3s; }
.drawer-panel { transition: transform 0.3s cubic-bezier(0.4,0,0.2,1); }
.fade-in { animation: fadeIn 0.5s ease both; }
@keyframes fadeIn { from { opacity:0; transform:translateY(16px); } to { opacity:1; transform:translateY(0); } }
@keyframes pulse-glow { 0%,100% { box-shadow: 0 0 0 0 rgba(244,63,94,0.4); } 50% { box-shadow: 0 0 0 12px rgba(244,63,94,0); } }
.pulse-glow { animation: pulse-glow 2s infinite; }
@keyframes shimmer { 0% { background-position: -200% 0; } 100% { background-position: 200% 0; } }
.promo-shimmer { background: linear-gradient(90deg, #f43f5e 0%, #fbbf24 25%, #f43f5e 50%, #fbbf24 75%, #f43f5e 100%); background-size: 200% 100%; animation: shimmer 3s linear infinite; -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
.toast-anim { animation: toastIn 0.4s ease, toastOut 0.4s ease 1.6s forwards; }
@keyframes toastIn { from { opacity:0; transform:translateY(20px) scale(0.9); } to { opacity:1; transform:translateY(0) scale(1); } }
@keyframes toastOut { from { opacity:1; } to { opacity:0; transform:translateY(-10px); } }
::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-thumb { background: #fda4af; border-radius: 3px; }
</style>
  <style>body { box-sizing: border-box; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full bg-cream-50 overflow-auto">
  <div id="app" class="w-full min-h-full flex flex-col"><!-- Header -->
   <header id="header" class="sticky top-0 z-40 backdrop-blur-lg bg-white/80 border-b border-rose-100 px-4 py-3">
    <div class="max-w-4xl mx-auto flex items-center justify-between">
     <div>
      <h1 id="store-name" class="text-xl font-900 text-rose-600">Geladinhos da Vovó 🍦</h1>
      <p id="location" class="text-xs text-gray-500">📍 Salvador - BA · Entregamos na sua região</p>
     </div><button id="cart-btn" onclick="toggleDrawer(true)" class="relative btn-bounce bg-rose-500 text-white rounded-full p-3 shadow-lg hover:bg-rose-600"> <i data-lucide="shopping-bag" class="w-5 h-5"></i> <span id="cart-badge" class="absolute -top-1 -right-1 bg-grape-500 text-white text-xs font-800 rounded-full w-5 h-5 flex items-center justify-center hidden">0</span> </button>
    </div>
   </header><!-- Hero -->
   <section class="px-4 pt-6 pb-4 max-w-4xl mx-auto w-full fade-in">
    <div class="bg-gradient-to-br from-rose-500 via-rose-400 to-grape-400 rounded-3xl p-6 text-white text-center relative overflow-hidden">
     <div class="absolute inset-0 opacity-10" style="background-image: url('data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 width=%2260%22 height=%2260%22><circle cx=%2230%22 cy=%2230%22 r=%228%22 fill=%22white%22/></svg>');"></div>
     <div class="text-5xl mb-2">
      🍧
     </div>
     <h2 id="hero-title" class="text-2xl font-900 mb-1">Os melhores geladinhos da cidade! 🧊</h2>
     <p id="hero-subtitle" class="text-sm opacity-90">Feitos com frutas frescas e muito amor. Peça já pelo WhatsApp!</p>
     <p class="mt-3 text-xs bg-white/20 inline-block px-3 py-1 rounded-full">⏰ Pedidos até 18h para entrega no mesmo dia</p>
    </div>
   </section><!-- Promo Banner -->
   <section class="px-4 pb-4 max-w-4xl mx-auto w-full fade-in" style="animation-delay:0.1s">
    <div class="bg-gradient-to-r from-amber-400 via-orange-400 to-rose-500 rounded-2xl p-4 flex items-center justify-between text-white shadow-lg">
     <div>
      <p class="font-900 text-lg" id="promo-main">🔥 Leve 5 por R$15!</p>
      <p class="text-xs opacity-90">Desconto aplicado automaticamente no carrinho</p>
     </div><span class="text-3xl">🎉</span>
    </div>
   </section><!-- Estoque limitado -->
   <div class="px-4 pb-2 max-w-4xl mx-auto w-full">
    <p class="text-center text-sm text-rose-600 font-700">⚠️ Estoque limitado — garanta os seus!</p>
   </div><!-- Products Grid -->
   <section class="px-4 pb-6 max-w-4xl mx-auto w-full flex-1">
    <div id="products-grid" class="grid grid-cols-2 md:grid-cols-3 gap-3"></div>
   </section><!-- Floating WhatsApp --> <a href="#" id="float-wpp" onclick="sendWhatsApp(); return false;" class="fixed bottom-5 right-5 z-30 bg-green-500 text-white rounded-full p-4 shadow-xl hover:bg-green-600 btn-bounce pulse-glow">
    <svg class="w-6 h-6" fill="currentColor" viewbox="0 0 24 24">
     <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z" /><path d="M12 0C5.373 0 0 5.373 0 12c0 2.625.846 5.059 2.284 7.034L.789 23.492a.5.5 0 00.611.611l4.458-1.495A11.952 11.952 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 22c-2.347 0-4.518-.809-6.242-2.163l-.436-.35-3.025 1.013 1.013-3.025-.35-.436A9.956 9.956 0 012 12C2 6.486 6.486 2 12 2s10 4.486 10 10-4.486 10-10 10z" />
    </svg></a> <!-- Cart Drawer -->
   <div id="drawer-overlay" class="fixed inset-0 z-50 hidden">
    <div class="drawer-overlay absolute inset-0 bg-black/40" onclick="toggleDrawer(false)"></div>
    <div id="drawer-panel" class="drawer-panel absolute right-0 top-0 h-full w-full max-w-sm bg-white shadow-2xl flex flex-col translate-x-full">
     <div class="p-4 border-b border-rose-100 flex items-center justify-between">
      <h3 class="font-800 text-lg text-rose-600">🛒 Seu Carrinho</h3><button onclick="toggleDrawer(false)" class="btn-bounce p-2 rounded-full hover:bg-rose-50"><i data-lucide="x" class="w-5 h-5 text-gray-500"></i></button>
     </div>
     <div id="cart-items" class="flex-1 overflow-auto p-4 space-y-3"></div>
     <div id="cart-footer" class="p-4 border-t border-rose-100 hidden">
      <div id="promo-notice" class="hidden bg-amber-50 border border-amber-200 rounded-xl p-2 mb-3 text-center text-sm text-amber-700 font-700"></div>
      <div class="flex justify-between items-center mb-3"><span class="font-700 text-gray-700">Total:</span> <span id="cart-total" class="font-900 text-xl text-rose-600">R$0,00</span>
      </div><button onclick="sendWhatsApp()" class="w-full bg-green-500 hover:bg-green-600 text-white font-800 py-3 rounded-2xl btn-bounce shadow-lg flex items-center justify-center gap-2 text-lg">
       <svg class="w-5 h-5" fill="currentColor" viewbox="0 0 24 24">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z" /><path d="M12 0C5.373 0 0 5.373 0 12c0 2.625.846 5.059 2.284 7.034L.789 23.492a.5.5 0 00.611.611l4.458-1.495A11.952 11.952 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 22c-2.347 0-4.518-.809-6.242-2.163l-.436-.35-3.025 1.013 1.013-3.025-.35-.436A9.956 9.956 0 012 12C2 6.486 6.486 2 12 2s10 4.486 10 10-4.486 10-10 10z" />
       </svg> Finalizar Pedido </button>
     </div>
    </div>
   </div><!-- Toast -->
   <div id="toast-container" class="fixed bottom-20 left-1/2 -translate-x-1/2 z-50 pointer-events-none"></div>
  </div>
  <script>
const PRODUCTS = [
  { id:1, name:'Morango Cremoso', price:4.00, emoji:'🍓', color:'from-rose-400 to-pink-300' },
  { id:2, name:'Maracujá', price:3.50, emoji:'💛', color:'from-amber-400 to-yellow-300' },
  { id:3, name:'Coco com Leite', price:4.00, emoji:'🥥', color:'from-stone-300 to-white' },
  { id:4, name:'Chocolate Intenso', price:5.00, emoji:'🍫', color:'from-amber-800 to-amber-600' },
  { id:5, name:'Limão', price:3.50, emoji:'🍋', color:'from-lime-400 to-green-300' },
  { id:6, name:'Açaí com Banana', price:6.00, emoji:'🫐', color:'from-purple-600 to-grape-400' }
];

const WHATSAPP = '5575999806162';
let cart = JSON.parse(localStorage.getItem('gv_cart') || '{}');

function saveCart() { localStorage.setItem('gv_cart', JSON.stringify(cart)); }

function getTotal() {
  let totalQty = 0, totalPrice = 0;
  PRODUCTS.forEach(p => {
    const qty = cart[p.id] || 0;
    totalQty += qty;
    totalPrice += qty * p.price;
  });
  // Promo: every 5 units = R$15 instead of individual prices
  const promoSets = Math.floor(totalQty / 5);
  const remainder = totalQty % promoSets ? totalQty - promoSets * 5 : 0;
  // We need to calculate promo differently - cheapest items get discounted
  if (promoSets > 0) {
    // Build array of all items
    let allItems = [];
    PRODUCTS.forEach(p => { for (let i = 0; i < (cart[p.id]||0); i++) allItems.push(p.price); });
    allItems.sort((a,b) => a - b); // cheapest first
    const promoCount = promoSets * 5;
    let discountedTotal = promoSets * 15;
    for (let i = promoCount; i < allItems.length; i++) discountedTotal += allItems[i];
    return { totalQty, totalPrice: discountedTotal, promoSets, originalPrice: totalPrice };
  }
  return { totalQty, totalPrice, promoSets: 0, originalPrice: totalPrice };
}

function fmt(v) { return 'R$' + v.toFixed(2).replace('.',','); }

function showToast(msg) {
  const c = document.getElementById('toast-container');
  const t = document.createElement('div');
  t.className = 'toast-anim bg-rose-600 text-white px-4 py-2 rounded-2xl shadow-xl text-sm font-700 mb-2';
  t.textContent = msg;
  c.appendChild(t);
  setTimeout(() => t.remove(), 2200);
}

function updateUI() {
  const { totalQty } = getTotal();
  const badge = document.getElementById('cart-badge');
  if (totalQty > 0) { badge.textContent = totalQty; badge.classList.remove('hidden'); }
  else { badge.classList.add('hidden'); }

  // Update product counters
  PRODUCTS.forEach(p => {
    const qty = cart[p.id] || 0;
    const el = document.getElementById('qty-' + p.id);
    if (el) el.textContent = qty;
    const minus = document.getElementById('minus-' + p.id);
    if (minus) minus.style.opacity = qty > 0 ? '1' : '0.3';
  });

  renderCart();
  saveCart();
}

function addItem(id) {
  cart[id] = (cart[id] || 0) + 1;
  updateUI();
  const p = PRODUCTS.find(x => x.id === id);
  showToast(`${p.emoji} ${p.name} adicionado!`);
}

function removeItem(id) {
  if (!cart[id]) return;
  cart[id]--;
  if (cart[id] <= 0) delete cart[id];
  updateUI();
}

function buyOne(id) {
  cart[id] = (cart[id] || 0) + 1;
  updateUI();
  toggleDrawer(true);
}

function renderProducts() {
  const grid = document.getElementById('products-grid');
  grid.innerHTML = PRODUCTS.map((p, i) => {
    const qty = cart[p.id] || 0;
    const darkText = p.id === 3 ? 'text-gray-700' : 'text-white';
    return `
    <div class="card-pop bg-white rounded-2xl shadow-md overflow-hidden fade-in" style="animation-delay:${i*0.08}s">
      <div class="bg-gradient-to-br ${p.color} p-4 text-center relative">
        <span class="text-5xl block mb-1">${p.emoji}</span>
        <div class="absolute top-2 right-2 bg-white/30 backdrop-blur rounded-full px-2 py-0.5 text-xs font-800 ${darkText}">${fmt(p.price)}</div>
      </div>
      <div class="p-3">
        <h3 class="font-800 text-sm text-gray-800 mb-2 leading-tight">${p.name}</h3>
        <div class="flex items-center justify-between mb-2">
          <button id="minus-${p.id}" onclick="removeItem(${p.id})" class="btn-bounce w-8 h-8 rounded-full bg-rose-100 text-rose-600 font-800 flex items-center justify-center text-lg" style="opacity:${qty>0?1:0.3}">−</button>
          <span id="qty-${p.id}" class="font-900 text-lg text-gray-800 min-w-[24px] text-center">${qty}</span>
          <button onclick="addItem(${p.id})" class="btn-bounce w-8 h-8 rounded-full bg-rose-500 text-white font-800 flex items-center justify-center text-lg shadow">+</button>
        </div>
        <button onclick="buyOne(${p.id})" class="w-full bg-gradient-to-r from-rose-500 to-grape-500 text-white text-xs font-700 py-2 rounded-xl btn-bounce hover:shadow-lg">Comprar 1 agora</button>
      </div>
    </div>`;
  }).join('');
}

function renderCart() {
  const container = document.getElementById('cart-items');
  const footer = document.getElementById('cart-footer');
  const items = PRODUCTS.filter(p => cart[p.id] > 0);

  if (!items.length) {
    container.innerHTML = '<div class="text-center text-gray-400 mt-12"><span class="text-5xl block mb-3">🛒</span><p class="font-700">Carrinho vazio</p><p class="text-sm">Adicione geladinhos deliciosos!</p></div>';
    footer.classList.add('hidden');
    return;
  }

  container.innerHTML = items.map(p => {
    const qty = cart[p.id];
    return `<div class="flex items-center gap-3 bg-rose-50 rounded-xl p-3">
      <span class="text-2xl">${p.emoji}</span>
      <div class="flex-1 min-w-0">
        <p class="font-700 text-sm text-gray-800 truncate">${p.name}</p>
        <p class="text-xs text-gray-500">${fmt(p.price)} × ${qty}</p>
      </div>
      <div class="flex items-center gap-2">
        <button onclick="removeItem(${p.id})" class="btn-bounce w-7 h-7 rounded-full bg-white text-rose-500 font-800 flex items-center justify-center shadow-sm">−</button>
        <span class="font-800 text-sm w-5 text-center">${qty}</span>
        <button onclick="addItem(${p.id})" class="btn-bounce w-7 h-7 rounded-full bg-rose-500 text-white font-800 flex items-center justify-center shadow-sm">+</button>
      </div>
      <p class="font-800 text-sm text-rose-600 ml-1">${fmt(qty * p.price)}</p>
    </div>`;
  }).join('');

  const { totalPrice, promoSets, originalPrice } = getTotal();
  const promoNotice = document.getElementById('promo-notice');
  if (promoSets > 0) {
    const saved = originalPrice - totalPrice;
    promoNotice.innerHTML = `🎉 Promoção aplicada! Você economizou <strong>${fmt(saved)}</strong>`;
    promoNotice.classList.remove('hidden');
  } else {
    promoNotice.classList.add('hidden');
  }

  document.getElementById('cart-total').textContent = fmt(totalPrice);
  footer.classList.remove('hidden');
}

function toggleDrawer(open) {
  const overlay = document.getElementById('drawer-overlay');
  const panel = document.getElementById('drawer-panel');
  if (open) {
    overlay.classList.remove('hidden');
    requestAnimationFrame(() => { panel.classList.remove('translate-x-full'); });
  } else {
    panel.classList.add('translate-x-full');
    setTimeout(() => overlay.classList.add('hidden'), 300);
  }
}

function sendWhatsApp() {
  const items = PRODUCTS.filter(p => cart[p.id] > 0);
  if (!items.length) { showToast('Adicione itens primeiro!'); return; }
  const { totalPrice } = getTotal();
  let msg = '🍦 *Pedido - Geladinhos da Vovó*\n\n';
  items.forEach(p => {
    const qty = cart[p.id];
    msg += `${p.emoji} ${p.name} × ${qty} = ${fmt(qty * p.price)}\n`;
  });
  msg += `\n💰 *Total: ${fmt(totalPrice)}*\n\nObrigado! 😊`;
  window.open(`https://wa.me/${WHATSAPP}?text=${encodeURIComponent(msg)}`, '_blank');
}

// Default config
const defaultConfig = {
  store_name: 'Geladinhos da Vovó 🍦',
  hero_title: 'Os melhores geladinhos da cidade! 🧊',
  hero_subtitle: 'Feitos com frutas frescas e muito amor. Peça já pelo WhatsApp!',
  location_text: 'Salvador - BA',
  promo_text: 'Leve 5 por R$15!',
  background_color: '#fffbf0',
  surface_color: '#ffffff',
  text_color: '#1f2937',
  primary_action_color: '#f43f5e',
  secondary_action_color: '#a855f7',
  font_family: 'Nunito',
  font_size: 16
};

function applyConfig(config) {
  const c = { ...defaultConfig, ...config };
  document.getElementById('store-name').textContent = c.store_name;
  document.getElementById('hero-title').textContent = c.hero_title;
  document.getElementById('hero-subtitle').textContent = c.hero_subtitle;
  document.getElementById('location').textContent = `📍 ${c.location_text} · Entregamos na sua região`;
  document.getElementById('promo-main').textContent = `🔥 ${c.promo_text}`;

  document.body.style.backgroundColor = c.background_color;
  document.body.style.color = c.text_color;
  document.body.style.fontFamily = `${c.font_family}, Nunito, sans-serif`;

  const base = c.font_size || 16;
  document.getElementById('store-name').style.fontSize = `${base * 1.3}px`;
  document.getElementById('hero-title').style.fontSize = `${base * 1.5}px`;
  document.getElementById('hero-subtitle').style.fontSize = `${base * 0.875}px`;

  // Apply colors
  document.querySelectorAll('.bg-rose-500').forEach(el => { el.style.backgroundColor = c.primary_action_color; });
  document.getElementById('header').style.backgroundColor = c.surface_color + 'cc';
}

window.elementSdk.init({
  defaultConfig,
  onConfigChange: async (config) => applyConfig(config),
  mapToCapabilities: (config) => ({
    recolorables: [
      { get: () => config.background_color || defaultConfig.background_color, set: v => { config.background_color = v; window.elementSdk.setConfig({ background_color: v }); } },
      { get: () => config.surface_color || defaultConfig.surface_color, set: v => { config.surface_color = v; window.elementSdk.setConfig({ surface_color: v }); } },
      { get: () => config.text_color || defaultConfig.text_color, set: v => { config.text_color = v; window.elementSdk.setConfig({ text_color: v }); } },
      { get: () => config.primary_action_color || defaultConfig.primary_action_color, set: v => { config.primary_action_color = v; window.elementSdk.setConfig({ primary_action_color: v }); } },
      { get: () => config.secondary_action_color || defaultConfig.secondary_action_color, set: v => { config.secondary_action_color = v; window.elementSdk.setConfig({ secondary_action_color: v }); } }
    ],
    borderables: [],
    fontEditable: {
      get: () => config.font_family || defaultConfig.font_family,
      set: v => { config.font_family = v; window.elementSdk.setConfig({ font_family: v }); }
    },
    fontSizeable: {
      get: () => config.font_size || defaultConfig.font_size,
      set: v => { config.font_size = v; window.elementSdk.setConfig({ font_size: v }); }
    }
  }),
  mapToEditPanelValues: (config) => new Map([
    ['store_name', config.store_name || defaultConfig.store_name],
    ['hero_title', config.hero_title || defaultConfig.hero_title],
    ['hero_subtitle', config.hero_subtitle || defaultConfig.hero_subtitle],
    ['location_text', config.location_text || defaultConfig.location_text],
    ['promo_text', config.promo_text || defaultConfig.promo_text]
  ])
});

renderProducts();
updateUI();
lucide.createIcons();
</script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9f5f9ae50317d79f',t:'MTc3NzgxNDg2Ni4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>