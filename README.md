<!DOCTYPE html>
<html>
  <head>
    <title>Hello, World!</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600;700&amp;family=Playfair+Display:wght@400;600;700&amp;display=swap" rel="stylesheet">
  <script>
tailwind.config = {
  theme: {
    extend: {
      colors: {
        brand: '#00A0C6',
        'brand-dark': '#007A99',
        'brand-light': '#E6F7FB',
        'brand-50': '#F0FAFC',
        surface: '#FFFFFF',
        txt: '#1E293B',
        subtle: '#64748B',
        accent: '#F59E0B'
      }
    }
  }
}
</script>
  <style>
* { box-sizing: border-box; }
html, body { height: 100%; margin: 0; }
body { font-family: 'Prompt', sans-serif; }
.font-display { font-family: 'Playfair Display', serif; }

.nav-btn { transition: all 0.3s ease; }
.nav-btn:hover, .nav-btn.active { background: #00A0C6; color: white; }
.nav-btn.active { box-shadow: 0 4px 12px rgba(0,160,198,0.3); }

.card-hover { transition: all 0.3s ease; }
.card-hover:hover { transform: translateY(-4px); box-shadow: 0 12px 32px rgba(0,160,198,0.15); }

.day-card { border-left: 4px solid #00A0C6; }

.fade-in { animation: fadeIn 0.5s ease forwards; }
@keyframes fadeIn { from { opacity:0; transform:translateY(16px); } to { opacity:1; transform:translateY(0); } }

.timeline-dot { width: 14px; height: 14px; border-radius: 50%; background: #00A0C6; border: 3px solid white; box-shadow: 0 0 0 2px #00A0C6; }

.meal-card { background: linear-gradient(135deg, #F0FAFC 0%, #FFFFFF 100%); }

.weather-icon { font-size: 2rem; }

::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: #F0FAFC; }
::-webkit-scrollbar-thumb { background: #00A0C6; border-radius: 3px; }

.hero-bg {
  background: linear-gradient(135deg, #00A0C6 0%, #007A99 40%, #005E78 100%);
  position: relative;
  overflow: hidden;
}
.hero-bg::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -30%;
  width: 80%;
  height: 200%;
  background: radial-gradient(ellipse, rgba(255,255,255,0.08) 0%, transparent 70%);
}
.hero-bg::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 60px;
  background: linear-gradient(to top, white, transparent);
}

.flight-path {
  background: repeating-linear-gradient(90deg, #00A0C6 0, #00A0C6 8px, transparent 8px, transparent 14px);
  height: 2px;
}

.tab-section { display: none; }
.tab-section.active { display: block; }

.day-tab { cursor: pointer; transition: all 0.2s; }
.day-tab:hover { background: #E6F7FB; }
.day-tab.active-day { background: #00A0C6; color: white; border-radius: 9999px; }
</style>
  <style>body { box-sizing: border-box; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full bg-white text-txt">
  <div id="app" class="h-full overflow-auto w-full"><!-- Hero -->
   <header class="hero-bg text-white px-4 py-10 md:py-16 text-center relative z-10">
    <div class="max-w-4xl mx-auto relative z-10">
     <p id="companyNameDisplay" class="text-sm tracking-[0.3em] uppercase opacity-80 mb-3">Bluefly Travel</p>
     <div class="flex items-center justify-center gap-3 mb-4"><span class="text-4xl">🇪🇸</span>
      <h1 id="mainTitleDisplay" class="font-display text-3xl md:text-5xl font-bold leading-tight">SPAIN</h1><span class="text-4xl">✈️</span>
     </div>
     <p class="text-lg md:text-xl opacity-90 font-light">Barcelona · Zaragoza · Madrid</p>
     <div class="flex items-center justify-center gap-4 mt-4 text-sm opacity-80"><span>📅 8 - 15 พฤษภาคม 2569</span> <span>•</span> <span>8 วัน 5 คืน</span>
     </div>
     <div class="flex flex-wrap justify-center gap-2 mt-6"><span class="bg-white/20 backdrop-blur px-3 py-1 rounded-full text-xs">⚽ FC Barcelona Vs Real Madrid</span> <span class="bg-white/20 backdrop-blur px-3 py-1 rounded-full text-xs">🛍️ Outlet Shopping</span>
     </div>
    </div>
   </header><!-- Navigation -->
   <nav class="sticky top-0 z-50 bg-white shadow-md border-b border-brand-light">
    <div class="max-w-5xl mx-auto flex overflow-x-auto gap-1 p-2"><button onclick="showSection('overview')" class="nav-btn active flex-shrink-0 px-4 py-2 rounded-full text-sm font-medium text-brand border border-brand/20" data-nav="overview"> <span class="hidden md:inline">🗺️ </span>ภาพรวม </button> <button onclick="showSection('flights')" class="nav-btn flex-shrink-0 px-4 py-2 rounded-full text-sm font-medium text-brand border border-brand/20" data-nav="flights"> <span class="hidden md:inline">✈️ </span>เที่ยวบิน </button> <button onclick="showSection('itinerary')" class="nav-btn flex-shrink-0 px-4 py-2 rounded-full text-sm font-medium text-brand border border-brand/20" data-nav="itinerary"> <span class="hidden md:inline">📋 </span>โปรแกรมทัวร์ </button> <button onclick="showSection('country')" class="nav-btn flex-shrink-0 px-4 py-2 rounded-full text-sm font-medium text-brand border border-brand/20" data-nav="country"> <span class="hidden md:inline">🏛️ </span>ข้อมูลประเทศ </button> <button onclick="showSection('weather')" class="nav-btn flex-shrink-0 px-4 py-2 rounded-full text-sm font-medium text-brand border border-brand/20" data-nav="weather"> <span class="hidden md:inline">🌤️ </span>สภาพอากาศ </button> <button onclick="showSection('clothing')" class="nav-btn flex-shrink-0 px-4 py-2 rounded-full text-sm font-medium text-brand border border-brand/20" data-nav="clothing"> <span class="hidden md:inline">👔 </span>การแต่งกาย </button> <button onclick="showSection('tips')" class="nav-btn flex-shrink-0 px-4 py-2 rounded-full text-sm font-medium text-brand border border-brand/20" data-nav="tips"> <span class="hidden md:inline">💡 </span>เกร็ดน่ารู้ </button> <button onclick="showSection('Passenger')" class="nav-btn flex-shrink-0 px-4 py-2 rounded-full text-sm font-medium text-brand border border-brand/20" data-nav="Passenger"> <span class="hidden md:inline"> </span>รายชื่อผู้เดินทาง </button>
    </div>
   </nav>
   <main class="max-w-5xl mx-auto px-4 py-8"><!-- OVERVIEW -->
    <section id="sec-overview" class="tab-section active fade-in">
     <h2 class="font-display text-2xl md:text-3xl font-bold text-brand-dark mb-6">🗺️ ภาพรวมการเดินทาง</h2>
     <div class="grid md:grid-cols-1 gap-4 mb-8">
      <div class="card-hover bg-brand-50 border border-brand/10 rounded-2xl p-5 text-center">
       <div class="text-4xl mb-2">
        🏛️
       </div>
       <h3 class="font-semibold text-brand-dark text-lg">Barcelona</h3>
       <p class="text-subtle text-sm mt-1">วันที่ 2-3 (9-10 พ.ค.)</p>
       <p class="text-xs text-subtle mt-2">Sagrada Familia • Camp Nou • La Roca Village</p>
      </div>
      <div class="card-hover bg-brand-50 border border-brand/10 rounded-2xl p-5 text-center">
       <div class="text-4xl mb-2">
        ⛪
       </div>
       <h3 class="font-semibold text-brand-dark text-lg">Zaragoza</h3>
       <p class="text-subtle text-sm mt-1">วันที่ 4 (11 พ.ค.)</p>
       <p class="text-xs text-subtle mt-2">Basilica of Our Lady of the Pillar • Plaza Del Pilar</p>
      </div>
      <div class="card-hover bg-brand-50 border border-brand/10 rounded-2xl p-5 text-center">
       <div class="text-4xl mb-2">
        👑
       </div>
       <h3 class="font-semibold text-brand-dark text-lg">Madrid</h3>
       <p class="text-subtle text-sm mt-1">วันที่ 5-7 (12-14 พ.ค.)</p>
       <p class="text-xs text-subtle mt-2">Gran Via • Plaza Mayor • Las Rozas Village</p>
      </div>
     </div><!-- Route Map Visual -->
     <div class="bg-gradient-to-r from-brand-50 to-white border border-brand/10 rounded-2xl p-6 mb-6">
      <h3 class="font-semibold text-brand-dark mb-4">🛤️ เส้นทางการเดินทาง</h3>
      <div class="flex items-center justify-between flex-wrap gap-4">
       <div class="text-center">
        <div class="w-14 h-14 bg-brand rounded-full flex items-center justify-center text-white text-xl mx-auto">
         🛫
        </div>
        <p class="text-xs mt-1 font-medium">กรุงเทพฯ</p>
       </div>
       <div class="flex-1 min-w-[40px] max-w-[80px]">
        <div class="flight-path"></div>
       </div>
       <div class="text-center">
        <div class="w-14 h-14 bg-gray-200 rounded-full flex items-center justify-center text-xl mx-auto">
         🔄
        </div>
        <p class="text-xs mt-1">เวียนนา</p>
       </div>
       <div class="flex-1 min-w-[40px] max-w-[80px]">
        <div class="flight-path"></div>
       </div>
       <div class="text-center">
        <div class="w-14 h-14 bg-amber-400 rounded-full flex items-center justify-center text-white text-xl mx-auto">
         🏛️
        </div>
        <p class="text-xs mt-1 font-medium">บาร์เซโลนา</p>
       </div>
       <div class="flex-1 min-w-[40px] max-w-[80px] border-t-2 border-dashed border-brand"></div>
       <div class="text-center">
        <div class="w-14 h-14 bg-orange-400 rounded-full flex items-center justify-center text-white text-xl mx-auto">
         ⛪
        </div>
        <p class="text-xs mt-1 font-medium">ซาราโกซ่า</p>
       </div>
       <div class="flex-1 min-w-[40px] max-w-[80px] border-t-2 border-dashed border-brand"></div>
       <div class="text-center">
        <div class="w-14 h-14 bg-red-500 rounded-full flex items-center justify-center text-white text-xl mx-auto">
         👑
        </div>
        <p class="text-xs mt-1 font-medium">มาดริด</p>
       </div>
       <div class="flex-1 min-w-[40px] max-w-[80px]">
        <div class="flight-path"></div>
       </div>
       <div class="text-center">
        <div class="w-14 h-14 bg-gray-200 rounded-full flex items-center justify-center text-xl mx-auto">
         🔄
        </div>
        <p class="text-xs mt-1">มิวนิก</p>
       </div>
       <div class="flex-1 min-w-[40px] max-w-[80px]">
        <div class="flight-path"></div>
       </div>
       <div class="text-center">
        <div class="w-14 h-14 bg-brand rounded-full flex items-center justify-center text-white text-xl mx-auto">
         🛬
        </div>
        <p class="text-xs mt-1 font-medium">กรุงเทพฯ</p>
       </div>
      </div>
     </div><!-- Hotels -->
     <h3 class="font-semibold text-brand-dark text-lg mb-3">🏨 โรงแรมที่พัก</h3>
     <div class="space-y-3">
      <div class="flex items-center gap-4 bg-white border border-brand/10 rounded-xl p-4 card-hover">
       <div class="text-3xl">
        🏨
       </div>
       <div class="flex-1">
        <h4 class="font-semibold">Melia Barcelona Sarriá</h4>
        <p class="text-sm text-subtle">บาร์เซโลนา • คืนที่ 1-2 (9-10 พ.ค.)</p>
       </div>
       <div class="text-amber-400 text-sm">
        ★★★★★
       </div>
      </div>
      <div class="flex items-center gap-4 bg-white border border-brand/10 rounded-xl p-4 card-hover">
       <div class="text-3xl">
        🏨
       </div>
       <div class="flex-1">
        <h4 class="font-semibold">NH Ciudad de Zaragoza</h4>
        <p class="text-sm text-subtle">ซาราโกซ่า • คืนที่ 3 (11 พ.ค.)</p>
       </div>
       <div class="text-amber-400 text-sm">
        ★★★★
       </div>
      </div>
      <div class="flex items-center gap-4 bg-white border border-brand/10 rounded-xl p-4 card-hover">
       <div class="text-3xl">
        🏨
       </div>
       <div class="flex-1">
        <h4 class="font-semibold">Melia Castilla</h4>
        <p class="text-sm text-subtle">มาดริด • คืนที่ 4-5 (12-13 พ.ค.)</p>
       </div>
       <div class="text-amber-400 text-sm">
        ★★★★
       </div>
      </div>
     </div>
    </section><!-- FLIGHTS -->
    <section id="sec-flights" class="tab-section fade-in">
     <h2 class="font-display text-2xl md:text-3xl font-bold text-brand-dark mb-6">✈️ ข้อมูลเที่ยวบิน</h2>
     <div class="bg-amber-50 border border-amber-200 rounded-2xl p-5 mb-6">
      <h4 class="font-semibold text-amber-800 mb-3">🎒 ข้อมูลน้ำหนักกระเป๋า</h4>
      <div class="grid md:grid-cols-2 gap-4 text-sm">
       <div>
        <p class="font-semibold text-amber-900 mb-2">✈️ Business Class</p>
        <ul class="text-amber-700 space-y-1 text-xs">
         <li>• Carry on: 2 ใบ × 8 kg max. (55×40×23 cm)</li>
         <li>• Personal item: 1 ใบ (40×30×15 cm)</li>
         <li>• Checked bag: 2 ใบ × 32 kg max.</li>
        </ul>
       </div>
       <div>
        <p class="font-semibold text-amber-900 mb-2">✈️ Economy Class</p>
        <ul class="text-amber-700 space-y-1 text-xs">
         <li>• Carry on: 1 ใบ × 8 kg max. (55×40×23 cm)</li>
         <li>• Personal item: 1 ใบ (40×30×15 cm)</li>
         <li>• Checked bag: 1 ใบ × 23 kg max.</li>
        </ul>
       </div>
      </div>
     </div>
     <h3 class="font-semibold text-brand mb-3">🛫 ขาไป — 8-9 พฤษภาคม 2569</h3><!-- Baggage Allowance -->
     
     <div class="space-y-4 mb-8">
      <div class="bg-white border border-brand/20 rounded-2xl p-5 card-hover">
       <div class="flex items-center gap-2 mb-3">
        <span class="bg-brand text-white px-3 py-1 rounded-full text-xs font-semibold">OS 008</span> <span class="text-sm text-subtle">Austrian Airlines</span>
       </div>
       <div class="flex items-center gap-4">
        <div class="text-center">
         <p class="text-2xl font-bold text-brand-dark">23:40</p>
         <p class="text-sm font-medium">BKK</p>
         <p class="text-xs text-subtle">กรุงเทพฯ</p>
         <p class="text-xs text-subtle">8 พ.ค.</p>
        </div>
        <div class="flex-1 flex flex-col items-center">
         <p class="text-xs text-subtle mb-1">10 ชม. 55 นาที</p>
         <div class="w-full flex items-center">
          <div class="w-2 h-2 rounded-full bg-brand"></div>
          <div class="flex-1 h-[2px] bg-gradient-to-r from-brand to-brand-dark"></div><span class="text-lg">✈️</span>
         </div>
        </div>
        <div class="text-center">
         <p class="text-2xl font-bold text-brand-dark">05:35</p>
         <p class="text-sm font-medium">VIE</p>
         <p class="text-xs text-subtle">เวียนนา</p>
         <p class="text-xs text-subtle">9 พ.ค. (+1)</p>
        </div>
       </div>
      </div>
      <div class="flex justify-center">
       <div class="bg-amber-50 border border-amber-200 rounded-full px-4 py-1 text-xs text-amber-700">
        🔄 เปลี่ยนเครื่องที่เวียนนา — Transit 1 ชม. 15 นาที
       </div>
      </div>
      <div class="bg-white border border-brand/20 rounded-2xl p-5 card-hover">
       <div class="flex items-center gap-2 mb-3"><span class="bg-brand text-white px-3 py-1 rounded-full text-xs font-semibold">OS 401</span> <span class="text-sm text-subtle">Austrian Airlines</span>
       </div>
       <div class="flex items-center gap-4">
        <div class="text-center">
         <p class="text-2xl font-bold text-brand-dark">06:50</p>
         <p class="text-sm font-medium">VIE</p>
         <p class="text-xs text-subtle">เวียนนา</p>
         <p class="text-xs text-subtle">9 พ.ค.</p>
        </div>
        <div class="flex-1 flex flex-col items-center">
         <p class="text-xs text-subtle mb-1">2 ชม. 20 นาที</p>
         <div class="w-full flex items-center">
          <div class="w-2 h-2 rounded-full bg-brand"></div>
          <div class="flex-1 h-[2px] bg-gradient-to-r from-brand to-brand-dark"></div><span class="text-lg">✈️</span>
         </div>
        </div>
        <div class="text-center">
         <p class="text-2xl font-bold text-brand-dark">09:10</p>
         <p class="text-sm font-medium">BCN</p>
         <p class="text-xs text-subtle">บาร์เซโลนา</p>
         <p class="text-xs text-subtle">9 พ.ค.</p>
        </div>
       </div>
      </div>
     </div>
     <h3 class="font-semibold text-brand mb-3">🛬 ขากลับ — 14-15 พฤษภาคม 2569</h3>
     <div class="space-y-4">
      <div class="bg-white border border-brand/20 rounded-2xl p-5 card-hover">
       <div class="flex items-center gap-2 mb-3"><span class="bg-brand-dark text-white px-3 py-1 rounded-full text-xs font-semibold">LH 1805</span> <span class="text-sm text-subtle">Lufthansa</span>
       </div>
       <div class="flex items-center gap-4">
        <div class="text-center">
         <p class="text-2xl font-bold text-brand-dark">18:25</p>
         <p class="text-sm font-medium">MAD</p>
         <p class="text-xs text-subtle">มาดริด</p>
         <p class="text-xs text-subtle">14 พ.ค.</p>
        </div>
        <div class="flex-1 flex flex-col items-center">
         <p class="text-xs text-subtle mb-1">2 ชม. 35 นาที</p>
         <div class="w-full flex items-center">
          <div class="w-2 h-2 rounded-full bg-brand-dark"></div>
          <div class="flex-1 h-[2px] bg-gradient-to-r from-brand-dark to-brand"></div><span class="text-lg">✈️</span>
         </div>
        </div>
        <div class="text-center">
         <p class="text-2xl font-bold text-brand-dark">21:00</p>
         <p class="text-sm font-medium">MUC</p>
         <p class="text-xs text-subtle">มิวนิก</p>
         <p class="text-xs text-subtle">14 พ.ค.</p>
        </div>
       </div>
      </div>
      <div class="flex justify-center">
       <div class="bg-amber-50 border border-amber-200 rounded-full px-4 py-1 text-xs text-amber-700">
        🔄 เปลี่ยนเครื่องที่มิวนิก — Transit 1 ชม. 20 นาที
       </div>
      </div>
      <div class="bg-white border border-brand/20 rounded-2xl p-5 card-hover">
       <div class="flex items-center gap-2 mb-3"><span class="bg-brand-dark text-white px-3 py-1 rounded-full text-xs font-semibold">LH 772</span> <span class="text-sm text-subtle">Lufthansa</span>
       </div>
       <div class="flex items-center gap-4">
        <div class="text-center">
         <p class="text-2xl font-bold text-brand-dark">22:20</p>
         <p class="text-sm font-medium">MUC</p>
         <p class="text-xs text-subtle">มิวนิก</p>
         <p class="text-xs text-subtle">14 พ.ค.</p>
        </div>
        <div class="flex-1 flex flex-col items-center">
         <p class="text-xs text-subtle mb-1">10 ชม. 40 นาที</p>
         <div class="w-full flex items-center">
          <div class="w-2 h-2 rounded-full bg-brand-dark"></div>
          <div class="flex-1 h-[2px] bg-gradient-to-r from-brand-dark to-brand"></div><span class="text-lg">✈️</span>
         </div>
        </div>
        <div class="text-center">
         <p class="text-2xl font-bold text-brand-dark">14:00</p>
         <p class="text-sm font-medium">BKK</p>
         <p class="text-xs text-subtle">กรุงเทพฯ</p>
         <p class="text-xs text-subtle">15 พ.ค. (+1)</p>
        </div>
       </div>
      </div>
     </div>
    </section><!-- ITINERARY -->
    <section id="sec-itinerary" class="tab-section fade-in">
     <h2 class="font-display text-2xl md:text-3xl font-bold text-brand-dark mb-6">📋 โปรแกรมทัวร์</h2><!-- Day tabs -->
     <div class="flex flex-wrap gap-2 mb-6"><button onclick="showDay(1)" class="day-tab active-day px-4 py-2 text-sm font-medium rounded-full border border-brand/20">วันที่ 1</button> <button onclick="showDay(2)" class="day-tab px-4 py-2 text-sm font-medium rounded-full border border-brand/20">วันที่ 2</button> <button onclick="showDay(3)" class="day-tab px-4 py-2 text-sm font-medium rounded-full border border-brand/20">วันที่ 3</button> <button onclick="showDay(4)" class="day-tab px-4 py-2 text-sm font-medium rounded-full border border-brand/20">วันที่ 4</button> <button onclick="showDay(5)" class="day-tab px-4 py-2 text-sm font-medium rounded-full border border-brand/20">วันที่ 5</button> <button onclick="showDay(6)" class="day-tab px-4 py-2 text-sm font-medium rounded-full border border-brand/20">วันที่ 6</button> <button onclick="showDay(7)" class="day-tab px-4 py-2 text-sm font-medium rounded-full border border-brand/20">วันที่ 7</button> <button onclick="showDay(8)" class="day-tab px-4 py-2 text-sm font-medium rounded-full border border-brand/20">วันที่ 8</button>
     </div><!-- Day 1 -->
     <div id="day-1" class="day-content">
      <div class="day-card bg-white rounded-2xl p-6 shadow-sm border border-brand/10">
       <div class="flex items-center gap-3 mb-4"><span class="bg-brand text-white w-10 h-10 rounded-full flex items-center justify-center font-bold">1</span>
        <div>
         <h3 class="font-semibold text-lg">วันศุกร์ที่ 8 พฤษภาคม 2569</h3>
         <p class="text-sm text-subtle">กรุงเทพฯ → เวียนนา</p>
        </div>
       </div>
       <div class="space-y-4 ml-5 border-l-2 border-brand/20 pl-6">
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">20:30 น.</span> — พบกันที่ สนามบินสุวรรณภูมิ อาคารผู้โดยสารขาออกระหว่างประเทศ ชั้น 4 ประตู 4 เคาน์เตอร์ G สายการบินออสเตรียน แอร์ไลน์</p>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">23:40 น.</span> — ✈️ ออกเดินทางสู่เวียนนา โดย Austrian Airlines เที่ยวบิน OS 008</p>
        </div>
       </div>
       <div class="mt-4 bg-brand-50 rounded-xl p-3 text-xs text-subtle flex items-center gap-2"><span>💡</span> แนะนำเดินทางมาถึงสนามบินก่อนเวลานัดหมายอย่างน้อย 30 นาที
       </div>
      </div>
     </div><!-- Day 2 -->
     <div id="day-2" class="day-content" style="display:none;">
      <div class="day-card bg-white rounded-2xl p-6 shadow-sm border border-brand/10">
       <div class="flex items-center gap-3 mb-4"><span class="bg-brand text-white w-10 h-10 rounded-full flex items-center justify-center font-bold">2</span>
        <div>
         <h3 class="font-semibold text-lg">วันเสาร์ที่ 9 พฤษภาคม 2569</h3>
         <p class="text-sm text-subtle">เวียนนา → บาร์เซโลนา</p>
        </div><span class="ml-auto text-2xl">🏛️</span>
       </div>
       <div class="space-y-4 ml-5 border-l-2 border-brand/20 pl-6">
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">05:35 น.</span> — เดินทางถึงสนามบินเวียนนา แวะเปลี่ยนเครื่อง</p>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">06:50 น.</span> — ✈️ ออกเดินทางสู่บาร์เซโลนา โดย Austrian Airlines เที่ยวบิน OS 401</p>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">09:10 น.</span> — เดินทางถึงสนามบินบาร์เซโลนา-เอล แปรต</p>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">📸 Passeig de Gracia </p>
          <p class="text-subtle">เป็นหนึ่งในถนนที่หรูหราและเป็นตัวแทนของกรุงบาร์เซโลนามากที่สุด ตั้งอยู่ใจกลางย่าน Eixample สร้างขึ้นในช่วงปลายศตวรรษที่ 19 ถึงต้นศตวรรษที่ 20 เชื่อมระหว่าง Catalunya Square กับย่าน Gràcia ถนนสายนี้มีชื่อเสียงด้านสถาปัตยกรรม Modernist อันโดดเด่น ได้แก่ Casa Batlló โดย Antoni Gaudí — รูปทรงอินทรีย์และโมเสกหลากสี Casa Milà (La Pedrera) — ผลงานชิ้นเอกอีกชิ้นของ Gaudí ซึ่งได้รับการขึ้นทะเบียนเป็นมรดกโลก UNESCO</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://blog.apartmentbarcelona.com/wp-content/uploads/2020/05/illa-de-discordia-scaled.jpg" loading="lazy" class="rounded-lg w-full h-40 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารกลางวัน — Rio Azul Restaurant</p>
          <div class="meal-card rounded-lg p-3 mt-2 text-xs">
           <p class="font-medium text-brand-dark mb-1">เมนู:</p>
           <p>Hongkong style soup • Steam Whole Fish • Hongkong style pork rib (Baked) • Salt and Pepper Shrimp • Steamed chicken Hong Kong style • Omelette with prawns • Half Roast duck</p>
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">⛪ Sagrada Familia</p>
          <p class="text-subtle">มหาวิหารที่สำคัญที่มีชื่อเสียงที่สุดของเมืองบาร์เซโลนาและเป็นสัญลักษณ์ของเมืองบาร์เซโลนา มีความสูงถึง 170 เมตร ไม่ว่าจะอยู่ที่ใดในเมืองสามารถมองเห็นยอดแหลมทั้งแปดอันโดดเด่นได้ มหาวิหารสร้างขึ้นในปี ค.ศ. 1882 ถึง ค.ศ. 1930 เพื่อเป็นอนุสรณ์แด่ครอบครัวพระเยซู</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://www.barcelo.com/guia-turismo/wp-content/uploads/sagrada-familia-1.jpg" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารค่ำ — Marina Bay Restaurant</p>
          <div class="meal-card rounded-lg p-3 mt-2 text-xs">
           <p class="font-medium text-brand-dark mb-1">เมนู :</p>
           <p>Salpicon Marisco (ซีฟู้ดรวม)  •  1/4 Langostino Cocido (กุ้ง)  •  1/4 Mejillones Marinera (หอยแมลงภู่)  •  Seafood Paella  •  Lemon Sorbet  •  Bread</p>
          </div>
         </div>
        </div>
       </div>
       <div class="mt-4 bg-amber-50 border border-amber-200 rounded-xl p-3 text-xs flex items-center gap-2"><span>🏨</span> <strong>Melia Barcelona Sarriá ★★★★★</strong>
       </div>
      </div>
     </div><!-- Day 3 -->
     <div id="day-3" class="day-content" style="display:none;">
      <div class="day-card bg-white rounded-2xl p-6 shadow-sm border border-brand/10">
       <div class="flex items-center gap-3 mb-4"><span class="bg-brand text-white w-10 h-10 rounded-full flex items-center justify-center font-bold">3</span>
        <div>
         <h3 class="font-semibold text-lg">วันอาทิตย์ที่ 10 พฤษภาคม 2569</h3>
         <p class="text-sm text-subtle">บาร์เซโลนา</p>
        </div><span class="ml-auto text-2xl">⚽</span>
       </div>
       <div class="space-y-4 ml-5 border-l-2 border-brand/20 pl-6">
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🛍️ La Roca Village</p>
          <p class="text-subtle">Outlet Shopping Village มีร้านค้ามากมายให้ท่านได้เลือกชมกว่า 90 ร้านค้า เช่น Burberry, Cacharel, Calvin Kline, Lacoste ฯลฯ ซึ่งท่านสามารถสนุกสนานกับการจับจ่ายสินค้ามากมายไม่ว่าจะเป็น เสื้อผ้าบุรุษ เสื้อผ้าสตรี อุปกรณ์กีฬา ของใช้ภายในบ้านและอื่นๆ อีกมายมาย</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://media.istockphoto.com/id/545113358/th/%E0%B8%A3%E0%B8%B9%E0%B8%9B%E0%B8%96%E0%B9%88%E0%B8%B2%E0%B8%A2/%E0%B8%8A%E0%B9%89%E0%B8%AD%E0%B8%9B%E0%B8%9B%E0%B8%B4%E0%B9%89%E0%B8%87%E0%B9%83%E0%B8%99%E0%B8%AB%E0%B8%A1%E0%B8%B9%E0%B9%88%E0%B8%9A%E0%B9%89%E0%B8%B2%E0%B8%99-la-roca-%E0%B8%82%E0%B8%AD%E0%B8%87%E0%B8%9A%E0%B8%B2%E0%B8%A3%E0%B9%8C%E0%B9%80%E0%B8%8B%E0%B9%82%E0%B8%A5%E0%B8%99%E0%B8%B2.jpg?s=612x612&w=0&k=20&c=wzpD4_T3x7pHimFKVop1keux1sSqOI2GfxvlK0qd7AA=" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารกลางวัน
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">📸 Spanish Village (Poble Espanyol)</p>
          <p class="text-subtle">หมู่บ้านชาวสเปนเล็กๆ แห่งนี้สร้างขึ้นเพื่อจัดแสดงนิทรรศการโลกปี 1929 หมู่บ้านขนาดเล็กที่มีเสน่ห์แห่งนี้มีอาคารในสไตล์สถาปัตยกรรมตามแบบฉบับของจังหวัดต่างๆ ในสเปนมีถนนเล็กๆ ที่สวยงามตรอกซอกซอยลานและบ้านที่อยู่รอบจัตุรัสหลัก Plaza Mayor</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://www.barcelona.de/images/poble-espanyol/480-poble-espanyol-02.jpg" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🏟️ Camp Nou</p>
          <p class="text-subtle">สนามกีฬาที่มีชื่อเสียงระดับโลก เป็นสนามเหย้าของสโมสรฟุตบอลบาร์เซโลนา (FC Barcelona) มาตั้งแต่เปิดใช้งานในปี ค.ศ. 1957 เป็นสนามฟุตบอลที่ใหญ่ที่สุดในยุโรป และใหญ่เป็นอันดับต้นๆ ของโลก</p>
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">⚽ FC Barcelona vs Real Madrid</p>
          <p class="text-sm opacity-90">21.00 น. ชมการแข่งขันฟุตบอล El Clásico!</p>
          <p class="text-xs opacity-70 mt-1">ประสบการณ์สุดยิ่งใหญ่ ณ Camp Nou</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://spookyexpress.com/wp-content/uploads/2025/10/Real-Madrid-vs-Barcelona.jpg" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารค่ำ
         </div>
        </div>
       </div>
       <div class="mt-4 bg-amber-50 border border-amber-200 rounded-xl p-3 text-xs flex items-center gap-2"><span>🏨</span> <strong>Melia Barcelona Sarriá ★★★★★</strong>
       </div>
      </div>
      </div>
     </div><!-- Day 4 -->
     <div id="day-4" class="day-content" style="display:none;">
      <div class="day-card bg-white rounded-2xl p-6 shadow-sm border border-brand/10">
       <div class="flex items-center gap-3 mb-4"><span class="bg-brand text-white w-10 h-10 rounded-full flex items-center justify-center font-bold">4</span>
        <div>
         <h3 class="font-semibold text-lg">วันจันทร์ที่ 11 พฤษภาคม 2569</h3>
         <p class="text-sm text-subtle">บาร์เซโลนา → ซาราโกซ่า</p>
        </div><span class="ml-auto text-2xl">⛪</span>
       </div>
       <div class="space-y-4 ml-5 border-l-2 border-brand/20 pl-6">
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">🚌</span> เดินทางสู่เมืองซาราโกซ่า (Zaragoza)(ใช้เวลาเดินทางประมาณ 3 ชั่วโมง 30 นาที) </p>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารกลางวัน — Paraiso Chinese restaurant</p>
          <div class="meal-card rounded-lg p-3 mt-2 text-xs">
           <p class="font-medium text-brand-dark mb-1">เมนู :</p>
           <p>Corn soup with crab meat • Pork rib with soya sauce • Beef with green peppers • Spicy tofu • Chinese vegetables • Fish in soya sauce</p>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">⛪ Basilica of Our Lady of the Pillar</p>
          <p class="text-subtle">ถ่ายรูปด้านหน้ามหาวิหารแม่พระแห่งเสาศักดิ์สิทธิ์ วิหารโรมันคาทอลิกที่ตั้งอยู่ริมแม่น้ำในบริเวณใจกลางเมืองซาราโกซ่า สร้างขึ้นครั้งแรกในช่วงศตวรรษที่ 1-2 ได้ชื่อว่าเป็นโบสถ์ที่อุทิศแด่พระแม่มารีแห่งแรกของโลกหรือที่รู้จักในนาม ซานตา มาเรีย เดอร์ฟิลลาร์</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://cdn.firespring.com/images/954fb4c9-2d55-4583-ad28-ae26b83ce0bd.jpg" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-70 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🏛️ Plaza Del Pilar</p>
          <p class="text-subtle">ได้ชื่อว่าเป็นจัตุรัสที่พลุกพล่านที่สุดในซาราโกซา รายล้อมไปด้วย มหาวิหารและอาคารประวัติศาสตร์มากมาย จัตุรัสแห่งนี้เป็นจุดศูนย์รวมของผู้คนในเมืองอีกทั้งยังเป็นสถานที่สำหรับจัดการแสดงฉลองเทศกาล และจัดกิจกรรมที่มีสีสันต่างๆ อยู่เสมอ</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://media.istockphoto.com/id/1068694928/es/foto/plaza-de-pilar-zaragoza-espa%C3%B1a.jpg?s=612x612&w=0&k=20&c=8X0Lkjj-uwM7M9Yo0Mr1ZlWOZun0ctQA_GXLg3Xvslo=" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-70 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารค่ำ
          </div>
       <div class="mt-4 bg-amber-50 border border-amber-200 rounded-xl p-3 text-xs flex items-center gap-2"><span>🏨</span> <strong>NH Ciudad de Zaragoza ★★★★</strong>
      </div>
      </div>
      </div>
      </div>
      </div>
      </div>
      </div>
      </div>
     </div><!-- Day 5 -->
     <div id="day-5" class="day-content" style="display:none;">
      <div class="day-card bg-white rounded-2xl p-6 shadow-sm border border-brand/10">
       <div class="flex items-center gap-3 mb-4"><span class="bg-brand text-white w-10 h-10 rounded-full flex items-center justify-center font-bold">5</span>
        <div>
         <h3 class="font-semibold text-lg">วันอังคารที่ 12 พฤษภาคม 2569</h3>
         <p class="text-sm text-subtle">ซาราโกซ่า → มาดริด</p>
        </div><span class="ml-auto text-2xl">💃</span>
       </div>
       <div class="space-y-4 ml-5 border-l-2 border-brand/20 pl-6">
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">🚌</span> เดินทางสู่กรุงมาดริด (ใช้เวลาเดินทางประมาณ 4 ชั่วโมง)</p>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารกลางวัน — Zen Bamboo</p>
          <div class="meal-card rounded-lg p-3 mt-2 text-xs">
           <p class="font-medium text-brand-dark mb-1">เมนู:</p>
           <p>Wanton Soup • Steamed Whole Fish • Omelette with Shrimp • Fried Chicken Wings • Pork with Oyster Sauce • Roast Duck • Seasonal Vegetables • Salt and Pepper Shrimp</p>
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🏛️ Plaza de Cibeles &amp; Cibeles Fountain</p>
          <p class="text-subtle">เป็นจัตุรัสที่มีอาคารสถาปัตยกรรมนีโอคลาสสิคที่โดดเด่นที่สุดกลางเมืองมาดริด แวดล้อมด้วยอาคารต่างๆ เป็นสถานที่ท่องเที่ยวสำคัญของเมืองมาดริด จัตุรัสแห่งนี้ใช้เป็นสถานที่สำหรับการเฉลิมฉลองชัยชนะของทีมมาดริดและทีมชาติสเปน ชื่อจัตุรัสนี้เป็นชื่อที่เรียกเลียนแบบเทพธิดา Cibeles ซึ่งมีประติมากรรมงดงามอยู่ที่น้ำพุ Cibeles Fountain และเริ่มต้นใช้เป็นชื่อทางการในปี ค.ศ. 1941</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://dynamic-media-cdn.tripadvisor.com/media/photo-o/1a/91/d1/5e/photo1jpg.jpg?w=900&h=500&s=1" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🚪 Puerta de Alcalá</p>
          <p class="text-subtle">เป็นอนุสรณ์สถานที่สำคัญ ประตูชัยของกรุงมาดริด สร้างขึ้นในปี 1599 ประตูชัยแห่งนี้สร้างขึ้นเพื่อถวายแด่พระเจ้าชาร์ลส์ที่ 3</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://caminoon.com/wp-content/uploads/2020/11/puerta-de-alcala-atardecer.jpg" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🛍️ Gran Vía</p>
          <p class="text-subtle">แหล่งช้อปปิ้งยอดนิยมที่สุดแห่งหนึ่งในกรุงมาดริด อยู่บริเวณใจกลางเมืองซึ่งมีโรงแรม ห้างสรรพสินค้า ร้านค้า และโรงภาพยนตร์มากมาย</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://cdn.sanity.io/images/nxpteyfv/goguides/2724cb77e243e26590137a78a8b6d7f7407754b5-1600x1066.jpg" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารค่ำ </p>
         </div>
        </div>
       </div>
       <div class="mt-4 bg-amber-50 border border-amber-200 rounded-xl p-3 text-xs flex items-center gap-2"><span>🏨</span> <strong>Melia Castilla ★★★★</strong>
       </div>
      </div>
      </div>
     </div><!-- Day 6 -->
     <div id="day-6" class="day-content" style="display:none;">
      <div class="day-card bg-white rounded-2xl p-6 shadow-sm border border-brand/10">
       <div class="flex items-center gap-3 mb-4"><span class="bg-brand text-white w-10 h-10 rounded-full flex items-center justify-center font-bold">6</span>
        <div>
         <h3 class="font-semibold text-lg">วันพุธที่ 13 พฤษภาคม 2569</h3>
         <p class="text-sm text-subtle">มาดริด</p>
        </div><span class="ml-auto text-2xl">🛍️</span>
       </div>
       <div class="space-y-4 ml-5 border-l-2 border-brand/20 pl-6">
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">☀️ Plaza Puerta del Sol</p>
          <p class="text-subtle">จัตุรัสกลางเมืองมาดริด จุดกิโลเมตรที่ 0 ของสเปน</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://estaticos.esmadrid.com/cdn/farfuture/nldtTlfQcQlA0xrodWcdVhLDu0vy8y7w2anxSeBmlYA/mtime:1586255274/sites/default/files/recursosturisticos/infoturistica/f_i_pg_111009_puerta_sol_-1.jpg" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🏛️ Plaza Mayor</p>
          <p class="text-subtle">ใกล้เขตปูเอต้าเดลซอล หรือประตูพระอาทิตย์ซึ่งเป็นจัตุรัสใจกลางเมือง จุดนับกิโลเมตรแรกของสเปน (กิโลเมตรที่ศูนย์) ยังเป็นศูนย์กลางรถไฟใต้ดินและรถเมล์ทุกสาย และยังเป็นจุดตัดของถนนสายสำคัญของเมืองที่หนาแน่นด้วยร้านค้าและห้างสรรพสินค้าใหญ่อีกด้วย</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://cityspotters.imgix.net/dAXnucTiv2ZASvCKs1gVdvUZ?ixlib=rails-3.1.0&auto=enhance%2Ccompress%2Cformat&q=50&fit=crop&crop=entropy&w=1200&h=630&s=768625bbf95f6c02f958a5ed84e3b5a9" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
          </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารกลางวัน — Tang Chu</p>
          <div class="meal-card rounded-lg p-3 mt-2 text-xs">
           <p class="font-medium text-brand-dark mb-1">เมนู:</p>
           <p>Corn and crab soup  •  White Rice, Fruit, Tea  •  Seasonal vegerables, Egg omelet, Fried noodles with vagetables  •  Steam whole fish, Kungpao chicken, Fried chicken wings, Pork with onion  •  Spicy squid </p>
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🛍️ Las Rozas Village</p>
          <p class="text-subtle">Outlet Shopping Village แบรนด์เนมสุดหรูที่ตั้งอยู่ใกล้กับกรุงมาดริด สินค้าจากคอลเลกชันก่อนหน้าจะถูกนำมาลดราคาตลอดทั้งปี โดยปกติจะเริ่มที่ 30-60% ครอบคลุมทั้งแบรนด์หรู (High-end) และแบรนด์สตรีทชั้นนำ เช่น Gucci, Prada, Burberry, Versace, Loewe, Coach, Michael Kors, Bally, Kenzo, Hugo Boss และแบรนด์กีฬาอย่าง Nike, New Balance</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://phantom-expansion.uecdn.es/c04f0753f282734ebae786940c19b814/f/webp/assets/multimedia/imagenes/2025/07/18/17528211248980.jpg" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍽️ อาหารค่ำ — Thaidy Restaurant </p>
          <div class="meal-card rounded-lg p-3 mt-2 text-xs">
           <p class="font-medium text-brand-dark mb-1">เมนู:</p>
           <p>Tom Yam Kung  •  Pla Lad Prik  •  Pad Pak Thaidy  •  Massaman Kai  •  Kai Tod  •  Plamuek Kapraw  •  Lab Kai </p>
        </div>
       </div>
       <div class="mt-4 bg-amber-50 border border-amber-200 rounded-xl p-3 text-xs flex items-center gap-2"><span>🏨</span> <strong>Melia Castilla ★★★★</strong>
       </div>
      </div>
      </div>
      </div>
      </div>
      </div>
      </div>
      </div>
      </div><!-- Day 7 -->
      <div id="day-7" class="day-content" style="display:none;">
      <div class="day-card bg-white rounded-2xl p-6 shadow-sm border border-brand/10">
       <div class="flex items-center gap-3 mb-4"><span class="bg-brand text-white w-10 h-10 rounded-full flex items-center justify-center font-bold">7</span>
        <div>
         <h3 class="font-semibold text-lg">วันพฤหัสบดีที่ 14 พฤษภาคม 2569</h3>
         <p class="text-sm text-subtle">มาดริด → มิวนิก → กรุงเทพฯ</p>
        </div><span class="ml-auto text-2xl">✈️</span>
       </div>
       <div class="space-y-4 ml-5 border-l-2 border-brand/20 pl-6">
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">👑 Plaza de Oriente</p>
          <p class="text-subtle">จัตุรัสนี้สร้างขึ้นตามคำสั่งของกษัตริย์โจเซฟที่ 1 กษัตริย์ปลาซูเอลาสในปี พ.ศ. 2352 ได้รับการออกแบบโดยสถาปนิก Narciso Pascual y Colomer ในใจกลางของจัตุรัส เป็นรูปปั้นขี่ม้าทองสัมฤทธิ์ของเฟลิเป้ที่ 4 ซึ่งเป็นรูปปั้นแรกในโลกที่ยืนบนขาหลังทั้งสองข้าง ประติมากร (ซึ่งใช้รูปเหมือนของกษัตริย์ที่วาดโดยเบลัซเกซด้วย) ที่ได้รับความช่วยเหลือจากกาลิเลโอ</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://tripaim.com/blog/wp-content/uploads/2020/12/Plaza-de-Oriente-en-Madrid.jpg" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <div class="text-sm">
          <p class="font-semibold">🍷 Mercado De San Miguel</p>
          <p class="text-subtle">เป็นหนึ่งในตลาดที่เก่าแก่ที่สุดในมาดริด นักท่องเที่ยวและชาวมาดริดหลงเสน่ห์ตลาดแห่งนี้เนื่องจากมีบรรยากาศที่คึกคักและการออกแบบสไตล์โบส์อาร์ตอันสง่างาม ตลาดดั้งเดิมนั้นเปิดทำการในปี 1916 และออกแบบตามตลาด Les Halles ในกรุงปารีส</p>
        <div class="grid grid-cols-1 gap-3 mb-3"><img src="https://www.madridhappypeople.com/wp-content/uploads/2024/01/mercado-de-san-miguel-00-jpg.webp" alt="Casa Batlló" loading="lazy" class="rounded-lg w-full h-60 object-cover" rounded-lg flex items-center justify-center text-2xl">
         </div>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">18:25 น.</span> — ✈️ เดินทางสู่มิวนิก โดย Lufthansa เที่ยวบิน LH 1805</p>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">21:00 น.</span> — เดินทางถึงมิวนิก แวะเปลี่ยนเครื่อง</p>
        </div>
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">22:20 น.</span> — ✈️ ออกเดินทางสู่กรุงเทพฯ โดย Lufthansa เที่ยวบิน LH 772</p>
        </div>
       </div>
      </div>
      </div>
      </div>
     </div><!-- Day 8 -->
     <div id="day-8" class="day-content" style="display:none;">
      <div class="day-card bg-white rounded-2xl p-6 shadow-sm border border-brand/10">
       <div class="flex items-center gap-3 mb-4"><span class="bg-brand text-white w-10 h-10 rounded-full flex items-center justify-center font-bold">8</span>
        <div>
         <h3 class="font-semibold text-lg">วันศุกร์ที่ 15 พฤษภาคม 2569</h3>
         <p class="text-sm text-subtle">กรุงเทพฯ</p>
        </div><span class="ml-auto text-2xl">🏠</span>
       </div>
       <div class="space-y-4 ml-5 border-l-2 border-brand/20 pl-6">
        <div class="relative">
         <div class="timeline-dot absolute -left-[31px] top-1"></div>
         <p class="text-sm"><span class="font-semibold text-brand">14:00 น.</span> — 🛬 เดินทางถึงกรุงเทพฯ โดยสวัสดิภาพ</p>
        </div>
       </div>
       <div class="mt-4 bg-green-50 border border-green-200 rounded-xl p-4 text-center">
        <p class="text-2xl mb-2">🎉</p>
        <p class="font-semibold text-green-700">เดินทางถึงกรุงเทพฯ โดยสวัสดิภาพ</p>
        <p class="text-xs text-green-600 mt-1">ขอบคุณที่ไว้วางใจเดินทางกับเรา</p>
       </div>
      </div>
     </div>
    </section><!-- COUNTRY INFO -->
    <section id="sec-country" class="tab-section fade-in">
     <h2 class="font-display text-2xl md:text-3xl font-bold text-brand-dark mb-6">🏛️ ข้อมูลประเทศสเปน</h2>
     <div class="grid md:grid-cols-1 gap-4 mb-6">
      <div class="bg-brand-50 rounded-2xl p-5 border border-brand/10">
       <h3 class="font-semibold text-brand-dark mb-3 text-lg">🇪🇸 ข้อมูลทั่วไป</h3>
       <div class="space-y-2 text-sm">
        <div class="flex justify-between">
         <span class="text-subtle">ชื่อทางการ</span><span class="font-medium">Kingdom of Spain</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">เมืองหลวง</span><span class="font-medium">มาดริด (Madrid)</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">ภาษาราชการ</span><span class="font-medium">สเปน (Español)</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">สกุลเงิน</span><span class="font-medium">ยูโร (EUR / €)</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">เวลาท้องถิ่น</span><span class="font-medium">GMT+2 (ช้ากว่าไทย 5 ชม.)</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">ปลั๊กไฟ</span><span class="font-medium">Type C/F (220V, 50Hz)</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">ประชากร</span><span class="font-medium">~47 ล้านคน</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">เบอร์ฉุกเฉิน</span><span class="font-medium">112</span>
        </div>
       </div>
      </div>
      <div class="bg-brand-50 rounded-2xl p-5 border border-brand/10">
       <h3 class="font-semibold text-brand-dark mb-3 text-lg">💶 สกุลเงินและค่าใช้จ่าย</h3>
       <div class="space-y-2 text-sm">
        <div class="flex justify-between">
         <span class="text-subtle">อัตราแลกเปลี่ยน (โดยประมาณ)</span><span class="font-medium">1 EUR ≈ 37-39 THB</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">น้ำดื่ม (ขวดเล็ก)</span><span class="font-medium">€1 - €2</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">กาแฟ</span><span class="font-medium">€1.50 - €3</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">อาหารจานเดียว</span><span class="font-medium">€10 - €20</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">รถไฟฟ้า/เมโทร</span><span class="font-medium">€1.50 - €2.50</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">แท็กซี่ (เริ่มต้น)</span><span class="font-medium">€3 - €4</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">ทิป (ร้านอาหาร)</span><span class="font-medium">5-10% หรือปัดเศษ</span>
        </div>
        <div class="flex justify-between">
         <span class="text-subtle">VAT Refund</span><span class="font-medium">ซื้อ €90.16+ ขอคืนภาษีได้</span>
        </div>
       </div>
      </div>
     </div>
     <div class="grid md:grid-cols-1 gap-4">
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-2">🏙️ บาร์เซโลนา</h4>
       <p class="text-sm text-subtle">เมืองหลวงของแคว้นคาตาลัน ศูนย์กลางศิลปะ สถาปัตยกรรม และฟุตบอล เต็มไปด้วยผลงานของ Gaudí</p>
      </div>
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-2">⛪ ซาราโกซ่า</h4>
       <p class="text-sm text-subtle">เมืองเก่าแก่ที่สุดแห่งหนึ่งของสเปน ตั้งอยู่ริมแม่น้ำ Ebro เป็นจุดกึ่งกลางระหว่างบาร์เซโลนาและมาดริด</p>
      </div>
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-2">👑 มาดริด</h4>
       <p class="text-sm text-subtle">เมืองหลวงของสเปน ศูนย์กลางการเมือง วัฒนธรรม และแฟชั่น มีพระราชวัง พิพิธภัณฑ์ และย่านช้อปปิ้งระดับโลก</p>
      </div>
     </div>
     <div class="mt-6 bg-amber-50 border border-amber-200 rounded-2xl p-5">
      <h4 class="font-semibold text-amber-800 mb-2">⚠️ ข้อควรระวัง</h4>
      <ul class="text-sm text-amber-700 space-y-1">
       <li>• ระวังมิจฉาชีพและนักล้วงกระเป๋าในย่านท่องเที่ยว โดยเฉพาะ La Rambla, Plaza Mayor</li>
       <li>• เก็บพาสปอร์ตไว้ในที่ปลอดภัย พกสำเนาติดตัวแทน</li>
       <li>• ร้านอาหารมักเปิดเสิร์ฟมื้อกลางวัน 13:30-16:00 และมื้อค่ำ 20:30-23:00</li>
       <li>• ร้านค้าบางแห่งปิดพักกลางวัน (Siesta) ช่วง 14:00-17:00</li>
       <li>• น้ำประปาดื่มได้ในสเปน แต่แนะนำซื้อน้ำขวดเพื่อความสะดวก</li>
      </ul>
     </div>
    </section><!-- WEATHER -->
    <section id="sec-weather" class="tab-section fade-in">
     <h2 class="font-display text-2xl md:text-3xl font-bold text-brand-dark mb-2">🌤️ สภาพอากาศ</h2>
     <p class="text-sm text-subtle mb-6">คาดการณ์สภาพอากาศช่วง 8-15 พฤษภาคม 2569 • อ้างอิง: <a href="https://www.accuweather.com" target="_blank" rel="noopener noreferrer" class="text-brand underline">accuweather.com</a></p>
     <div class="grid sm:grid-cols-1 lg:grid-cols-1 gap-4"><!-- Day 1 - BKK -->
      <div class="bg-white border border-brand/10 rounded-2xl p-4 card-hover text-center">
       <p class="text-xs text-subtle">8 พ.ค. (วันที่ 1)</p>
       <p class="font-semibold text-sm">กรุงเทพฯ</p>
       <div class="weather-icon my-2">
        🌙
       </div>
       <p class="text-2xl font-bold text-brand-dark">33°<span class="text-base font-normal text-subtle">/27°C</span></p>
       <p class="text-xs text-subtle mt-1">ร้อนชื้น เมฆบางส่วน</p>
       <div class="flex justify-center gap-3 mt-2 text-xs text-subtle"><span>💧 70%</span> <span>🌧️ 30%</span>
       </div>
      </div><!-- Day 2 - BCN -->
      <div class="bg-white border border-brand/10 rounded-2xl p-4 card-hover text-center">
       <p class="text-xs text-subtle">9 พ.ค. (วันที่ 2)</p>
       <p class="font-semibold text-sm">บาร์เซโลนา</p>
       <div class="weather-icon my-2">
        ⛅
       </div>
       <p class="text-2xl font-bold text-brand-dark">22°<span class="text-base font-normal text-subtle">/15°C</span></p>
       <p class="text-xs text-subtle mt-1">อากาศอบอุ่น มีเมฆบ้าง</p>
       <div class="flex justify-center gap-3 mt-2 text-xs text-subtle"><span>💧 55%</span> <span>🌧️ 15%</span>
       </div>
      </div><!-- Day 3 - BCN -->
      <div class="bg-white border border-brand/10 rounded-2xl p-4 card-hover text-center">
       <p class="text-xs text-subtle">10 พ.ค. (วันที่ 3)</p>
       <p class="font-semibold text-sm">บาร์เซโลนา</p>
       <div class="weather-icon my-2">
        ☀️
       </div>
       <p class="text-2xl font-bold text-brand-dark">24°<span class="text-base font-normal text-subtle">/16°C</span></p>
       <p class="text-xs text-subtle mt-1">แดดออก อากาศดี</p>
       <div class="flex justify-center gap-3 mt-2 text-xs text-subtle"><span>💧 50%</span> <span>🌧️ 10%</span>
       </div>
      </div><!-- Day 4 - ZAR -->
      <div class="bg-white border border-brand/10 rounded-2xl p-4 card-hover text-center">
       <p class="text-xs text-subtle">11 พ.ค. (วันที่ 4)</p>
       <p class="font-semibold text-sm">ซาราโกซ่า</p>
       <div class="weather-icon my-2">
        🌤️
       </div>
       <p class="text-2xl font-bold text-brand-dark">25°<span class="text-base font-normal text-subtle">/13°C</span></p>
       <p class="text-xs text-subtle mt-1">แดดจัด อากาศแห้ง</p>
       <div class="flex justify-center gap-3 mt-2 text-xs text-subtle"><span>💧 40%</span> <span>🌧️ 5%</span>
       </div>
      </div><!-- Day 5 - MAD -->
      <div class="bg-white border border-brand/10 rounded-2xl p-4 card-hover text-center">
       <p class="text-xs text-subtle">12 พ.ค. (วันที่ 5)</p>
       <p class="font-semibold text-sm">มาดริด</p>
       <div class="weather-icon my-2">
        ☀️
       </div>
       <p class="text-2xl font-bold text-brand-dark">26°<span class="text-base font-normal text-subtle">/14°C</span></p>
       <p class="text-xs text-subtle mt-1">แดดออก อากาศสดใส</p>
       <div class="flex justify-center gap-3 mt-2 text-xs text-subtle"><span>💧 35%</span> <span>🌧️ 5%</span>
       </div>
      </div><!-- Day 6 - MAD -->
      <div class="bg-white border border-brand/10 rounded-2xl p-4 card-hover text-center">
       <p class="text-xs text-subtle">13 พ.ค. (วันที่ 6)</p>
       <p class="font-semibold text-sm">มาดริด</p>
       <div class="weather-icon my-2">
        ⛅
       </div>
       <p class="text-2xl font-bold text-brand-dark">24°<span class="text-base font-normal text-subtle">/13°C</span></p>
       <p class="text-xs text-subtle mt-1">มีเมฆบางส่วน</p>
       <div class="flex justify-center gap-3 mt-2 text-xs text-subtle"><span>💧 45%</span> <span>🌧️ 20%</span>
       </div>
      </div><!-- Day 7 - MAD -->
      <div class="bg-white border border-brand/10 rounded-2xl p-4 card-hover text-center">
       <p class="text-xs text-subtle">14 พ.ค. (วันที่ 7)</p>
       <p class="font-semibold text-sm">มาดริด</p>
       <div class="weather-icon my-2">
        🌤️
       </div>
       <p class="text-2xl font-bold text-brand-dark">25°<span class="text-base font-normal text-subtle">/14°C</span></p>
       <p class="text-xs text-subtle mt-1">อากาศดี แดดอ่อน</p>
       <div class="flex justify-center gap-3 mt-2 text-xs text-subtle"><span>💧 40%</span> <span>🌧️ 10%</span>
       </div>
      </div><!-- Day 8 - BKK -->
      <div class="bg-white border border-brand/10 rounded-2xl p-4 card-hover text-center">
       <p class="text-xs text-subtle">15 พ.ค. (วันที่ 8)</p>
       <p class="font-semibold text-sm">กรุงเทพฯ</p>
       <div class="weather-icon my-2">
        🌤️
       </div>
       <p class="text-2xl font-bold text-brand-dark">34°<span class="text-base font-normal text-subtle">/27°C</span></p>
       <p class="text-xs text-subtle mt-1">ร้อนชื้น</p>
       <div class="flex justify-center gap-3 mt-2 text-xs text-subtle"><span>💧 70%</span> <span>🌧️ 40%</span>
       </div>
      </div>
     </div>
     <div class="mt-6 bg-brand-50 border border-brand/10 rounded-2xl p-5">
      <h4 class="font-semibold text-brand-dark mb-2">📊 สรุปอากาศสเปนช่วงพฤษภาคม</h4>
      <div class="grid md:grid-cols-1 gap-4 text-sm">
       <div>
        <p class="font-medium">🏛️ บาร์เซโลนา</p>
        <p class="text-subtle">อุณหภูมิ 15-24°C อากาศอบอุ่นสบาย ชายทะเลลมเย็น</p>
       </div>
       <div>
        <p class="font-medium">⛪ ซาราโกซ่า</p>
        <p class="text-subtle">อุณหภูมิ 13-25°C อากาศแห้ง แดดแรง กลางคืนเย็น</p>
       </div>
       <div>
        <p class="font-medium">👑 มาดริด</p>
        <p class="text-subtle">อุณหภูมิ 13-26°C อากาศแห้ง แดดแรง เช้า-ค่ำเย็นสบาย</p>
       </div>
      </div>
     </div>
     <p class="text-xs text-subtle mt-4 italic">* ข้อมูลสภาพอากาศเป็นการคาดการณ์โดยประมาณ อ้างอิงจาก accuweather.com สำหรับช่วงเดือนพฤษภาคม กรุณาตรวจสอบอีกครั้งก่อนเดินทาง</p>
    </section><!-- CLOTHING -->
    <section id="sec-clothing" class="tab-section fade-in">
     <h2 class="font-display text-2xl md:text-3xl font-bold text-brand-dark mb-6">👔 คำแนะนำการแต่งกาย</h2>
     <div class="bg-brand-50 rounded-2xl p-5 border border-brand/10 mb-6">
      <h3 class="font-semibold text-brand-dark mb-2">🌡️ สภาพอากาศโดยรวม</h3>
      <p class="text-sm text-subtle">สเปนช่วงเดือนพฤษภาคม อากาศอบอุ่น กลางวัน 22-26°C กลางคืนเย็นลง 13-16°C แนะนำแต่งกายแบบ <strong>Layering (หลายชั้น)</strong> เพื่อปรับตามอุณหภูมิ</p>
     </div>
     <div class="grid md:grid-cols-1 gap-4 mb-6">
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-3">☀️ เสื้อผ้าสำหรับกลางวัน</h4>
       <ul class="text-sm space-y-2">
        <li class="flex items-start gap-2"><span>👕</span> เสื้อยืดแขนสั้น หรือเสื้อเชิ้ตบาง ระบายอากาศดี</li>
        <li class="flex items-start gap-2"><span>👖</span> กางเกงขายาวผ้าบาง หรือกระโปรงยาว</li>
        <li class="flex items-start gap-2"><span>👟</span> รองเท้าผ้าใบสวมสบาย (เดินเยอะมาก!)</li>
        <li class="flex items-start gap-2"><span>🧢</span> หมวกกันแดด</li>
        <li class="flex items-start gap-2"><span>🕶️</span> แว่นกันแดด</li>
       </ul>
      </div>
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-3">🌙 เสื้อผ้าสำหรับตอนเย็น-ค่ำ</h4>
       <ul class="text-sm space-y-2">
        <li class="flex items-start gap-2"><span>🧥</span> แจ็คเก็ตบางหรือเสื้อคลุมน้ำหนักเบา (จำเป็นมาก!)</li>
        <li class="flex items-start gap-2"><span>🧣</span> ผ้าพันคอบาง (สำหรับลมเย็น)</li>
        <li class="flex items-start gap-2"><span>🧤</span> เสื้อแขนยาวสำหรับชมฟุตบอลตอนค่ำ</li>
       </ul>
      </div>
     </div><!-- Day-specific recommendations -->
     <h3 class="font-semibold text-brand-dark text-lg mb-3">📅 แนะนำตามรายวัน</h3>
     <div class="space-y-3">
      <div class="bg-white border-l-4 border-brand rounded-r-xl p-4">
       <p class="font-semibold text-sm">วันที่ 2-3 | บาร์เซโลนา (22-24°C)</p>
       <p class="text-xs text-subtle mt-1">👕 เสื้อยืด + กางเกงขายาว + รองเท้าผ้าใบ สำหรับเดินชม Sagrada Familia และ Camp Nou / 🧥 แจ็คเก็ตบางสำหรับชมฟุตบอลตอนค่ำ</p>
      </div>
      <div class="bg-white border-l-4 border-orange-400 rounded-r-xl p-4">
       <p class="font-semibold text-sm">วันที่ 4 | ซาราโกซ่า (13-25°C)</p>
       <p class="text-xs text-subtle mt-1">👕 เสื้อยืด + เสื้อคลุม (อุณหภูมิต่างกันมากระหว่างกลางวัน-กลางคืน) / 🧢 หมวกกันแดด + ครีมกันแดด (แดดแรง)</p>
      </div>
      <div class="bg-white border-l-4 border-red-500 rounded-r-xl p-4">
       <p class="font-semibold text-sm">วันที่ 5 | มาดริด  (14-26°C)</p>
       <p class="text-xs text-subtle mt-1">🧥 พกแจ็คเก็ตไปด้วย</p>
      </div>
      <div class="bg-white border-l-4 border-amber-400 rounded-r-xl p-4">
       <p class="font-semibold text-sm">วันที่ 6 | มาดริด + Shopping (13-24°C)</p>
       <p class="text-xs text-subtle mt-1">👟 รองเท้าสบายสำหรับเดินช้อปปิ้งที่ Las Rozas Village / 🎒 กระเป๋าสำรองสำหรับใส่ของที่ซื้อ</p>
      </div>
      <div class="bg-white border-l-4 border-brand-dark rounded-r-xl p-4">
       <p class="font-semibold text-sm">วันที่ 7 | มาดริด → สนามบิน (14-25°C)</p>
       <p class="text-xs text-subtle mt-1">👕 แต่งกายสบายสำหรับเดินทาง / 🧥 พกแจ็คเก็ตบนเครื่องบิน (เครื่องเย็น)</p>
      </div>
     </div>
     <div class="mt-6 bg-amber-50 border border-amber-200 rounded-2xl p-5">
      <h4 class="font-semibold text-amber-800 mb-2">🎒 สิ่งที่ควรพกติดตัว</h4>
      <div class="grid grid-cols-1 gap-2 text-sm">
       <div class="flex items-center gap-2">
        <span>🧴</span> ครีมกันแดด SPF 50+
       </div>
       <div class="flex items-center gap-2">
        <span>🧥</span> แจ็คเก็ตบางน้ำหนักเบา
       </div>
       <div class="flex items-center gap-2">
        <span>☂️</span> ร่มพับขนาดเล็ก
       </div>
       <div class="flex items-center gap-2">
        <span>🔌</span> Adapter ปลั๊กแบบ C/F
       </div>
       <div class="flex items-center gap-2">
        <span>💊</span> ยาประจำตัว
       </div>
       <div class="flex items-center gap-2">
        <span>🎒</span> กระเป๋าสำรองพับได้
       </div>
      </div>
     </div>
    </section><!-- TIPS -->
    <section id="sec-tips" class="tab-section fade-in">
     <h2 class="font-display text-2xl md:text-3xl font-bold text-brand-dark mb-6">💡 เกร็ดน่ารู้</h2>
     <div class="space-y-4">
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-2">🍽️ วัฒนธรรมการกิน</h4>
       <ul class="text-sm text-subtle space-y-1">
        <li>• มื้อเที่ยง (Almuerzo): 14:00-16:00 / มื้อค่ำ (Cena): 21:00-23:00</li>
        <li>• ทิปไม่บังคับ ปัดเศษหรือเพิ่ม 5-10% เป็นมารยาท</li>
        <li>• Tapas คืออาหารจานเล็กๆ สั่งหลายจานแชร์กัน</li>
        <li>• น้ำเปล่าบางร้านไม่ฟรี ต้องสั่ง "Agua" (น้ำขวด)</li>
       </ul>
      </div>
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-2">🗣️ ภาษาสเปนพื้นฐาน</h4>
       <div class="grid grid-cols-1 gap-2 text-sm">
        <div class="bg-brand-50 rounded-lg p-2">
         <span class="font-medium">Hola</span> <span class="text-subtle">— สวัสดี</span>
        </div>
        <div class="bg-brand-50 rounded-lg p-2">
         <span class="font-medium">Gracias</span> <span class="text-subtle">— ขอบคุณ</span>
        </div>
        <div class="bg-brand-50 rounded-lg p-2">
         <span class="font-medium">Por favor</span> <span class="text-subtle">— กรุณา</span>
        </div>
        <div class="bg-brand-50 rounded-lg p-2">
         <span class="font-medium">¿Cuánto?</span> <span class="text-subtle">— ราคาเท่าไร?</span>
        </div>
        <div class="bg-brand-50 rounded-lg p-2">
         <span class="font-medium">La cuenta</span> <span class="text-subtle">— เก็บเงิน</span>
        </div>
        <div class="bg-brand-50 rounded-lg p-2">
         <span class="font-medium">¿Dónde está...?</span> <span class="text-subtle">— ...อยู่ที่ไหน?</span>
        </div>
        <div class="bg-brand-50 rounded-lg p-2">
         <span class="font-medium">Sí / No</span> <span class="text-subtle">— ใช่ / ไม่</span>
        </div>
        <div class="bg-brand-50 rounded-lg p-2">
         <span class="font-medium">Perdón</span> <span class="text-subtle">— ขอโทษ</span>
        </div>
       </div>
      </div>
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-2">🛍️ ช้อปปิ้ง &amp; Tax Refund</h4>
       <ul class="text-sm text-subtle space-y-1">
        <li>• ซื้อสินค้าตั้งแต่ €90.16 ขึ้นไปต่อร้าน สามารถขอ Tax Refund ได้</li>
        <li>• ขอใบ Tax Free ที่ร้าน แล้วนำไปประทับตราที่สนามบินก่อนเช็คอิน</li>
        <li>• La Roca Village (บาร์เซโลนา) &amp; Las Rozas Village (มาดริด) ลดราคา 30-70%</li>
        <li>• แบรนด์แนะนำ: Zara, Mango, Loewe, Camper, Massimo Dutti</li>
       </ul>
      </div>
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-2">⚽ ดูบอล El Clásico</h4>
       <ul class="text-sm text-subtle space-y-1">
        <li>• Camp Nou จุผู้ชมกว่า 99,000 คน</li>
        <li>• แนะนำไปถึงสนามล่วงหน้า 1-2 ชม.</li>
        <li>• พกเฉพาะกระเป๋าขนาดเล็ก (มีข้อจำกัดด้านขนาด)</li>
        <li>• ห้ามนำอาหารและเครื่องดื่มจากข้างนอกเข้า</li>
        <li>• เตรียมแจ็คเก็ตสำหรับชมฟุตบอลตอนค่ำ</li>
       </ul>
      </div>
      <div class="bg-white border border-brand/10 rounded-2xl p-5 card-hover">
       <h4 class="font-semibold text-brand-dark mb-2">📱 การสื่อสารและอินเทอร์เน็ต</h4>
       <ul class="text-sm text-subtle space-y-1">
        <li>• แนะนำซื้อ eSIM หรือ Pocket WiFi ก่อนเดินทาง</li>
        <li>• โรงแรมและร้านอาหารส่วนใหญ่มี WiFi ฟรี</li>
        <li>• โทรฉุกเฉิน: 112 (ใช้ได้ทั่วยุโรป)</li>
        <li>• สถานทูตไทย ณ กรุงมาดริด: +34 91 563 2903</li>
       </ul>
    </section><!-- PASSENGER -->
    <section id="sec-Passenger" class="tab-section fade-in">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Traveler Room List</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;600;700&amp;family=Playfair+Display:wght@600;700&amp;display=swap" rel="stylesheet">
  <style>
    * { box-sizing: border-box; }
    body { font-family: 'Sarabun', sans-serif; margin: 0; }
    .font-display { font-family: 'Playfair Display', serif; }
    .room-card {
      background: linear-gradient(135deg, rgba(255,255,255,0.95), rgba(255,255,255,0.85));
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255,255,255,0.6);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }
    .room-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 20px 40px rgba(0,0,0,0.12);
    }
    .badge {
      display: inline-flex; align-items: center; gap: 4px;
      padding: 4px 12px; border-radius: 9999px; font-size: 0.75rem; font-weight: 600;
    }
    .dietary-badge {
      background: #fef3c7; color: #92400e; border: 1px solid #fde68a;
    }
    .room-badge {
      background: #dbeafe; color: #1e40af; border: 1px solid #bfdbfe;
    }
    .guest-row { display: flex; align-items: center; gap: 12px; padding: 12px 0; }
    .guest-row + .guest-row { border-top: 1px dashed #e5e7eb; }
    .avatar {
      width: 33px; height: 33px; border-radius: 50%; display: flex;
      align-items: center; justify-content: center; font-weight: 700;
      font-size: 0.85rem; flex-shrink: 0; color: #fff;
    }
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .animate-in { animation: fadeUp 0.5s ease forwards; opacity: 0; }
  </style>
  <style>body { box-sizing: border-box; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
</head>
 <body class="h-full">
  <div id="app" class="h-full w-full overflow-auto" style="background: linear-gradient(160deg, #0f172a 0%, #1e3a5f 50%, #0f172a 100%);">
   <div class="max-w-3xl mx-auto px-4 py-10">
    <header class="text-center mb-10 animate-in" style="animation-delay: 0.1s;">
     <div class="inline-flex items-center gap-2 mb-3 px-4 py-1.5 rounded-full" style="background: rgba(255,255,255,0.1); border: 1px solid rgba(255,255,255,0.15);"><i data-lucide="plane" style="width:16px;height:16px;color:#60a5fa;"></i> <span class="text-xs font-semibold tracking-widest uppercase" style="color:#93c5fd;">Passenger name</span>
     </div>
     <h1 id="pageTitle" class="font-display text-3xl md:text-4xl font-bold text-white mt-3">รายชื่อผู้เดินทาง</h1>
     <p class="mt-2 text-sm" style="color:#94a3b8;">ข้อมูลห้องพักของผู้เดินทาง</p>
    </header><!-- Room Card -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 0.25s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 1</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div><!-- Guest 1 -->
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #3b82f6, #1d4ed8);">
        1
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MR. THANAKRIT ITTIANAN</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div><!-- Guest 2 -->
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #ec4899, #be185d);">
        2
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MISS POPPORN INGKATAWEERUT</p>
        <div class="flex flex-wrap items-center gap-2 mt-1"><span class="text-xs text-gray-400">ผู้เดินทาง</span> <span class="badge dietary-badge"> <i data-lucide="leaf" style="width:12px;height:12px;"></i> ไม่ทานเนื้อ </span>
        </div>
       </div>
      </div>
     </div>
    </div><!-- Room Card 2 -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 0.35s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 2</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div><!-- Guest 1 -->
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #10b981, #047857);">
        3
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MR. NIKOM TORRUNGRUEANGKIT</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div><!-- Guest 2 -->
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #f59e0b, #d97706);">
        4
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MISS PAWEENA BOONNAK</p>
        <div class="flex flex-wrap items-center gap-2 mt-1"><span class="text-xs text-gray-400">ผู้เดินทาง</span> <span class="badge dietary-badge"> <i data-lucide="leaf" style="width:12px;height:12px;"></i> ไม่ทานเนื้อ </span>
        </div>
       </div>
      </div>
     </div>
    </div><!-- Room Card 3 -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 0.45s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 3</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #8b5cf6, #6d28d9);">
        5
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MR. SORACHAI CHIAMSIRIWATTANA</p>
        <div class="flex flex-wrap items-center gap-2 mt-1"><span class="text-xs text-gray-400">ผู้เดินทาง</span> <span class="badge dietary-badge"><i data-lucide="leaf" style="width:12px;height:12px;"></i> ไม่ทานเนื้อ</span>
        </div>
       </div>
      </div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #06b6d4, #0891b2);">
        6
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MISS TARA KARNTARA</p>
        <div class="flex flex-wrap items-center gap-2 mt-1"><span class="text-xs text-gray-400">ผู้เดินทาง</span> <span class="badge dietary-badge"><i data-lucide="leaf" style="width:12px;height:12px;"></i> ไม่ทานเนื้อ</span>
        </div>
       </div>
      </div>
     </div>
    </div><!-- Room Card 4 -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 0.55s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 4</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #14b8a6, #0d9488);">
        7
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MISS AURAPAN CHANTAROJVANICH</p>
        <div class="flex flex-wrap items-center gap-2 mt-1"><span class="text-xs text-gray-400">ผู้เดินทาง</span> <span class="badge dietary-badge"><i data-lucide="leaf" style="width:12px;height:12px;"></i> ไม่ทานเนื้อ</span>
        </div>
       </div>
      </div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #f43f5e, #e11d48);">
        8
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MISS THAWANRATH PHACHARAWITKAMON</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
     </div>
    </div><!-- Room Card 5 -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 0.65s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 5</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #a855f7, #9333ea);">
        9
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MR. NARIN BOVONRATTANAKOSOL</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #7c3aed, #6d28d9);">
        10
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">NAN MYA HNIN OO</p>
        <div class="flex flex-wrap items-center gap-2 mt-1"><span class="text-xs text-gray-400">ผู้เดินทาง (เมียนม่า)</span> <span class="badge" style="background: #e0f2fe; color: #0369a1; border: 1px solid #bae6fd;"><i data-lucide="tv" style="width:12px;height:12px;"></i> ไม่ดูบอล</span>
        </div>
       </div>
      </div>
     </div>
    </div><!-- Room Card 6 -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 0.75s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 6</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #06b6d4, #0891b2);">
        11
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MR. KITTISAK SUVISUTTIMONTRE</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #f59e0b, #d97706);">
        12
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MISS ISSADAORN PAKTAWEE</p>
        <div class="flex flex-wrap items-center gap-2 mt-1"><span class="text-xs text-gray-400">ผู้เดินทาง</span> <span class="badge" style="background: #e0f2fe; color: #0369a1; border: 1px solid #bae6fd;"><i data-lucide="tv" style="width:12px;height:12px;"></i> ไม่ดูบอล</span>
        </div>
       </div>
      </div>
     </div>
    </div><!-- Room Card 7 -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 0.85s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 7</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #10b981, #047857);">
        13
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MR. APICHA CHANTARAWARAROJ</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #ec4899, #be185d);">
        14
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MISS TANYALUK HIRANKAIPHOT</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
     </div>
    </div><!-- Room Card 8 -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 0.95s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 8</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #8b5cf6, #6d28d9);">
        15
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MR. TEERATAN THAMMANICHANONT</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #14b8a6, #0d9488);">
        16
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MRS. SARANPHAT THAMMANICHANONT</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
     </div>
    </div><!-- Room Card 9 -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 1.05s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 9</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #f43f5e, #e11d48);">
        17
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MISS PANNAPHAT SUWANNAPHAN</p>
        <div class="flex flex-wrap items-center gap-2 mt-1"><span class="text-xs text-gray-400">ผู้เดินทาง</span> <span class="badge dietary-badge"><i data-lucide="leaf" style="width:12px;height:12px;"></i> ไม่ทานเนื้อ</span>
        </div>
       </div>
      </div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #06b6d4, #0891b2);">
        18
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MISS THIDA NARKNIYOM</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
     </div>
    </div><!-- Room Card 10 -->
    <div class="room-card rounded-2xl p-6 mb-6 animate-in" style="animation-delay: 1.15s;">
     <div class="flex flex-wrap items-center gap-2 mb-4"><i data-lucide="bed-double" style="width:20px;height:20px;color:#1e40af;"></i> <span class="font-bold text-gray-800 text-lg">ห้องที่ 10</span> <span class="badge room-badge"><i data-lucide="door-open" style="width:12px;height:12px;"></i> Twin Room</span>
     </div>
     <div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #a855f7, #9333ea);">
        19
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MASTER PATTRADIT CHANTAROJVANICH</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
      <div class="guest-row">
       <div class="avatar" style="background: linear-gradient(135deg, #3b82f6, #1d4ed8);">
        20
       </div>
       <div class="flex-1 min-w-0">
        <p class="font-semibold text-gray-800 text-sm md:text-base">MR. SIRICHAI PUMKRACHANG</p>
        <p class="text-xs text-gray-400">ผู้เดินทาง</p>
       </div>
      </div>
     </div>
    </div><!-- Summary -->
    <div class="animate-in rounded-xl p-4 flex flex-wrap gap-6 justify-center text-sm" style="animation-delay: 1.3s; background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.1);">
     <div class="flex items-center gap-2 text-blue-300"><i data-lucide="users" style="width:16px;height:16px;"></i> <span>ผู้เดินทางทั้งหมด <strong class="text-white">20</strong> ท่าน</span>
     </div>
     <div class="flex items-center gap-2 text-blue-300"><i data-lucide="bed-double" style="width:16px;height:16px;"></i> <span>ห้องพัก <strong class="text-white">10</strong> ห้อง</span>
     </div>
     <div class="flex items-center gap-2 text-amber-300"><i data-lucide="utensils" style="width:16px;height:16px;"></i> <span>ไม่ทานเนื้อ <strong class="text-white">6</strong> ท่าน</span>
     </div>
     <div class="flex items-center gap-2 text-cyan-300"><i data-lucide="tv" style="width:16px;height:16px;"></i> <span>ไม่ดูบอล <strong class="text-white">2</strong> ท่าน</span>
     </div>
    </div>
     </div>
    </section>
   </main><!-- Footer -->
   <footer class="bg-brand-dark text-white text-center py-6 px-4">
    <p class="text-sm opacity-80" id="footerText">Spain Explorer 2026 — Barcelona · Zaragoza · Madrid</p>
    <p class="text-xs opacity-50 mt-1">8 - 15 พฤษภาคม 2569 | 8 วัน 5 คืน</p>
   </footer>
  </div>
  <script>
// Navigation
function showSection(id) {
  document.querySelectorAll('.tab-section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
  const sec = document.getElementById('sec-' + id);
  if (sec) { sec.classList.add('active'); sec.classList.remove('fade-in'); void sec.offsetWidth; sec.classList.add('fade-in'); }
  document.querySelector(`[data-nav="${id}"]`)?.classList.add('active');
}

// Day tabs
function showDay(n) {
  document.querySelectorAll('.day-content').forEach(d => d.style.display = 'none');
  document.querySelectorAll('.day-tab').forEach(t => t.classList.remove('active-day'));
  const dayEl = document.getElementById('day-' + n);
  if (dayEl) { dayEl.style.display = 'block'; dayEl.classList.remove('fade-in'); void dayEl.offsetWidth; dayEl.classList.add('fade-in'); }
  document.querySelectorAll('.day-tab')[n - 1]?.classList.add('active-day');
}

// Element SDK
const defaultConfig = {
  main_title: 'SPAIN EXPLORER',
  company_name: 'Professional Travel Agency',
  background_color: '#FFFFFF',
  surface_color: '#F0FAFC',
  text_color: '#1E293B',
  primary_action_color: '#00A0C6',
  secondary_action_color: '#007A99',
  font_family: 'Prompt',
  font_size: 16
};

function applyConfig(config) {
  const t = (k) => config[k] || defaultConfig[k];
  const el = (id) => document.getElementById(id);

  if (el('mainTitleDisplay')) el('mainTitleDisplay').textContent = t('main_title');
  if (el('companyNameDisplay')) el('companyNameDisplay').textContent = t('company_name');

  const bg = t('background_color');
  const surface = t('surface_color');
  const txt = t('text_color');
  const primary = t('primary_action_color');
  const secondary = t('secondary_action_color');

  document.body.style.backgroundColor = bg;
  document.body.style.color = txt;

  // Apply surface color to cards
  document.querySelectorAll('.bg-brand-50, .meal-card').forEach(el => el.style.backgroundColor = surface);

  // Apply primary color accents
  document.querySelectorAll('.nav-btn.active').forEach(el => { el.style.backgroundColor = primary; el.style.color = '#fff'; });
  document.querySelectorAll('.day-tab.active-day').forEach(el => { el.style.backgroundColor = primary; el.style.color = '#fff'; });
  document.querySelectorAll('.timeline-dot').forEach(el => { el.style.backgroundColor = primary; el.style.boxShadow = `0 0 0 2px ${primary}`; });

  // Footer
  const footer = document.querySelector('footer');
  if (footer) footer.style.backgroundColor = secondary;

  // Font
  const font = t('font_family');
  const baseSize = t('font_size');
  document.body.style.fontFamily = `${font}, Prompt, sans-serif`;
  document.querySelectorAll('h1').forEach(el => el.style.fontSize = `${baseSize * 2.5}px`);
  document.querySelectorAll('h2').forEach(el => el.style.fontSize = `${baseSize * 1.75}px`);
  document.querySelectorAll('h3').forEach(el => el.style.fontSize = `${baseSize * 1.25}px`);
  document.querySelectorAll('p, li, span, td').forEach(el => {
    if (!el.closest('h1, h2, h3, h4, button')) el.style.fontSize = `${baseSize}px`;
  });
}

if (window.elementSdk) {
  window.elementSdk.init({
    defaultConfig,
    onConfigChange: async (config) => applyConfig(config),
    mapToCapabilities: (config) => ({
      recolorables: [
        { get: () => config.background_color || defaultConfig.background_color, set: (v) => { config.background_color = v; window.elementSdk.setConfig({ background_color: v }); } },
        { get: () => config.surface_color || defaultConfig.surface_color, set: (v) => { config.surface_color = v; window.elementSdk.setConfig({ surface_color: v }); } },
        { get: () => config.text_color || defaultConfig.text_color, set: (v) => { config.text_color = v; window.elementSdk.setConfig({ text_color: v }); } },
        { get: () => config.primary_action_color || defaultConfig.primary_action_color, set: (v) => { config.primary_action_color = v; window.elementSdk.setConfig({ primary_action_color: v }); } },
        { get: () => config.secondary_action_color || defaultConfig.secondary_action_color, set: (v) => { config.secondary_action_color = v; window.elementSdk.setConfig({ secondary_action_color: v }); } }
      ],
      borderables: [],
      fontEditable: { get: () => config.font_family || defaultConfig.font_family, set: (v) => { config.font_family = v; window.elementSdk.setConfig({ font_family: v }); } },
      fontSizeable: { get: () => config.font_size || defaultConfig.font_size, set: (v) => { config.font_size = v; window.elementSdk.setConfig({ font_size: v }); } }
    }),
    mapToEditPanelValues: (config) => new Map([
      ['main_title', config.main_title || defaultConfig.main_title],
      ['company_name', config.company_name || defaultConfig.company_name]
    ])
  });
}

lucide.createIcons();
</script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9f1257de51b66097',t:'MTc3NzAwNDcxOC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script>
  </body>
</html>
