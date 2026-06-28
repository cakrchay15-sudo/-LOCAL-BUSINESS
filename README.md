
<!DOCTYPE html>
<html lang="th" class="scroll-smooth dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Local Business | ค้นหาร้านอร่อยและสนับสนุนธุรกิจท้องถิ่น</title>
    
    <!-- Google Fonts: Prompt สำหรับดีไซน์สไตล์ macOS ที่พรีเมียมและอ่านง่าย -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    
    <!-- Font Awesome for Modern Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        navy: {
                            light: '#1e293b',
                            DEFAULT: '#0f172a',
                            dark: '#020617'
                        },
                        gold: {
                            light: '#fbbf24',
                            DEFAULT: '#d4af37',
                            dark: '#b45309'
                        },
                        bluegrey: {
                            light: '#cbd5e1',
                            DEFAULT: '#64748b',
                            dark: '#334155'
                        }
                    },
                    fontFamily: {
                        sans: ['Prompt', '-apple-system', 'BlinkMacSystemFont', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <!-- Custom CSS for Immersive macOS Aero Glass Design & Transitions -->
    <style>
        body {
            transition: background-color 0.4s cubic-bezier(0.16, 1, 0.3, 1), color 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }
        
        /* Premium macOS-style Glassmorphism and Backdrop Blur */
        .mac-glass {
            background: rgba(15, 23, 42, 0.65);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 20px 40px -10px rgba(0, 0, 0, 0.5);
        }

        .light .mac-glass {
            background: rgba(255, 255, 255, 0.75);
            backdrop-filter: blur(25px);
            -webkit-backdrop-filter: blur(25px);
            border: 1px solid rgba(15, 23, 42, 0.08);
            box-shadow: 0 20px 40px -10px rgba(15, 23, 42, 0.1);
        }

        /* Nav Glass Effect */
        .mac-nav-glass {
            background: rgba(15, 23, 42, 0.75);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
        }

        .light .mac-nav-glass {
            background: rgba(255, 255, 255, 0.85);
            border-bottom: 1px solid rgba(15, 23, 42, 0.05);
        }

        /* macOS Smooth Page Transition Animation */
        @keyframes macSlideIn {
            from {
                opacity: 0;
                transform: translateY(20px) scale(0.98);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }
        
        .animate-mac-page {
            animation: macSlideIn 0.5s cubic-bezier(0.16, 1, 0.3, 1) forwards;
        }

        .page-view {
            opacity: 0;
            display: none;
        }
        
        /* Interactive macOS Dock Tooltips and Hover Zoom */
        .dock-item {
            transition: transform 0.25s cubic-bezier(0.16, 1, 0.3, 1), margin 0.25s cubic-bezier(0.16, 1, 0.3, 1);
        }
        .dock-item:hover {
            transform: scale(1.22) translateY(-6px);
        }

        /* Font Size Utilities based on setting */
        .text-scale-sm { font-size: 0.9rem; }
        .text-scale-md { font-size: 1rem; }
        .text-scale-lg { font-size: 1.15rem; }

        /* Slow Spin Logo */
        .animate-spin-slow {
            animation: spin 12s linear infinite;
        }

        /* Rich Premium Card Glow Effect */
        .gold-glow-card {
            border: 1px solid rgba(212, 175, 55, 0.4);
            box-shadow: 0 0 25px rgba(212, 175, 55, 0.15);
        }
        .dark .gold-glow-card {
            border: 1px solid rgba(212, 175, 55, 0.6);
            box-shadow: 0 0 35px rgba(212, 175, 55, 0.25);
        }
    </style>
</head>
<body class="font-sans bg-slate-950 text-slate-100 antialiased min-h-screen pb-32 overflow-x-hidden text-scale-md" id="app-body">

    <!-- 1. เมนูบาร์บนสุดแบบดึงตึง (Sticky Top Navigation) -->
    <nav class="fixed top-0 w-full z-50 mac-nav-glass text-white transition-all duration-300">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <!-- โลโก้แอปพลิเคชันทางซ้าย - เปลี่ยนเป็น Local Business -->
                <div class="flex items-center space-x-2.5 cursor-pointer group" onclick="navigateTo('home')">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-yellow-500 via-gold to-yellow-300 flex items-center justify-center shadow-lg shadow-gold/20 transform group-hover:rotate-12 transition-transform">
                        <i class="fa-solid fa-shop text-navy text-xl"></i>
                    </div>
                    <div>
                        <span class="font-bold text-lg tracking-wide bg-gradient-to-r from-white via-gray-100 to-gold bg-clip-text text-transparent">Local Business</span>
                        <span class="block text-[9px] text-gold tracking-widest font-semibold uppercase -mt-1.5">Thai Community & Food</span>
                    </div>
                </div>
                
                <!-- ตัวเลือกขวา: แชร์และปุ่มเปิดรายการตัวเลือก -->
                <div class="flex items-center space-x-3">
                    <button id="shareBtn" class="bg-white/10 hover:bg-gold/20 hover:text-gold w-10 h-10 rounded-xl flex items-center justify-center transition-all duration-300 border border-white/10" aria-label="Share App">
                        <i class="fa-solid fa-arrow-up-from-bracket"></i>
                    </button>
                    <button id="menuBtn" class="bg-white/10 hover:bg-gold/20 hover:text-gold w-10 h-10 rounded-xl flex items-center justify-center transition-all duration-300 border border-white/10" aria-label="Menu list">
                        <i class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- หน้าต่างเปิดเมนูควบคุม (Dropdown Menu Window) -->
        <div id="dropdownMenu" class="hidden absolute right-4 top-20 w-64 mac-glass rounded-2xl shadow-2xl py-3 border border-gray-200/50 dark:border-gray-700/50 transform origin-top-right transition-all duration-300">
            <div class="px-4 py-2 border-b border-gray-200/40 dark:border-gray-700/40 mb-2">
                <p class="text-xs font-semibold text-bluegrey tracking-wider uppercase">สารบัญระบบ</p>
            </div>
            <a href="#home" onclick="navigateTo('home')" class="flex items-center px-4 py-2.5 text-sm hover:bg-navy/5 dark:hover:bg-white/5 hover:text-gold transition-colors"><i class="fa-solid fa-house w-8 text-center text-bluegrey"></i> หน้าแรก (Home)</a>
            <a href="#food" onclick="navigateTo('food')" class="flex items-center px-4 py-2.5 text-sm hover:bg-navy/5 dark:hover:bg-white/5 hover:text-gold transition-colors"><i class="fa-solid fa-utensils w-8 text-center text-bluegrey"></i> หมวดหมู่อาหาร (Food)</a>
            <a href="#books" onclick="navigateTo('books')" class="flex items-center px-4 py-2.5 text-sm hover:bg-navy/5 dark:hover:bg-white/5 hover:text-gold transition-colors"><i class="fa-solid fa-book-open w-8 text-center text-bluegrey"></i> ห้องหนังสือ (Books)</a>
            <a href="#coupon" onclick="navigateTo('coupon')" class="flex items-center px-4 py-2.5 text-sm hover:bg-navy/5 dark:hover:bg-white/5 hover:text-gold transition-colors"><i class="fa-solid fa-ticket w-8 text-center text-bluegrey"></i> คูปองชุมชน (Coupon)</a>
            <a href="#game" onclick="navigateTo('game')" class="flex items-center px-4 py-2.5 text-sm hover:bg-navy/5 dark:hover:bg-white/5 hover:text-gold transition-colors"><i class="fa-solid fa-gamepad w-8 text-center text-bluegrey"></i> เกมทายสนุก (Game)</a>
            <a href="#profile" onclick="navigateTo('profile')" class="flex items-center px-4 py-2.5 text-sm hover:bg-navy/5 dark:hover:bg-white/5 hover:text-gold transition-colors"><i class="fa-solid fa-user w-8 text-center text-bluegrey"></i> บัญชีของฉัน (Profile)</a>
            <a href="#setting" onclick="navigateTo('setting')" class="flex items-center px-4 py-2.5 text-sm hover:bg-navy/5 dark:hover:bg-white/5 hover:text-gold transition-colors"><i class="fa-solid fa-gear w-8 text-center text-bluegrey"></i> ปรับแต่งการตั้งค่า (Setting)</a>
            <a href="#report" onclick="navigateTo('report')" class="flex items-center px-4 py-2.5 text-sm hover:bg-navy/5 dark:hover:bg-white/5 hover:text-gold transition-colors"><i class="fa-solid fa-flag w-8 text-center text-bluegrey"></i> แจ้งรายงานปัญหา (Report)</a>
        </div>
    </nav>

    <!-- ระบบแสดงข้อความแจ้งเตือน Toast สไตล์ macOS -->
    <div class="fixed top-20 right-4 z-50 flex flex-col space-y-2 pointer-events-none" id="toast-container"></div>

    <!-- macOS Alert Modal System -->
    <div id="macAlertModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-navy/60 backdrop-blur-md hidden transition-opacity duration-300 opacity-0">
        <div class="mac-glass rounded-3xl p-6 max-w-sm w-full border border-white/20 shadow-2xl text-center transform scale-95 transition-transform duration-300">
            <div id="macAlertIcon" class="w-16 h-16 rounded-2xl bg-gradient-to-tr from-yellow-500 to-gold text-white flex items-center justify-center mx-auto text-2xl shadow-lg mb-4">
                <i class="fa-solid fa-circle-exclamation"></i>
            </div>
            <h3 id="macAlertTitle" class="text-lg font-bold text-navy dark:text-white mb-2">แจ้งเตือนระบบ</h3>
            <p id="macAlertMessage" class="text-sm text-gray-600 dark:text-gray-300 mb-6 leading-relaxed">รายละเอียดข้อความแจ้งเตือน</p>
            <button onclick="closeMacAlert()" class="w-full bg-navy hover:bg-navy-light text-white font-medium py-3 rounded-xl text-sm transition-all shadow-md active:scale-95 dark:bg-gold dark:text-navy dark:hover:bg-gold-light">ตกลง</button>
        </div>
    </div>

    <!-- macOS Custom Confirm Modal -->
    <div id="macConfirmModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-navy/60 backdrop-blur-md hidden transition-opacity duration-300 opacity-0">
        <div class="mac-glass rounded-3xl p-6 max-w-sm w-full border border-white/20 shadow-2xl text-center transform scale-95 transition-transform duration-300">
            <div class="w-16 h-16 rounded-2xl bg-gradient-to-tr from-red-500 to-amber-500 text-white flex items-center justify-center mx-auto text-2xl shadow-lg mb-4">
                <i class="fa-solid fa-triangle-exclamation"></i>
            </div>
            <h3 class="text-lg font-bold text-navy dark:text-white mb-2">ยืนยันทำรายการ?</h3>
            <p id="macConfirmMessage" class="text-sm text-gray-600 dark:text-gray-300 mb-6 leading-relaxed">รายละเอียดเรื่องการลบข้อมูล</p>
            <div class="flex space-x-3">
                <button onclick="closeMacConfirm(false)" class="w-1/2 bg-gray-200 hover:bg-gray-300 text-gray-800 dark:bg-slate-800 dark:text-white dark:hover:bg-slate-700 font-medium py-3 rounded-xl text-sm transition-all">ยกเลิก</button>
                <button onclick="closeMacConfirm(true)" class="w-1/2 bg-red-500 hover:bg-red-600 text-white font-medium py-3 rounded-xl text-sm transition-all shadow-md shadow-red-500/20">ยืนยัน</button>
            </div>
        </div>
    </div>

    <!-- macOS Share Sheet Modal -->
    <div id="macShareModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/60 backdrop-blur-md hidden transition-opacity duration-300">
        <div class="mac-glass rounded-3xl p-6 max-w-md w-full border border-white/20 shadow-2xl text-center transform scale-95 transition-transform duration-300">
            <div class="flex justify-between items-center mb-4">
                <h3 class="text-lg font-bold text-navy dark:text-white flex items-center"><i class="fa-solid fa-arrow-up-from-bracket text-gold mr-2"></i>แชร์หน้าต่างนี้</h3>
                <button onclick="closeShareModal()" class="text-gray-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <p class="text-xs text-gray-400 mb-4 text-left">เลือกช่องทางเพื่อแชร์เว็บไซต์สนับสนุนธุรกิจท้องถิ่นและเรียนรู้วัฒนธรรมไทย</p>
            
            <div class="flex space-x-2 bg-slate-900/60 p-2 rounded-2xl mb-4 border border-white/10">
                <input type="text" id="shareUrlInput" readonly class="w-full bg-transparent border-none text-xs text-white focus:ring-0 outline-none select-all px-2">
                <button onclick="copyShareUrl()" class="bg-gold text-navy px-4 py-2 rounded-xl text-xs font-semibold whitespace-nowrap active:scale-95 transition-all">
                    คัดลอกลิงก์
                </button>
            </div>

            <div class="grid grid-cols-3 gap-2">
                <a id="shareFbLink" target="_blank" class="flex flex-col items-center p-3 rounded-xl bg-blue-950/20 text-blue-400 hover:bg-blue-900/30 transition-colors">
                    <i class="fa-brands fa-facebook text-xl mb-1"></i>
                    <span class="text-[10px] font-semibold">Facebook</span>
                </a>
                <a id="shareLineLink" target="_blank" class="flex flex-col items-center p-3 rounded-xl bg-green-950/20 text-green-400 hover:bg-green-900/30 transition-colors">
                    <i class="fa-brands fa-line text-xl mb-1"></i>
                    <span class="text-[10px] font-semibold">Line</span>
                </a>
                <a id="shareTwitterLink" target="_blank" class="flex flex-col items-center p-3 rounded-xl bg-sky-950/20 text-sky-400 hover:bg-sky-900/30 transition-colors">
                    <i class="fa-brands fa-twitter text-xl mb-1"></i>
                    <span class="text-[10px] font-semibold">Twitter</span>
                </a>
            </div>
        </div>
    </div>

    <!-- ======================= 2. หน้าแรก (HOME VIEW) - ถอดแบบองค์ประกอบจากภาพต้นฉบับ ======================= -->
    <section id="view-home" class="page-view min-h-screen relative flex flex-col justify-between">
        <!-- ภาพพื้นหลัง Hero เต็มจอตามในภาพที่ส่งมา (เกาะหินปูนและเรือหัวโทง) -->
        <div class="absolute inset-0 z-0 overflow-hidden">
            <img src="https://images.unsplash.com/photo-1552465011-b4e21bf6e79a?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80" alt="Phang Nga Thailand" class="w-full h-full object-cover select-none">
            <div class="absolute inset-0 bg-gradient-to-b from-slate-950/85 via-slate-900/70 to-slate-950"></div>
        </div>

        <div class="relative z-10 pt-32 px-4 max-w-4xl mx-auto text-center flex-grow flex flex-col justify-center items-center">
            <!-- ป้ายต้อนรับด้านบนสุดเหมือนในภาพเป๊ะๆ -->
            <div class="mb-4 px-4 py-1.5 bg-white/10 backdrop-blur-md rounded-full border border-white/20 text-gold text-xs font-semibold tracking-widest uppercase shadow">
                ยินดีต้อนรับสู่ LOCAL BUSINESS
            </div>
            
            <!-- พาดหัวหลักตามภาพจริง -->
            <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold text-white mb-6 leading-tight drop-shadow-2xl">
                ท่องเที่ยวอย่างปราศจากความกังวล <br><span class="bg-gradient-to-r from-yellow-400 via-gold to-yellow-200 bg-clip-text text-transparent">อุดหนุนสุดคุ้มร้านอาหารท้องถิ่น</span>
            </h1>
            
            <!-- คำโปรยตามภาพจริง -->
            <p class="text-base md:text-lg text-gray-200 mb-8 max-w-2xl mx-auto font-light leading-relaxed drop-shadow">
                ค้นพบและนำทางตรงสู่ร้านอาหารลับในชุมชน ตรวจสอบคะแนนดาว รีวิวจริง ยอดไลก์ และดูพิกัดอย่างสะดวกรวดเร็วโดยไม่ต้องเสียค่า GP
            </p>
            
            <!-- ช่องค้นหาแบบ macOS Spotlight ในภาพจริง -->
            <div class="w-full max-w-xl mac-glass rounded-2xl p-2.5 flex items-center shadow-2xl border border-white/30 mb-12 hover:border-gold/50 transition-colors">
                <i class="fa-solid fa-magnifying-glass text-bluegrey px-3 text-lg"></i>
                <input type="text" id="homeSearchInput" placeholder="ค้นหาจุดหมาย, ร้านอาหาร, หนังสือ OTOP, คูปอง..." class="w-full bg-transparent border-none text-white placeholder-bluegrey focus:ring-0 outline-none text-sm py-2">
                <button onclick="executeSpotlightSearch()" class="bg-gradient-to-r from-yellow-500 to-gold text-slate-950 font-bold px-6 py-2.5 rounded-xl text-xs hover:shadow-lg hover:shadow-gold/30 active:scale-95 transition-all">
                    ค้นหา
                </button>
            </div>

            <!-- กล่องสถิติด่วนสไตล์ macOS Widgets เหมือนในภาพต้นฉบับเป๊ะๆ -->
            <div class="grid grid-cols-3 gap-4 w-full max-w-lg mb-16">
                <div class="mac-glass p-5 rounded-3xl border border-white/20 text-center cursor-pointer hover:scale-105 transition-all" onclick="navigateTo('food')">
                    <span class="block text-3xl mb-1 text-gold"><i class="fa-solid fa-utensils"></i></span>
                    <span class="block text-[10px] font-bold text-bluegrey tracking-wider uppercase">ร้านอาหาร</span>
                    <span class="text-sm font-bold text-white" id="stat-places-count">12 พิกัดหลัก</span>
                </div>
                <div class="mac-glass p-5 rounded-3xl border border-white/20 text-center cursor-pointer hover:scale-105 transition-all" onclick="navigateTo('game')">
                    <span class="block text-3xl mb-1 text-yellow-500"><i class="fa-solid fa-trophy"></i></span>
                    <span class="block text-[10px] font-bold text-bluegrey tracking-wider uppercase">สถิติเกม</span>
                    <span class="text-sm font-bold text-white" id="stat-game-score">0 แต้ม</span>
                </div>
                <div class="mac-glass p-5 rounded-3xl border border-white/20 text-center cursor-pointer hover:scale-105 transition-all" onclick="navigateTo('profile')">
                    <span class="block text-3xl mb-1 text-sky-400"><i class="fa-solid fa-heart"></i></span>
                    <span class="block text-[10px] font-bold text-bluegrey tracking-wider uppercase">ที่บันทึก</span>
                    <span class="text-sm font-bold text-white" id="stat-saved-count">0 ที่โปรด</span>
                </div>
            </div>
        </div>
    </section>

    <!-- ======================= 3. หน้าอาหาร/แหล่งชุมชน (FOOD VIEW - อดีตหน้า GPS) ======================= -->
    <section id="view-food" class="page-view pt-24 px-4 max-w-7xl mx-auto min-h-screen pb-32">
        <div class="text-center mb-8">
            <span class="text-gold text-xs font-bold tracking-widest uppercase">พิกัดร้านค้าและเมนูอร่อย</span>
            <h2 class="text-3xl md:text-4xl font-bold text-white">หมวดหมู่อาหารและของดีชุมชน</h2>
            <p class="text-bluegrey text-sm mt-1">หมดปัญหาโดนหักเปอร์เซ็นต์ค่า GP ช่วยเหลือพ่อค้าแม่ค้ารายย่อย ค้นหาร้านอร่อย ดูรีวิว และนำทางไปอุดหนุนได้ทันที</p>
        </div>

        <!-- ตัวค้นหาพิกัดและประเพณี -->
        <div class="max-w-md mx-auto mb-6 text-slate-100">
            <div class="mac-glass rounded-2xl p-2 flex items-center shadow border border-white/20">
                <i class="fa-solid fa-magnifying-glass text-bluegrey px-3"></i>
                <input type="text" id="gpsSearchInput" oninput="filterPlacesByCriteria()" placeholder="พิมพ์ชื่อร้านค้า, ประเภทอาหาร, จังหวัด..." class="w-full bg-transparent border-none text-white placeholder-bluegrey focus:ring-0 outline-none text-sm py-1.5">
            </div>
        </div>

        <!-- ระบบคัดกรอง 2 มิติ (Region & Type Filter) -->
        <div class="space-y-3 mb-8 max-w-3xl mx-auto">
            <div>
                <p class="text-xs font-semibold text-bluegrey mb-2 ml-1 text-center sm:text-left"><i class="fa-solid fa-globe mr-1"></i> เลือกภูมิภาค:</p>
                <div class="flex flex-wrap justify-center sm:justify-start gap-1.5 bg-slate-900/40 p-1.5 rounded-2xl mac-glass">
                    <button onclick="setRegionFilter('all')" class="region-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl transition-all duration-300 bg-gold text-slate-950 shadow" id="reg-all">ทุกภาค</button>
                    <button onclick="setRegionFilter('central')" class="region-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl text-bluegrey hover:text-white" id="reg-central">ภาคกลาง</button>
                    <button onclick="setRegionFilter('north')" class="region-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl text-bluegrey hover:text-white" id="reg-north">ภาคเหนือ</button>
                    <button onclick="setRegionFilter('northeast')" class="region-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl text-bluegrey hover:text-white" id="reg-northeast">ภาคอีสาน</button>
                    <button onclick="setRegionFilter('south')" class="region-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl text-bluegrey hover:text-white" id="reg-south">ภาคใต้</button>
                </div>
            </div>

            <div>
                <p class="text-xs font-semibold text-bluegrey mb-2 ml-1 text-center sm:text-left"><i class="fa-solid fa-tags mr-1"></i> เลือกประเภทอาหาร/ธุรกิจ:</p>
                <div class="flex flex-wrap justify-center sm:justify-start gap-1.5 bg-slate-900/40 p-1.5 rounded-2xl mac-glass">
                    <button onclick="setTypeFilter('all')" class="type-filter-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl transition-all duration-300 bg-gold text-slate-950 shadow" id="type-all">ทั้งหมด</button>
                    <button onclick="setTypeFilter('food')" class="type-filter-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl text-bluegrey hover:text-white" id="type-food">ร้านอาหารเด่น</button>
                    <button onclick="setTypeFilter('historic')" class="type-filter-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl text-bluegrey hover:text-white" id="type-historic">โบราณสถาน</button>
                    <button onclick="setTypeFilter('culture')" class="type-filter-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl text-bluegrey hover:text-white" id="type-culture">วิถีชุมชน OTOP</button>
                </div>
            </div>
        </div>

        <!-- รายการการ์ดสถานที่ (Dynamic Grid List) -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6" id="placesGrid">
            <!-- ไดนามิกเรนเดอร์ผ่าน JS -->
        </div>

        <!-- แผ่นรายละเอียดนำทาง (macOS Style Slide sheet) -->
        <div id="placeDetailModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/60 backdrop-blur-md hidden transition-opacity duration-300 opacity-0">
            <div class="mac-glass rounded-3xl max-w-2xl w-full border border-white/20 shadow-2xl overflow-hidden flex flex-col max-h-[85vh] transform scale-95 transition-transform duration-300 text-white">
                <div class="flex justify-between items-center px-6 py-4 bg-slate-900 border-b border-white/10">
                    <div class="flex items-center space-x-2">
                        <button onclick="closePlaceDetail()" class="w-3 h-3 rounded-full bg-red-500 hover:opacity-85"></button>
                        <div class="w-3 h-3 rounded-full bg-yellow-400"></div>
                        <div class="w-3 h-3 rounded-full bg-green-500"></div>
                        <span class="text-xs font-semibold ml-2">รายงานวิถีเดินทางชุมชน</span>
                    </div>
                    <button onclick="closePlaceDetail()" class="text-white hover:text-gold text-lg"><i class="fa-solid fa-xmark"></i></button>
                </div>

                <div class="p-6 overflow-y-auto space-y-6">
                    <div class="relative h-64 rounded-2xl overflow-hidden shadow-lg border border-white/10">
                        <img id="detail-image" src="" alt="Cover" class="w-full h-full object-cover">
                        <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent"></div>
                        <div class="absolute bottom-4 left-4 text-white">
                            <h3 id="detail-name" class="text-2xl font-bold">ชื่อพิกัด</h3>
                            <p id="detail-location" class="text-xs text-gray-200 mt-1"><i class="fa-solid fa-location-dot text-red-500 mr-1"></i> ตำแหน่ง</p>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div class="bg-slate-900/50 p-4 rounded-2xl border border-white/10">
                            <h4 class="text-sm font-bold text-gold flex items-center mb-3">
                                <i class="fa-solid fa-map-location text-gold mr-2"></i> สถิติและการให้คะแนน
                            </h4>
                            <div class="space-y-2 text-xs">
                                <p class="flex justify-between"><span>คะแนนเฉลี่ยจริง:</span> <strong class="text-gold flex items-center"><i class="fa-solid fa-star mr-1"></i> <span id="detail-gmaps-stars">4.9</span>/5.0</strong></p>
                                <p class="flex justify-between"><span>ผู้โหวตรีวิวรวม:</span> <strong id="detail-gmaps-reviews">38,000+ รีวิว</strong></p>
                                <p class="flex justify-between"><span>ถูกใจจากระบบ (Likes):</span> <strong class="text-red-500" id="detail-gmaps-likes"><i class="fa-solid fa-heart mr-0.5"></i> 15,400 ครั้ง</strong></p>
                            </div>
                        </div>

                        <div class="bg-slate-900/50 p-4 rounded-2xl border border-white/10">
                            <h4 class="text-sm font-bold text-gold flex items-center mb-3">
                                <i class="fa-solid fa-route text-gold mr-2"></i> ข้อมูลนำทางจราจร
                            </h4>
                            <div class="space-y-2 text-xs">
                                <p class="flex justify-between"><span>เส้นทางหลัก:</span> <strong class="text-white">ถนนชุมชนหลวง</strong></p>
                                <p class="flex justify-between"><span>จราจรโดยรอบ:</span> <strong class="text-emerald-500">คล่องตัวสีเขียว</strong></p>
                                <p class="flex justify-between"><span>ระยะทางจากจุดของคุณ:</span> <strong class="text-white" id="detail-calculated-distance">12.5 กม.</strong></p>
                            </div>
                        </div>
                    </div>

                    <div class="bg-slate-900/50 p-4 rounded-2xl border border-white/10">
                        <p class="text-xs font-bold text-bluegrey mb-3 uppercase tracking-wider">เลือกรูปแบบการเดินทาง</p>
                        <div class="grid grid-cols-4 gap-2">
                            <button onclick="setTravelVehicleMode('car')" id="veh-car" class="vehicle-btn flex flex-col items-center p-2 rounded-xl border border-gold bg-gold/15 text-gold font-bold transition-all">
                                <i class="fa-solid fa-car text-lg mb-1"></i>
                                <span class="text-[10px]">รถยนต์</span>
                            </button>
                            <button onclick="setTravelVehicleMode('motorcycle')" id="veh-motorcycle" class="vehicle-btn flex flex-col items-center p-2 rounded-xl border border-white/10 text-bluegrey hover:text-white transition-all">
                                <i class="fa-solid fa-motorcycle text-lg mb-1"></i>
                                <span class="text-[10px]">มอเตอร์ไซค์</span>
                            </button>
                            <button onclick="setTravelVehicleMode('transit')" id="veh-transit" class="vehicle-btn flex flex-col items-center p-2 rounded-xl border border-white/10 text-bluegrey hover:text-white transition-all">
                                <i class="fa-solid fa-bus text-lg mb-1"></i>
                                <span class="text-[10px]">รถสองแถว</span>
                            </button>
                            <button onclick="setTravelVehicleMode('walking')" id="veh-walking" class="vehicle-btn flex flex-col items-center p-2 rounded-xl border border-white/10 text-bluegrey hover:text-white transition-all">
                                <i class="fa-solid fa-walking text-lg mb-1"></i>
                                <span class="text-[10px]">เดินเท้า</span>
                            </button>
                        </div>

                        <div class="grid grid-cols-2 gap-4 mt-4 pt-4 border-t border-white/10 text-center">
                            <div>
                                <span class="text-[10px] text-bluegrey block uppercase">ระยะเวลาเดินทางโดยประมาณ</span>
                                <span class="text-lg font-bold text-white" id="detail-travel-duration">15 นาที</span>
                            </div>
                            <div>
                                <span class="text-[10px] text-bluegrey block uppercase">คาดเวลาที่จะไปถึงพิกัด</span>
                                <span class="text-lg font-bold text-gold" id="detail-arrival-time">13:30 น.</span>
                            </div>
                        </div>
                    </div>

                    <div class="space-y-3">
                        <h4 class="text-sm font-bold text-white flex items-center"><i class="fa-solid fa-comments text-gold mr-2"></i> ความคิดเห็นจากผู้ใช้จริง</h4>
                        <div id="detail-gmaps-comments-container" class="space-y-2"></div>
                    </div>

                    <button id="detail-gmaps-direction-btn" class="w-full bg-gradient-to-r from-yellow-500 to-gold text-slate-950 py-4 rounded-2xl font-bold hover:shadow-xl active:scale-95 transition-all text-center block text-sm shadow-lg">
                        <i class="fa-solid fa-map-location-dot mr-1"></i> ขอเส้นทางเพื่อไปร้านค้านี้ทันที (Google Maps)
                    </button>
                </div>
            </div>
        </div>
    </section>

    <!-- ======================= 4. หน้าห้องสมุดบทความประวัติศาสตร์และ OTOP (BOOKS VIEW) ======================= -->
    <section id="view-books" class="page-view pt-24 px-4 max-w-7xl mx-auto min-h-screen pb-32">
        <div class="text-center mb-10">
            <span class="text-gold text-xs font-bold tracking-widest uppercase">ห้องหนังสือดิจิทัลชุมชน</span>
            <h2 class="text-3xl md:text-4xl font-bold text-white">มรดกทางวรรณกรรมและวรรณคดีสยาม</h2>
            <p class="text-bluegrey text-sm mt-1">คลังความรู้สำหรับประวัติศาสตร์ไทย แหล่งความรู้ท้องถิ่น OTOP และเกร็ดวรรณกรรมล้ำค่า</p>
            
            <!-- ปุ่มเปลี่ยนสถานะ Admin สำหรับแก้ไขเนื้อหาหนังสือ -->
            <div class="mt-4 inline-flex items-center space-x-2 bg-slate-900/60 p-1.5 rounded-full border border-white/10">
                <span class="text-xs text-bluegrey font-medium pl-3" id="adminStatusLabel">สถานะ: ผู้ชมทั่วไป</span>
                <button onclick="toggleAdminMode()" class="bg-gold text-navy px-4 py-1.5 rounded-full text-xs font-bold transition-all shadow" id="adminToggleBtn">
                    <i class="fa-solid fa-lock-open mr-1"></i> เข้าสู่ระบบ Admin
                </button>
            </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-8" id="booksGridContainer">
            <!-- ไดนามิกสร้างการ์ดหนังสือ -->
        </div>

        <!-- หน้าต่างอ่านหนังสือปกติ (Normal macOS Book Reader Modal) -->
        <div id="bookReaderModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/60 backdrop-blur-md hidden transition-opacity duration-300">
            <div class="mac-glass rounded-3xl max-w-2xl w-full border border-white/25 shadow-2xl overflow-hidden flex flex-col max-h-[85vh] text-white">
                <div class="flex justify-between items-center px-6 py-4 bg-slate-900 border-b border-white/10">
                    <div class="flex items-center space-x-2">
                        <div class="w-3 h-3 rounded-full bg-red-500 cursor-pointer" onclick="closeBookReader()"></div>
                        <div class="w-3 h-3 rounded-full bg-yellow-400"></div>
                        <div class="w-3 h-3 rounded-full bg-green-500"></div>
                        <span class="text-xs font-semibold ml-2" id="readerBarTitle">คลังประวัติศาสตร์</span>
                    </div>
                    <button onclick="closeBookReader()" class="text-white hover:text-gold text-lg"><i class="fa-solid fa-xmark"></i></button>
                </div>
                
                <div id="readerImageGallery" class="px-6 pt-6 flex gap-2 overflow-x-auto select-none py-2 border-b border-white/10">
                    <!-- โหลดรูปไดนามิก -->
                </div>

                <div class="p-6 md:p-8 overflow-y-auto text-gray-200 space-y-4" id="readerContentBody">
                    <!-- ข้อมูลบทความ -->
                </div>
            </div>
        </div>

        <!-- หน้าต่างพิเศษ พลิกหน้ากระดาษ (Interactive Page-Flipping Reader) -->
        <div id="specialBookReaderModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/75 backdrop-blur-md hidden transition-opacity duration-300">
            <div class="mac-glass rounded-3xl max-w-4xl w-full border border-white/20 shadow-2xl overflow-hidden flex flex-col h-[80vh] transform scale-95 transition-all duration-300 text-white">
                <div class="flex justify-between items-center px-6 py-4 bg-slate-900 border-b border-white/10">
                    <div class="flex items-center space-x-2">
                        <div class="w-3 h-3 rounded-full bg-red-500 cursor-pointer" onclick="closeSpecialBookReader()"></div>
                        <div class="w-3 h-3 rounded-full bg-yellow-400"></div>
                        <div class="w-3 h-3 rounded-full bg-green-500"></div>
                        <span class="text-xs font-semibold ml-2">สมุดภาพสยามและ OTOP ท้องถิ่น</span>
                    </div>
                    <div class="flex items-center space-x-3 text-xs">
                        <span class="bg-gold/20 text-gold font-bold px-2.5 py-0.5 rounded-full" id="special-page-indicator">หน้า 1/3</span>
                        <button onclick="closeSpecialBookReader()" class="text-white hover:text-gold text-lg"><i class="fa-solid fa-xmark"></i></button>
                    </div>
                </div>

                <div class="flex-grow relative flex items-center justify-center overflow-hidden bg-slate-950 p-4 md:p-8 select-none" 
                     id="special-book-drag-zone"
                     mousedown="handleBookDragStart(event)"
                     mouseup="handleBookDragEnd(event)"
                     touchstart="handleBookTouchStart(event)"
                     touchend="handleBookTouchEnd(event)">
                    
                    <div onclick="prevSpecialPage()" class="absolute left-0 top-0 bottom-0 w-1/12 z-10 cursor-w-resize bg-gradient-to-r from-black/50 to-transparent flex items-center justify-start pl-4 text-white hover:text-gold transition-colors">
                        <i class="fa-solid fa-chevron-left text-3xl"></i>
                    </div>

                    <div onclick="nextSpecialPage()" class="absolute right-0 top-0 bottom-0 w-1/12 z-10 cursor-e-resize bg-gradient-to-l from-black/50 to-transparent flex items-center justify-end pr-4 text-white hover:text-gold transition-colors">
                        <i class="fa-solid fa-chevron-right text-3xl"></i>
                    </div>

                    <div id="special-page-content-wrapper" class="w-full h-full flex flex-col md:flex-row rounded-2xl overflow-hidden shadow-2xl transition-all duration-300 transform scale-100">
                        <div class="w-full md:w-1/2 h-1/2 md:h-full bg-black relative">
                            <img id="special-page-img" src="" alt="Siam Photo" class="w-full h-full object-cover">
                        </div>
                        <div class="w-full md:w-1/2 h-1/2 md:h-full p-6 md:p-10 bg-slate-900 flex flex-col justify-center space-y-4">
                            <span class="text-gold font-bold text-xs tracking-wider uppercase"><i class="fa-solid fa-feather mr-1"></i> จารึกและเรื่องราวชุมชน</span>
                            <div class="h-px bg-gold/30 w-16"></div>
                            <p id="special-page-caption" class="text-base md:text-lg text-slate-100 leading-relaxed font-light">
                                กำลังดึงข้อมูล...
                            </p>
                        </div>
                    </div>
                </div>

                <div class="px-6 py-4 bg-slate-900 border-t border-white/10 flex justify-between items-center text-xs">
                    <p class="text-bluegrey"><i class="fa-regular fa-hand-pointer mr-1"></i> ปัดหน้าจอซ้าย-ขวา เพื่อเปลี่ยนหน้าอ่านหนังสือ</p>
                    <div class="flex space-x-2">
                        <button onclick="prevSpecialPage()" class="bg-white/10 hover:bg-white/20 text-white px-3 py-1.5 rounded-xl font-bold">ย้อนกลับ</button>
                        <button onclick="nextSpecialPage()" class="bg-gold text-navy px-3 py-1.5 rounded-xl font-bold shadow shadow-gold/20">หน้าถัดไป</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- แผงแอดมินแก้ไขรูปภาพหนังสือทั่วไป (Admin Book Media Manager Modal) -->
        <div id="adminBookEditModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/60 backdrop-blur-md hidden transition-opacity duration-300">
            <div class="mac-glass rounded-3xl max-w-md w-full border border-white/20 shadow-2xl overflow-hidden flex flex-col text-white">
                <div class="flex justify-between items-center px-6 py-4 bg-slate-900">
                    <span class="text-xs font-bold"><i class="fa-solid fa-user-gear mr-1"></i> ปรับแต่งรูปภาพคลังหนังสือ OTOP</span>
                    <button onclick="closeAdminEditModal()" class="text-white hover:text-gold text-lg"><i class="fa-solid fa-xmark"></i></button>
                </div>
                <div class="p-6 space-y-4">
                    <h4 class="text-sm font-bold" id="adminBookTitle">แก้ไขหนังสือ</h4>
                    <p class="text-xs text-bluegrey">ระบุ URL รูปภาพ (บรรทัดละ 1 ลิงก์ เพื่อเป็นแกลเลอรีรูปภาพเมื่อเปิดอ่าน)</p>
                    
                    <textarea id="adminBookImagesText" rows="6" class="w-full bg-slate-900 border border-white/10 text-xs rounded-xl block p-3 outline-none resize-none font-mono text-white focus:border-gold" placeholder="https://example.com/image1.jpg&#10;https://example.com/image2.jpg"></textarea>

                    <div class="flex space-x-2">
                        <button onclick="closeAdminEditModal()" class="w-1/2 bg-slate-800 hover:bg-slate-700 text-xs font-bold py-3 rounded-xl transition-all">ยกเลิก</button>
                        <button onclick="saveAdminBookImages()" class="w-1/2 bg-gold text-navy text-xs font-bold py-3 rounded-xl transition-all shadow-md">บันทึกรูปภาพ</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- แผงผู้ดูแลสำหรับแก้ไขหนังสือเล่มพิเศษ (Admin Special Book Editor Modal) -->
        <div id="adminSpecialBookEditModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/60 backdrop-blur-md hidden transition-opacity duration-300">
            <div class="mac-glass rounded-3xl max-w-lg w-full border border-white/20 shadow-2xl overflow-hidden flex flex-col h-[75vh] text-white">
                <div class="flex justify-between items-center px-6 py-4 bg-slate-900">
                    <span class="text-xs font-bold"><i class="fa-solid fa-wand-magic-sparkles mr-1"></i> ตกแต่งหน้าสมุดภาพพิเศษ OTOP เล่มที่ 5</span>
                    <button onclick="closeAdminSpecialBookModal()" class="text-white hover:text-gold text-lg"><i class="fa-solid fa-xmark"></i></button>
                </div>
                <div class="p-6 space-y-4 overflow-y-auto flex-grow">
                    <div class="flex justify-between items-center">
                        <h4 class="text-xs font-bold text-bluegrey uppercase">จัดการหน้าเอกสาร OTOP</h4>
                        <button onclick="addNewAdminSpecialPage()" class="bg-gold text-navy text-[11px] font-bold px-3 py-1.5 rounded-xl transition-all"><i class="fa-solid fa-plus mr-1"></i> เพิ่มหน้าใหม่</button>
                    </div>
                    <div id="admin-special-pages-container" class="space-y-4"></div>
                </div>
                <div class="p-6 bg-slate-900/80 border-t border-white/10 flex space-x-2">
                    <button onclick="closeAdminSpecialBookModal()" class="w-1/2 bg-slate-800 hover:bg-slate-700 text-xs font-bold py-3 rounded-xl transition-all">ยกเลิก</button>
                    <button onclick="saveAdminSpecialBookData()" class="w-1/2 bg-gold text-navy text-xs font-bold py-3 rounded-xl transition-all shadow-md">บันทึกรูป & คำโปรย OTOP</button>
                </div>
            </div>
        </div>
    </section>

    <!-- ======================= 5. หน้าคูปองส่วนลดธุรกิจชุมชน (COUPON VIEW) ======================= -->
    <section id="view-coupon" class="page-view pt-24 px-4 max-w-7xl mx-auto min-h-screen pb-32">
        <div class="text-center mb-10">
            <span class="text-gold text-xs font-bold tracking-widest uppercase">คูปองสนับสนุนผู้ค้า</span>
            <h2 class="text-3xl md:text-4xl font-bold text-white">ส่วนลด & สิทธิประโยชน์พิเศษ</h2>
            <p class="text-bluegrey text-sm mt-1">กดรับคูปองเพื่อสิทธิพิเศษ และแสดงคูปองต่อหน้าร้านในชุมชนเมื่อเดินทางไปอุดหนุน</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6" id="couponsContainer">
            <!-- คูปองชุดที่ 1 -->
            <div class="mac-glass rounded-3xl border border-white/10 p-6 flex flex-col justify-between relative overflow-hidden group">
                <div class="absolute -right-8 -top-8 w-24 h-24 bg-gold/10 rounded-full blur-xl"></div>
                <div>
                    <span class="bg-red-500/20 text-red-400 font-bold text-[10px] px-2.5 py-1 rounded-full uppercase tracking-wider mb-3 inline-block">เครื่องดื่ม & เบเกอรี</span>
                    <h3 class="text-xl font-bold text-white mb-1">ร้านคาเฟ่ชุมชน บ้านขุนเขาวิว</h3>
                    <p class="text-xs text-gold mb-4"><i class="fa-solid fa-ticket mr-1"></i> ส่วนลด 15% เมื่อซื้อเครื่องดื่มแก้วที่สอง</p>
                    <p class="text-xs text-bluegrey leading-relaxed mb-6">ใช้ได้เฉพาะวันเสาร์-อาทิตย์ เพื่อส่งเสริมการท่องเที่ยวนอกเทศกาล</p>
                </div>
                <button onclick="claimCoupon('คาเฟ่ชุมชน บ้านขุนเขาวิว Discount 15%')" class="w-full py-3 bg-gold text-navy rounded-2xl text-xs font-bold hover:bg-gold-light active:scale-95 transition-all">
                    กดรับคูปองรหัสพิเศษ
                </button>
            </div>

            <!-- คูปองชุดที่ 2 -->
            <div class="mac-glass rounded-3xl border border-white/10 p-6 flex flex-col justify-between relative overflow-hidden group">
                <div class="absolute -right-8 -top-8 w-24 h-24 bg-gold/10 rounded-full blur-xl"></div>
                <div>
                    <span class="bg-blue-500/20 text-blue-400 font-bold text-[10px] px-2.5 py-1 rounded-full uppercase tracking-wider mb-3 inline-block">อาหารพื้นถิ่น</span>
                    <h3 class="text-xl font-bold text-white mb-1">ครัวสมศักดิ์ ขนมจีนน้ำยาปู</h3>
                    <p class="text-xs text-gold mb-4"><i class="fa-solid fa-ticket mr-1"></i> ซื้อเซ็ทใหญ่ รับฟรีน้ำสมุนไพร 2 แก้ว</p>
                    <p class="text-xs text-bluegrey leading-relaxed mb-6">สนับสนุนวัตถุดิบและอาหารทะเลสดโดยตรงจากชาวประมงพื้นบ้าน</p>
                </div>
                <button onclick="claimCoupon('ครัวสมศักดิ์ ซื้อเซ็ทใหญ่รับฟรีน้ำสมุนไพร')" class="w-full py-3 bg-gold text-navy rounded-2xl text-xs font-bold hover:bg-gold-light active:scale-95 transition-all">
                    กดรับคูปองรหัสพิเศษ
                </button>
            </div>

            <!-- คูปองชุดที่ 3 -->
            <div class="mac-glass rounded-3xl border border-white/10 p-6 flex flex-col justify-between relative overflow-hidden group">
                <div class="absolute -right-8 -top-8 w-24 h-24 bg-gold/10 rounded-full blur-xl"></div>
                <div>
                    <span class="bg-teal-500/20 text-teal-400 font-bold text-[10px] px-2.5 py-1 rounded-full uppercase tracking-wider mb-3 inline-block">สินค้าหัตถกรรม OTOP</span>
                    <h3 class="text-xl font-bold text-white mb-1">กลุ่มแม่บ้านหัตถกรรมเพ้นท์ลาย</h3>
                    <p class="text-xs text-gold mb-4"><i class="fa-solid fa-ticket mr-1"></i> ส่วนลดทันที 50 บาท เมื่อช้อปครบ 300 บาท</p>
                    <p class="text-xs text-bluegrey leading-relaxed mb-6">สนับสนุนกลุ่มสตรีในชุมชนและเพิ่มโอกาสทางเศรษฐกิจอย่างยั่งยืน</p>
                </div>
                <button onclick="claimCoupon('กลุ่มแม่บ้านหัตถกรรมเพ้นท์ลาย Discount 50 THB')" class="w-full py-3 bg-gold text-navy rounded-2xl text-xs font-bold hover:bg-gold-light active:scale-95 transition-all">
                    กดรับคูปองรหัสพิเศษ
                </button>
            </div>
        </div>
    </section>

    <!-- ======================= 6. หน้าเกมประลองความรู้ (GAME VIEW) ======================= -->
    <section id="view-game" class="page-view pt-24 px-4 max-w-2xl mx-auto min-h-screen pb-32">
        <div class="text-center mb-8">
            <span class="text-gold text-xs font-bold tracking-widest uppercase">เกมนักสำรวจความรู้</span>
            <h2 class="text-3xl font-bold text-white">ประลองภูมิปัญญาสยามและวิถีทางวัฒนธรรม</h2>
            <p class="text-bluegrey text-sm mt-1">ตอบคำถามทักษะประเพณีไทยและมารยาทท้องถิ่น เพื่อสะสมคะแนนในระดับยศโปรไฟล์ของคุณ</p>
        </div>

        <div id="game-start-panel" class="mac-glass rounded-3xl p-8 border border-white/10 text-center shadow-xl">
            <div class="w-20 h-20 rounded-full bg-gradient-to-tr from-yellow-400 to-gold mx-auto flex items-center justify-center text-slate-950 text-3xl shadow-lg mb-6 animate-bounce">
                <i class="fa-solid fa-gamepad"></i>
            </div>
            <h3 class="text-xl font-bold text-white mb-2">กติกาเกมนักสำรวจ</h3>
            <p class="text-sm text-gray-300 leading-relaxed mb-6">
                ตอบคำถาม 5 ข้อเกี่ยวกับขนมโบราณ กฎระเบียบ มารยาทการเยี่ยมชมสถานที่ศักดิ์สิทธิ์ หากคุณทำคะแนนเต็มจะมีสิทธิ์รับป้ายตราฐานะยศวัฒนธรรมสุดพิเศษ!
            </p>
            <button onclick="startCultureQuiz()" class="w-full bg-gradient-to-r from-yellow-500 to-gold text-slate-950 py-4 rounded-2xl font-bold hover:shadow-xl active:scale-95 transition-all">
                เริ่มประลองภูมิปัญญาความรู้
            </button>
        </div>

        <div id="game-quiz-panel" class="mac-glass rounded-3xl p-6 border border-white/10 shadow-xl hidden text-white">
            <div class="flex justify-between items-center mb-4">
                <span class="text-xs font-semibold text-bluegrey" id="quiz-step-label">คำถามที่ 1 จาก 5</span>
                <span class="text-xs font-semibold text-gold" id="quiz-score-live">แต้ม: 0</span>
            </div>
            <div class="w-full bg-slate-800 rounded-full h-2.5 mb-6 overflow-hidden border border-white/5">
                <div class="bg-gradient-to-r from-yellow-500 to-gold h-2.5 rounded-full transition-all duration-300" id="quiz-progressbar" style="width: 20%"></div>
            </div>

            <h4 class="text-lg font-bold text-white mb-6 leading-relaxed" id="quiz-question-text">
                คำถามทดสอบ
            </h4>

            <div class="space-y-3 mb-6" id="quiz-options-container"></div>
        </div>

        <div id="game-result-panel" class="mac-glass rounded-3xl p-8 border border-white/10 text-center shadow-xl hidden text-white">
            <div id="game-medal-icon" class="w-24 h-24 rounded-full bg-yellow-100 dark:bg-yellow-950/40 text-gold flex items-center justify-center mx-auto text-5xl mb-6 shadow-md">
                <i class="fa-solid fa-medal"></i>
            </div>
            <h3 class="text-2xl font-bold text-white mb-2" id="game-evaluation-title">สุดยอดขุนนางผู้เชี่ยวชาญ!</h3>
            <p class="text-sm text-gray-300 mb-6" id="game-result-summary">ตอบคำถามเสร็จสมบูรณ์ คะแนนของคุณได้รับการอัปเดตลงโปรไฟล์แล้ว</p>
            
            <div class="bg-slate-900/60 rounded-2xl p-4 mb-6 border border-white/10">
                <p class="text-xs text-bluegrey uppercase font-bold tracking-wider">ฐานะทางวัฒนธรรมของคุณ</p>
                <p class="text-lg font-bold text-gold mt-1" id="game-user-rank-status">นักเดินทางรอบรู้วิถีไทย</p>
            </div>

            <div class="flex flex-col space-y-3">
                <button onclick="startCultureQuiz()" class="w-full bg-gold text-slate-950 py-3.5 rounded-2xl font-bold hover:shadow-lg active:scale-95 transition-all">
                    ทำแบบทดสอบอีกครั้ง
                </button>
                <button onclick="navigateTo('profile')" class="w-full bg-transparent hover:bg-white/5 text-white border border-white/20 py-3 rounded-2xl text-sm font-semibold transition-all">
                    ไปเช็คโปรไฟล์และสถานที่โปรด
                </button>
            </div>
        </div>
    </section>

    <!-- ======================= 7. หน้าบัญชีผู้ใช้งาน (PROFILE VIEW) ======================= -->
    <section id="view-profile" class="page-view pt-24 px-4 max-w-2xl mx-auto min-h-screen pb-32">
        <div class="text-center mb-8">
            <span class="text-gold text-xs font-bold tracking-widest uppercase">หน้าต่างบัญชีของคุณ</span>
            <h2 class="text-3xl font-bold text-white">โปรไฟล์ข้อมูลผู้ใช้</h2>
            <p class="text-bluegrey text-sm mt-1">จัดการชื่อผู้ใช้งาน ถ่ายภาพอวตาร และบันทึกติดตามสถานที่ท้องถิ่นที่คุณชื่นชอบ</p>
        </div>

        <div class="mac-glass rounded-3xl p-6 border border-white/10 shadow-xl mb-6 text-white">
            <div class="flex flex-col sm:flex-row items-center space-y-4 sm:space-y-0 sm:space-x-6 pb-6 border-b border-white/10">
                <div class="relative group">
                    <img id="profile-avatar-img" src="https://randomuser.me/api/portraits/men/32.jpg" alt="Profile" class="w-24 h-24 rounded-full object-cover border-4 border-gold shadow-lg">
                    <button onclick="cycleAvatar()" class="absolute bottom-0 right-0 bg-navy hover:bg-gold hover:text-navy text-white w-8 h-8 rounded-full flex items-center justify-center border border-white transition-all shadow" title="Change Avatar">
                        <i class="fa-solid fa-camera text-xs"></i>
                    </button>
                </div>
                <div class="flex-grow text-center sm:text-left">
                    <div class="flex flex-col sm:flex-row sm:items-center space-y-2 sm:space-y-0 sm:space-x-3">
                        <input type="text" id="profile-name-input" value="นักเดินทางนิรนาม" class="text-xl font-bold text-white bg-transparent border-b border-transparent hover:border-gold focus:border-gold focus:ring-0 outline-none w-full sm:w-auto text-center sm:text-left">
                        <button onclick="saveProfileName()" class="text-xs bg-white/10 hover:bg-gold/20 hover:text-gold px-2.5 py-1 rounded-lg transition-all">บันทึกชื่อ</button>
                    </div>
                    <p class="text-xs text-bluegrey mt-1">ยศและระดับ: <span class="font-semibold text-gold" id="profile-rank-label">ผู้เริ่มเรียนรู้วัฒนธรรม</span></p>
                </div>
            </div>

            <div class="grid grid-cols-2 gap-4 pt-6">
                <div class="bg-slate-900/40 rounded-2xl p-4 border border-white/10 text-center">
                    <span class="block text-bluegrey text-xs">แต้มวัฒนธรรมสะสม</span>
                    <span class="text-2xl font-bold text-white" id="profile-points-display">0 แต้ม</span>
                </div>
                <div class="bg-slate-900/40 rounded-2xl p-4 border border-white/10 text-center">
                    <span class="block text-bluegrey text-xs">เกียรติยศสูงสุด</span>
                    <span class="text-sm font-bold text-gold mt-1 block" id="profile-title-display">ผู้ศึกษาวัฒนธรรมสามัญ</span>
                </div>
            </div>
        </div>

        <div class="mac-glass rounded-3xl p-6 border border-white/10 shadow-xl text-white">
            <h3 class="text-lg font-bold text-white mb-4 flex items-center"><i class="fa-solid fa-heart text-red-500 mr-2 animate-pulse"></i>พิกัดร้านค้า OTOP ที่กดบันทึกโปรด</h3>
            <div id="saved-places-container" class="space-y-3"></div>
        </div>
    </section>

    <!-- ======================= 8. หน้าปรับแต่งการตั้งค่า (SETTING VIEW) ======================= -->
    <section id="view-setting" class="page-view pt-24 px-4 max-w-2xl mx-auto min-h-screen pb-32">
        <div class="text-center mb-8">
            <span class="text-gold text-xs font-bold tracking-widest uppercase">ความพึงพอใจการแสดงผล</span>
            <h2 class="text-3xl font-bold text-white">การควบคุมและตั้งค่าระบบ</h2>
            <p class="text-bluegrey text-sm mt-1">ปรับระดับขนาดฟอนต์ข้อความสยาย ปรับโหมดมืดสว่างเพื่อรักษาสุขภาพสายตา</p>
        </div>

        <div class="mac-glass rounded-3xl p-6 border border-white/10 shadow-xl space-y-6 text-white">
            <div class="flex items-center justify-between pb-4 border-b border-white/10">
                <div>
                    <span class="block font-bold text-white">โหมดสว่าง-มืด (Dark & Light Mode)</span>
                    <span class="text-xs text-bluegrey">เปิดหรือปิดการถนอมดวงตาเมื่อเยี่ยมชมเว็บไซต์</span>
                </div>
                <label class="relative inline-flex items-center cursor-pointer">
                    <input type="checkbox" id="darkModeToggle" class="sr-only peer" onchange="toggleThemeMode()" checked>
                    <div class="w-11 h-6 bg-slate-700 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-gold"></div>
                </label>
            </div>

            <div class="flex flex-col space-y-2 pb-4 border-b border-white/10">
                <div class="flex justify-between items-center">
                    <div>
                        <span class="block font-bold text-white">ขนาดตัวอักษรของระบบ (Text Size Scale)</span>
                        <span class="text-xs text-bluegrey">ปรับขนาดความละเอียดตัวอักษรของทุกบทความ</span>
                    </div>
                    <span class="text-xs font-semibold px-2.5 py-1 bg-white/10 rounded-lg text-gold" id="current-fontSize-label">กลาง</span>
                </div>
                <div class="flex items-center space-x-4">
                    <span class="text-xs text-bluegrey">เล็ก</span>
                    <input type="range" id="fontSizeSlider" min="1" max="3" value="2" class="w-full accent-gold bg-slate-800 h-1.5 rounded-lg appearance-none cursor-pointer" oninput="changeFontSizeSetting(this.value)">
                    <span class="text-xs text-bluegrey">ใหญ่</span>
                </div>
            </div>

            <div class="flex items-center justify-between">
                <div>
                    <span class="block font-bold text-red-400">ล้างข้อมูลส่วนตัวในเครื่อง</span>
                    <span class="text-xs text-bluegrey">กู้คืนคะแนนสะสม ประวัติการบันทึกโปรด กลับสู่ค่ามาตรฐาน</span>
                </div>
                <button onclick="requestResetConfirmation()" class="px-4 py-2 bg-red-500/20 hover:bg-red-500 text-red-200 rounded-xl text-xs font-bold transition-all">
                    ล้างทั้งหมด
                </button>
            </div>
        </div>
    </section>

    <!-- ======================= 9. หน้าแบบฟอร์มรายงานปัญหาและติดต่อ (REPORT VIEW) ======================= -->
    <section id="view-report" class="page-view pt-24 px-4 max-w-2xl mx-auto min-h-screen pb-32">
        <div class="text-center mb-8">
            <span class="text-gold text-xs font-bold tracking-widest uppercase">ติดต่อสื่อสารฝ่ายพัฒนา</span>
            <h2 class="text-3xl font-bold text-white">แนะนําสถานที่ท่องเที่ยวหรือแจ้งปัญหา</h2>
            <p class="text-bluegrey text-sm mt-1">ยินดีรับฟังทุกเสียงแนะแนวเพื่อส่งเสริมเศรษฐกิจชุมชนท้องถิ่นให้ดียิ่งขึ้นไป</p>
        </div>

        <div class="mac-glass rounded-3xl p-6 border border-white/10 shadow-xl relative overflow-hidden text-white">
            <form id="feedbackForm" onsubmit="handleFormSubmission(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold mb-1.5 ml-1">ชื่อ - นามสกุลผู้รายงาน</label>
                    <input type="text" id="report-name" required class="w-full bg-slate-900 border border-white/10 text-white text-sm rounded-xl focus:ring-2 focus:ring-gold focus:border-gold block p-3 outline-none transition-all" placeholder="คุณมั่งมี ศรีสุข">
                </div>
                <div>
                    <label class="block text-xs font-semibold mb-1.5 ml-1">อีเมลเพื่อติดต่อกลับ</label>
                    <input type="email" id="report-email" required class="w-full bg-slate-900 border border-white/10 text-white text-sm rounded-xl focus:ring-2 focus:ring-gold focus:border-gold block p-3 outline-none transition-all" placeholder="mungmee@example.com">
                </div>
                <div>
                    <label class="block text-xs font-semibold mb-1.5 ml-1">หัวข้อการติดต่อ</label>
                    <select id="report-topic" class="w-full bg-slate-900 border border-white/10 text-white text-sm rounded-xl focus:ring-2 focus:ring-gold focus:border-gold block p-3 outline-none transition-all">
                        <option value="suggest">แนะนำร้านค้า/พิกัดชุมชนใหม่</option>
                        <option value="bug">แจ้งระบบขัดข้อง/ปัญหาการใช้งานแอป</option>
                        <option value="business">ติดต่อประสานงานชุมชน</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold mb-1.5 ml-1">ข้อเสนอแนะเพิ่มเติม</label>
                    <textarea id="report-desc" rows="4" required class="w-full bg-slate-900 border border-white/10 text-white text-sm rounded-xl focus:ring-2 focus:ring-gold focus:border-gold block p-3 outline-none transition-all resize-none" placeholder="บอกข้อมูลเพิ่มเติมเกี่ยวกับสถานที่ OTOP ที่อยากส่งเสริม..."></textarea>
                </div>
                <button type="submit" class="w-full text-slate-950 bg-gradient-to-r from-yellow-400 to-gold hover:shadow-lg hover:shadow-gold/20 font-bold rounded-xl text-sm py-3.5 text-center transition-all duration-300 shadow-lg">
                    ส่งข้อมูลหาฝ่ายสนับสนุนชุมชน <i class="fa-regular fa-paper-plane ml-1"></i>
                </button>
            </form>
        </div>
    </section>

    <!-- ส่วนท้ายสุดของหน้าเว็บ (Footer) พร้อมเครดิตและช่องทางติดต่อทางสังคมตามเงื่อนไขเป๊ะๆ -->
    <footer class="bg-slate-950 text-white pt-16 pb-36 border-t border-white/10 rounded-t-[3rem] mt-12 relative overflow-hidden">
        <div class="absolute bottom-0 left-1/2 transform -translate-x-1/2 w-[800px] h-[300px] bg-gold/5 blur-[100px] rounded-full pointer-events-none"></div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="flex flex-col md:flex-row justify-between items-center text-center md:text-left space-y-6 md:space-y-0">
                <div class="mb-4 md:mb-0">
                    <div class="flex items-center justify-center md:justify-start mb-2">
                        <i class="fa-solid fa-shop text-gold text-3xl mr-2 animate-spin-slow"></i>
                        <span class="font-bold text-2xl tracking-wide text-white">Local Business</span>
                    </div>
                    <p class="text-xs text-gray-400 max-w-xs">พอร์ทัลรวบรวมพิกัดท่องเที่ยววิถีไทย ร้านค้า OTOP ลับของชุมชน สนับสนุนชุมชน 100% ปราศจากค่า GP</p>
                </div>

                <!-- การเข้าลิงก์ภายนอกตามเงื่อนไขเป๊ะๆ -->
                <div class="flex items-center space-x-4">
                    <a href="https://www.facebook.com/phuket.cic" target="_blank" class="w-12 h-12 rounded-2xl bg-white/5 flex items-center justify-center hover:bg-gold hover:text-navy transition-all duration-300 shadow-lg border border-white/5" title="Facebook Page">
                        <i class="fa-brands fa-facebook-f text-lg text-white"></i>
                    </a>
                    <a href="https://www.instagram.com/cicphuket?fbclid=IwY2xjawSSVxhleHRuA2FlbQIxMABicmlkETFCTWliaEkxTEM1WFBpZEU5c3J0YwZhcHBfaWQQMjIyMDM5MTc4ODIwMDg5MgABHofGziiRUmcqrgPolEwtK8g-hJNZ72gfCD7FtKoxh-a8Q1OQUD033O49XzIa_aem_DDIVjigrYNBAUCFXdgEU-Q" target="_blank" class="w-12 h-12 rounded-2xl bg-white/5 flex items-center justify-center hover:bg-gold hover:text-navy transition-all duration-300 shadow-lg border border-white/5" title="Instagram Profile">
                        <i class="fa-brands fa-instagram text-lg text-white"></i>
                    </a>
                    <a href="tel:076379012" class="w-12 h-12 rounded-2xl bg-white/5 flex items-center justify-center hover:bg-gold hover:text-navy transition-all duration-300 shadow-lg border border-white/5" title="Call Center">
                        <i class="fa-solid fa-phone text-lg text-white"></i>
                    </a>
                </div>
            </div>
            
            <div class="h-px bg-white/10 my-8"></div>
            
            <div class="text-center text-[10px] text-gray-500">
                <p>&copy; 2026 Local Business App. พัฒนาและส่งเสริมความดีงามของเศรษฐกิจชุมชนยั่งยืน</p>
                <p class="mt-1">ออกแบบในสไตล์ความหรูหราของแอร์โรกระจกเงา (macOS Premium Aero Glassmorphism UI)</p>
            </div>
        </div>
    </footer>

    <!-- ======================= 10. แถบหมวดหมู่ลอยด้านล่างจอ (MACOS DOCK NAVIGATION) ======================= -->
    <div class="fixed bottom-6 left-1/2 transform -translate-x-1/2 z-40 w-11/12 max-w-lg">
        <!-- แถบทรงวงรียาว โปร่งใสสีขาวขุ่นสไตล์ macOS Glassmorphism -->
        <div class="mac-glass rounded-full px-4 py-2.5 sm:px-5 sm:py-3.5 flex items-center justify-around shadow-2xl border border-white/20">
            
            <!-- Home Item -->
            <a href="#home" onclick="navigateTo('home')" class="dock-item flex flex-col items-center text-bluegrey hover:text-gold relative" aria-label="Go to Home" id="dock-home">
                <div class="w-9 h-9 sm:w-11 sm:h-11 rounded-full flex items-center justify-center transition-all bg-white/0 hover:bg-white/15">
                    <i class="fa-solid fa-house text-base sm:text-xl"></i>
                </div>
                <div class="active-dot w-1 sm:w-1.5 h-1 sm:h-1.5 bg-gold rounded-full absolute -bottom-1 hidden"></div>
            </a>
            
            <!-- Food Item (อัปเดตจาก GPS) -->
            <a href="#food" onclick="navigateTo('food')" class="dock-item flex flex-col items-center text-bluegrey hover:text-gold relative" aria-label="Go to Food Category" id="dock-food">
                <div class="w-9 h-9 sm:w-11 sm:h-11 rounded-full flex items-center justify-center transition-all bg-white/0 hover:bg-white/15">
                    <i class="fa-solid fa-utensils text-base sm:text-xl"></i>
                </div>
                <div class="active-dot w-1 sm:w-1.5 h-1 sm:h-1.5 bg-gold rounded-full absolute -bottom-1 hidden"></div>
            </a>
            
            <!-- Books Item -->
            <a href="#books" onclick="navigateTo('books')" class="dock-item flex flex-col items-center text-bluegrey hover:text-gold relative" aria-label="Go to Books" id="dock-books">
                <div class="w-9 h-9 sm:w-11 sm:h-11 rounded-full flex items-center justify-center transition-all bg-white/0 hover:bg-white/15">
                    <i class="fa-solid fa-book-open text-base sm:text-xl"></i>
                </div>
                <div class="active-dot w-1 sm:w-1.5 h-1 sm:h-1.5 bg-gold rounded-full absolute -bottom-1 hidden"></div>
            </a>

            <!-- Coupon Item -->
            <a href="#coupon" onclick="navigateTo('coupon')" class="dock-item flex flex-col items-center text-bluegrey hover:text-gold relative" aria-label="Go to Coupons" id="dock-coupon">
                <div class="w-9 h-9 sm:w-11 sm:h-11 rounded-full flex items-center justify-center transition-all bg-white/0 hover:bg-white/15">
                    <i class="fa-solid fa-ticket text-base sm:text-xl"></i>
                </div>
                <div class="active-dot w-1 sm:w-1.5 h-1 sm:h-1.5 bg-gold rounded-full absolute -bottom-1 hidden"></div>
            </a>
            
            <!-- Game Item (ทดสอบความรู้) -->
            <a href="#game" onclick="navigateTo('game')" class="dock-item flex flex-col items-center text-bluegrey hover:text-gold relative" aria-label="Go to Quiz Game" id="dock-game">
                <div class="w-9 h-9 sm:w-11 sm:h-11 rounded-full flex items-center justify-center transition-all bg-white/0 hover:bg-white/15">
                    <i class="fa-solid fa-gamepad text-base sm:text-xl"></i>
                </div>
                <div class="active-dot w-1 sm:w-1.5 h-1 sm:h-1.5 bg-gold rounded-full absolute -bottom-1 hidden"></div>
            </a>

            <!-- Profile Item -->
            <a href="#profile" onclick="navigateTo('profile')" class="dock-item flex flex-col items-center text-bluegrey hover:text-gold relative" aria-label="Go to Profile" id="dock-profile">
                <div class="w-9 h-9 sm:w-11 sm:h-11 rounded-full flex items-center justify-center transition-all bg-white/0 hover:bg-white/15">
                    <i class="fa-solid fa-user text-base sm:text-xl"></i>
                </div>
                <div class="active-dot w-1 sm:w-1.5 h-1 sm:h-1.5 bg-gold rounded-full absolute -bottom-1 hidden"></div>
            </a>
            
            <!-- Setting Item -->
            <a href="#setting" onclick="navigateTo('setting')" class="dock-item flex flex-col items-center text-bluegrey hover:text-gold relative" aria-label="Go to Settings" id="dock-setting">
                <div class="w-9 h-9 sm:w-11 sm:h-11 rounded-full flex items-center justify-center transition-all bg-white/0 hover:bg-white/15">
                    <i class="fa-solid fa-gear text-base sm:text-xl"></i>
                </div>
                <div class="active-dot w-1 sm:w-1.5 h-1 sm:h-1.5 bg-gold rounded-full absolute -bottom-1 hidden"></div>
            </a>

        </div>
    </div>

    <!-- ======================= 11. JAVASCRIPT LOGIC CONTROLLERS ======================= -->
    <script>
        // ข้อมูลหลักและสถานะภายในระบบ (Internal State)
        const appState = {
            activeRoute: 'home',
            savedPlaces: [],
            gameScore: 0,
            currentQuizIndex: 0,
            quizScore: 0,
            isAdmin: false,
            currentSelectedAdminBookKey: null,
            specialBookCurrentPage: 0,
            dragStartX: 0,
            isDraggingBook: false,
            profile: {
                name: 'นักเดินทางนิรนาม',
                avatarIndex: 0,
                rank: 'ผู้ศึกษาเริ่มเรียนรู้วัฒนธรรม'
            },
            avatars: [
                'https://randomuser.me/api/portraits/men/32.jpg',
                'https://randomuser.me/api/portraits/women/44.jpg',
                'https://randomuser.me/api/portraits/men/85.jpg',
                'https://randomuser.me/api/portraits/women/68.jpg'
            ],
            fontSizeScale: 'md'
        };

        // ชุดคำถามและคำตอบสำหรับเกมประลองวัฒนธรรม
        const quizData = [
            {
                question: 'เมื่อไปกราบพระหรือเยี่ยมชมสถานที่ศักดิ์สิทธิ์ ควรแต่งกายในรูปแบบใดเหมาะสมที่สุด?',
                options: [
                    'แต่งกายด้วยผ้าที่ปกปิดไหล่และหัวเข่ามิดชิดสุภาพ',
                    'สวมเสื้อกล้าม สตรีใส่กระโปรงสั้นเหนือเข่าพองาม',
                    'สวมชุดกีฬาขาสั้นเพื่อความคล่องตัวในการเดินชม'
                ],
                answer: 0,
                points: 20
            },
            {
                question: 'ข้อใดคือจุดประสงค์หลักของการสนับสนุนร้านค้าชุมชนที่ไม่หักเปอร์เซ็นต์ค่า GP?',
                options: [
                    'ทำให้ผู้ค้าลดปริมาณและคุณภาพอาหารลง',
                    'ช่วยผู้ค้ามีรายได้เต็มเม็ดเต็มหน่วย เสริมสร้างความยั่งยืนของครอบครัว',
                    'เพื่อให้ร้านค้ารวมตัวกันขึ้นราคาสินค้าขึ้นไปอีก'
                ],
                answer: 1,
                points: 20
            },
            {
                question: 'หากต้องการเดินทางไปช้อปปิ้งของดี OTOP และขนมจีนอร่อย ควรเตรียมตัวอย่างไรให้เหมาะสมที่สุด?',
                options: [
                    'ตรวจสอบระยะทาง ค้นหารีวิวจริง และแลกเปลี่ยนคูปองส่วนลดจากแอปเพื่อนำไปใช้',
                    'จ้างบริษัทท่องเที่ยวราคาแพงนำทางอย่างเดียวเท่านั้น',
                    'ขับรถสุ่มหาเส้นทางไปเรื่อยๆ โดยไม่ใช้ข้อมูลนำทาง'
                ],
                answer: 0,
                points: 20
            },
            {
                question: 'การถอดรองเท้าก่อนก้าวเข้าสู่วิหารหรืออุโบสถเพื่อเหตุผลหลักข้อใด?',
                options: [
                    'เพื่อรักษาความสะอาดสูงสุดและแสดงความเคารพสถานที่ศักดิ์สิทธิ์',
                    'ป้องกันรองเท้าชำรุดเสียหายจากแดดบนพื้นดินเผา',
                    'เพื่อความสะดวกในการจัดระเบียบรองเท้าของนักท่องเที่ยว'
                ],
                answer: 0,
                points: 20
            },
            {
                question: 'การไหว้แบบสยามประเภทประนมมือไหว้ระดับอก มักใช้ทักทายกับกลุ่มบุคคลใด?',
                options: [
                    'การไหว้เพื่อทักทายกลุ่มบุคคลทั่วไปหรือเพื่อนวัยเดียวกันด้วยไมตรีจิต',
                    'การประนมไหว้เพื่อกราบเคารพพระรัตนตรัยและพระภิกษุสงฆ์',
                    'การประนมไหว้เพื่อการแสดงความกตัญญูกตเวทิตาแก่บิดามารดา'
                ],
                answer: 0,
                points: 20
            }
        ];

        // ฐานข้อมูลร้านค้าชุมชนและมรดกทางวัฒนธรรมรอบประเทศไทย (12 พิกัดหลัก)
        const placesData = [
            {
                id: 0,
                name: "ครัวยายเป้า ขนมจีนน้ำยาปู",
                region: "south",
                type: "food",
                province: "ภูเก็ต",
                rating: "4.9",
                reviews: "2,845",
                likes: "1,240",
                lat: 7.8804,
                lng: 98.3922,
                image: "https://images.unsplash.com/photo-1552465011-b4e21bf6e79a?auto=format&fit=crop&w=800&q=80",
                rules: ["ยินดีต้อนรับนักท่องเที่ยวทุกท่านด้วยความอบอุ่น", "เปิดคูปองลดพิเศษ 10% จากทางแอปเพื่อรับสิทธิ์ด่วน", "งดสูบบุหรี่ในบริเวณร้านเพื่อส่วนรวม"],
                comments: [
                    { author: "สมศรี พิกัดอร่อย", text: "ปูแน่นมากค่ะ น้ำยารสชาติเข้มข้นสมชื่อ ไม่โดนหัก GP ทำให้ร้านรักษาคุณภาพได้เต็มที่จริงๆ" },
                    { author: "Kiat S.", text: "ร้านอาหารตามแบบฉบับท้องถิ่น ค้นหาเส้นทางในซอยลึกจากแอปนี้บอกแม่นยำมาก" }
                ]
            },
            {
                id: 1,
                name: "วัดพระศรีรัตนศาสดาราม (วัดพระแก้ว)",
                region: "central",
                type: "historic",
                province: "กรุงเทพมหานคร",
                rating: "4.9",
                reviews: "38,421",
                likes: "45,210",
                lat: 13.7516,
                lng: 100.4927,
                image: "https://images.unsplash.com/photo-1508009603885-50cf7c579365?auto=format&fit=crop&w=800&q=80",
                rules: ["แต่งกายสุภาพอย่างเคร่งครัด (งดกางเกงขาสั้น/เสื้อแขนกุด)", "ห้ามถ่ายภาพด้านในพระอุโบสถหลัก", "ถอดรองเท้าก่อนก้าวเข้าสู่วิหารศักดิ์สิทธิ์"],
                comments: [
                    { author: "พลอยตะวัน", text: "งดงามเป็นเอกลักษณ์ทางสถาปัตยกรรมของแผ่นดินสยามอย่างแท้จริง" },
                    { author: "John D.", text: "A spectacular place of history and spirituality. Keep proper dress code." }
                ]
            },
            {
                id: 2,
                name: "ตลาดย้อนยุคบ้านละมุน OTOP",
                region: "central",
                type: "culture",
                province: "พระนครศรีอยุธยา",
                rating: "4.7",
                reviews: "1,452",
                likes: "3,110",
                lat: 14.3587,
                lng: 100.5614,
                image: "https://images.unsplash.com/photo-1627589851823-8bc685f40e02?auto=format&fit=crop&w=800&q=80",
                rules: ["สนับสนุนการลดขยะพลาสติกด้วยตะกร้าและใบตอง", "โปรดจอดรถในจุดที่คณะกรรมการชุมชนจัดสรรไว้", "งดการสัมผัสป้ายจำลองโบราณสถานโดยตรง"],
                comments: [
                    { author: "สุทัศน์ ดีจัง", text: "ขนมครกโบราณอร่อยมาก มีของสะสมงานฝีมือชาวบ้านให้ช้อปเพียบ ราคาสบายกระเป๋า" }
                ]
            },
            {
                id: 3,
                name: "เรือนแพขนมถ้วยสูตรลับชุมชน",
                region: "north",
                type: "food",
                province: "เชียงใหม่",
                rating: "4.8",
                reviews: "954",
                likes: "2,400",
                lat: 18.7883,
                lng: 98.9853,
                image: "https://images.unsplash.com/photo-1598970434795-0c54fe7c0648?auto=format&fit=crop&w=800&q=80",
                rules: ["กรุณารับบัตรคิวเพื่อลดความแออัดบริเวณระเบียงน้ำ", "พกถุงเก็บขยะเพื่อรักษาสิ่งแวดล้อมริมคลองแม่ข่า", "สามารถใช้คูปองส่วนลดจากแอปได้ฟรี"],
                comments: [
                    { author: "นภาพร", text: "ทานขนมถ้วยร้อนๆ บนเก้าอี้ริมแพน้ำ ชิลมากค่ะ ได้ความรู้สึกดั้งเดิมจริงๆ" }
                ]
            },
            {
                id: 4,
                name: "อุทยานประวัติศาสตร์สุโขทัย",
                region: "north",
                type: "historic",
                province: "สุโขทัย",
                rating: "4.8",
                reviews: "8,412",
                likes: "9,800",
                lat: 17.0186,
                lng: 99.7035,
                image: "https://images.unsplash.com/photo-1608601015851-30043d9f9f23?auto=format&fit=crop&w=800&q=80",
                rules: ["ห้ามจับ ปีน หรือขูดขีดเนื้อหินศิลาแลงโบราณเด็ดขาด", "จำกัดความเร็วพาหนะจักรยานต่ำกว่า 20 กม./ชม.", "ไม่อนุญาตให้นำของมึนเมาเข้ามาในเขตโบราณสถาน"],
                comments: [
                    { author: "สมจิตร รักษ์ไทย", text: "ปั่นจักรยานรับลมเย็นๆ ถ่ายภาพเงาสะท้อนเจดีย์โบราณมีความสุขที่สุดเลย" }
                ]
            },
            {
                id: 5,
                name: "วิถีเพ้นท์ร่มบ้านบ่อสร้าง OTOP",
                region: "north",
                type: "culture",
                province: "เชียงใหม่",
                rating: "4.7",
                reviews: "1,230",
                likes: "4,500",
                lat: 18.8050,
                lng: 98.9216,
                image: "https://images.unsplash.com/photo-1517089539092-b4e21bf6e79a?auto=format&fit=crop&w=800&q=80",
                rules: ["สามารถทดลองทาสีทำร่มกระดาษสาขนาดพกพาได้ด้วยตัวเอง", "งดการถ่ายภาพรบกวนสมาธิศิลปินขณะวาดลายวิจิตร", "อุดหนุนร่มจริงเพื่อส่งเสริมอาชีพให้คุณยายในชุมชน"],
                comments: [
                    { author: "Araya W.", text: "คุณยายสอนเพ้นท์น่ารักมาก ได้ร่มเพ้นท์ลายดอกไม้ฝีมือตัวเองกลับบ้านประทับใจสุดๆค่ะ" }
                ]
            },
            {
                id: 6,
                name: "อ่างปลาเผา สมุนไพรลุ่มโขง",
                region: "northeast",
                type: "food",
                province: "นครพนม",
                rating: "4.8",
                reviews: "812",
                likes: "1,940",
                lat: 16.9427,
                lng: 104.7247,
                image: "https://images.unsplash.com/photo-1596402184320-417e7178b2cd?auto=format&fit=crop&w=800&q=80",
                rules: ["ปลาสดใหม่จากลำน้ำโขง ตกจากธรรมชาติโดยประมงพื้นบ้าน", "จองคิวรับส่วนลดสุดคุ้มผ่านแอป", "เปิดบริการเฉพาะช่วงเย็นรับลมแม่น้ำโขงสุดคูล"],
                comments: [
                    { author: "สุวัจน์ เจริญวงศ์", text: "เนื้อปลาหวานมาก สมุนไพรแน่นจมูก ทานริมแม่น้ำโขงได้บรรยากาศฟินสุดยอด" }
                ]
            },
            {
                id: 7,
                name: "ปราสาทหินพิมาย",
                region: "northeast",
                type: "historic",
                province: "นครราชสีมา",
                rating: "4.7",
                reviews: "5,420",
                likes: "6,100",
                lat: 15.2211,
                lng: 102.4939,
                image: "https://images.unsplash.com/photo-1601132359277-2b0607637b17?auto=format&fit=crop&w=800&q=80",
                rules: ["ห้ามสลักชื่อตนเองหรือทิ้งร่องรอยบนหินโบราณปราสาท", "โปรดพกน้ำดื่มขวดขนาดเล็กเพื่อความสะดวกจากอากาศร้อน", "แต่งกายพ้นหัวเข่าด้วยท่าทีสำรวม"],
                comments: [
                    { author: "Kamon J.", text: "เป็นสถาปัตยกรรมขอมโบราณที่สมบูรณ์และเด่นชัดที่สุด ลายแกะสลักสวยละเอียด" }
                ]
            },
            {
                id: 8,
                name: "กลุ่มหัตถกรรมทอผ้าไหมมัดหมี่ OTOP",
                region: "northeast",
                type: "culture",
                province: "ขอนแก่น",
                rating: "4.9",
                reviews: "510",
                likes: "1,890",
                lat: 16.4322,
                lng: 102.8236,
                image: "https://images.unsplash.com/photo-1506157786151-b8491531f063?auto=format&fit=crop&w=800&q=80",
                rules: ["สามารถเลือกชมกระบวนการมัดไหมและย้อมครามแบบโบราณ", "สามารถทดลองทอมือโดยได้รับความดูแลจากมัคคุเทศก์ชาวบ้าน", "ซื้อผ้าพันคอแฮนด์เมดเพื่องานหัตถศิลป์สืบต่อ"],
                comments: [
                    { author: "วรรณภา ดีไซน์", text: "ไหมเนื้อดี ลายมัดหมี่ละเอียดมาก ได้ของขวัญล้ำค่าไปฝากผู้ใหญ่ปลื้มใจกันทุกคนค่ะ" }
                ]
            },
            {
                id: 9,
                name: "ย่านประมงโบราณและอู่แกงไตปลา",
                region: "south",
                type: "food",
                province: "นครศรีธรรมราช",
                rating: "4.9",
                reviews: "780",
                likes: "1,600",
                lat: 8.4111,
                lng: 99.9664,
                image: "https://images.unsplash.com/photo-1582468546235-9bf31e5bc4a1?auto=format&fit=crop&w=800&q=80",
                rules: ["แกงไตปลาสดๆ รสจัดจ้านตามตำหรับชาวใต้แท้", "ปลาสดๆ ส่งตรงจากหัวสะพานปลาปากพนัง", "ยินดีให้บริการสลับปรับความเผ็ดตามนักท่องเที่ยวต้องการ"],
                comments: [
                    { author: "ขุนแกงทอง", text: "สุดยอดแห่งความเผ็ดร้อนรสปักษ์ใต้แท้ ทานกับผักสดๆ เยอะๆ สะใจมากครับ" }
                ]
            },
            {
                id: 10,
                name: "ย่านตึกเก่าชิโนโปรตุกีส",
                region: "south",
                type: "historic",
                province: "ภูเก็ต",
                rating: "4.8",
                reviews: "22,410",
                likes: "25,400",
                lat: 7.8804,
                lng: 98.3922,
                image: "https://images.unsplash.com/photo-1583212292454-1fe6229603b7?auto=format&fit=crop&w=800&q=80",
                rules: ["จอดรถอย่างเกรงใจทางเข้าตึกสไตล์ประวัติศาสตร์โบราณ", "ร่วมสนับสนุนร้านขายผ้าพื้นเมืองและโอ้เอ๋วเพื่อชุมชน", "งดทิ้งขยะหรือทำลายผนังตึกเก่าตามกำแพงสตรีทอาร์ต"],
                comments: [
                    { author: "Anon K.", text: "เสน่ห์สตรีทอาร์ตและตึกโบราณ เดินเล่นเพลินดี ขนมพื้นเมืองรอบๆ อร่อยสุดใจ" }
                ]
            },
            {
                id: 11,
                name: "กลุ่มทำกระดองปูเปรี้ยวงานศิลป์ OTOP",
                region: "south",
                type: "culture",
                province: "สุราษฎร์ธานี",
                rating: "4.7",
                reviews: "320",
                likes: "940",
                lat: 9.1415,
                lng: 99.3331,
                image: "https://images.unsplash.com/photo-1540959733332-eab4deceeaf7?auto=format&fit=crop&w=800&q=80",
                rules: ["ทดลองรังสรรค์ลวดลายจากวัสดุขยะเปลือกหอยและกะลาปู", "สนับสนุนผลิตภัณฑ์หอยเปรี้ยวประดิษฐ์จากเยาวชนในโรงเรียนชุมชน", "โปรดพกน้ำดื่มระหว่างเข้าฐานเวิร์กช็อปหัตถกรรม"],
                comments: [
                    { author: "เด็กชายนัท", text: "งานประดิษฐ์จากวัสดุธรรมชาติที่มีความรักและการจัดการที่สร้างสรรค์มาก" }
                ]
            }
        ];

        // ฐานข้อมูลหนังสือ OTOP และวรรณคดี
        const bookLibrary = {
            architecture: {
                title: "สถาปัตยกรรมพระเจดีย์กรุงรัตนโกสินทร์",
                description: "เจาะลึกพุทธศิลป์และรูปแบบเจดีย์ทองคำ ย่อมุมสิบสอง ความงดงามประดับกระเบื้องถ้วยสไตล์พระราชวังหลวงที่สืบทอดอย่างวิจิตร",
                images: [
                    "https://images.unsplash.com/photo-1508009603885-50cf7c579365?auto=format&fit=crop&w=400&q=80",
                    "https://images.unsplash.com/photo-1598970434795-0c54fe7c0648?auto=format&fit=crop&w=400&q=80"
                ],
                content: `<h4 class="text-xl font-bold text-gold mb-3">ศิลปกรรมกระเบื้องเคลือบเบญจรงค์สไตล์ไทย</h4>
                          <p class="mb-4">เจดีย์และปรางค์ยอดแหลมที่ประดิษฐานโดดเด่นสะท้อนถึงการออกแบบขั้นครูที่มีอารยธรรมพุทธบูชาและการผสานวัสดุเคลือบสีโบราณที่นำเข้ามาจากเมืองจีน นำมารังสรรค์เป็นกลีบบัวและยอดสถูปที่งดงามเหนือการเวลา</p>`
            },
            desserts: {
                title: "แกะรอยตำรับขนมไทย ท้าวทองกีบม้า OTOP",
                description: "บันทึกประวัติศาสตร์จากแผ่นดินสมเด็จพระนารายณ์มหาราช สู่ขนมหวานทองหยิบ ทองหยอด ฝอยทอง เอกลักษณ์อาหารมงคลสยาม",
                images: [
                    "https://images.unsplash.com/photo-1552465011-b4e21bf6e79a?auto=format&fit=crop&w=400&q=80"
                ],
                content: `<h4 class="text-xl font-bold text-gold mb-3">ความลงตัวแห่งไข่และน้ำตลามพร้าว</h4>
                          <p class="mb-4">สตรีลูกครึ่งโปรตุเกส นามว่า 'มารี กีมาร์' ได้ปรับประยุกต์ใช้วัตถุดิถุดิบท้องถิ่นอย่างมะพร้าวป่น น้ำตาลโตนด และใบเตยคั้นสด มาร่วมกับไข่แดงจนเกิดความหวานสีทองอร่าม ที่สื่อถึงความเจริญก้าวหน้าของวิถีธุรกิจในชุมชนสยามตั้งแต่สมัยโบราณ</p>`
            },
            special_edition: {
                title: "📖 สมุดภาพ OTOP & วรรณศิลป์ไทย (ฉบับแอนิเมชันพลิกหน้าพิเศษ)",
                description: "คลังภาพวรรณกรรมและสินค้าหัตถกรรมไทยล้ำค่า ออกแบบด้วยเอฟเฟกต์พลิกกระดาษโต้ตอบ (Interactive Swipe / Drag) ปรับแต่งเนื้อหาและเรียงลำดับรูปภาพได้อย่างสมบูรณ์ผ่านแผง Admin",
                isSpecial: true,
                pages: [
                    {
                        image: "https://images.unsplash.com/photo-1508009603885-50cf7c579365?auto=format&fit=crop&w=800&q=80",
                        caption: "จารึกความวิจิตรของวัดอรุณฯ: ยอดปรางค์พระเจดีย์ประดับด้วยเศษกระเบื้องเคลือบหลากสี สะท้อนแสงแดดริมแม่น้ำเจ้าพระยาอย่างงดงาม สมกับเป็นมรดกคู่แผ่นดินไทย"
                    },
                    {
                        image: "https://images.unsplash.com/photo-1598970434795-0c54fe7c0648?auto=format&fit=crop&w=800&q=80",
                        caption: "สืบสายงานพุทธบูชา: สถาปัตยกรรมแห่งจิตวิญญาณบนยอดดอยสูง ที่ซึ่งสายหมอกและแรงศรัทธาของชาวเหนือมารรวมใจเพื่อจรรโลงอารยธรรมไทยอันบริสุทธิ์"
                    },
                    {
                        image: "https://images.unsplash.com/photo-1627589851823-8bc685f40e02?auto=format&fit=crop&w=800&q=80",
                        caption: "ความรุ่งเรืองของกรุงเก่า: ภาพอุทยานประวัติศาสตร์แห่งแผ่นดินพระนครศรีอยุธยา อิฐดินเผาสีแดงล้ำค่าที่ทอแสงอบอุ่นเป็นแรงบันดาลใจให้แก่ชุมชนยั่งยืน"
                    }
                ]
            }
        };

        // สถานะการกรองพิกัดสถานที่
        let currentRegionFilter = 'all';
        let currentTypeFilter = 'all';
        let currentSelectedPlaceId = null;
        let currentSelectedVehicle = 'car';

        // พิกัดจำลองสำหรับการคำนวณระยะทาง
        let userLocation = { lat: 8.48, lng: 99.96 };

        // คำนวณระยะทางตามเส้นทางคมนาคม (Haversine Formula x 1.25)
        function calculateRealRoadDistance(lat1, lon1, lat2, lon2) {
            const R = 6371; 
            const dLat = (lat2 - lat1) * Math.PI / 180;
            const dLon = (lon2 - lon1) * Math.PI / 180;
            const a = Math.sin(dLat / 2) * Math.sin(dLat / 2) +
                      Math.cos(lat1 * Math.PI / 180) * Math.cos(lat2 * Math.PI / 180) *
                      Math.sin(dLon / 2) * Math.sin(dLon / 2);
            const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
            return R * c * 1.25; // คดเคี้ยวตามถนนหนทางจริง
        }

        // ตัวกรองภูมิภาค
        function setRegionFilter(region) {
            currentRegionFilter = region;
            document.querySelectorAll('.region-btn').forEach(btn => {
                btn.className = "region-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl text-bluegrey hover:text-white transition-all";
            });
            const activeBtn = document.getElementById(`reg-${region}`);
            if (activeBtn) {
                activeBtn.className = "region-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl transition-all duration-300 bg-gold text-slate-950 shadow font-bold";
            }
            filterPlacesByCriteria();
        }

        // ตัวกรองประเภท
        function setTypeFilter(type) {
            currentTypeFilter = type;
            document.querySelectorAll('.type-filter-btn').forEach(btn => {
                btn.className = "type-filter-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl text-bluegrey hover:text-white transition-all";
            });
            const activeBtn = document.getElementById(`type-${type}`);
            if (activeBtn) {
                activeBtn.className = "type-filter-btn flex-1 text-xs font-semibold px-3 py-2 rounded-xl transition-all duration-300 bg-gold text-slate-950 shadow font-bold";
            }
            filterPlacesByCriteria();
        }

        // แสดงพิกัดร้านค้า OTOP และสถานที่ท่องเที่ยวชุมชน
        function filterPlacesByCriteria() {
            const searchQuery = document.getElementById('gpsSearchInput').value.trim().toLowerCase();
            const grid = document.getElementById('placesGrid');
            grid.innerHTML = '';

            const filtered = placesData.filter(place => {
                const matchesRegion = (currentRegionFilter === 'all' || place.region === currentRegionFilter);
                const matchesType = (currentTypeFilter === 'all' || place.type === currentTypeFilter);
                const matchesSearch = (
                    place.name.toLowerCase().includes(searchQuery) ||
                    place.province.toLowerCase().includes(searchQuery)
                );
                return matchesRegion && matchesType && matchesSearch;
            });

            if (filtered.length === 0) {
                grid.innerHTML = `
                    <div class="col-span-full text-center py-12">
                        <i class="fa-regular fa-folder-open text-4xl text-bluegrey mb-3"></i>
                        <p class="text-sm text-bluegrey font-medium">ไม่พบผลลัพธ์พิกัดร้านค้าชุมชน OTOP ตามเงื่อนไขดังกล่าว</p>
                    </div>
                `;
                return;
            }

            filtered.forEach(place => {
                const roadKm = calculateRealRoadDistance(userLocation.lat, userLocation.lng, place.lat, place.lng).toFixed(1);
                const isFav = appState.savedPlaces.includes(place.name);
                const heartIconClass = isFav ? "fa-solid fa-heart text-red-500 animate-pulse" : "fa-regular fa-heart";

                let typeBadge = '';
                if (place.type === 'food') typeBadge = '<span class="text-[11px] font-bold bg-amber-500/20 text-amber-300 px-2.5 py-0.5 rounded-md border border-amber-500/30">ร้านอาหาร</span>';
                else if (place.type === 'historic') typeBadge = '<span class="text-[11px] font-bold bg-teal-500/20 text-teal-300 px-2.5 py-0.5 rounded-md border border-teal-500/30">โบราณสถาน</span>';
                else typeBadge = '<span class="text-[11px] font-bold bg-indigo-500/20 text-indigo-300 px-2.5 py-0.5 rounded-md border border-indigo-500/30">วิถี OTOP</span>';

                const cardHtml = `
                    <div class="place-card mac-glass rounded-3xl overflow-hidden group hover:shadow-2xl transition-all duration-500 transform hover:-translate-y-1.5 border border-white/10 text-white">
                        <div class="relative h-48 overflow-hidden cursor-pointer" onclick="openPlaceDetail(${place.id})">
                            <img src="${place.image}" alt="${place.name}" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-700">
                            <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent flex items-end p-3 opacity-0 group-hover:opacity-100 transition-opacity">
                                <span class="text-white text-xs font-semibold"><i class="fa-solid fa-circle-info mr-1"></i> คลิกเพื่อเช็ครีวิว & แผนที่อย่างละเอียด</span>
                            </div>
                            <div class="absolute top-3 right-3 bg-slate-900/90 backdrop-blur-sm px-3 py-1 rounded-full text-xs font-semibold text-white flex items-center shadow-lg border border-white/10">
                                <i class="fa-solid fa-star text-gold mr-1"></i> ${place.rating}
                            </div>
                        </div>
                        <div class="p-6">
                            <div class="flex justify-between items-start mb-2 gap-2">
                                <h3 class="text-lg font-bold text-white cursor-pointer hover:text-gold transition-colors" onclick="openPlaceDetail(${place.id})">${place.name}</h3>
                                ${typeBadge}
                            </div>
                            <p class="text-xs text-bluegrey mb-4"><i class="fa-solid fa-location-dot text-red-500 mr-1"></i> จ.${place.province} (ห่างจากคุณ ~ ${roadKm} กม.)</p>
                            
                            <div class="flex space-x-2">
                                <!-- ปุ่มสีเหลืองแบบพรีเมียมตามสั่ง: กดแล้วขอเส้นทางนำทางจริงไปยัง Google Maps ทันที -->
                                <button onclick="requestDirectionsDirectly(${place.id}, event)" class="flex-1 bg-gold hover:bg-gold-light text-navy py-3 rounded-2xl text-xs font-bold hover:shadow-lg active:scale-95 transition-all flex items-center justify-center space-x-1">
                                    <i class="fa-solid fa-map-location-dot"></i>
                                    <span>ขอเส้นทาง</span>
                                </button>
                                <!-- ปุ่มสีน้ำเงินสำหรับดูรีวิว/คอมเมนต์และระยะทางโดยละเอียด -->
                                <button onclick="openPlaceDetail(${place.id})" class="px-3 bg-slate-800 hover:bg-slate-700 text-white rounded-2xl text-xs font-bold transition-all border border-white/10 active:scale-90" title="ดูรีวิว & รายละเอียด">
                                    <i class="fa-solid fa-magnifying-glass-location"></i>
                                </button>
                                <button onclick="toggleFavorite('${place.name}', this)" class="fav-btn w-11 h-11 rounded-2xl border border-white/10 hover:text-gold hover:border-gold flex items-center justify-center transition-all bg-white/5 active:scale-90">
                                    <i class="${heartIconClass}"></i>
                                </button>
                            </div>
                        </div>
                    </div>
                `;
                grid.insertAdjacentHTML('beforeend', cardHtml);
            });
        }

        // ฟังก์ชันพิเศษสำหรับกดปุ่มสีเหลืองเพื่อขอเส้นทางโดยตรงไปยัง Google Maps
        function requestDirectionsDirectly(placeId, event) {
            if (event) event.stopPropagation();
            const place = placesData.find(p => p.id === placeId);
            if (!place) return;
            
            // เปิด URL ไปยัง Google Maps เพื่อขอเส้นทางทันที
            const gmapsUrl = `https://www.google.com/maps/dir/?api=1&origin=${userLocation.lat},${userLocation.lng}&destination=${place.lat},${place.lng}&travelmode=car`;
            window.open(gmapsUrl, '_blank');
            showNotification("เปิดแผนที่นำทาง", `กำลังเชื่อมต่อไปยัง Google Maps เพื่อขอเส้นทางไป ${place.name}`, "success");
        }

        // เปิดรายละเอียดสถานที่และข้อมูลรีวิว
        function openPlaceDetail(id) {
            currentSelectedPlaceId = id;
            const place = placesData.find(p => p.id === id);
            if (!place) return;

            document.getElementById('detail-image').src = place.image;
            document.getElementById('detail-name').innerText = place.name;
            document.getElementById('detail-location').innerHTML = `<i class="fa-solid fa-location-dot text-red-500 mr-1"></i> จ.${place.province}`;
            
            document.getElementById('detail-gmaps-stars').innerText = place.rating;
            document.getElementById('detail-gmaps-reviews').innerText = `${place.reviews} รีวิว`;
            document.getElementById('detail-gmaps-likes').innerHTML = `<i class="fa-solid fa-heart mr-0.5"></i> ${place.likes} ครั้ง`;

            const commentsContainer = document.getElementById('detail-gmaps-comments-container');
            commentsContainer.innerHTML = '';
            place.comments.forEach(c => {
                const cDiv = document.createElement('div');
                cDiv.className = "bg-slate-900/60 p-3 rounded-xl border border-white/10 text-xs text-slate-200";
                cDiv.innerHTML = `
                    <div class="flex justify-between font-semibold text-gold mb-1">
                        <span><i class="fa-solid fa-user-circle mr-1"></i> ${c.author}</span>
                        <span class="text-[10px] text-bluegrey">ผู้ให้รีวิวจริง</span>
                    </div>
                    <p class="text-gray-300 leading-relaxed">"${c.text}"</p>
                `;
                commentsContainer.appendChild(cDiv);
            });

            const roadKm = calculateRealRoadDistance(userLocation.lat, userLocation.lng, place.lat, place.lng);
            document.getElementById('detail-calculated-distance').innerText = `${roadKm.toFixed(1)} กม.`;

            setTravelVehicleMode('car');
            updateGoogleMapsRedirectBtn();

            const modal = document.getElementById('placeDetailModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.add('opacity-100');
                modal.querySelector('.transform').classList.remove('scale-95');
            }, 50);
        }

        function closePlaceDetail() {
            const modal = document.getElementById('placeDetailModal');
            modal.classList.remove('opacity-100');
            modal.querySelector('.transform').classList.add('scale-95');
            setTimeout(() => {
                modal.classList.add('hidden');
            }, 300);
        }

        // เปลี่ยนวิธีการเดินทาง
        function setTravelVehicleMode(mode) {
            currentSelectedVehicle = mode;
            document.querySelectorAll('.vehicle-btn').forEach(btn => {
                btn.className = "vehicle-btn flex flex-col items-center p-2 rounded-xl border border-white/10 text-bluegrey hover:text-white transition-all";
            });

            const activeBtn = document.getElementById(`veh-${mode}`);
            if (activeBtn) {
                activeBtn.className = "vehicle-btn flex flex-col items-center p-2 rounded-xl border border-gold bg-gold/15 text-gold font-bold transition-all";
            }

            const place = placesData.find(p => p.id === currentSelectedPlaceId);
            if (!place) return;

            const roadKm = calculateRealRoadDistance(userLocation.lat, userLocation.lng, place.lat, place.lng);

            let speed = 75; 
            if (mode === 'motorcycle') speed = 55;
            else if (mode === 'transit') speed = 35;
            else if (mode === 'walking') speed = 4.8;

            let hours = roadKm / speed;
            if (mode === 'transit') hours += 0.2; 

            const totalMins = Math.round(hours * 60);
            let timeText = `${totalMins} นาที`;
            if (totalMins >= 60) {
                const h = Math.floor(totalMins / 60);
                const m = totalMins % 60;
                timeText = `${h} ชั่วโมง ${m} นาที`;
            }

            document.getElementById('detail-travel-duration').innerText = timeText;

            const arrivalDate = new Date();
            arrivalDate.setMinutes(arrivalDate.getMinutes() + totalMins);
            const pad = (n) => String(n).padStart(2, '0');
            document.getElementById('detail-arrival-time').innerText = `${pad(arrivalDate.getHours())}:${pad(arrivalDate.getMinutes())} น.`;

            updateGoogleMapsRedirectBtn();
        }

        function updateGoogleMapsRedirectBtn() {
            const place = placesData.find(p => p.id === currentSelectedPlaceId);
            if (!place) return;

            const gmapsUrl = `https://www.google.com/maps/dir/?api=1&origin=${userLocation.lat},${userLocation.lng}&destination=${place.lat},${place.lng}&travelmode=${currentSelectedVehicle}`;
            
            const btn = document.getElementById('detail-gmaps-direction-btn');
            btn.onclick = () => {
                window.open(gmapsUrl, '_blank');
            };
        }

        // ======================= คลังหนังสือ & แอดมินรูปภาพ OTOP =======================
        function renderBooksLibrary() {
            const container = document.getElementById('booksGridContainer');
            container.innerHTML = '';

            Object.keys(bookLibrary).forEach(key => {
                const book = bookLibrary[key];
                
                if (book.isSpecial) {
                    const imageCount = book.pages.length;
                    const adminSpecialBtn = appState.isAdmin ? `
                        <button onclick="openAdminSpecialBookModal()" class="mt-2 text-xs bg-gold text-navy hover:scale-105 px-3 py-1.5 rounded-xl font-bold flex items-center justify-center space-x-1 transition-all shadow">
                            <i class="fa-solid fa-wand-magic-sparkles"></i> <span>แก้ไขรูปภาพ OTOP (${imageCount} หน้า)</span>
                        </button>
                    ` : '';

                    const specialCardHtml = `
                        <div class="gold-glow-card mac-glass p-6 rounded-3xl border-2 border-gold flex flex-col justify-between col-span-1 md:col-span-2 relative overflow-hidden group text-white">
                            <div class="absolute -right-16 -top-16 w-32 h-32 bg-gold/10 rounded-full blur-2xl pointer-events-none group-hover:scale-150 transition-transform duration-500"></div>
                            
                            <div>
                                <div class="flex justify-between items-start mb-4">
                                    <span class="bg-gradient-to-r from-yellow-500 to-gold text-navy font-bold text-[10px] px-3 py-1 rounded-full uppercase tracking-widest shadow animate-pulse"><i class="fa-solid fa-star mr-1"></i> เล่มพิเศษโต้ตอบชุมชน</span>
                                    ${adminSpecialBtn}
                                </div>
                                <h3 class="text-2xl font-bold text-white mb-2">${book.title}</h3>
                                <p class="text-xs text-bluegrey mb-2">จำนวนหน้ารวม: ${imageCount} หน้า • พลิกสัมผัสภาพ OTOP ดั้งเดิม</p>
                                <p class="text-sm text-gray-300 leading-relaxed mb-6">
                                    ${book.description}
                                </p>
                            </div>
                            <button onclick="openSpecialBookReader()" class="w-full py-4 bg-gradient-to-r from-yellow-400 via-gold to-yellow-300 text-slate-950 rounded-2xl text-xs font-bold hover:shadow-xl active:scale-95 transition-all text-center">
                                <i class="fa-solid fa-book-open mr-1"></i> เปิดดูรูปภาพและอ่านสารบัญเล่มพิเศษ OTOP <i class="fa-solid fa-chevron-right ml-1"></i>
                            </button>
                        </div>
                    `;
                    container.insertAdjacentHTML('afterbegin', specialCardHtml); 
                } else {
                    const imageCount = book.images.length;
                    const adminEditBtn = appState.isAdmin ? `
                        <button onclick="openAdminEditModal('${key}')" class="mt-2 text-xs bg-white/10 hover:bg-gold/20 hover:text-gold px-3 py-1.5 rounded-xl font-bold flex items-center justify-center space-x-1 transition-colors text-white">
                            <i class="fa-solid fa-pen-to-square"></i> <span>แก้ไขภาพ (${imageCount} รูป)</span>
                        </button>
                    ` : '';

                    const cardHtml = `
                        <div class="mac-glass p-6 rounded-3xl border border-white/10 hover:scale-[1.01] transition-all duration-300 flex flex-col justify-between text-white">
                            <div>
                                <div class="flex justify-between items-start mb-4">
                                    <div class="w-12 h-12 rounded-2xl bg-slate-900 text-gold flex items-center justify-center text-xl border border-white/10">
                                        <i class="fa-solid fa-book-open-reader"></i>
                                    </div>
                                    ${adminEditBtn}
                                </div>
                                <h3 class="text-lg font-bold text-white mb-2">${book.title}</h3>
                                <p class="text-xs text-bluegrey mb-1">ภาพประกอบที่มี: ${imageCount} ภาพ</p>
                                <p class="text-sm text-gray-300 leading-relaxed line-clamp-3 mb-4">
                                    ${book.description}
                                </p>
                            </div>
                            <button onclick="readBookContent('${key}')" class="w-full py-3 bg-gold text-navy rounded-2xl text-xs font-bold active:scale-95 transition-all">
                                เปิดอ่านเนื้อหาเอกสาร OTOP <i class="fa-solid fa-chevron-right ml-1"></i>
                            </button>
                        </div>
                    `;
                    container.insertAdjacentHTML('beforeend', cardHtml);
                }
            });
        }

        function readBookContent(bookKey) {
            const book = bookLibrary[bookKey];
            if (!book) return;

            document.getElementById('readerBarTitle').innerText = book.title;
            document.getElementById('readerContentBody').innerHTML = book.content;

            const gallery = document.getElementById('readerImageGallery');
            gallery.innerHTML = '';
            
            if (book.images && book.images.length > 0) {
                book.images.forEach(imgUrl => {
                    const img = document.createElement('img');
                    img.src = imgUrl;
                    img.className = "h-32 w-48 object-cover rounded-xl shadow-md flex-shrink-0 border border-white/10 hover:scale-105 transition-all duration-300 cursor-zoom-in";
                    img.onclick = () => window.open(imgUrl, '_blank');
                    gallery.appendChild(img);
                });
                gallery.classList.remove('hidden');
            } else {
                gallery.classList.add('hidden');
            }

            const modal = document.getElementById('bookReaderModal');
            modal.classList.remove('hidden');
            setTimeout(() => { modal.classList.add('opacity-100'); }, 50);
        }

        function closeBookReader() {
            const modal = document.getElementById('bookReaderModal');
            modal.classList.remove('opacity-100');
            setTimeout(() => { modal.classList.add('hidden'); }, 300);
        }

        // ======================= คอนโทรลหน้าสมุดภาพพิเศษเล่มที่ 5 (Page Flipping) =======================
        function openSpecialBookReader() {
            appState.specialBookCurrentPage = 0;
            renderSpecialBookPage();

            const modal = document.getElementById('specialBookReaderModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.add('opacity-100');
                modal.querySelector('.transform').classList.remove('scale-95');
            }, 50);
        }

        function closeSpecialBookReader() {
            const modal = document.getElementById('specialBookReaderModal');
            modal.classList.remove('opacity-100');
            modal.querySelector('.transform').classList.add('scale-95');
            setTimeout(() => { modal.classList.add('hidden'); }, 300);
        }

        function renderSpecialBookPage() {
            const book = bookLibrary.special_edition;
            const pageData = book.pages[appState.specialBookCurrentPage];
            if (!pageData) return;

            const wrapper = document.getElementById('special-page-content-wrapper');
            wrapper.classList.add('opacity-0', 'translate-x-4');

            setTimeout(() => {
                document.getElementById('special-page-img').src = pageData.image;
                document.getElementById('special-page-caption').innerText = pageData.caption;
                document.getElementById('special-page-indicator').innerText = `หน้า ${appState.specialBookCurrentPage + 1}/${book.pages.length}`;
                wrapper.classList.remove('opacity-0', 'translate-x-4');
            }, 150);
        }

        function prevSpecialPage() {
            if (appState.specialBookCurrentPage > 0) {
                appState.specialBookCurrentPage--;
                renderSpecialBookPage();
                playSimpleBeep(700, 0.08); 
            } else {
                showNotification("หน้าแรกสุด", "ท่านอยู่ในสารบัญหน้าแรกแล้ว", "warning");
            }
        }

        function nextSpecialPage() {
            const book = bookLibrary.special_edition;
            if (appState.specialBookCurrentPage < book.pages.length - 1) {
                appState.specialBookCurrentPage++;
                renderSpecialBookPage();
                playSimpleBeep(700, 0.08);
            } else {
                showNotification("หน้าสุดท้าย", "ไม่มีหน้าถัดไปแล้ว", "warning");
            }
        }

        function handleBookDragStart(e) {
            appState.isDraggingBook = true;
            appState.dragStartX = e.clientX;
        }

        function handleBookDragEnd(e) {
            if (!appState.isDraggingBook) return;
            appState.isDraggingBook = false;
            const dragDistance = e.clientX - appState.dragStartX;

            if (dragDistance > 60) {
                prevSpecialPage();
            } else if (dragDistance < -60) {
                nextSpecialPage();
            }
        }

        function handleBookTouchStart(e) {
            appState.isDraggingBook = true;
            appState.dragStartX = e.touches[0].clientX;
        }

        function handleBookTouchEnd(e) {
            if (!appState.isDraggingBook) return;
            appState.isDraggingBook = false;
            const dragDistance = e.changedTouches[0].clientX - appState.dragStartX;

            if (dragDistance > 60) {
                prevSpecialPage();
            } else if (dragDistance < -60) {
                nextSpecialPage();
            }
        }

        // ======================= ระบบแอดมินแก้ไขเล่ม 5 =======================
        function openAdminSpecialBookModal() {
            const book = bookLibrary.special_edition;
            const container = document.getElementById('admin-special-pages-container');
            container.innerHTML = '';

            book.pages.forEach((page, index) => {
                appendSpecialPageEditorRow(page.image, page.caption, index);
            });

            const modal = document.getElementById('adminSpecialBookEditModal');
            modal.classList.remove('hidden');
            setTimeout(() => { modal.classList.add('opacity-100'); }, 50);
        }

        function closeAdminSpecialBookModal() {
            const modal = document.getElementById('adminSpecialBookEditModal');
            modal.classList.remove('opacity-100');
            setTimeout(() => { modal.classList.add('hidden'); }, 300);
        }

        function appendSpecialPageEditorRow(image, caption, index) {
            const container = document.getElementById('admin-special-pages-container');
            const rowHtml = `
                <div class="p-4 bg-slate-900 border border-white/10 rounded-2xl space-y-2 special-page-row-item text-white" data-index="${index}">
                    <div class="flex justify-between items-center">
                        <span class="text-xs font-bold text-gold">หน้าลำดับที่ <span class="row-num">${index + 1}</span></span>
                        <button onclick="removeAdminSpecialPageRow(this)" class="text-red-400 hover:text-red-500 text-xs font-semibold"><i class="fa-solid fa-trash-can mr-1"></i> ลบหน้านี้</button>
                    </div>
                    <div>
                        <label class="block text-[10px] text-bluegrey font-bold mb-1">URL รูปภาพ OTOP:</label>
                        <input type="text" value="${image}" class="page-img-input w-full bg-slate-950 border border-white/10 text-xs rounded-lg p-2 outline-none text-white focus:border-gold">
                    </div>
                    <div>
                        <label class="block text-[10px] text-bluegrey font-bold mb-1">บทประพันธ์/คำโปรยคำบรรยาย:</label>
                        <textarea class="page-caption-input w-full bg-slate-950 border border-white/10 text-xs rounded-lg p-2 outline-none resize-none text-white focus:border-gold" rows="2">${caption}</textarea>
                    </div>
                </div>
            `;
            container.insertAdjacentHTML('beforeend', rowHtml);
            reorderAdminPageNumbers();
        }

        function addNewAdminSpecialPage() {
            appendSpecialPageEditorRow("", "", document.querySelectorAll('.special-page-row-item').length);
        }

        function removeAdminSpecialPageRow(btn) {
            btn.closest('.special-page-row-item').remove();
            reorderAdminPageNumbers();
        }

        function reorderAdminPageNumbers() {
            document.querySelectorAll('.special-page-row-item').forEach((row, i) => {
                row.querySelector('.row-num').innerText = i + 1;
            });
        }

        function saveAdminSpecialBookData() {
            const rows = document.querySelectorAll('.special-page-row-item');
            const newPages = [];

            rows.forEach(row => {
                const imgVal = row.querySelector('.page-img-input').value.trim();
                const capVal = row.querySelector('.page-caption-input').value.trim();

                if (imgVal || capVal) {
                    newPages.push({
                        image: imgVal || "https://images.unsplash.com/photo-1508009603885-50cf7c579365?auto=format&fit=crop&w=800&q=80",
                        caption: capVal || "คำอธิบายภาพ OTOP ชุมชน"
                    });
                }
            });

            if (newPages.length === 0) {
                showNotification("ระวัง", "กรุณากรอกข้อมูลหน้ารายการอย่างน้อย 1 หน้าสำหรับการใช้งาน", "warning");
                return;
            }

            bookLibrary.special_edition.pages = newPages;
            showNotification("บันทึกสำเร็จ", `คลังภาพสมุด OTOP ชุมชนเล่ม 5 ได้รับการบันทึกแล้ว ${newPages.length} หน้า`, "success");
            closeAdminSpecialBookModal();
            renderBooksLibrary();
        }

        // ======================= ระบบแอดมินโหมดปกติ (Admin Controls) =======================
        function toggleAdminMode() {
            if (appState.isAdmin) {
                appState.isAdmin = false;
                document.getElementById('adminStatusLabel').innerText = "สถานะ: ผู้ชมทั่วไป";
                document.getElementById('adminToggleBtn').innerHTML = `<i class="fa-solid fa-lock-open mr-1"></i> เข้าสู่ระบบ Admin`;
                showNotification("ออกจากระบบ", "กลับสู่สถานะผู้ใช้งานทั่วไปเป็นที่เรียบร้อย", "info");
                renderBooksLibrary();
            } else {
                const pass = prompt("กรุณากรอกรหัสผ่านเพื่อจำลองระบบแอดมิน:\n(ระบุรหัสคือ: 1234)");
                if (pass === '1234') {
                    appState.isAdmin = true;
                    document.getElementById('adminStatusLabel').innerText = "สถานะ: แอดมินผู้ดูแล";
                    document.getElementById('adminToggleBtn').innerHTML = `<i class="fa-solid fa-lock mr-1"></i> ออกจากระบบ Admin`;
                    showNotification("แอดมินลงทะเบียนสำเร็จ", "คุณได้รับอนุญาตให้ทำการแก้ไขภาพของคลังหนังสือ OTOP", "success");
                    renderBooksLibrary();
                } else if (pass !== null) {
                    showNotification("รหัสผ่านผิด", "รหัสผ่านไม่ถูกต้องกรุณาตรวจสอบใหม่อีกครั้ง", "warning");
                }
            }
        }

        function openAdminEditModal(bookKey) {
            currentSelectedAdminBookKey = bookKey;
            const book = bookLibrary[bookKey];
            if (!book) return;

            document.getElementById('adminBookTitle').innerText = `ปรับแต่งแกลเลอรีรูปภาพ: ${book.title}`;
            document.getElementById('adminBookImagesText').value = book.images.join('\n');

            const modal = document.getElementById('adminBookEditModal');
            modal.classList.remove('hidden');
            setTimeout(() => { modal.classList.add('opacity-100'); }, 50);
        }

        function closeAdminEditModal() {
            const modal = document.getElementById('adminBookEditModal');
            modal.classList.remove('opacity-100');
            setTimeout(() => { modal.classList.add('hidden'); }, 300);
        }

        function saveAdminBookImages() {
            const key = currentSelectedAdminBookKey;
            if (!key || !bookLibrary[key]) return;

            const txt = document.getElementById('adminBookImagesText').value.trim();
            const lines = txt.split('\n').map(l => l.trim()).filter(l => l.length > 0);

            bookLibrary[key].images = lines;

            showNotification("บันทึกแกลเลอรีสำเร็จ", `จำนวนรูปภาพได้รับการอัปเดตแล้วทั้งหมด ${lines.length} รูป`, "success");
            closeAdminEditModal();
            renderBooksLibrary();
        }

        // ======================= คูปอง (COUPON LOGIC) =======================
        function claimCoupon(couponTitle) {
            playSimpleBeep(850, 0.12);
            openMacAlert("ยินดีด้วยครับ!", `คุณได้รับรหัสคูปองส่วนลดพิเศษของ "${couponTitle}" เรียบร้อยแล้ว แสดงหน้าจอแอปพลิเคชันนี้ต่อทางร้านค้าเพื่อรับสิทธิ์โดยตรงได้ทันที!`, "success");
        }

        // ======================= ระบบการจัดเส้นทางหน้าเพจแยกหมวดหมู่ (Separated Routing System) =======================
        function navigateTo(pageId) {
            const allowedPages = ['home', 'food', 'books', 'coupon', 'game', 'profile', 'setting', 'report'];
            if (!allowedPages.includes(pageId)) pageId = 'home';

            appState.activeRoute = pageId;

            // ปิดซ่อนหน้าเพจเดิมทั้งหมดอย่างสมบูรณ์แบบ (ตามเงื่อนไขแยกหมวดหมู่ ไม่เอารวมกันในหน้าเดียว)
            document.querySelectorAll('.page-view').forEach(element => {
                element.style.display = 'none';
                element.classList.remove('animate-mac-page');
            });

            const activeTarget = document.getElementById(`view-${pageId}`);
            if (activeTarget) {
                activeTarget.style.display = 'block';
                void activeTarget.offsetWidth; // Force reflow
                activeTarget.classList.add('animate-mac-page');
            }

            if (window.location.hash !== `#${pageId}`) {
                history.pushState(null, null, `#${pageId}`);
            }

            // ตั้งค่าไอคอนปุ่มลอยของ Dock เมนูใต้จอ
            document.querySelectorAll('.dock-item').forEach(item => {
                const activeDot = item.querySelector('.active-dot');
                if (activeDot) activeDot.classList.add('hidden');
                item.className = "dock-item flex flex-col items-center text-bluegrey hover:text-gold relative";
            });

            const activeDock = document.getElementById(`dock-${pageId}`);
            if (activeDock) {
                activeDock.className = "dock-item flex flex-col items-center text-gold relative font-bold";
                const dot = activeDock.querySelector('.active-dot');
                if (dot) dot.classList.remove('hidden');
            }

            document.getElementById('dropdownMenu').classList.add('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // ======================= เกมนักสะสมความรู้วิถีไทย (GAME LOGIC) =======================
        function startCultureQuiz() {
            appState.currentQuizIndex = 0;
            appState.quizScore = 0;
            document.getElementById('game-start-panel').classList.add('hidden');
            document.getElementById('game-result-panel').classList.add('hidden');
            document.getElementById('game-quiz-panel').classList.remove('hidden');
            loadNextQuizQuestion();
        }

        function loadNextQuizQuestion() {
            const currentQuestion = quizData[appState.currentQuizIndex];
            
            document.getElementById('quiz-step-label').innerText = `คำถามที่ ${appState.currentQuizIndex + 1} จาก ${quizData.length}`;
            document.getElementById('quiz-score-live').innerText = `แต้มสะสม: ${appState.quizScore}`;
            
            const percentage = ((appState.currentQuizIndex + 1) / quizData.length) * 100;
            document.getElementById('quiz-progressbar').style.width = `${percentage}%`;
            document.getElementById('quiz-question-text').innerText = currentQuestion.question;

            const container = document.getElementById('quiz-options-container');
            container.innerHTML = '';

            currentQuestion.options.forEach((option, index) => {
                const btn = document.createElement('button');
                btn.className = "w-full text-left p-4 rounded-2xl bg-slate-900/60 hover:bg-gold/10 border border-white/10 text-sm font-medium hover:border-gold transition-all duration-300 flex justify-between items-center group active:scale-[0.98]";
                btn.innerHTML = `
                    <span>${index + 1}. ${option}</span>
                    <i class="fa-regular fa-circle-play text-bluegrey group-hover:text-gold transition-colors"></i>
                `;
                btn.onclick = () => selectQuizAnswer(index);
                container.appendChild(btn);
            });
        }

        function selectQuizAnswer(selectedIndex) {
            const currentQuestion = quizData[appState.currentQuizIndex];
            const isCorrect = selectedIndex === currentQuestion.answer;

            if (isCorrect) {
                appState.quizScore += currentQuestion.points;
                showNotification("ถูกต้องที่สุด!", `ท่านได้รับเพิ่มขึ้นอีก ${currentQuestion.points} แต้มเกียรติยศ`, 'success');
                playSimpleBeep(650, 0.12); 
            } else {
                showNotification("ยังไม่ถูกเล็กน้อย", `ข้อเสนอที่เหมาะสมคือข้อที่ ${currentQuestion.answer + 1}`, 'warning');
                playSimpleBeep(350, 0.2); 
            }

            appState.currentQuizIndex++;
            if (appState.currentQuizIndex < quizData.length) {
                setTimeout(loadNextQuizQuestion, 900);
            } else {
                setTimeout(displayQuizResults, 1100);
            }
        }

        function displayQuizResults() {
            document.getElementById('game-quiz-panel').classList.add('hidden');
            const resultPanel = document.getElementById('game-result-panel');
            resultPanel.classList.remove('hidden');

            const scoreText = document.getElementById('game-result-summary');
            scoreText.innerText = `คุณทำการประลองความรู้ OTOP และวัฒนธรรมเรียบร้อย ทำคะแนนได้ทั้งสิ้น ${appState.quizScore} จาก 100 แต้มเต็ม!`;

            const rankStatus = document.getElementById('game-user-rank-status');
            const medalBox = document.getElementById('game-medal-icon');
            const evalTitle = document.getElementById('game-evaluation-title');

            let finalRank = "ขุนนางวิถีไทยขั้นต้น";
            if (appState.quizScore >= 80) {
                finalRank = "ขุนหลวงสยามผู้ชำนาญความรู้";
                medalBox.innerHTML = `<i class="fa-solid fa-crown text-gold"></i>`;
                evalTitle.innerText = "ท่านผ่านการคัดสรรชั้นเลิศ!";
            } else if (appState.quizScore >= 40) {
                finalRank = "นักเดินทางรอบรู้วิถีชุมชน";
                medalBox.innerHTML = `<i class="fa-solid fa-medal text-silver"></i>`;
                evalTitle.innerText = "ความรู้ของท่านอยู่ในระดับดี";
            } else {
                finalRank = "สามัญชนผู้เริ่มต้นศึกษา OTOP";
                medalBox.innerHTML = `<i class="fa-solid fa-shoe-prints text-amber-600"></i>`;
                evalTitle.innerText = "ศึกษาเพิ่มเติมเพื่อช่วยชุมชนกันต่อ";
            }

            rankStatus.innerText = finalRank;
            if (appState.quizScore > appState.gameScore) {
                appState.gameScore = appState.quizScore;
            }
            appState.profile.rank = finalRank;

            saveDataToLocalStorage();
            updateStatsDisplays();
            syncProfileUI();
        }

        // ======================= แฟนซีโนติฟิเคชันและแชร์คอนโทรล (Fancy Toast / Share) =======================
        function openShareModal() {
            const modal = document.getElementById('macShareModal');
            const urlInput = document.getElementById('shareUrlInput');
            urlInput.value = window.location.href;

            const textToShare = encodeURIComponent("ร่วมส่งเสริมและเดินทางค้นหาร้านลับ OTOP ประจำชุมชนที่ไม่โดนหักเปอร์เซ็นต์ค่า GP ผ่านแอป Local Business ได้เลยที่นี่!");
            const encodedUrl = encodeURIComponent(window.location.href);

            document.getElementById('shareFbLink').href = `https://www.facebook.com/sharer/sharer.php?u=${encodedUrl}`;
            document.getElementById('shareLineLink').href = `https://social-plugins.line.me/lineit/share?url=${encodedUrl}&text=${textToShare}`;
            document.getElementById('shareTwitterLink').href = `https://twitter.com/intent/tweet?url=${encodedUrl}&text=${textToShare}`;

            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.add('opacity-100');
                modal.querySelector('.transform').classList.remove('scale-95');
            }, 50);
        }

        function closeShareModal() {
            const modal = document.getElementById('macShareModal');
            modal.classList.remove('opacity-100');
            modal.querySelector('.transform').classList.add('scale-95');
            setTimeout(() => { modal.classList.add('hidden'); }, 300);
        }

        function copyShareUrl() {
            const urlInput = document.getElementById('shareUrlInput');
            urlInput.select();
            document.execCommand('copy');
            showNotification("คัดลอกสำเร็จ", "ลิงก์เว็บไซต์คัดลอกลงกระดานเรียบร้อยแล้ว พร้อมให้คุณนำไปแชร์ต่อ!", "success");
            playSimpleBeep(800, 0.15);
        }

        function toggleFavorite(placeName, buttonElement) {
            const icon = buttonElement.querySelector('i');
            const isFavorite = appState.savedPlaces.includes(placeName);

            if (isFavorite) {
                appState.savedPlaces = appState.savedPlaces.filter(p => p !== placeName);
                icon.className = "fa-regular fa-heart";
                showNotification("บันทึกสำเร็จ", `ลบร้านค้า "${placeName}" ออกจากพิกัดโปรดแล้ว`, 'info');
            } else {
                appState.savedPlaces.push(placeName);
                icon.className = "fa-solid fa-heart text-red-500 animate-pulse";
                showNotification("ชื่นชอบ", `บันทึกร้านค้า "${placeName}" ลงในรายการโปรดสำหรับการอุดหนุนแล้ว`, 'success');
            }

            saveDataToLocalStorage();
            updateSavedPlacesUI();
            updateStatsDisplays();
        }

        let confirmPromiseResolver = null;
        function openMacConfirm(message) {
            document.getElementById('macConfirmMessage').innerText = message;
            const modal = document.getElementById('macConfirmModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.add('opacity-100');
                modal.querySelector('.transform').classList.remove('scale-95');
            }, 50);

            return new Promise((resolve) => {
                confirmPromiseResolver = resolve;
            });
        }

        function closeMacConfirm(result) {
            const modal = document.getElementById('macConfirmModal');
            modal.classList.remove('opacity-100');
            modal.querySelector('.transform').classList.add('scale-95');
            setTimeout(() => { modal.classList.add('hidden'); }, 300);
            
            if (confirmPromiseResolver) {
                confirmPromiseResolver(result);
                confirmPromiseResolver = null;
            }
        }

        async function requestResetConfirmation() {
            const confirmed = await openMacConfirm("การทำรายการนี้ลบประวัติการทำแบบทดสอบ แหล่งสะสม OTOP และประวัติร้านโปรดของคุณทั้งหมดออกอย่างถาวร ยืนยันการเคลียร์ประวัติหรือไม่?");
            if (confirmed) {
                localStorage.clear();
                appState.gameScore = 0;
                appState.savedPlaces = [];
                appState.profile.name = 'นักเดินทางนิรนาม';
                appState.profile.avatarIndex = 0;
                appState.profile.rank = 'ผู้เรียนรู้เริ่มวิถีไทย';
                
                updateStatsDisplays();
                syncProfileUI();
                updateSavedPlacesUI();
                filterPlacesByCriteria();
                
                openMacAlert("ล้างระบบเรียบร้อย", "ข้อมูลประวัติส่วนบุคคล คูปอง และร้านค้าที่บันทึกโปรด ได้รับการกู้คืนเป็นค่าเริ่มต้นแล้ว", "success");
            }
        }

        function saveProfileName() {
            const input = document.getElementById('profile-name-input');
            const newName = input.value.trim();

            if (newName) {
                appState.profile.name = newName;
                saveDataToLocalStorage();
                showNotification("อัปเดตสำเร็จ", `ชื่อผู้ใช้งานได้รับการบันทึกเป็น: ${newName}`, 'success');
            } else {
                input.value = appState.profile.name;
                showNotification("ขอภัย", "ชื่อส่วนบุคคลไม่ควรถูกปล่อยเป็นช่องว่าง", "warning");
            }
        }

        function cycleAvatar() {
            appState.profile.avatarIndex = (appState.profile.avatarIndex + 1) % appState.avatars.length;
            document.getElementById('profile-avatar-img').src = appState.avatars[appState.profile.avatarIndex];
            saveDataToLocalStorage();
            showNotification("อัปเดตอวตาร", "รูปภาพอวตารของคุณได้รับการเปลี่ยนเรียบร้อย", "info");
        }

        function updateSavedPlacesUI() {
            const container = document.getElementById('saved-places-container');
            if (appState.savedPlaces.length === 0) {
                container.innerHTML = `<p class="text-sm text-bluegrey py-4 text-center">ยังไม่มีพิกัดร้านค้า OTOP ที่บันทึกชื่นชอบในสารบบ</p>`;
                return;
            }

            container.innerHTML = '';
            appState.savedPlaces.forEach(place => {
                const div = document.createElement('div');
                div.className = "flex justify-between items-center p-3.5 bg-slate-900/60 rounded-2xl border border-white/10";
                div.innerHTML = `
                    <div class="flex items-center space-x-3 text-white">
                        <i class="fa-solid fa-map-pin text-gold"></i>
                        <span class="text-sm font-bold">${place}</span>
                    </div>
                    <button onclick="removeFavoriteFromProfile('${place}')" class="text-xs text-red-400 hover:text-red-500 font-semibold">ลบออก</button>
                `;
                container.appendChild(div);
            });
        }

        function removeFavoriteFromProfile(placeName) {
            appState.savedPlaces = appState.savedPlaces.filter(p => p !== placeName);
            saveDataToLocalStorage();
            updateSavedPlacesUI();
            updateStatsDisplays();
            filterPlacesByCriteria();
            showNotification("สำเร็จ", "ลบร้านค้าพิกัดโปรดเรียบร้อย", "info");
        }

        function updateStatsDisplays() {
            document.getElementById('stat-places-count').innerText = `${placesData.length} พิกัดหลัก`;
            document.getElementById('stat-game-score').innerText = `${appState.gameScore} แต้ม`;
            document.getElementById('stat-saved-count').innerText = `${appState.savedPlaces.length} ที่โปรด`;
            
            document.getElementById('profile-points-display').innerText = `${appState.gameScore} แต้ม`;
            document.getElementById('profile-title-display').innerText = appState.profile.rank;
        }

        function syncProfileUI() {
            document.getElementById('profile-name-input').value = appState.profile.name;
            document.getElementById('profile-rank-label').innerText = appState.profile.rank;
            document.getElementById('profile-avatar-img').src = appState.avatars[appState.profile.avatarIndex];
        }

        function toggleThemeMode() {
            const isDark = document.getElementById('darkModeToggle').checked;
            const body = document.body;
            if (isDark) {
                body.classList.add('dark');
                body.classList.remove('light');
                localStorage.setItem('theme', 'dark');
                showNotification("ปรับแต่งธีม", "เปลี่ยนมาใช้โหมดสีเข้มระดับพรีเมียม", "info");
            } else {
                body.classList.remove('dark');
                body.classList.add('light');
                localStorage.setItem('theme', 'light');
                showNotification("ปรับแต่งธีม", "เปลี่ยนระบบการแสดงผลสีสว่างเพื่อความชัดเจน", "info");
            }
        }

        function changeFontSizeSetting(val) {
            const body = document.getElementById('app-body');
            const label = document.getElementById('current-fontSize-label');
            body.classList.remove('text-scale-sm', 'text-scale-md', 'text-scale-lg');
            
            if (val == 1) {
                body.classList.add('text-scale-sm');
                label.innerText = "เล็ก";
                appState.fontSizeScale = 'sm';
            } else if (val == 2) {
                body.classList.add('text-scale-md');
                label.innerText = "กลาง";
                appState.fontSizeScale = 'md';
            } else {
                body.classList.add('text-scale-lg');
                label.innerText = "ใหญ่";
                appState.fontSizeScale = 'lg';
            }
            saveDataToLocalStorage();
        }

        function handleFormSubmission(event) {
            event.preventDefault();
            const name = document.getElementById('report-name').value;
            const topic = document.getElementById('report-topic').value;
            openMacAlert(
                "รับเรื่องสำรวจสำเร็จ", 
                `สวัสดีคุณ ${name} เจ้าหน้าที่ได้รับเรื่องแจ้งหัวข้อ "${topic}" ของคุณเรียบร้อย เราจะรีบประมวลผลเพื่อเพิ่มความแข็งแกร่งให้ธุรกิจ OTOP ท้องถิ่นโดยด่วนที่สุด!`, 
                "success"
            );
            document.getElementById('feedbackForm').reset();
        }

        function saveDataToLocalStorage() {
            localStorage.setItem('CICCultureExploreState', JSON.stringify(appState));
        }

        function loadSavedData() {
            const savedTheme = localStorage.getItem('theme');
            const isDarkToggle = document.getElementById('darkModeToggle');
            const body = document.body;
            
            if (savedTheme === 'light') {
                body.classList.remove('dark');
                body.classList.add('light');
                if (isDarkToggle) isDarkToggle.checked = false;
            } else {
                body.classList.add('dark');
                body.classList.remove('light');
                if (isDarkToggle) isDarkToggle.checked = true;
            }

            const rawData = localStorage.getItem('CICCultureExploreState');
            if (rawData) {
                try {
                    const parsed = JSON.parse(rawData);
                    appState.savedPlaces = parsed.savedPlaces || [];
                    appState.gameScore = parsed.gameScore || 0;
                    appState.profile = parsed.profile || { name: 'นักเดินทางนิรนาม', avatarIndex: 0, rank: 'ผู้เรียนรู้เริ่มวิถีไทย' };
                    appState.fontSizeScale = parsed.fontSizeScale || 'md';

                    const slider = document.getElementById('fontSizeSlider');
                    if (appState.fontSizeScale === 'sm') {
                        if (slider) slider.value = 1;
                        changeFontSizeSetting(1);
                    } else if (appState.fontSizeScale === 'md') {
                        if (slider) slider.value = 2;
                        changeFontSizeSetting(2);
                    } else {
                        if (slider) slider.value = 3;
                        changeFontSizeSetting(3);
                    }
                } catch (e) {
                    console.error("Failed to parse local storage state:", e);
                }
            }

            syncProfileUI();
            updateSavedPlacesUI();
            updateStatsDisplays();
        }

        // ตัวเล่นเสียงสังเคราะห์ด้วย Web Audio API (age-appropriate, clean)
        function playSimpleBeep(freq, duration) {
            try {
                const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
                const oscillator = audioCtx.createOscillator();
                const gainNode = audioCtx.createGain();
                oscillator.type = 'sine';
                oscillator.frequency.value = freq;
                gainNode.gain.setValueAtTime(0.08, audioCtx.currentTime);
                gainNode.gain.exponentialRampToValueAtTime(0.005, audioCtx.currentTime + duration);
                oscillator.connect(gainNode);
                gainNode.connect(audioCtx.destination);
                oscillator.start();
                oscillator.stop(audioCtx.currentTime + duration);
            } catch (err) {
                console.log("Audio limitations processed.");
            }
        }

        // ระบบแจ้งเตือน Notification Toast สไตล์ macOS
        function showNotification(title, message, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            
            let icon = '<i class="fa-solid fa-circle-check text-emerald-400 text-lg mr-3"></i>';
            if (type === 'warning') {
                icon = '<i class="fa-solid fa-circle-exclamation text-yellow-400 text-lg mr-3"></i>';
            } else if (type === 'info') {
                icon = '<i class="fa-solid fa-circle-info text-sky-400 text-lg mr-3"></i>';
            }

            toast.className = 'pointer-events-auto w-80 mac-glass rounded-2xl p-4 border border-white/20 shadow-xl flex items-start transition-all duration-300 transform translate-x-12 opacity-0 text-white';
            toast.innerHTML = `
                ${icon}
                <div class="flex-grow">
                    <h5 class="text-xs font-bold text-white mb-0.5">${title}</h5>
                    <p class="text-[11px] text-gray-300 leading-normal">${message}</p>
                </div>
                <button class="text-gray-400 hover:text-white ml-2 text-xs" onclick="this.closest('.pointer-events-auto').remove()"><i class="fa-solid fa-xmark"></i></button>
            `;

            container.appendChild(toast);
            
            // Slide in animation
            setTimeout(() => {
                toast.classList.remove('translate-x-12', 'opacity-0');
            }, 50);

            // Auto dismiss after 3.5 seconds
            setTimeout(() => {
                toast.classList.add('translate-x-12', 'opacity-0');
                setTimeout(() => { toast.remove(); }, 300);
            }, 3500);
        }

        // macOS Custom System Alert Dialog
        function openMacAlert(title, message, type = 'success') {
            document.getElementById('macAlertTitle').innerText = title;
            document.getElementById('macAlertMessage').innerText = message;
            
            const iconContainer = document.getElementById('macAlertIcon');
            if (type === 'success') {
                iconContainer.className = 'w-16 h-16 rounded-2xl bg-gradient-to-tr from-emerald-500 to-teal-500 text-white flex items-center justify-center mx-auto text-2xl shadow-lg mb-4';
                iconContainer.innerHTML = '<i class="fa-solid fa-circle-check"></i>';
            } else {
                iconContainer.className = 'w-16 h-16 rounded-2xl bg-gradient-to-tr from-yellow-500 to-gold text-white flex items-center justify-center mx-auto text-2xl shadow-lg mb-4';
                iconContainer.innerHTML = '<i class="fa-solid fa-circle-exclamation"></i>';
            }

            const modal = document.getElementById('macAlertModal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.add('opacity-100');
                modal.querySelector('.transform').classList.remove('scale-95');
            }, 50);
        }

        function closeMacAlert() {
            const modal = document.getElementById('macAlertModal');
            modal.classList.remove('opacity-100');
            modal.querySelector('.transform').classList.add('scale-95');
            setTimeout(() => { modal.classList.add('hidden'); }, 300);
        }

        // ช่องพิมพ์ค้นหาด่วนระดับแอป Spotlight
        function executeSpotlightSearch() {
            const query = document.getElementById('homeSearchInput').value.trim().toLowerCase();
            if (!query) {
                showNotification("กรุณาระบุคำค้นหา", "พิมพ์สิ่งที่คุณต้องการค้นหาลงในช่องป้อนข้อมูล", "warning");
                return;
            }

            let foundPlace = false;
            for (let i = 0; i < placesData.length; i++) {
                if (placesData[i].name.toLowerCase().includes(query) || placesData[i].province.toLowerCase().includes(query)) {
                    navigateTo('food');
                    document.getElementById('gpsSearchInput').value = query;
                    filterPlacesByCriteria();
                    showNotification("ค้นพบข้อมูลร้านค้า OTOP", `ระบุนำทางไปพิกัด "${placesData[i].name}" ให้คุณเรียบร้อย`, "success");
                    foundPlace = true;
                    break;
                }
            }

            if (!foundPlace) {
                if (query.includes('หนังสือ') || query.includes('ประวัติศาสตร์') || query.includes('มรดก') || query.includes('otop')) {
                    navigateTo('books');
                    showNotification("สารบัญหนังสือ OTOP", "เข้าสู่มุมมองแกลเลอรีความรู้ล้ำค่าชาวบ้าน", "success");
                } else if (query.includes('เกม') || query.includes('เล่น') || query.includes('ทดสอบ')) {
                    navigateTo('game');
                    showNotification("พร้อมรบประลองปัญญา", "เข้าสู่หมวดทดสอบความรู้วัฒนธรรมไทยแล้ว", "info");
                } else if (query.includes('คูปอง') || query.includes('ลด') || query.includes('ส่วนลด')) {
                    navigateTo('coupon');
                    showNotification("สิทธิประโยชน์", "เปิดหมวดคูปองส่วนลดร้านค้าเพื่อชุมชนแล้ว", "success");
                } else {
                    openMacAlert("ไม่พบรายการที่เกี่ยวข้อง", `ระบบไม่สามารถตรวจหาพิกัด OTOP หรือบทความที่ตรงกับ "${query}" ได้ ลองตรวจสอบคำทับศัพท์ใหม่อีกครั้ง เช่น "ขนมจีน" หรือ "สุโขทัย"`, "warning");
                }
            }
        }

        // ======================= ตัวเริ่มต้นระบบ (DOMContentLoaded) =======================
        function initApp() {
            loadSavedData();
            
            // สั่งจัดหน้าเพจแยกหมวดหมู่ตามแฮช URL ในปัจจุบัน
            const initialHash = window.location.hash.replace('#', '') || 'home';
            // ป้องกันแฮชเก่าของ gps ลิงก์เสีย
            const targetRoute = initialHash === 'gps' ? 'food' : initialHash;
            navigateTo(targetRoute);
            
            // เชื่อมโยง Event Listeners
            const shareBtn = document.getElementById('shareBtn');
            shareBtn.addEventListener('click', (e) => {
                e.stopPropagation();
                openShareModal();
            });

            const menuBtn = document.getElementById('menuBtn');
            menuBtn.addEventListener('click', (e) => {
                e.stopPropagation();
                const dropdown = document.getElementById('dropdownMenu');
                dropdown.classList.toggle('hidden');
            });

            document.addEventListener('click', (e) => {
                const dropdown = document.getElementById('dropdownMenu');
                if (e.target !== menuBtn && !dropdown.contains(e.target)) {
                    dropdown.classList.add('hidden');
                }
                const shareModal = document.getElementById('macShareModal');
                if (e.target === shareModal) {
                    closeShareModal();
                }
                const detailModal = document.getElementById('placeDetailModal');
                if (e.target === detailModal) {
                    closePlaceDetail();
                }
            });

            const nav = document.querySelector('nav');
            window.addEventListener('scroll', () => {
                if (window.scrollY > 40) {
                    nav.classList.add('shadow-lg');
                    nav.classList.replace('mac-nav-glass', 'mac-glass');
                } else {
                    nav.classList.remove('shadow-lg');
                    nav.classList.replace('mac-glass', 'mac-nav-glass');
                }
            });

            filterPlacesByCriteria();
            renderBooksLibrary();
        }

        // พร้อมสั่งงานระบบหลักทันทีเมื่อโหลดเพจเสร็จสมบูรณ์
        if (document.readyState === 'loading') {
            document.addEventListener('DOMContentLoaded', initApp);
        } else {
            initApp();
        }
    </script>
</body>
</html>
