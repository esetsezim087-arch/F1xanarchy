<!DOCTYPE html>
<html lang="kk" class="h-full scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>F1x Anarchy — Күзгі Маусым</title>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        autumn: {
                            base: '#0f0a06',
                            card: 'rgba(26, 17, 10, 0.85)',
                            border: 'rgba(245, 158, 11, 0.25)',
                            orange: '#f97316',
                            amber: '#d97706',
                            gold: '#fbbf24',
                            red: '#991b1b'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif']
                    }
                }
            }
        }
    </script>

    <!-- Google Fonts & FontAwesome -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        /* Global Reset & Base Styles */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            -webkit-tap-highlight-color: transparent;
        }

        html, body {
            max-width: 100%;
            overflow-x: hidden;
            background-color: #0f0a06;
            color: #f3f4f6;
            font-family: 'Inter', sans-serif;
        }

        /* Animated Canvas Background */
        #leavesCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
            z-index: 0;
        }

        /* Glassmorphism Effects */
        .glass-panel {
            background: rgba(24, 16, 10, 0.8);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(245, 158, 11, 0.2);
            box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.7);
        }

        .glass-card {
            background: rgba(35, 22, 12, 0.7);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(217, 119, 6, 0.2);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .glass-card:hover {
            border-color: rgba(251, 191, 36, 0.6);
            transform: translateY(-4px);
            box-shadow: 0 12px 25px -5px rgba(249, 115, 22, 0.25);
        }

        /* Glowing Effects */
        .glow-text {
            text-shadow: 0 0 15px rgba(249, 115, 22, 0.6), 0 0 30px rgba(217, 119, 6, 0.4);
        }

        .glow-button {
            box-shadow: 0 0 20px rgba(249, 115, 22, 0.4);
            transition: all 0.3s ease;
        }

        .glow-button:hover {
            box-shadow: 0 0 30px rgba(249, 115, 22, 0.7);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0f0a06;
        }
        ::-webkit-scrollbar-thumb {
            background: #d97706;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #f97316;
        }
    </style>
</head>
<body class="min-h-full flex flex-col justify-between relative selection:bg-amber-500 selection:text-black">

    <!-- Autumn Falling Leaves Canvas Layer -->
    <canvas id="leavesCanvas"></canvas>

    <!-- Notification Toast -->
    <div id="toast" class="fixed bottom-5 right-5 z-50 transform translate-y-20 opacity-0 transition-all duration-300 flex items-center space-x-3 bg-gradient-to-r from-amber-600 to-orange-600 text-white px-5 py-3 rounded-xl shadow-2xl border border-amber-300/40">
        <i class="fa-solid fa-circle-check text-xl"></i>
        <span id="toast-msg" class="font-medium text-sm">Сілтеме көшірілді!</span>
    </div>

    <div class="relative z-10 flex flex-col min-h-screen">
        
        <!-- Navbar -->
        <header class="w-full px-4 sm:px-8 py-4 sticky top-0 z-40 glass-panel border-b border-amber-500/20">
            <div class="max-w-7xl mx-auto flex flex-col sm:flex-row items-center justify-between gap-4">
                
                <!-- Logo & Title -->
                <a href="#" class="flex items-center space-x-3 group">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-amber-500 to-orange-600 flex items-center justify-center text-white font-extrabold text-xl shadow-lg group-hover:scale-105 transition-transform">
                        F1
                    </div>
                    <div class="flex flex-col">
                        <span class="text-xl sm:text-2xl font-black tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-amber-400 via-orange-400 to-amber-200">
                            F1X ANARCHY
                        </span>
                        <span class="text-[10px] text-amber-400/80 font-semibold tracking-widest uppercase">
                            🍁 Autumn Season
                        </span>
                    </div>
                </a>

                <!-- IP Copy & Social Links -->
                <div class="flex flex-wrap items-center justify-center gap-3 w-full sm:w-auto">
                    <!-- IP Button -->
                    <button onclick="copyIP()" class="flex-1 sm:flex-none flex items-center justify-center space-x-2.5 px-4 py-2.5 rounded-xl bg-gradient-to-r from-amber-900/40 to-orange-900/40 border border-amber-500/40 hover:border-amber-400 text-amber-200 hover:text-white transition-all duration-300 group">
                        <i class="fa-solid fa-server text-amber-400 group-hover:rotate-12 transition-transform"></i>
                        <div class="text-left text-xs sm:text-sm">
                            <span class="font-bold block text-white">f1x.mcmc.kz</span>
                            <span class="text-[11px] text-amber-300/70">PORT: 19151</span>
                        </div>
                        <i class="fa-regular fa-copy ml-1 text-xs opacity-70 group-hover:opacity-100"></i>
                    </button>

                    <!-- Telegram Button -->
                    <a href="https://t.me/f1xanarchy" target="_blank" rel="noopener noreferrer" class="flex items-center space-x-2 px-4 py-2.5 rounded-xl bg-sky-600/20 hover:bg-sky-600/30 border border-sky-500/40 text-sky-300 hover:text-white text-xs sm:text-sm font-semibold transition-all duration-300">
                        <i class="fa-brands fa-telegram text-base text-sky-400"></i>
                        <span>Канал</span>
                    </a>
                </div>

            </div>
        </header>

        <!-- Main Content -->
        <main class="max-w-7xl mx-auto px-4 sm:px-6 py-8 sm:py-12 flex-grow w-full">
            
            <!-- Hero Banner Section -->
            <section class="mb-12 glass-panel rounded-3xl p-6 sm:p-10 text-center relative overflow-hidden border border-amber-500/30">
                <div class="absolute -top-24 -left-24 w-60 h-60 bg-orange-600/20 rounded-full blur-3xl pointer-events-none"></div>
                <div class="absolute -bottom-24 -right-24 w-60 h-60 bg-amber-500/20 rounded-full blur-3xl pointer-events-none"></div>

                <div class="inline-flex items-center space-x-2 px-4 py-1.5 rounded-full bg-red-500/20 border border-red-500/40 text-red-300 text-xs sm:text-sm font-black mb-6 animate-pulse">
                    <i class="fa-solid fa-fire text-red-500"></i>
                    <span>🔥 БАРЛЫҚ ТАУАРЛАРҒА 25% ЖЕҢІЛДІК (СКИДКА)! ⏳</span>
                </div>

                <h1 class="text-3xl sm:text-5xl md:text-6xl font-black text-white tracking-tight mb-4 uppercase">
                    F1X ANARCHY <span class="text-transparent bg-clip-text bg-gradient-to-r from-amber-400 to-orange-500 glow-text">СЕРВЕРІ</span>
                </h1>

                <p class="max-w-2xl mx-auto text-gray-300 text-sm sm:text-base md:text-lg mb-8 leading-relaxed font-normal">
                    Қазақстандағы №1 Анархия сервері! Өз кланыңды құр, ресурстар жина, қарсыластарыңды талқандап, сервердің ең мықты билеушісіне айнал!
                </p>

                <!-- Telegram CTA Banner Box -->
                <div class="max-w-md mx-auto p-4 rounded-2xl bg-gradient-to-r from-sky-950/60 to-blue-950/60 border border-sky-500/30 flex items-center justify-between gap-4">
                    <div class="flex items-center space-x-3 text-left">
                        <div class="w-12 h-12 rounded-xl bg-sky-500/20 flex items-center justify-center text-sky-400 text-2xl flex-shrink-0">
                            <i class="fa-brands fa-telegram"></i>
                        </div>
                        <div>
                            <h4 class="text-sm font-bold text-white">Ресми Telegram Канал</h4>
                            <p class="text-xs text-sky-200/70">Жаңалықтар, конкурстар мен ивенттер!</p>
                        </div>
                    </div>
                    <a href="https://t.me/f1xanarchy" target="_blank" rel="noopener noreferrer" class="px-4 py-2 rounded-xl bg-sky-500 hover:bg-sky-400 text-white font-bold text-xs shadow-lg transition-all flex-shrink-0 whitespace-nowrap">
                        ЖАЗЫЛУ <i class="fa-solid fa-arrow-right ml-1"></i>
                    </a>
                </div>
            </section>

            <!-- Navigation Categories Tabs -->
            <div class="flex flex-wrap justify-center gap-2 sm:gap-4 mb-8">
                <button onclick="switchTab('ranks')" id="tab-ranks" class="tab-btn active px-4 sm:px-6 py-3 rounded-xl font-bold text-xs sm:text-sm transition-all duration-300 flex items-center space-x-2 bg-gradient-to-r from-amber-500 to-orange-600 text-white shadow-lg">
                    <span>🛡️ Донат Дәрежелер</span>
                </button>
                <button onclick="switchTab('don-cases')" id="tab-don-cases" class="tab-btn px-4 sm:px-6 py-3 rounded-xl font-bold text-xs sm:text-sm transition-all duration-300 flex items-center space-x-2 glass-card text-gray-300 hover:text-white">
                    <span>🎁 Донат Кейстер</span>
                </button>
                <button onclick="switchTab('money-cases')" id="tab-money-cases" class="tab-btn px-4 sm:px-6 py-3 rounded-xl font-bold text-xs sm:text-sm transition-all duration-300 flex items-center space-x-2 glass-card text-gray-300 hover:text-white">
                    <span>💰 Ақшалай кейстер</span>
                </button>
                <button onclick="switchTab('unban')" id="tab-unban" class="tab-btn px-4 sm:px-6 py-3 rounded-xl font-bold text-xs sm:text-sm transition-all duration-300 flex items-center space-x-2 glass-card text-gray-300 hover:text-white">
                    <span>🔓 Разбан</span>
                </button>
            </div>

            <!-- TAB 1: DONATE RANKS -->
            <div id="section-ranks" class="tab-content grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                
                <!-- Rank 1: Жасақ -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-amber-500 relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="flex justify-between items-start mb-4">
                            <span class="text-3xl">🛡️</span>
                            <span class="px-3 py-1 bg-amber-500/20 text-amber-300 rounded-full text-xs font-semibold">Бастапқы</span>
                        </div>
                        <h3 class="text-2xl font-black text-amber-400 mb-2">[Жасақ]</h3>
                        <p class="text-xs text-gray-400 mb-4">Серверде өз жолыңды бастауға арналған ыңғайлы донат дәрежесі.</p>
                        <div class="space-y-2 mb-6 text-sm">
                            <div class="flex justify-between items-center text-gray-300">
                                <span>30 күнге:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">200 ₸</span>
                                    <span class="font-bold text-amber-400">150 ₸</span>
                                </div>
                            </div>
                            <div class="flex justify-between items-center text-gray-300">
                                <span>Мәңгілік:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">500 ₸</span>
                                    <span class="font-bold text-amber-400">375 ₸</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <button onclick="openModal('Жасақ', { '30 күн': '150 ₸', 'Мәңгілік': '375 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-amber-600 to-orange-600 hover:from-amber-500 hover:to-orange-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

                <!-- Rank 2: Мерген -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-orange-500 relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="flex justify-between items-start mb-4">
                            <span class="text-3xl">🏹</span>
                            <span class="px-3 py-1 bg-orange-500/20 text-orange-300 rounded-full text-xs font-semibold">Орташа</span>
                        </div>
                        <h3 class="text-2xl font-black text-orange-400 mb-2">[Мерген]</h3>
                        <p class="text-xs text-gray-400 mb-4">Қосымша мүмкіндіктер мен артықшылықтар жиынтығы.</p>
                        <div class="space-y-2 mb-6 text-sm">
                            <div class="flex justify-between items-center text-gray-300">
                                <span>30 күнге:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">450 ₸</span>
                                    <span class="font-bold text-amber-400">337,5 ₸</span>
                                </div>
                            </div>
                            <div class="flex justify-between items-center text-gray-300">
                                <span>Мәңгілік:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">1 000 ₸</span>
                                    <span class="font-bold text-amber-400">750 ₸</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <button onclick="openModal('Мерген', { '30 күн': '337,5 ₸', 'Мәңгілік': '750 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-amber-600 to-orange-600 hover:from-amber-500 hover:to-orange-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

                <!-- Rank 3: Батыр -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-red-500 relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="flex justify-between items-start mb-4">
                            <span class="text-3xl">🗡️</span>
                            <span class="px-3 py-1 bg-red-500/20 text-red-300 rounded-full text-xs font-semibold">Пайдалы</span>
                        </div>
                        <h3 class="text-2xl font-black text-red-400 mb-2">[Батыр]</h3>
                        <p class="text-xs text-gray-400 mb-4">Сервердегі мықты жауынгерлерге арналған толық пакет.</p>
                        <div class="space-y-2 mb-6 text-sm">
                            <div class="flex justify-between items-center text-gray-300">
                                <span>30 күнге:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">900 ₸</span>
                                    <span class="font-bold text-amber-400">675 ₸</span>
                                </div>
                            </div>
                            <div class="flex justify-between items-center text-gray-300">
                                <span>Мәңгілік:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">2 200 ₸</span>
                                    <span class="font-bold text-amber-400">1 650 ₸</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <button onclick="openModal('Батыр', { '30 күн': '675 ₸', 'Мәңгілік': '1 650 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-amber-600 to-orange-600 hover:from-amber-500 hover:to-orange-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

                <!-- Rank 4: Сері -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-yellow-500 relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="flex justify-between items-start mb-4">
                            <span class="text-3xl">⚔️</span>
                            <span class="px-3 py-1 bg-yellow-500/20 text-yellow-300 rounded-full text-xs font-semibold">Жоғары</span>
                        </div>
                        <h3 class="text-2xl font-black text-yellow-400 mb-2">[Сері]</h3>
                        <p class="text-xs text-gray-400 mb-4">Ерекше артықшылықтар мен командалар жиынтығы.</p>
                        <div class="space-y-2 mb-6 text-sm">
                            <div class="flex justify-between items-center text-gray-300">
                                <span>30 күнге:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">1 800 ₸</span>
                                    <span class="font-bold text-amber-400">1 350 ₸</span>
                                </div>
                            </div>
                            <div class="flex justify-between items-center text-gray-300">
                                <span>Мәңгілік:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">4 000 ₸</span>
                                    <span class="font-bold text-amber-400">3 000 ₸</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <button onclick="openModal('Сері', { '30 күн': '1 350 ₸', 'Мәңгілік': '3 000 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-amber-600 to-orange-600 hover:from-amber-500 hover:to-orange-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

                <!-- Rank 5: Хан -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-amber-300 relative overflow-hidden">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black z-10">-25%</span>
                    <div class="absolute -right-8 -top-8 w-24 h-24 bg-amber-400/10 rounded-full blur-xl"></div>
                    <div>
                        <div class="flex justify-between items-start mb-4">
                            <span class="text-3xl">👑</span>
                            <span class="px-3 py-1 bg-amber-300/20 text-amber-200 rounded-full text-xs font-semibold">VIP Элита</span>
                        </div>
                        <h3 class="text-2xl font-black text-amber-300 mb-2">[Хан]</h3>
                        <p class="text-xs text-gray-400 mb-4">Жоғары дәрежелі билеуші мәртебесі.</p>
                        <div class="space-y-2 mb-6 text-sm">
                            <div class="flex justify-between items-center text-gray-300">
                                <span>30 күнге:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">3 500 ₸</span>
                                    <span class="font-bold text-amber-300">2 625 ₸</span>
                                </div>
                            </div>
                            <div class="flex justify-between items-center text-gray-300">
                                <span>Мәңгілік:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">7 500 ₸</span>
                                    <span class="font-bold text-amber-300">5 625 ₸</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <button onclick="openModal('Хан', { '30 күн': '2 625 ₸', 'Мәңгілік': '5 625 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-amber-500 to-yellow-500 hover:from-amber-400 hover:to-yellow-400 font-bold text-black shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

                <!-- Rank 6: ҚАҒАН -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-2 border-amber-400 relative shadow-2xl">
                    <div class="absolute -top-3 left-4 px-3 py-0.5 bg-gradient-to-r from-amber-500 to-red-600 rounded-full text-[10px] font-black text-white uppercase tracking-wider shadow">
                        ТОП РАҢГ
                    </div>
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="flex justify-between items-start mb-4 mt-2">
                            <span class="text-4xl">⚡</span>
                            <span class="px-3 py-1 bg-orange-500/20 text-orange-300 rounded-full text-xs font-semibold">TOP TYPE</span>
                        </div>
                        <h3 class="text-3xl font-black text-transparent bg-clip-text bg-gradient-to-r from-amber-300 via-orange-400 to-red-400 mb-2">[ҚАҒАН]</h3>
                        <p class="text-xs text-gray-400 mb-4">Сервердегі ең жоғарғы, шексіз билік мен құқықтар.</p>
                        <div class="space-y-2 mb-6 text-sm">
                            <div class="flex justify-between items-center text-gray-300">
                                <span>30 күнге:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">6 000 ₸</span>
                                    <span class="font-bold text-amber-400">4 500 ₸</span>
                                </div>
                            </div>
                            <div class="flex justify-between items-center text-gray-300">
                                <span>Мәңгілік:</span>
                                <div>
                                    <span class="text-xs line-through text-gray-500 mr-1.5">12 000 ₸</span>
                                    <span class="font-bold text-amber-400 text-lg">9 000 ₸</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <button onclick="openModal('ҚАҒАН', { '30 күн': '4 500 ₸', 'Мәңгілік': '9 000 ₸' })" class="w-full py-3.5 rounded-xl bg-gradient-to-r from-amber-500 via-orange-500 to-red-600 hover:opacity-90 font-black text-white shadow-xl transition-all text-sm tracking-wider">
                        САТЫП АЛУ
                    </button>
                </div>

            </div>

            <!-- TAB 2: DONATION CASES -->
            <div id="section-don-cases" class="tab-content hidden grid grid-cols-1 md:grid-cols-3 gap-6">
                
                <!-- 1 Case -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-amber-500 text-center relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="text-5xl mb-4">📦</div>
                        <h3 class="text-xl font-bold text-white mb-2">1 Донат Кейс</h3>
                        <p class="text-xs text-gray-400 mb-6">Кез келген донат түсу мүмкіндігі бар құпия кейс.</p>
                        <div class="mb-6">
                            <span class="text-xs line-through text-gray-500 block mb-1">590 ₸</span>
                            <span class="text-3xl font-black text-amber-400">442,5 ₸</span>
                        </div>
                    </div>
                    <button onclick="openModal('1 Донат Кейс', { '1 кейс': '442,5 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-amber-600 to-orange-600 hover:from-amber-500 hover:to-orange-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

                <!-- 3 Cases -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-orange-500 text-center relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="text-5xl mb-4">📦📦</div>
                        <h3 class="text-xl font-bold text-white mb-2">3 Донат Кейс</h3>
                        <p class="text-xs text-gray-400 mb-6">Үш есе көп мүмкіндік пен бағалы сыйлықтар!</p>
                        <div class="mb-6">
                            <span class="text-xs line-through text-gray-500 block mb-1">1 590 ₸</span>
                            <span class="text-3xl font-black text-amber-400">1 192,5 ₸</span>
                        </div>
                    </div>
                    <button onclick="openModal('3 Донат Кейс', { '3 кейс': '1 192,5 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-amber-600 to-orange-600 hover:from-amber-500 hover:to-orange-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

                <!-- 5 Cases -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-yellow-500 text-center relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="text-5xl mb-4">📦📦📦</div>
                        <h3 class="text-xl font-bold text-white mb-2">5 Донат Кейс</h3>
                        <p class="text-xs text-gray-400 mb-6">Максималды үнемдеу және жоғары мүмкіндік!</p>
                        <div class="mb-6">
                            <span class="text-xs line-through text-gray-500 block mb-1">2 590 ₸</span>
                            <span class="text-3xl font-black text-amber-400">1 942,5 ₸</span>
                        </div>
                    </div>
                    <button onclick="openModal('5 Донат Кейс', { '5 кейс': '1 942,5 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-amber-600 to-orange-600 hover:from-amber-500 hover:to-orange-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

            </div>

            <!-- TAB 3: MONEY / EXTRA CASES -->
            <div id="section-money-cases" class="tab-content hidden grid grid-cols-1 md:grid-cols-3 gap-6">
                
                <!-- 1 Money Case -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-emerald-500 text-center relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="text-5xl mb-4">💰</div>
                        <h3 class="text-xl font-bold text-white mb-2">1 Қосымша Кейс</h3>
                        <p class="text-xs text-gray-400 mb-6">Ойын ішіндегі ресурстар мен бонустар.</p>
                        <div class="mb-6">
                            <span class="text-xs line-through text-gray-500 block mb-1">219 ₸</span>
                            <span class="text-3xl font-black text-emerald-400">164,25 ₸</span>
                        </div>
                    </div>
                    <button onclick="openModal('1 Қосымша Кейс', { '1 кейс': '164,25 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-500 hover:to-teal-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

                <!-- 5 Money Cases -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-emerald-500 text-center relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="text-5xl mb-4">💰💰</div>
                        <h3 class="text-xl font-bold text-white mb-2">5 Қосымша Кейс</h3>
                        <p class="text-xs text-gray-400 mb-6">Дамуға арналған 5 кейс жиынтығы.</p>
                        <div class="mb-6">
                            <span class="text-xs line-through text-gray-500 block mb-1">790 ₸</span>
                            <span class="text-3xl font-black text-emerald-400">592,5 ₸</span>
                        </div>
                    </div>
                    <button onclick="openModal('5 Қосымша Кейс', { '5 кейс': '592,5 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-500 hover:to-teal-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

                <!-- 10 Money Cases -->
                <div class="glass-card rounded-2xl p-6 flex flex-col justify-between border-t-4 border-emerald-400 text-center relative">
                    <span class="absolute top-3 right-3 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25%</span>
                    <div>
                        <div class="text-5xl mb-4">💰💰💰</div>
                        <h3 class="text-xl font-bold text-white mb-2">10 Қосымша Кейс</h3>
                        <p class="text-xs text-gray-400 mb-6">Ең үлкен бонус пен мүмкіндіктер кейсі!</p>
                        <div class="mb-6">
                            <span class="text-xs line-through text-gray-500 block mb-1">1 590 ₸</span>
                            <span class="text-3xl font-black text-emerald-400">1 192,5 ₸</span>
                        </div>
                    </div>
                    <button onclick="openModal('10 Қосымша Кейс', { '10 кейс': '1 192,5 ₸' })" class="w-full py-3 rounded-xl bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-500 hover:to-teal-500 font-bold text-white shadow-lg transition-all text-sm">
                        САТЫП АЛУ
                    </button>
                </div>

            </div>

            <!-- TAB 4: UNBAN -->
            <div id="section-unban" class="tab-content hidden max-w-xl mx-auto">
                <div class="glass-card rounded-2xl p-8 text-center border-t-4 border-red-600 relative">
                    <span class="absolute top-4 right-4 px-2 py-0.5 bg-red-500/20 text-red-400 border border-red-500/30 rounded text-[10px] font-black">-25% СКИДКА</span>
                    <div class="text-6xl mb-4">🔓</div>
                    <h3 class="text-3xl font-black text-white mb-3">Серверден Разбан Алу</h3>
                    <p class="text-sm text-gray-300 mb-6 leading-relaxed">
                        Егер бан алып қалсаңыз, осы қызмет арқылы аккаунтыңызды бұғаттаудан дереу босатып, ойынды қайта жалғастыра аласыз.
                    </p>
                    <div class="mb-8">
                        <span class="text-sm line-through text-gray-500 block mb-1">650 ₸</span>
                        <span class="text-4xl font-black text-amber-400">487,5 ₸</span>
                    </div>
                    <button onclick="openModal('РАЗБАН БҰҒАТТАН ШЫҒАРУ', { 'Разбан': '487,5 ₸' })" class="w-full py-4 rounded-xl bg-gradient-to-r from-red-600 to-orange-600 hover:from-red-500 hover:to-orange-500 font-black text-white text-base shadow-xl transition-all tracking-wider">
                        БҰҒАТТАН ШЫҒАРУ САТЫП АЛУ
                    </button>
                </div>
            </div>

        </main>

        <!-- Footer -->
        <footer class="w-full py-6 px-4 glass-panel border-t border-amber-500/20 text-center text-xs text-gray-400 mt-12">
            <div class="max-w-7xl mx-auto flex flex-col sm:flex-row items-center justify-between gap-4">
                <p>© 2026 <span class="text-amber-400 font-bold">F1x Anarchy</span>. Барлық құқықтар қорғалған.</p>
                <div class="flex items-center space-x-4">
                    <a href="https://t.me/f1xanarchy" target="_blank" class="hover:text-amber-400 transition-colors">Telegram Канал</a>
                    <span>•</span>
                    <a href="https://t.me/F1x_9o" target="_blank" class="hover:text-amber-400 transition-colors">Администрация (@F1x_9o)</a>
                </div>
            </div>
        </footer>

    </div>

    <!-- Purchase Modal -->
    <div id="purchaseModal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/80 backdrop-blur-md opacity-0 pointer-events-none transition-all duration-300">
        <div class="glass-panel w-full max-w-md rounded-3xl p-6 sm:p-8 border border-amber-500/40 shadow-2xl transform scale-95 transition-all duration-300 relative" id="modalContainer">
            
            <!-- Close Button -->
            <button onclick="closeModal()" class="absolute top-5 right-5 w-9 h-9 rounded-full bg-white/5 hover:bg-white/10 text-gray-400 hover:text-white flex items-center justify-center transition-colors">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>

            <!-- Modal Header -->
            <div class="text-center mb-6">
                <span class="text-xs font-bold text-amber-400 uppercase tracking-widest">Тапсырысты рәсімдеу</span>
                <h3 id="modalItemTitle" class="text-2xl font-black text-white mt-1">--</h3>
            </div>

            <!-- Modal Form -->
            <form onsubmit="submitPurchase(event)" class="space-y-5">
                
                <!-- Duration Selector (If multiple options exist) -->
                <div id="durationWrapper" class="hidden">
                    <label class="block text-xs font-semibold text-gray-300 mb-2">Мерзімді таңдаңыз:</label>
                    <div id="durationOptions" class="grid grid-cols-2 gap-3">
                        <!-- Injected via JS -->
                    </div>
                </div>

                <!-- Nickname Input -->
                <div>
                    <label for="mcNickname" class="block text-xs font-semibold text-gray-300 mb-2">
                        Minecraft Нигіңізді жазыңыз:
                    </label>
                    <div class="relative">
                        <span class="absolute left-4 top-3.5 text-gray-400"><i class="fa-solid fa-user"></i></span>
                        <input type="text" id="mcNickname" required placeholder="Мысалы: Steve_F1x" class="w-full bg-black/50 border border-amber-500/30 rounded-xl py-3 pl-11 pr-4 text-white placeholder-gray-500 focus:outline-none focus:border-amber-400 focus:ring-1 focus:ring-amber-400 transition-all text-sm font-medium">
                    </div>
                </div>

                <!-- Price Display -->
                <div class="p-4 rounded-xl bg-amber-500/10 border border-amber-500/20 flex items-center justify-between">
                    <span class="text-xs text-gray-300 font-medium">Төлем сомасы:</span>
                    <span id="modalPriceDisplay" class="text-2xl font-black text-amber-400">0 ₸</span>
                </div>

                <!-- Action Button -->
                <button type="submit" class="w-full py-4 rounded-xl bg-gradient-to-r from-sky-500 via-sky-600 to-blue-600 hover:from-sky-400 hover:to-blue-500 font-bold text-white shadow-xl transition-all flex items-center justify-center space-x-2 text-sm">
                    <i class="fa-brands fa-telegram text-lg"></i>
                    <span>ТӨЛЕМГЕ ӨТУ (@F1x_9o)</span>
                </button>
            </form>

        </div>
    </div>

    <!-- JavaScript Script -->
    <script>
        /* ----------------------------------------------------
           Falling Leaves Canvas Animation
        ---------------------------------------------------- */
        const canvas = document.getElementById('leavesCanvas');
        const ctx = canvas.getContext('2d');

        let width = canvas.width = window.innerWidth;
        let height = canvas.height = window.innerHeight;

        window.addEventListener('resize', () => {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        });

        const leaves = [];
        const leafColors = ['#f97316', '#d97706', '#fbbf24', '#991b1b', '#7c2d12'];

        class Leaf {
            constructor() {
                this.reset();
            }
            reset() {
                this.x = Math.random() * width;
                this.y = -20;
                this.size = Math.random() * 12 + 8;
                this.speedY = Math.random() * 1.5 + 0.8;
                this.speedX = Math.random() * 1 - 0.5;
                this.color = leafColors[Math.floor(Math.random() * leafColors.length)];
                this.rotation = Math.random() * 360;
                this.rotSpeed = (Math.random() - 0.5) * 2;
                this.opacity = Math.random() * 0.5 + 0.3;
            }
            update() {
                this.y += this.speedY;
                this.x += Math.sin(this.y * 0.02) + this.speedX;
                this.rotation += this.rotSpeed;

                if (this.y > height + 20) {
                    this.reset();
                }
            }
            draw() {
                ctx.save();
                ctx.translate(this.x, this.y);
                ctx.rotate((this.rotation * Math.PI) / 180);
                ctx.globalAlpha = this.opacity;
                ctx.fillStyle = this.color;

                // Draw simple leaf shape
                ctx.beginPath();
                ctx.moveTo(0, -this.size / 2);
                ctx.quadraticCurveTo(this.size / 2, 0, 0, this.size / 2);
                ctx.quadraticCurveTo(-this.size / 2, 0, 0, -this.size / 2);
                ctx.fill();

                ctx.restore();
            }
        }

        // Initialize 35 leaves
        for (let i = 0; i < 35; i++) {
            leaves.push(new Leaf());
        }

        function animateLeaves() {
            ctx.clearRect(0, 0, width, height);
            leaves.forEach(leaf => {
                leaf.update();
                leaf.draw();
            });
            requestAnimationFrame(animateLeaves);
        }

        window.onload = function() {
            animateLeaves();
        };

        /* ----------------------------------------------------
           Tabs Switching Logic
        ---------------------------------------------------- */
        function switchTab(tabName) {
            // Hide all contents
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            
            // Deactivate all tab buttons
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.className = "tab-btn px-4 sm:px-6 py-3 rounded-xl font-bold text-xs sm:text-sm transition-all duration-300 flex items-center space-x-2 glass-card text-gray-300 hover:text-white";
            });

            // Activate chosen tab
            document.getElementById(`section-${tabName}`).classList.remove('hidden');
            const activeBtn = document.getElementById(`tab-${tabName}`);
            activeBtn.className = "tab-btn active px-4 sm:px-6 py-3 rounded-xl font-bold text-xs sm:text-sm transition-all duration-300 flex items-center space-x-2 bg-gradient-to-r from-amber-500 to-orange-600 text-white shadow-lg";
        }

        /* ----------------------------------------------------
           Copy Server IP Function
        ---------------------------------------------------- */
        function copyIP() {
            const serverIP = "f1x.mcmc.kz:19151";
            
            // Using standard execCommand fallback for seamless clipboard copy in iframes
            const dummy = document.createElement("input");
            document.body.appendChild(dummy);
            dummy.value = serverIP;
            dummy.select();
            document.execCommand("copy");
            document.body.removeChild(dummy);

            showToast("Server IP көшірілді: f1x.mcmc.kz:19151");
        }

        function showToast(msg) {
            const toast = document.getElementById('toast');
            const toastMsg = document.getElementById('toast-msg');
            toastMsg.innerText = msg;
            
            toast.classList.remove('translate-y-20', 'opacity-0');
            toast.classList.add('translate-y-0', 'opacity-100');

            setTimeout(() => {
                toast.classList.remove('translate-y-0', 'opacity-100');
                toast.classList.add('translate-y-20', 'opacity-0');
            }, 3000);
        }

        /* ----------------------------------------------------
           Modal & Telegram Redirect Logic
        ---------------------------------------------------- */
        let activeItemTitle = "";
        let activePrices = {};
        let selectedDuration = "";

        function openModal(title, priceOptions) {
            activeItemTitle = title;
            activePrices = priceOptions;

            document.getElementById('modalItemTitle').innerText = title;
            const durationWrapper = document.getElementById('durationWrapper');
            const durationOptionsContainer = document.getElementById('durationOptions');
            durationOptionsContainer.innerHTML = '';

            const keys = Object.keys(priceOptions);

            if (keys.length > 1) {
                durationWrapper.classList.remove('hidden');
                keys.forEach((duration, index) => {
                    const isFirst = index === 0;
                    if (isFirst) selectedDuration = duration;

                    const btn = document.createElement('button');
                    btn.type = 'button';
                    btn.className = `duration-opt py-2 px-3 rounded-xl text-xs font-bold border transition-all ${
                        isFirst ? 'bg-amber-500/20 border-amber-400 text-amber-300' : 'bg-black/40 border-gray-700 text-gray-400'
                    }`;
                    btn.innerText = `${duration} (${priceOptions[duration]} ₸)`;
                    btn.onclick = () => selectDuration(duration, btn);
                    durationOptionsContainer.appendChild(btn);
                });
            } else {
                durationWrapper.classList.add('hidden');
                selectedDuration = keys[0];
            }

            updateModalPrice();

            const modal = document.getElementById('purchaseModal');
            const modalContainer = document.getElementById('modalContainer');
            modal.classList.remove('opacity-0', 'pointer-events-none');
            modalContainer.classList.remove('scale-95');
            modalContainer.classList.add('scale-100');
        }

        function selectDuration(duration, element) {
            selectedDuration = duration;
            document.querySelectorAll('.duration-opt').forEach(btn => {
                btn.className = 'duration-opt py-2 px-3 rounded-xl text-xs font-bold border transition-all bg-black/40 border-gray-700 text-gray-400';
            });
            element.className = 'duration-opt py-2 px-3 rounded-xl text-xs font-bold border transition-all bg-amber-500/20 border-amber-400 text-amber-300';
            updateModalPrice();
        }

        function updateModalPrice() {
            const currentPrice = activePrices[selectedDuration] || '0 ₸';
            document.getElementById('modalPriceDisplay').innerText = currentPrice;
        }

        function closeModal() {
            const modal = document.getElementById('purchaseModal');
            const modalContainer = document.getElementById('modalContainer');
            modalContainer.classList.remove('scale-100');
            modalContainer.classList.add('scale-95');
            modal.classList.add('opacity-0', 'pointer-events-none');
        }

        function submitPurchase(e) {
            e.preventDefault();
            const nick = document.getElementById('mcNickname').value.trim();
            if (!nick) return;

            const currentPrice = activePrices[selectedDuration];
            
            // Custom Telegram pre-filled text
            let text = `Сәлеметсіз бе! Мен F1x Anarchy серверінен сатып алу жасағым келеді:\n\n`;
            text += `🔹 Тауар: ${activeItemTitle}\n`;
            if (selectedDuration) {
                text += `⏱ Мерзімі: ${selectedDuration}\n`;
            }
            text += `👤 Нигім: ${nick}\n`;
            text += `💰 Сомасы: ${currentPrice} ₸\n\n`;
            text += `Төлем реквизиттерін жіберіңізші!`;

            const encodedText = encodeURIComponent(text);
            const tgLink = `https://t.me/F1x_9o?text=${encodedText}`;

            window.open(tgLink, '_blank');
            closeModal();
        }

        // Close modal on background click
        document.getElementById('purchaseModal').addEventListener('click', function(e) {
            if (e.target === this) closeModal();
        });
    </script>
</body>
