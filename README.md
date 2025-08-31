# OCikasuankami.github.oi
<!DOCTYPE html>
<html lang="zh-TW" class="light scroll-smooth dark">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="深入了解七腳川社後裔如何遷徙、落地生根，形成今日的壽豐部落，探索其三大部落的獨特故事與豐富的 Miladis 捕魚祭文化。">
    <title>七腳川社的傳承：壽豐部落的故事</title>

    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
    <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;500;700&display=swap" rel="stylesheet">
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>

    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: { DEFAULT: '#00A99D', dark: '#FF6F61' },
                        secondary: { DEFAULT: '#FF6F61', dark: '#00A99D' },
                        background: { DEFAULT: '#F7F9FB', dark: '#1A2A3A', light: '#FFFFFF', 'dark-soft': '#2C3E50' },
                        text: { DEFAULT: '#2C3E50', dark: '#E0E0E0', 'secondary': '#55606A', 'dark-secondary': '#B0B0B0' },
                        accent: { DEFAULT: '#FFC107', dark: '#FFC107' }
                    },
                    fontFamily: {
                        sans: ['Noto Sans TC', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <style>
        html {
            scroll-behavior: smooth;
        }

        .animate-on-scroll {
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
        }

        .animate-on-scroll.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .card-hover {
            transition: all 0.3s ease;
        }

        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
        }

        .btn-hover {
            transition: all 0.2s ease;
        }

        .btn-hover:hover {
            transform: scale(1.05);
        }

        /* Tooltip Styles */
        .tooltip-trigger {
            border-bottom: 2px dotted #00A99D;
            cursor: help;
            position: relative;
        }

        .dark .tooltip-trigger {
            border-bottom-color: #FF6F61;
        }

        .tooltip-content {
            visibility: hidden;
            opacity: 0;
            position: absolute;
            bottom: 130%;
            left: 50%;
            transform: translateX(-50%);
            background-color: #2C3E50;
            color: #E0E0E0;
            padding: 8px 12px;
            border-radius: 6px;
            font-size: 0.875rem;
            z-index: 10;
            width: max-content;
            max-width: 280px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
            transition: opacity 0.3s ease, visibility 0.3s ease;
            text-align: left;
        }

        .dark .tooltip-content {
            background-color: #F7F9FB;
            color: #1A2A3A;
        }

        .tooltip-content a {
            color: #FF6F61;
            font-weight: bold;
            text-decoration: none;
        }

        .dark .tooltip-content a {
            color: #00A99D;
        }

        .tooltip-trigger:hover .tooltip-content {
            visibility: visible;
            opacity: 1;
        }

        /* Timeline styles */
        .timeline-item {
            position: relative;
            padding-bottom: 2rem;
            border-left: 2px solid #00A99D;
        }

        .dark .timeline-item {
            border-left-color: #FF6F61;
        }

        .timeline-item:last-child {
            border-left: none;
            padding-bottom: 0;
        }

        .timeline-dot {
            position: absolute;
            left: -10px;
            top: 0;
            height: 20px;
            width: 20px;
            background-color: #FF6F61;
            border-radius: 50%;
            border: 4px solid #F7F9FB;
        }

        .dark .timeline-dot {
            background-color: #00A99D;
            border-color: #1A2A3A;
        }
        
        /* New rule for spacing between dot and text */
        .timeline-item h4,
        .timeline-item p {
            margin-left: 20px;
        }

        /* Interviewee photo circle */
        .interviewee-photo, .age-grade-photo {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background-color: #ccc;
            margin: 0 auto 1rem;
            overflow: hidden;
            border: 4px solid #fff;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        .dark .interviewee-photo, .dark .age-grade-photo {
            border-color: #1A2A3A;
            box-shadow: 0 4px 12px rgba(255, 255, 255, 0.1);
        }

        .interviewee-photo img, .age-grade-photo img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            object-position: center;
        }

        .interview-content {
            display: none;
        }

        .interview-content.active {
            display: grid;
        }

        @media (prefers-reduced-motion: reduce) {
            html {
                scroll-behavior: auto;
            }

            .animate-on-scroll {
                animation: none !important;
                transition: none !important;
                opacity: 1 !important;
                transform: none !important;
            }

            .card-hover:hover,
            .btn-hover:hover {
                transform: none;
            }

            .tooltip-content {
                transition: none !important;
            }
        }
    </style>
</head>

<body class="font-sans bg-background text-text dark:bg-background-dark dark:text-text-dark">

    <header id="header" class="sticky top-0 z-50 w-full transition-all duration-300 bg-background/80 dark:bg-background-dark/80 backdrop-blur-sm shadow-md">
        <div class="container mx-auto px-4">
            <div class="flex items-center justify-between h-20">
                <a href="#hero" class="flex items-center space-x-2">
                    <i class="fas fa-water text-primary dark:text-primary-dark text-2xl"></i>
                    <h1 class="text-xl font-bold text-text dark:text-text-dark">壽豐部落精華</h1>
                </a>

                <nav class="hidden md:flex items-center space-x-6">
                    <a href="#formation" class="font-medium text-text-secondary dark:text-text-dark-secondary hover:text-primary dark:hover:text-primary-dark transition-colors">歷史淵源</a>
                    <a href="#composition" class="font-medium text-text-secondary dark:text-text-dark-secondary hover:text-primary dark:hover:text-primary-dark transition-colors">部落構成</a>
                    <a href="#interview" class="font-medium text-primary dark:text-primary-dark transition-colors">文化訪談</a>
                    <a href="#ceremony" class="font-medium text-text-secondary dark:text-text-dark-secondary hover:text-primary dark:hover:text-primary-dark transition-colors">傳統祭儀</a>
                    <a href="#age-grade" class="font-medium text-text-secondary dark:text-text-dark-secondary hover:text-primary dark:hover:text-primary-dark transition-colors">年齡階級</a>
                    <a href="#glossary" class="font-medium text-text-secondary dark:text-text-dark-secondary hover:text-primary dark:hover:text-primary-dark transition-colors">關鍵術語</a>
                </nav>

                <div class="flex items-center space-x-4">
                    <button id="theme-toggle" aria-label="Toggle Dark Mode" class="text-text-secondary dark:text-text-dark-secondary hover:text-primary dark:hover:text-primary-dark transition-colors">
                        <i class="fas fa-sun dark:hidden"></i>
                        <i class="fas fa-moon hidden dark:inline"></i>
                    </button>
                    <button id="mobile-menu-button" class="md:hidden text-text dark:text-text-dark" aria-label="Open menu">
                        <i class="fas fa-bars text-2xl"></i>
                    </button>
                </div>
            </div>
            <div id="mobile-menu" class="hidden md:hidden pb-4">
                <a href="#formation" class="block py-2 px-4 text-sm hover:bg-background-dark-soft rounded">歷史淵源</a>
                <a href="#composition" class="block py-2 px-4 text-sm hover:bg-background-dark-soft rounded">部落構成</a>
                <a href="#interview" class="block py-2 px-4 text-sm hover:bg-background-dark-soft rounded">文化訪談</a>
                <a href="#ceremony" class="block py-2 px-4 text-sm hover:bg-background-dark-soft rounded">傳統祭儀</a>
                <a href="#age-grade" class="block py-2 px-4 text-sm hover:bg-background-dark-soft rounded">年齡階級</a>
                <a href="#glossary" class="block py-2 px-4 text-sm hover:bg-background-dark-soft rounded">關鍵術語</a>
            </div>
        </div>
    </header>

    <main>
        <section id="hero" class="relative min-h-screen flex items-center justify-center text-center bg-gradient-to-br from-primary/10 via-background to-secondary/10 dark:from-primary-dark/10 dark:via-background-dark dark:to-secondary-dark/10 overflow-hidden px-4">
            <div class="container mx-auto z-10">
                <div class="max-w-4xl mx-auto">
                    <h2 class="text-4xl md:text-6xl font-bold text-text dark:text-text-dark mb-4 animate__animated animate__fadeInDown">
                        <span class="text-primary dark:text-primary-dark">七腳川社</span>的傳承<br>壽豐部落的故事
                    </h2>
                    <p class="text-lg md:text-xl text-text-secondary dark:text-text-dark-secondary mb-8 animate__animated animate__fadeInUp animate__delay-1s">
                        探索因歷史事件與自然變遷而生的阿美族部落，從被迫遷移到落地生根的堅韌篇章。
                    </p>
                    <a href="#formation" class="btn-hover inline-block bg-primary text-white dark:bg-primary-dark dark:text-background-dark font-bold py-3 px-8 rounded-full text-lg shadow-lg hover:shadow-xl transform transition-all duration-300 animate__animated animate__pulse animate__delay-2s animate__infinite">
                        開始閱讀 <i class="fas fa-arrow-down ml-2"></i>
                    </a>
                </div>
                <div class="mt-16 grid grid-cols-2 md:grid-cols-4 gap-8 max-w-5xl mx-auto animate__animated animate__fadeIn animate__delay-2s">
                    <div class="text-center">
                        <i class="fas fa-shoe-prints text-4xl text-secondary dark:text-secondary-dark mb-2"></i>
                        <h3 class="font-semibold">歷史的足跡</h3>
                    </div>
                    <div class="text-center">
                        <i class="fas fa-sitemap text-4xl text-secondary dark:text-secondary-dark mb-2"></i>
                        <h3 class="font-semibold">三大部落</h3>
                    </div>
                    <div class="text-center">
                        <i class="fas fa-feather text-4xl text-secondary dark:text-secondary-dark mb-2"></i>
                        <h3 class="font-semibold">傳統祭儀</h3>
                    </div>
                    <div class="text-center">
                        <i class="fas fa-book-open text-4xl text-secondary dark:text-secondary-dark mb-2"></i>
                        <h3 class="font-semibold">族語智慧</h3>
                    </div>
                </div>
            </div>
        </section>

        <div class="container mx-auto px-4 py-16 md:py-24 space-y-20">

            <section id="formation" class="animate-on-scroll">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">
                    <i class="fas fa-map-signs text-primary dark:text-primary-dark mr-3"></i>壹、歷史淵源：從七腳川到壽豐
                </h2>
                <div class="grid md:grid-cols-5 gap-8 items-center">
                    <div class="md:col-span-3">
                        <p class="text-lg text-text-secondary dark:text-text-dark-secondary mb-4">
                            現今的壽豐部落，其根源可追溯至百年前的<span class="tooltip-trigger">七腳川社<span class="tooltip-content">Cikasuan，為阿美族七大部落之一，原居於花蓮平原。 <a href="#glossary-cikasuan">更多...</a></span></span>。族人的遷徙歷程充滿艱辛，部分族人在遷移過程中因疲憊而停留，亦有部分是為便於日軍管理而被迫遷徙。
                        </p>
                        <p class="text-lg text-text-secondary dark:text-text-dark-secondary mb-6">
                            部落最初的所在地是一片廣大的沼澤地。在農業時代，周邊耕種水稻所排出的水匯流於此，後因日軍的規劃而逐漸轉變為居住地。
                        </p>
                        <p class="text-lg text-text-secondary dark:text-text-dark-secondary bg-background-light dark:bg-background-dark-soft p-4 rounded-lg border-l-4 border-secondary dark:border-secondary-dark">
                            抗日的<span class="tooltip-trigger">七腳川社<span class="tooltip-content">Cikasuan，為阿美族七大部落之一，原居於花蓮平原。 <a href="#glossary-cikasuan">更多...</a></span></span>族人，在大正三年(1914)因日警的大舉攻擊，退居今重光上方的(Cimiyawan)，次年歸順，社眾下山，初居魯給(Loki)，後因耕地不足，向外遷徙或出外謀生。至民國三十四年(1945)，Loki社因遭遇三次颱風，農田嚴重流失，共三十四戶遷來定居。民國九十四年(2005年)六之人口統計，壽豐目前有650位阿美族人，其中七腳川後裔占大多數。
                        </p>
                    </div>
                    <div class="md:col-span-2">
                        <div class="relative pl-6">
                            <div class="timeline-item">
                                <div class="timeline-dot"></div>
                                <h4 class="font-bold text-primary dark:text-primary-dark">1908年</h4>
                                <p class="text-text-secondary dark:text-text-dark-secondary">發生<span class="tooltip-trigger">七腳川事件<span class="tooltip-content">日本統治時期，因日警欺凌族人而引發的阿美族抗日事件，導致七腳川社被摧毀，族人被迫遷徙。 <a href="#glossary-cikasuan-incident">更多...</a></span></span>，族人從吉安太昌部落遷徙至臺東鹿野，途經多個部落。</p>
                            </div>
                            <div class="timeline-item">
                                <div class="timeline-dot"></div>
                                <h4 class="font-bold text-primary dark:text-primary-dark">1915年</h4>
                                <p class="text-text-secondary dark:text-text-dark-secondary">歸順的族人下山，初居魯給(Loki)。</p>
                            </div>
                            <div class="timeline-item">
                                <div class="timeline-dot"></div>
                                <h4 class="font-bold text-primary dark:text-primary-dark">1945年</h4>
                                <p class="text-text-secondary dark:text-text-dark-secondary">因颱風侵襲，34戶族人從Loki遷至現址，形成壽豐部落。</p>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <section id="composition" class="animate-on-scroll">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">
                    <i class="fas fa-sitemap text-primary dark:text-primary-dark mr-3"></i>貳、部落構成：一脈相承的三個家園
                </h2>
                <p class="text-center text-lg text-text-secondary dark:text-text-dark-secondary max-w-3xl mx-auto mb-12">
                    今日的<span class="tooltip-trigger">壽豐部落<span class="tooltip-content">由七腳川社後裔組成的阿美族部落，位於花蓮縣壽豐鄉。 <a href="#glossary-shoufeng-tribe">更多...</a></span></span>，在行政上被劃分為三個緊密相連的小部落，各自擁有獨特的名稱由來與故事。
                </p>
                <div class="grid md:grid-cols-3 gap-8">
                    <div class="card-hover bg-background-light dark:bg-background-dark-soft p-8 rounded-xl shadow-lg text-center animate-on-scroll">
                        <i class="fas fa-bridge-water text-5xl text-accent mb-4"></i>
                        <h3 class="text-2xl font-bold mb-2">Cihamengan<br><span class="text-xl font-normal">(橋頭部落)</span></h3>
                        <p class="text-text-secondary dark:text-text-dark-secondary">
                            Cihamengan的命名是為了感念一位名叫Hameng的先驅者。早期此地是一片適合種植水稻的沼澤區，由從山下部落遷移來的族人定居。為感謝第一位來此開墾並召集親友共同奮鬥的Hameng，部落便將此地命名為Cihamengan。
                        </p>
                    </div>
                    <div class="card-hover bg-background-light dark:bg-background-dark-soft p-8 rounded-xl shadow-lg text-center animate-on-scroll" style="--delay: 0.2s;">
                        <i class="fas fa-tree text-5xl text-accent mb-4"></i>
                        <h3 class="text-2xl font-bold mb-2">Ci’alupalan<br><span class="text-xl font-normal">(山下部落)</span></h3>
                        <p class="text-text-secondary dark:text-text-dark-secondary">
                            Ci’alupalan的歷史與Cikasuan戰役息息相關。戰後族人被迫遷徙，順從日人命令居於今日鯉魚潭露營區一帶，後因1940年代的頻繁颱風洪水而再次遷徙，最終形成了現在的部落。據耆老所述，此地曾種植許多<span class="tooltip-trigger">alupal<span class="tooltip-content">阿美族語，指「柿子」。 <a href="#glossary-alupal">更多...</a></span></span> (柿子)而得名，又因緊鄰壽神社，俗稱為山下部落。這裡被視為壽豐村部落形成的初始之地，目前約有235位居民。
                        </p>
                    </div>
                    <div class="card-hover bg-background-light dark:bg-background-dark-soft p-8 rounded-xl shadow-lg text-center animate-on-scroll" style="--delay: 0.4s;">
                        <svg class="mx-auto mb-4" width="60" height="60" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M50 95V50M50 50L10 10M50 50L90 10" stroke="#FFC107" stroke-width="10" stroke-linecap="round"/>
                        </svg>
                        <h3 class="text-2xl font-bold mb-2">Cisanasay<br><span class="text-xl font-normal">(三文路部落)</span></h3>
                        <p class="text-text-secondary dark:text-text-dark-secondary">
                            Cisanasay的名稱由來有二說：一為紀念漢人Sanfan與原住民女性通婚並在此開墾，故鄉公所將此處命名為「三文路」。另一說則指此地為重要的三叉路口，分別通往平和、光榮部落與壽豐街上，而<span class="tooltip-trigger">Sanasay<span class="tooltip-content">阿美族語，意為「三叉路口」。 <a href="#glossary-sanasay">更多...</a></span></span> 即「三叉」之意。目前，此部落約有36戶原住民家庭居住。
                        </p>
                    </div>
                </div>
            </section>
            
            <section id="interview" class="animate-on-scroll bg-background-light dark:bg-background-dark-soft p-8 rounded-xl shadow-lg">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">
                    <i class="fas fa-microphone-lines text-primary dark:text-primary-dark mr-3"></i>參、文化復振者訪談
                </h2>
                <p class="text-lg text-text-secondary dark:text-text-dark-secondary text-center max-w-3xl mx-auto mb-10">
                    在對壽豐部落的歷史有了更深的認識後，我們訪問了正在推動文化復振的李玟慧阿姨，了解她與部落的故事，以及她為文化傳承所付出的心力。
                </p>

                <div class="grid md:grid-cols-2 gap-8 text-center">
                    <div>
                        <a href="#void" class="block" onclick="showProfile('li-wenhui')">
                            <div class="interviewee-photo bg-gray-300 dark:bg-gray-700 flex items-center justify-center">
                                <img src="https://github.com/OCikasuankami/OCikasuankami.github.oi/blob/main/%E6%88%91%E5%AA%BD%E5%AA%BD.jpg?raw=true" alt="李玟慧 (O'ol Kacaw)" class="object-cover object-center">
                            </div>
                            <h3 class="text-xl font-bold mt-2">李玟慧 (O'ol Kacaw)</h3>
                            <p class="text-primary dark:text-primary-dark font-medium">阿蜜斯工藝坊 負責人</p>
                        </a>
                    </div>
                    
                    <div>
                        <a href="#void" class="block" onclick="showProfile('unnamed')">
                            <div class="interviewee-photo bg-gray-300 dark:bg-gray-700 flex items-center justify-center">
                                <img src="https://raw.githubusercontent.com/OCikasuankami/OCikasuankami.github.oi/refs/heads/main/%E6%88%91%E9%98%BF%E5%AC%A4.jpg" alt="何秀蘭個人照片" class="object-cover object-center">
                            </div>
                            <h3 class="text-xl font-bold mt-2">何秀蘭(Dongi Banil)</h3>
                            <p class="text-primary dark:text-primary-dark font-medium">阿蜜斯工藝坊 原負責人</p>
                        </a>
                    </div>
                </div>

                <div id="li-wenhui-content" class="interview-content active mt-12">
                    <div class="grid md:grid-cols-2 gap-8">
                        <div>
                            <h4 class="text-xl font-bold mb-4">從小在部落感受的凝聚力</h4>
                            <p class="text-text-secondary dark:text-text-dark-secondary">
                                O'ol從小在哈門岸部落長大，從部落豐年祭、社區打掃到母親節、父親節、聯歡晚會等活動，她們全家都會參與。這讓她從小就深刻感受到部落強大的凝聚力與人際間的溫暖。
                            </p>
                        </div>
                        <div>
                            <h4 class="text-xl font-bold mb-4">七腳川事件的歷史觸動</h4>
                            <p class="text-text-secondary dark:text-text-dark-secondary">
                                大學畢業後，O'ol回到部落參與七腳川事件百週年展覽，這成為她投入文化傳承的轉捩點。她發現許多老人家不願承認自己是七腳川人，這讓她意識到若不主動挖掘與傳承，這段歷史將永遠消失。對她來說，部落文化與土地、農作、祭典是密不可分的。面對少子化與歷史斷層的危機感，她堅信必須讓下一代知道自己的根源，才能延續文化。
                            </p>
                        </div>
                        <div>
                            <h4 class="text-xl font-bold mb-4">推動文化傳承的實踐</h4>
                            <p class="text-text-secondary dark:text-text-dark-secondary">
                                傳統部落階層制度對女性的限制，讓O'ol必須透過男性長輩來傳達想法。她們藉由舉辦文化課程與年齡階級訓練，從部落歷史到手工技藝，逐步說服家長支持孩子參與。從最初的「守護長輩的記憶」，到現在轉向「培育下一代的能力」，課程設計更加細緻多元，涵蓋小獵人訓練、祭歌傳唱、傳統編織與服飾製作、釀酒與烹飪等，並依年齡階級的需求開設。
                            </p>
                        </div>
                        <div>
                            <h4 class="text-xl font-bold mb-4">生命的象徵與延續：年齡階級</h4>
                            <p class="text-text-secondary dark:text-text-dark-secondary">
                                年齡階級是部落文化的核心。每八年誕生一個新階級，每個階級名稱都象徵著動植物的特質。階級制度確保了技能與知識的代代相傳，由上一階的哥哥們帶領訓練。即使孩子較少，未入階的小朋友也能先參加訓練，展現了部落互助共榮的精神。
                            </p>
                        </div>
                        <div class="md:col-span-2">
                            <h4 class="text-xl font-bold mb-4">文化的精神核心：豐年祭</h4>
                            <p class="text-text-secondary dark:text-text-dark-secondary">
                                豐年祭是部落最核心的文化活動，為期三天：
                            </p>
                            <ul class="list-disc list-inside space-y-2 text-text-secondary dark:text-text-dark-secondary">
                                <li><strong>第一天：</strong>準備日，主要由族人進行場地布置與相關事宜。</li>
                                <li><strong>第二天：：</strong>運動會與趣味競賽，晚上則有青年之夜，各年齡階級會表演。</li>
                                <li><strong>第三天：：</strong>祭典高峰，下午男性階級跳祭歌，傍晚女性入場送餐，晚上七點後是服裝最為整齊的時段，祭典會持續到深夜。今年特別的是，星期日只保留純粹的祭歌舞蹈。</li>
                            </ul>
                        </div>
                    </div>
                </div>

                <div id="unnamed-content" class="interview-content mt-12">
                    <div class="grid md:grid-cols-2 gap-8">
                        <div>
                            <h4 class="text-xl font-bold mb-4">未命名個人的簡介標題一</h4>
                            <p class="text-text-secondary dark:text-text-dark-secondary">
                                您可以在這裡填寫未命名個人的詳細簡介內容，例如其背景、貢獻或與部落的連結。
                            </p>
                        </div>
                        <div>
                            <h4 class="text-xl font-bold mb-4">未命名個人的簡介標題二</h4>
                            <p class="text-text-secondary dark:text-text-dark-secondary">
                                這裡可以放置更多關於這位未命名人士的資訊。
                            </p>
                        </div>
                        <div class="md:col-span-2">
                            <h4 class="text-xl font-bold mb-4">未命名個人的其他資訊</h4>
                            <p class="text-text-secondary dark:text-text-dark-secondary">
                                補充說明或重要事蹟。
                            </p>
                        </div>
                    </div>
                </div>

                <div class="mt-12 text-center text-lg italic text-text-secondary dark:text-text-dark-secondary">
                    <p id="quote-li-wenhui" class="active">「我深深相信，部落文化只有在代代人的生活中延續，才能真正地活下去。」-李玟慧O'ol Kacaw</p>
                    <p id="quote-unnamed" class="hidden">「這是為「未命名」個人簡介準備的一句話。」</p>
                </div>
            </section>

            <section id="ceremony" x-data="{ tab: 'miladis' }" class="animate-on-scroll">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">
                    <i class="fas fa-feather-alt text-primary dark:text-primary-dark mr-3"></i>肆、傳統祭儀
                </h2>

                <div class="max-w-4xl mx-auto">
                    <div class="flex justify-center border-b border-gray-300 dark:border-gray-600 mb-8">
                        <button @click="tab = 'miladis'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': tab === 'miladis', 'border-transparent': tab !== 'miladis'}" class="py-2 px-6 font-semibold border-b-2 transition-colors">捕魚祭</button>
                        <button @click="tab = 'milisin'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': tab === 'milisin', 'border-transparent': tab !== 'milisin'}" class="py-2 px-6 font-semibold border-b-2 transition-colors">豐年祭</button>
                        <button @click="tab = 'paken-to-liliw'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': tab === 'paken-to-liliw', 'border-transparent': tab !== 'paken-to-liliw'}" class="py-2 px-6 font-semibold border-b-2 transition-colors">捕鳥祭</button>
                    </div>

                    <div x-show="tab === 'miladis'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn">
                        <h3 class="text-2xl font-bold mb-4">Miladis (捕魚祭)</h3>
                        <p class="text-lg text-text-secondary dark:text-text-dark-secondary mb-6">
                            在每年5、6月小米、水稻收成後，部落會舉行捕魚祭。早期部落盛行<span class="tooltip-trigger">Mapapaliw<span class="tooltip-content">指部落成員間互相幫忙、交換勞力的傳統習俗。 <a href="#glossary-mapapaliw">更多...</a></span></span>(換工)，待所有家戶收成完畢，大家便會一同捕魚，並在最後收成的家戶中聚餐，象徵一年的辛勞圓滿結束。
                        </p>
                        <h4 class="text-xl font-semibold mb-4">階級合作的捕魚法：</h4>
                        <div class="bg-background-light dark:bg-background-dark-soft p-6 rounded-lg">
                            <p class="mb-4">不同年齡階級會運用不同的捕魚技巧。例如，古老的<span class="tooltip-trigger">Alamay<span class="tooltip-content">阿美族一個傳統的年齡階級名稱。 <a href="#glossary-alamay">更多...</a></span></span>階級，會展現與自然共存的智慧：</p>
                            <div class="grid md:grid-cols-4 gap-4 text-center">
                                <div class="flex flex-col items-center p-2">
                                    <i class="fas fa-leaf text-4xl text-green-500 mb-2"></i>
                                    <span class="font-bold">1. 採集</span>
                                    <p class="text-sm">青年至山上採集<span class="tooltip-trigger">菇婆芋<span class="tooltip-content">一種大型葉片的植物，其葉子被用來輔助傳統捕魚。 <a href="#glossary-gupoyu">更多...</a></span></span>葉。</p>
                                </div>
                                <div class="flex flex-col items-center p-2">
                                    <i class="fas fa-hand-rock text-4xl text-gray-500 mb-2"></i>
                                    <span class="font-bold">2. 截流</span>
                                    <p class="text-sm">在河中用石頭築壩，僅留一處水道。</p>
                                </div>
                                <div class="flex flex-col items-center p-2">
                                    <i class="fas fa-puzzle-piece text-4xl text-green-700 mb-2"></i>
                                    <span class="font-bold">3. 貼葉</span>
                                    <p class="text-sm">將菇婆芋葉貼在石縫上，防止魚隻鑽隙逃脫。</p>
                                </div>
                                <div class="flex flex-col items-center p-2">
                                    <i class="fas fa-shopping-basket text-4xl text-yellow-700 mb-2"></i>
                                    <span class="font-bold">4. 置簍</span>
                                    <p class="text-sm">在出水口放置魚簍，等待魚群自投羅網。</p>
                                </div>
                            </div>
                        </div>
                        <div class="mt-8">
                            <h3 class="text-2xl font-bold mb-4">現代祭儀的傳承</h3>
                            <p class="text-lg text-text-secondary dark:text-text-dark-secondary">
                                現今的捕魚祭，年齡階級的兄長們會帶領新進的弟弟們，在花蓮溪的米棧大橋與月眉大橋之間進行。雖然場域與工具已有改變，但文化傳承的核心精神不變。
                            </p>
                            <ul class="list-disc list-inside mt-4 space-y-2 text-text-secondary dark:text-text-dark-secondary">
                                <li><strong>地點：</strong>花蓮溪流 (米棧大橋與月眉大橋間)。</li>
                                <li><strong>工具：：</strong>主要使用<span class="tooltip-trigger">八卦網<span class="tooltip-content">一種圓形手拋式漁網，用於淺水區域捕魚。 <a href="#glossary-bagua-net">更多...</a></span></span>與<span class="tooltip-trigger">魚荃<span class="tooltip-content">一種傳統的竹編或網製的捕魚陷阱。 <a href="#glossary-fish-trap">更多...</a></span></span>。</li>
                                <li><strong>歷史方式：：</strong>在更早的時期，族人曾使用<span class="tooltip-trigger">魚藤<span class="tooltip-content">一種含有天然毒素的植物，其汁液可暫時麻痺魚類，便於捕捉，現已較少使用。 <a href="#glossary-fish-vine">更多...</a></span></span>的汁液來麻痺魚群，這是一種更古老的漁法。</li>
                            </ul>
                        </div>
                    </div>

                    <div x-show="tab === 'milisin'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn">
                        <h3 class="text-2xl font-bold mb-4">Milisin (豐年祭)</h3>
                        <div class="bg-background-light dark:bg-background-dark-soft p-6 rounded-lg mb-6">
                            <h4 class="text-xl font-semibold mb-2">豐年祭前的準備</h4>
                            <p class="text-lg text-text-secondary dark:text-text-dark-secondary mb-4">
                                過去豐年祭每年九月舉行，為期七天，時機在第二期稻作插秧與除草後，以確保所有族人都能參與。
                            </p>
                            <div class="bg-gray-100 dark:bg-gray-800 p-4 rounded-md border-l-4 border-accent dark:border-accent">
                                <h5 class="font-bold text-lg mb-2">重要的驅除儀式：Mikeroh</h5>
                                <p class="text-text-secondary dark:text-text-dark-secondary">
                                    為了祈求豐收，豐年祭前會先進行Mikeroh驅除儀式。Sikawasay（祭司）會到農地進行儀式，驅除穢氣，並與祖靈對話。儀式中會使用麻糬（tolon）和酒，結束後參與者一同分享，直到酒喝完才能回家。
                                </p>
                            </div>
                        </div>
                        <div class="bg-background-light dark:bg-background-dark-soft p-6 rounded-lg">
                            <h4 class="text-xl font-semibold mb-2">豐年祭的三天</h4>
                            <ul class="list-disc list-inside space-y-4 text-text-secondary dark:text-text-dark-secondary">
                                <li>
                                    <strong class="text-text dark:text-text-dark">第一天：</strong>各階級成員搭建瞭望台並準備祭典事宜。過去青年會上山打獵，現則改為宰殺部落飼養的牲畜。男子們會在會場過夜，並整理場地。
                                </li>
                                <li>
                                    <strong class="text-text dark:text-text-dark">第二天：：</strong>運動會與趣味競賽，晚上則有青年之夜，各年齡階級會表演。
                                </li>
                                <li>
                                    <strong class="text-text dark:text-text-dark">第三天：：</strong>Malialac（分食魚肉）。此活動僅限男性參與，考驗年輕人的體力。過去漁獲量少，魚僅供當場食用；現多向漁場採購，捕魚方式也已改變。
                                </li>
                            </ul>
                            <div class="bg-secondary/10 dark:bg-secondary-dark/10 p-4 rounded-md mt-6">
                                <h5 class="font-bold text-lg text-secondary dark:text-secondary-dark mb-2">獨特的求愛儀式</h5>
                                <p class="text-text-secondary dark:text-text-dark-secondary">
                                    在豐年祭第二天，女性若對心儀的男性有好感，可送檳榔表達情意。若男孩收下，代表雙方有意。這讓豐年祭也成為部落男女重要的社交與情感交流場所。
                                </p>
                            </div>
                        </div>
                    </div>

                    <div x-show="tab === 'paken-to-liliw'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn">
                        <h3 class="text-2xl font-bold mb-4">Paken to liliw (捕鳥祭)</h3>
                        <p class="text-lg text-text-secondary dark:text-text-dark-secondary mb-4">
                            過去小米田常遭鳥類啄食，因此族人會在每年十二月至隔年二月間進行捕鳥。根據李明德（Kacaw Dawkin）的說法，此習俗有其重要原因：
                        </p>
                        <ul class="list-disc list-inside space-y-2 text-text-secondary dark:text-text-dark-secondary mb-6">
                            <li>生態平衡：只在成鳥時期捕捉，以維持生態永續。</li>
                            <li>農事考量：播種後農忙，僅在特定時間有空閒。</li>
                            <li>社交聚會：捕鳥活動是難得的休息時光，讓族人能聚餐聊天。</li>
                            <li>飲食文化：最初在田邊烤給幫忙的人吃，後演變為正式的祭儀。</li>
                        </ul>
                        <div class="bg-background-light dark:bg-background-dark-soft p-6 rounded-lg">
                            <h4 class="text-xl font-semibold mb-2">祭儀禁忌與規範</h4>
                            <p class="text-text-secondary dark:text-text-dark-secondary mb-4">
                                捕鳥時會使用陷阱、網子等獵具，但女性不得參與。男子在進山前必須向祖靈祈求平安，並祭拜山神和獵神Calah。同時，族人不能隨意觸摸他人的獵具，以免身體不適。獵到動物後，必須將獵物的頭部祭拜山神，以示感謝。
                            </p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="age-grade" x-data="{ currentGrade: 'ladiwas' }" class="animate-on-scroll">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">
                    <i class="fas fa-shield-alt text-primary dark:text-primary-dark mr-3"></i>伍、年齡階級和訓練
                </h2>
                <p class="text-center text-lg text-text-secondary dark:text-text-dark-secondary max-w-3xl mx-auto mb-12">
                    阿美族的年齡階級是維繫部落社會結構與文化傳承的核心，每個階級都肩負著不同的責任與任務，並透過嚴格的訓練來培養部落未來的領導者。
                </p>

                <div class="max-w-4xl mx-auto">
                    <div class="flex flex-wrap justify-center border-b border-gray-300 dark:border-gray-600 mb-8">
                        <button @click="currentGrade = 'ladiwas'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': currentGrade === 'ladiwas', 'border-transparent': currentGrade !== 'ladiwas'}" class="py-2 px-4 md:px-6 font-semibold border-b-2 transition-colors">Ladiwas</button>
                        <button @click="currentGrade = 'alamya'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': currentGrade === 'alamya', 'border-transparent': currentGrade !== 'alamya'}" class="py-2 px-4 md:px-6 font-semibold border-b-2 transition-colors">Alamya</button>
                        <button @click="currentGrade = 'maoway'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': currentGrade === 'maoway', 'border-transparent': currentGrade !== 'maoway'}" class="py-2 px-4 md:px-6 font-semibold border-b-2 transition-colors">Ma'oway</button>
                        <button @click="currentGrade = 'alemet'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': currentGrade === 'alemet', 'border-transparent': currentGrade !== 'alemet'}" class="py-2 px-4 md:px-6 font-semibold border-b-2 transition-colors">Alemet</button>
                        <button @click="currentGrade = 'kohakoh'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': currentGrade === 'kohakoh', 'border-transparent': currentGrade !== 'kohakoh'}" class="py-2 px-4 md:px-6 font-semibold border-b-2 transition-colors">Kohakoh</button>
                        <button @click="currentGrade = 'copolan'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': currentGrade === 'copolan', 'border-transparent': currentGrade !== 'copolan'}" class="py-2 px-4 md:px-6 font-semibold border-b-2 transition-colors">Copolan</button>
                        <button @click="currentGrade = 'alafangas'" :class="{'border-primary dark:border-primary-dark text-primary dark:text-primary-dark': currentGrade === 'alafangas', 'border-transparent': currentGrade !== 'alafangas'}" class="py-2 px-4 md:px-6 font-semibold border-b-2 transition-colors">Alafangas</button>
                    </div>

                    <div x-show="currentGrade === 'ladiwas'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn flex flex-col md:flex-row items-center gap-8 bg-background-light dark:bg-background-dark-soft p-6 rounded-lg shadow-md">
                        <div class="age-grade-photo bg-gray-300 dark:bg-gray-700 flex-shrink-0">
                            <img src="https://raw.githubusercontent.com/OCikasuankami/OCikasuankami.github.oi/refs/heads/main/%E7%A5%9E%E5%A3%BA.jpg" alt="Ladiwas 階級" class="object-cover object-center">
                        </div>
                        <div>
                            <h3 class="text-2xl font-bold mb-4">Ladiwas 階級</h3>
                            <p class="text-lg text-text-secondary dark:text-text-dark-secondary">
                                此處為 Ladiwas 階級的介紹，請編輯此段文字。這個年齡階級通常代表著部落中較為年輕的成員，他們剛開始接受訓練，學習部落的傳統知識和技能。他們負責部落中的輕勞動和雜務，並在長者的指導下逐步成長。
                            </p>
                        </div>
                    </div>

                    <div x-show="currentGrade === 'alamya'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn flex flex-col md:flex-row items-center gap-8 bg-background-light dark:bg-background-dark-soft p-6 rounded-lg shadow-md">
                        <div class="age-grade-photo bg-gray-300 dark:bg-gray-700 flex-shrink-0">
                            <img src="https://raw.githubusercontent.com/OCikasuankami/OCikasuankami.github.oi/refs/heads/main/%E9%AD%9A%E9%B1%97%E9%9B%B2.JPG" alt="Alamya 階級" class="object-cover object-center">
                        </div>
                        <div>
                            <h3 class="text-2xl font-bold mb-4">Alamya 階級</h3>
                            <p class="text-lg text-text-secondary dark:text-text-dark-secondary">
                                此處為 Alamya 階級的介紹，請編輯此段文字。這個階級的成員已經累積了一定的經驗，開始參與部落中更重要的事務，例如狩獵、捕魚等。他們是部落的勞動主力，也是未來中堅力量的培養對象。
                            </p>
                        </div>
                    </div>

                    <div x-show="currentGrade === 'maoway'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn flex flex-col md:flex-row items-center gap-8 bg-background-light dark:bg-background-dark-soft p-6 rounded-lg shadow-md">
                        <div class="age-grade-photo bg-gray-300 dark:bg-gray-700 flex-shrink-0">
                            <img src="https://raw.githubusercontent.com/OCikasuankami/OCikasuankami.github.oi/refs/heads/main/%E9%BB%83%E8%97%A4.jpg" alt="Ma'oway 階級" class="object-cover object-center">
                        </div>
                        <div>
                            <h3 class="text-2xl font-bold mb-4">Ma'oway 階級</h3>
                            <p class="text-lg text-text-secondary dark:text-text-dark-secondary">
                                此處為 Ma'oway 階級的介紹，請編輯此段文字。這個階級的成員在部落中擁有較高的地位和權力，他們負責領導和管理部落事務，並在重要決策中扮演關鍵角色。他們也是年輕一代的導師，傳授知識和經驗。
                            </p>
                        </div>
                    </div>

                    <div x-show="currentGrade === 'alemet'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn flex flex-col md:flex-row items-center gap-8 bg-background-light dark:bg-background-dark-soft p-6 rounded-lg shadow-md">
                        <div class="age-grade-photo bg-gray-300 dark:bg-gray-700 flex-shrink-0">
                            <img src="https://raw.githubusercontent.com/OCikasuankami/OCikasuankami.github.oi/refs/heads/main/%E8%87%BA%E6%9D%B1%E7%81%AB%E5%88%BA%E6%9C%A8.jpg" alt="Alemet 階級" class="object-cover object-center">
                        </div>
                        <div>
                            <h3 class="text-2xl font-bold mb-4">Alemet 階級</h3>
                            <p class="text-lg text-text-secondary dark:text-text-dark-secondary">
                                此處為 Alemet 階級的介紹，請編輯此段文字。這個階級的成員通常是部落中的資深長者，他們擁有豐富的人生經驗和智慧，是部落的精神領袖。他們負責主持祭典、傳承傳統文化，並在部落中享有崇高的聲望。
                            </p>
                        </div>
                    </div>

                    <div x-show="currentGrade === 'kohakoh'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn flex flex-col md:flex-row items-center gap-8 bg-background-light dark:bg-background-dark-soft p-6 rounded-lg shadow-md">
                        <div class="age-grade-photo bg-gray-300 dark:bg-gray-700 flex-shrink-0">
                            <img src="https://raw.githubusercontent.com/OCikasuankami/OCikasuankami.github.oi/refs/heads/main/%E7%9C%BC%E9%8F%A1%E8%9B%87.jpg" alt="Kohakoh 階級" class="object-cover object-center">
                        </div>
                        <div>
                            <h3 class="text-2xl font-bold mb-4">Kohakoh 階級</h3>
                            <p class="text-lg text-text-secondary dark:text-text-dark-secondary">
                                此處為 Kohakoh 階級的介紹，請編輯此段文字。這個階級的成員是部落的決策核心，他們負責制定部落的發展方向，解決部落內部衝突，並對外代表部落。他們是部落的最高領導者，也是部落的守護者。
                            </p>
                        </div>
                    </div>

                    <div x-show="currentGrade === 'copolan'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn flex flex-col md:flex-row items-center gap-8 bg-background-light dark:bg-background-dark-soft p-6 rounded-lg shadow-md">
                        <div class="age-grade-photo bg-gray-300 dark:bg-gray-700 flex-shrink-0">
                            <img src="https://raw.githubusercontent.com/OCikasuankami/OCikasuankami.github.oi/refs/heads/main/%E8%BE%A3%E6%A4%92.jpg" alt="Copolan 階級" class="object-cover object-center">
                        </div>
                        <div>
                            <h3 class="text-2xl font-bold mb-4">Copolan 階級</h3>
                            <p class="text-lg text-text-secondary dark:text-text-dark-secondary">
                                此處為 Copolan 階級的介紹，請編輯此段文字。這個階級的成員是部落的長老，他們在部落中享有最高的尊敬和權威。他們是部落歷史和文化的活字典，也是部落精神的象徵。
                            </p>
                        </div>
                    </div>
                    
                    <div x-show="currentGrade === 'alafangas'" x-transition:enter="animate__animated animate__fadeIn" class="animate__animated animate__fadeIn flex flex-col md:flex-row items-center gap-8 bg-background-light dark:bg-background-dark-soft p-6 rounded-lg shadow-md">
                        <div class="age-grade-photo bg-gray-300 dark:bg-gray-700 flex-shrink-0">
                            <img src="https://raw.githubusercontent.com/OCikasuankami/OCikasuankami.github.oi/refs/heads/main/%E8%8B%A6%E6%A5%9D%E6%A8%B9.jpg" alt="Alafangas 階級" class="object-cover object-center">
                        </div>
                        <div>
                            <h3 class="text-2xl font-bold mb-4">Alafangas 階級</h3>
                            <p class="text-lg text-text-secondary dark:text-text-dark-secondary">
                                此處為 Alafangas 階級的介紹，請編輯此段文字。這是阿美族年齡階級中最高階的長老，他們是部落的精神領袖和決策者，擁有最高的權威和智慧。他們負責部落的重大決策，並在部落中享有最高的尊敬。
                            </p>
                        </div>
                    </div>
                </div>

                <div class="mt-8 bg-background-light dark:bg-background-dark-soft p-6 rounded-lg shadow-inner">
                    <h4 class="text-2xl font-bold text-center mb-4">Mamiseral 成年儀式</h4>
                    <p class="text-lg text-text-secondary dark:text-text-dark-secondary text-center">
                        現今部落的年齡階級組織，每 8 年會舉行一次新一級的入階儀式，這項儀式活動被稱為 masiseral。其運作模式嚴謹且富有傳承意義。
    部落規定，男孩子們在 國小四、五年級 左右就必須加入年齡階級組織，成為部落的一份子。特別的是，新加入的年齡階級會沿用即將退休並晉升為部落耆老的那個年齡階級的名稱。這套共有 七個級名 的循環制度，每 49 年會完整循環一次，確保了級名與輩分制度的延續性。
    在這長達 8 年的入階週期中，部落會分批招募新生力軍，共分為三梯次。這不僅讓部落能夠持續補充新血，也讓不同年齡層的男孩能有機會參與。

                    </p>
                </div>
            </section>

            <section id="glossary" class="animate-on-scroll bg-background-light dark:bg-background-dark-soft rounded-lg shadow-md py-12 px-6 md:px-10">
                <h2 class="text-3xl md:text-4xl font-bold text-center mb-8 text-primary dark:text-primary-dark">關鍵術語詞彙表</h2>
                <dl class="grid md:grid-cols-2 gap-x-8 gap-y-6">
                    <div id="glossary-cikasuan">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">七腳川社 (Cikasuan)</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">阿美族七大社之一，原居住於今日花蓮市吉安鄉一帶，是壽豐部落族人的祖居地。</dd>
                    </div>
                    <div id="glossary-cikasuan-incident">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">七腳川事件</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">1908年發生的阿美族抗日事件。事件後，七腳川社遭日軍焚毀，族人被迫離開原居地，四處遷徙。</dd>
                    </div>
                    <div id="glossary-shoufeng-tribe">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">壽豐部落</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">由七腳川社後裔因歷史事件與天災遷徙後，於現今花蓮縣壽豐鄉所建立的部落。</dd>
                    </div>
                    <div id="glossary-alupal">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">alupal</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">阿美族語，指「柿子」。山下部落的名稱由來之一。</dd>
                    </div>
                    <div id="glossary-sanasay">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">Sanasay</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">阿美族語，意為「三叉路口」。三文路部落的名稱由來之一。</dd>
                    </div>
                    <div id="glossary-miladis">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">Miladis (Palael)</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">阿美族的傳統祭儀「捕魚祭」，通常在每年5-6月農作物收成後舉行，象徵感恩與團結。</dd>
                    </div>
                    <div id="glossary-mapapaliw">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">Mapapaliw</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">阿美族語，指「換工」，是部落成員間互相幫忙、交換勞力的傳統互助制度。</dd>
                    </div>
                    <div id="glossary-alamay">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">Alamay</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">阿美族一個傳統的年齡階級名稱。</dd>
                    </div>
                    <div id="glossary-gupoyu">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">菇婆芋</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">一種大型葉片的植物，其葉子被用來輔助傳統捕魚。</dd>
                    </div>
                    <div id="glossary-bagua-net">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">八卦網</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">一種圓形手拋式漁網，用於淺水區域捕魚。</dd>
                    </div>
                    <div id="glossary-fish-trap">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">魚荃</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">一種傳統的竹編或網製的捕魚陷阱。</dd>
                    </div>
                    <div id="glossary-fish-vine">
                        <dt class="text-xl font-semibold text-text dark:text-text-dark">魚藤</dt>
                        <dd class="mt-1 text-text-secondary dark:text-text-dark-secondary ml-4">一種含有天然毒素的植物，其汁液可暫時麻痺魚類，便於捕捉，現已較少使用。</dd>
                    </div>
                </dl>
            </section>
        </div>
    </main>
    <script>
        document.addEventListener("DOMContentLoaded", function () {
            // Theme Toggle
            const themeToggle = document.getElementById('theme-toggle');
            const htmlTag = document.documentElement;
            const currentTheme = localStorage.getItem('theme') || 'light';
            if (currentTheme === 'dark') {
                htmlTag.classList.add('dark');
            }
            themeToggle.addEventListener('click', () => {
                if (htmlTag.classList.contains('dark')) {
                    htmlTag.classList.remove('dark');
                    localStorage.setItem('theme', 'light');
                } else {
                    htmlTag.classList.add('dark');
                    localStorage.setItem('theme', 'dark');
                }
            });

            // Mobile Menu Toggle
            const mobileMenuButton = document.getElementById('mobile-menu-button');
            const mobileMenu = document.getElementById('mobile-menu');
            mobileMenuButton.addEventListener('click', () => {
                mobileMenu.classList.toggle('hidden');
            });

            // Interviewer Content Toggle
            window.showProfile = function (profileId) {
                const contents = document.querySelectorAll('.interview-content');
                contents.forEach(content => content.classList.remove('active'));
                const targetContent = document.getElementById(profileId + '-content');
                if (targetContent) {
                    targetContent.classList.add('active');
                }
                const quotes = document.querySelectorAll('[id^="quote-"]');
                quotes.forEach(quote => quote.classList.add('hidden'));
                const targetQuote = document.getElementById('quote-' + profileId);
                if (targetQuote) {
                    targetQuote.classList.remove('hidden');
                }
            };
            // Initial call to set the default active profile
            showProfile('li-wenhui');

            // Scroll Animation
            const elementsToAnimate = document.querySelectorAll('.animate-on-scroll');
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('visible');
                        observer.unobserve(entry.target);
                    }
                });
            }, {
                threshold: 0.1
            });
            elementsToAnimate.forEach(element => {
                observer.observe(element);
            });
        });
    </script>
</body>

</html>
