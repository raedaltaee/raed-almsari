<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>حقيبة تدريبية تفاعلية لتقنية DWDM</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals & Tech Blue -->
    <!-- Application Structure Plan: The SPA uses a tab-based navigation to create a thematic, non-linear user experience. The content is grouped into logical sections: "الأساسيات" (Fundamentals), "المكونات" (Components), "تصميم الشبكة" (Network Design), "التطبيقات والمعايير" (Applications & Standards), and a hands-on "مختبر تفاعلي" (Interactive Lab). This structure allows users to explore topics based on their immediate questions (e.g., "What is it?", "How does it work?") rather than following the rigid structure of the source report. This enhances usability and encourages self-directed learning, making complex technical information more accessible. -->
    <!-- Visualization & Content Choices: The application transforms static report data into interactive elements. Key choices include: 1) Fundamentals: An interactive HTML/JS table for DWDM vs. CWDM comparison. Goal: Compare. Justification: More engaging than a static table. 2) Components: A clickable HTML/CSS diagram of a DWDM link. Goal: Organize & Inform. Justification: Provides a visual map for exploration. 3) Network Design: An interactive Power Budget Calculator using JS and a Chart.js visualizer. Goal: Calculate & Analyze. Justification: Turns a theoretical example into a hands-on tool, boosting comprehension. 4) Applications: A responsive card grid for use cases. Goal: Inform. Justification: Modern and scannable presentation. 5) Interactive Lab: A Channel Plan Visualizer using JS and Chart.js. Goal: Visualize & Apply. Justification: Demonstrates channel density dynamically. All visualizations are built with Chart.js or HTML/CSS, confirming no SVG/Mermaid usage. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Tajawal', sans-serif;
        }
        .tab-active {
            border-color: #3B82F6;
            color: #3B82F6;
            background-color: #EFF6FF;
        }
        .panel {
            display: none;
        }
        .panel.active {
            display: block;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .component:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px rgba(59, 130, 246, 0.5);
        }
        .component {
            transition: all 0.3s ease-in-out;
        }
        .accordion-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.5s ease-in-out;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800">

    <div class="container mx-auto p-4 md:p-8">

        <!-- Header -->
        <header class="text-center mb-8">
            <h1 class="text-4xl md:text-5xl font-bold text-slate-900 mb-2">محور التدريب التفاعلي لتقنية DWDM</h1>
            <p class="text-lg text-slate-600">استكشف عالم شبكات الألياف الضوئية عالية السعة بطريقة مبتكرة</p>
            <div class="mt-4 text-sm text-slate-500">
                <p>إعداد: رائد ابراهيم خليل | ماجستير هندسة اتصالات</p>
                <p>ديوان الوقف الشيعي | الجامعة المستنصرية</p>
            </div>
        </header>

        <!-- Navigation Tabs -->
        <nav class="flex flex-wrap justify-center border-b border-slate-300 mb-8" id="tab-nav">
            <button data-tab="fundamentals" class="tab-btn text-lg py-3 px-6 border-b-4 border-transparent hover:bg-slate-100 tab-active">الأساسيات</button>
            <button data-tab="components" class="tab-btn text-lg py-3 px-6 border-b-4 border-transparent hover:bg-slate-100">المكونات</button>
            <button data-tab="design" class="tab-btn text-lg py-3 px-6 border-b-4 border-transparent hover:bg-slate-100">تصميم الشبكة</button>
            <button data-tab="apps" class="tab-btn text-lg py-3 px-6 border-b-4 border-transparent hover:bg-slate-100">التطبيقات والمعايير</button>
            <button data-tab="lab" class="tab-btn text-lg py-3 px-6 border-b-4 border-transparent hover:bg-slate-100">مختبر تفاعلي</button>
        </nav>

        <main>
            <!-- Fundamentals Panel -->
            <section id="fundamentals" class="panel active">
                <div class="bg-white p-6 rounded-lg shadow-md">
                    <h2 class="text-3xl font-bold mb-4 text-slate-800">ما هي تقنية DWDM؟</h2>
                    <p class="mb-6 text-slate-600 leading-relaxed">
                        هذا القسم يضع حجر الأساس لفهم تقنية تعدد الإرسال بتقسيم الطول الموجي الكثيف (DWDM). ستتعرف على المبادئ الجوهرية التي تجعل هذه التقنية العمود الفقري للإنترنت الحديث، وكيف تتيح نقل كميات هائلة من البيانات عبر ليف بصري واحد، بالإضافة إلى مقارنة تفاعلية مع تقنية CWDM لتوضيح الفروق الرئيسية.
                    </p>

                    <div class="grid md:grid-cols-2 gap-8">
                        <div>
                            <h3 class="text-2xl font-semibold mb-3 text-blue-600">المبدأ الأساسي</h3>
                            <p class="mb-4">تخيل طريقًا سريعًا. بدلاً من السماح لسيارة واحدة فقط بالمرور، تقوم تقنية DWDM بطلاء كل سيارة (إشارة بيانات) بلون مختلف (طول موجي) وتسمح لجميع السيارات بالمرور في نفس الوقت على نفس الطريق (ليف بصري واحد). هذا يزيد من "سعة" الطريق بشكل هائل.</p>
                            
                            <h3 class="text-2xl font-semibold mb-3 text-blue-600">المزايا الرئيسية</h3>
                            <ul class="list-disc pr-5 space-y-2">
                                <li><strong class="font-semibold">سعة هائلة:</strong> نقل ما يصل إلى 160 قناة بيانات أو أكثر على ليف واحد.</li>
                                <li><strong class="font-semibold">فعالية التكلفة:</strong> ترقية سعة الشبكات الحالية دون الحاجة لمد ألياف جديدة باهظة الثمن.</li>
                                <li><strong class="font-semibold">مسافات طويلة:</strong> إمكانية تضخيم الإشارة تسمح بنقل البيانات لآلاف الكيلومترات.</li>
                                <li><strong class="font-semibold">مرونة عالية:</strong> نقل أنواع مختلفة من البيانات (IP, SONET, ATM) على نفس البنية التحتية.</li>
                            </ul>
                        </div>
                        <div class="bg-slate-100 p-4 rounded-lg">
                            <h3 class="text-2xl font-semibold mb-4 text-center">مقارنة تفاعلية: DWDM ضد CWDM</h3>
                            <p class="text-sm text-center mb-4 text-slate-500">انقر على أي صف للمزيد من التفاصيل</p>
                            <table class="w-full text-right border-collapse">
                                <thead>
                                    <tr class="border-b-2 border-slate-300">
                                        <th class="p-2 font-semibold">الميزة</th>
                                        <th class="p-2 font-semibold text-blue-600">DWDM (الكثيف)</th>
                                        <th class="p-2 font-semibold text-teal-600">CWDM (الخشن)</th>
                                    </tr>
                                </thead>
                                <tbody id="comparison-table">
                                    <tr class="border-b border-slate-200 cursor-pointer hover:bg-blue-50" data-detail="DWDM تستخدم تباعداً ضيقاً جداً (0.8/0.4 نانومتر)، مما يسمح بحشر عدد كبير من القنوات. CWDM تستخدم تباعداً واسعاً (20 نانومتر)، مما يحد من عدد القنوات.">
                                        <td class="p-3 font-medium">تباعد القنوات</td>
                                        <td class="p-3">ضيق (50/100 GHz)</td>
                                        <td class="p-3">واسع (20 nm)</td>
                                    </tr>
                                    <tr class="border-b border-slate-200 cursor-pointer hover:bg-blue-50" data-detail="بسبب التباعد الضيق، يمكن لـ DWDM دعم ما يصل إلى 160 قناة، بينما تقتصر CWDM على 18 قناة كحد أقصى.">
                                        <td class="p-3 font-medium">عدد القنوات</td>
                                        <td class="p-3">عالي (حتى 160+)</td>
                                        <td class="p-3">منخفض (حتى 18)</td>
                                    </tr>
                                    <tr class="border-b border-slate-200 cursor-pointer hover:bg-blue-50" data-detail="قنوات DWDM تقع في نطاق يمكن تضخيمه بسهولة باستخدام مضخمات EDFA، مما يجعلها مثالية للمسافات الطويلة. قنوات CWDM لا يمكن تضخيمها بنفس الكفاءة.">
                                        <td class="p-3 font-medium">إمكانية التضخيم</td>
                                        <td class="p-3">نعم (EDFA / Raman)</td>
                                        <td class="p-3">لا</td>
                                    </tr>
                                     <tr class="border-b border-slate-200 cursor-pointer hover:bg-blue-50" data-detail="التضخيم يسمح لشبكات DWDM بالوصول لمسافات تتجاوز 1000 كم، بينما تقتصر CWDM على حوالي 70-80 كم.">
                                        <td class="p-3 font-medium">المسافة</td>
                                        <td class="p-3">طويلة جداً (1000+ كم)</td>
                                        <td class="p-3">قصيرة (حتى 80 كم)</td>
                                    </tr>
                                    <tr class="cursor-pointer hover:bg-blue-50" data-detail="تاريخياً كانت DWDM أغلى ثمناً، لكن التطورات الحديثة جعلت التكلفة متقاربة، مع أفضلية لـ DWDM في السعات العالية والشبكات المستقبلية.">
                                        <td class="p-3 font-medium">التكلفة</td>
                                        <td class="p-3">أعلى نسبياً</td>
                                        <td class="p-3">أقل نسبياً</td>
                                    </tr>
                                </tbody>
                            </table>
                            <div id="comparison-detail" class="mt-4 p-3 bg-white rounded-md text-slate-700 min-h-[50px] transition-all duration-300"></div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Components Panel -->
            <section id="components" class="panel">
                <div class="bg-white p-6 rounded-lg shadow-md">
                    <h2 class="text-3xl font-bold mb-4 text-slate-800">مكونات نظام DWDM</h2>
                    <p class="mb-6 text-slate-600 leading-relaxed">
                        استكشف البنية التشريحية لنظام DWDM. هذا المخطط التفاعلي يسمح لك بالنقر على أي مكون رئيسي في مسار الإشارة الضوئية لمعرفة وظيفته وأهميته. من تحويل الإشارة في جهاز الإرسال إلى تضخيمها وتعويض تشوهها، ستفهم كيف تعمل هذه الأجزاء معًا بتناغم.
                    </p>
                    <div class="grid lg:grid-cols-3 gap-6 items-center">
                        <div class="lg:col-span-2">
                             <div class="flex items-center justify-around bg-slate-100 p-4 rounded-lg overflow-x-auto">
                                <!-- Client Signal -->
                                <div class="text-center flex-shrink-0 mx-2">
                                    <div class="component bg-white p-3 rounded-lg shadow-sm cursor-pointer" data-info="جهاز العميل" data-detail="يمثل مصدر البيانات الأصلي، مثل جهاز توجيه (Router) أو خادم (Server) يرسل إشارات كهربائية أو بصرية قصيرة المدى.">
                                        <span class="text-4xl">💻</span>
                                        <p class="font-semibold text-sm">إشارة العميل</p>
                                    </div>
                                </div>
                                <div class="text-3xl text-slate-400 font-thin mx-1">→</div>
                                <!-- Transponder -->
                                <div class="text-center flex-shrink-0 mx-2">
                                     <div class="component bg-white p-3 rounded-lg shadow-sm cursor-pointer" data-info="جهاز الإرسال والاستقبال (Transponder)" data-detail="قلب النظام! يستقبل إشارة العميل، يحولها إلى طول موجي محدد ودقيق ضمن شبكة DWDM (عملية O-E-O)، ويقوم بتجديد الإشارة (3R: Re-amplifying, Re-shaping, Re-timing) لضمان جودتها.">
                                        <span class="text-4xl">🔄</span>
                                        <p class="font-semibold text-sm">Transponder</p>
                                    </div>
                                </div>
                                <div class="text-3xl text-slate-400 font-thin mx-1">→</div>
                                <!-- MUX -->
                                <div class="text-center flex-shrink-0 mx-2">
                                    <div class="component bg-white p-3 rounded-lg shadow-sm cursor-pointer" data-info="المُجمّع (Multiplexer - MUX)" data-detail="يقوم بدمج عدة أطوال موجية (ألوان) قادمة من أجهزة Transponders مختلفة في ليف بصري واحد، مما يخلق إشارة مركبة تحتوي على جميع القنوات.">
                                        <span class="text-4xl">🚦</span>
                                        <p class="font-semibold text-sm">MUX</p>
                                    </div>
                                </div>
                               <div class="text-3xl text-slate-400 font-thin mx-1">→</div>
                                <!-- Fiber & Amplifier -->
                                <div class="text-center flex-shrink-0 mx-2">
                                    <div class="component bg-white p-3 rounded-lg shadow-sm cursor-pointer" data-info="الألياف والمضخمات (Fiber & Amplifiers)" data-detail="الليف البصري هو مسار انتقال الإشارة. مع المسافات الطويلة، تضعف الإشارة (التوهين). تقوم المضخمات (مثل EDFA) بتعزيز قوة جميع الأطوال الموجية في نفس الوقت دون تحويلها لإشارة كهربائية، مما يسمح بالوصول لمسافات بعيدة.">
                                        <span class="text-4xl">〰️ Amplified 〰️</span>
                                        <p class="font-semibold text-sm">ليف بصري</p>
                                    </div>
                                </div>
                                <div class="text-3xl text-slate-400 font-thin mx-1">→</div>
                                <!-- DEMUX -->
                                <div class="text-center flex-shrink-0 mx-2">
                                    <div class="component bg-white p-3 rounded-lg shadow-sm cursor-pointer" data-info="فاصل الإشارة (Demultiplexer - DEMUX)" data-detail="في الطرف المستقبل، يقوم بعملية عكسية للمُجمّع. يفصل الإشارة المركبة مرة أخرى إلى الأطوال الموجية الفردية (الألوان) المكونة لها، ويوجه كل طول موجي إلى جهاز Transponder خاص به.">
                                        <span class="text-4xl">🚥</span>
                                        <p class="font-semibold text-sm">DEMUX</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div id="component-info-box" class="bg-blue-50 p-4 rounded-lg min-h-[200px]">
                            <h3 id="component-title" class="text-2xl font-bold text-blue-700 mb-2">انقر على مكون</h3>
                            <p id="component-detail" class="text-slate-700">مرر مؤشر الفأرة وانقر على أي مكون في المخطط على اليسار لعرض وظيفته التفصيلية هنا.</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Design Panel -->
            <section id="design" class="panel">
                 <div class="bg-white p-6 rounded-lg shadow-md">
                    <h2 class="text-3xl font-bold mb-4 text-slate-800">تصميم وهندسة شبكات DWDM</h2>
                    <p class="mb-6 text-slate-600 leading-relaxed">
                        تعمق في الجانب العملي لهندسة DWDM. هذا القسم يغطي الطوبولوجيا المختلفة للشبكات ويقارن بينها، ويوفر أداة تفاعلية لحساب "ميزانية الطاقة"، وهي خطوة حيوية لضمان وصول الإشارة بسلامة عبر مسافات طويلة. جرب تغيير المعلمات لترى كيف تؤثر على تصميم الرابط.
                    </p>

                    <div class="grid md:grid-cols-2 gap-8">
                        <div>
                             <h3 class="text-2xl font-semibold mb-4 text-blue-600">طوبولوجيا الشبكات</h3>
                             <div class="space-y-4">
                                <div class="accordion-item bg-slate-50 rounded-lg">
                                    <button class="accordion-header w-full p-4 text-right font-semibold flex justify-between items-center">
                                        <span>نقطة إلى نقطة (Point-to-Point)</span>
                                        <span class="text-xl transition-transform duration-300">▼</span>
                                    </button>
                                    <div class="accordion-content px-4 pb-4 text-slate-600">
                                        <p>أبسط تصميم، يربط بين موقعين مباشرة. مثالي للروابط عالية السعة بين مراكز البيانات (DCI) أو المدن. يتميز بأقصى استفادة من سعة الألياف ولكنه يفتقر إلى التكرار الذاتي.</p>
                                    </div>
                                </div>
                                <div class="accordion-item bg-slate-50 rounded-lg">
                                    <button class="accordion-header w-full p-4 text-right font-semibold flex justify-between items-center">
                                        <span>حلقية (Ring)</span>
                                        <span class="text-xl transition-transform duration-300">▼</span>
                                    </button>
                                    <div class="accordion-content px-4 pb-4 text-slate-600">
                                        <p>تربط عدة مواقع في حلقة، وتوفر مسارًا بديلاً في حالة انقطاع الألياف، مما يمنحها قدرة عالية على تحمل الأخطاء (self-healing). شائعة جدًا في شبكات المترو والشبكات الأساسية.</p>
                                    </div>
                                </div>
                                 <div class="accordion-item bg-slate-50 rounded-lg">
                                    <button class="accordion-header w-full p-4 text-right font-semibold flex justify-between items-center">
                                        <span>شبكية (Mesh)</span>
                                         <span class="text-xl transition-transform duration-300">▼</span>
                                    </button>
                                    <div class="accordion-content px-4 pb-4 text-slate-600">
                                        <p>التصميم الأكثر مرونة وموثوقية، حيث توجد مسارات متعددة بين المواقع. توفر أعلى درجات الحماية ولكنها الأكثر تكلفة وتعقيدًا في الإدارة. تستخدم في الشبكات الأساسية الحيوية.</p>
                                    </div>
                                </div>
                             </div>
                        </div>

                        <div class="bg-slate-100 p-6 rounded-lg">
                            <h3 class="text-2xl font-semibold mb-4 text-center">حاسبة ميزانية الطاقة التفاعلية</h3>
                            <form id="power-budget-form">
                                <div class="mb-4">
                                    <label for="distance" class="block mb-1 font-medium">مسافة الرابط (كم): <span id="distance-val" class="text-blue-600 font-bold">80</span></label>
                                    <input type="range" id="distance" min="10" max="200" value="80" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer">
                                </div>
                                <div class="mb-4">
                                    <label for="attenuation" class="block mb-1 font-medium">فقدان الألياف (dB/km): <span id="attenuation-val" class="text-blue-600 font-bold">0.25</span></label>
                                    <input type="range" id="attenuation" min="0.15" max="0.5" value="0.25" step="0.01" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer">
                                </div>
                                <div class="mb-4">
                                    <label for="component-loss" class="block mb-1 font-medium">فقدان المكونات (Mux/Demux, Connectors) (dB): <span id="component-loss-val" class="text-blue-600 font-bold">5.5</span></label>
                                    <input type="range" id="component-loss" min="2" max="10" value="5.5" step="0.1" class="w-full h-2 bg-slate-200 rounded-lg appearance-none cursor-pointer">
                                </div>
                            </form>
                            <div class="mt-6 text-center">
                                <p class="text-lg">إجمالي فقدان الرابط: <strong id="total-loss" class="text-red-600">25.5 dB</strong></p>
                                <p class="text-lg">هامش النظام المتبقي: <strong id="system-margin" class="text-green-600">-2.5 dB</strong></p>
                                <p id="conclusion" class="mt-2 font-semibold text-red-700">تحذير: النظام سيفشل! فقدان الرابط يتجاوز الميزانية المتاحة.</p>
                            </div>
                        </div>

                    </div>
                 </div>
            </section>
            
            <!-- Apps & Standards Panel -->
            <section id="apps" class="panel">
                <div class="bg-white p-6 rounded-lg shadow-md">
                    <h2 class="text-3xl font-bold mb-4 text-slate-800">التطبيقات، المعايير، والاقتصاديات</h2>
                    <p class="mb-6 text-slate-600 leading-relaxed">
                       أين تُستخدم تقنية DWDM في عالمنا اليوم، وما هي القواعد التي تحكمها؟ يستعرض هذا القسم أبرز تطبيقات DWDM من شبكات الجيل الخامس (5G) إلى ربط مراكز البيانات العملاقة. كما يسلط الضوء على المعايير الدولية التي تضمن عمل الأجهزة مع بعضها البعض، والفوائد الاقتصادية التي تجعل هذه التقنية استثماراً ذكياً.
                    </p>
                     <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-4 text-center">
                        <div class="bg-slate-100 p-4 rounded-lg">
                            <span class="text-4xl">📡</span>
                            <h4 class="font-bold text-lg mt-2">شبكات 5G</h4>
                            <p class="text-sm text-slate-600">توفر السعة الهائلة المطلوبة لدعم شبكات الجيل الخامس.</p>
                        </div>
                        <div class="bg-slate-100 p-4 rounded-lg">
                            <span class="text-4xl">🏢</span>
                            <h4 class="font-bold text-lg mt-2">ربط مراكز البيانات (DCI)</h4>
                            <p class="text-sm text-slate-600">تربط مراكز البيانات بسرعات فائقة وزمن وصول منخفض.</p>
                        </div>
                        <div class="bg-slate-100 p-4 rounded-lg">
                            <span class="text-4xl">🏙️</span>
                            <h4 class="font-bold text-lg mt-2">شبكات المترو والأساسية</h4>
                            <p class="text-sm text-slate-600">تشكل العمود الفقري لشبكات الاتصالات داخل المدن وبينها.</p>
                        </div>
                         <div class="bg-slate-100 p-4 rounded-lg">
                            <span class="text-4xl">📈</span>
                            <h4 class="font-bold text-lg mt-2">الفوائد الاقتصادية</h4>
                            <p class="text-sm text-slate-600">تقلل النفقات الرأسمالية (CAPEX) والتشغيلية (OPEX).</p>
                        </div>
                    </div>

                    <div class="mt-8">
                        <h3 class="text-2xl font-semibold mb-3 text-blue-600">المعايير الحاكمة</h3>
                        <p>تضمن المعايير الدولية من منظمات مثل <strong class="font-semibold">ITU-T</strong> و <strong class="font-semibold">IEEE</strong> أن أجهزة DWDM من مختلف المصنعين يمكنها العمل معًا بسلاسة. أهم معيار هو <strong class="font-semibold">ITU-T G.694.1</strong> الذي يحدد "شبكة الترددات" أو القنوات المسموح بها، مما يمنع التداخل بين الإشارات.</p>
                    </div>

                </div>
            </section>

            <!-- Interactive Lab Panel -->
            <section id="lab" class="panel">
                <div class="bg-white p-6 rounded-lg shadow-md">
                    <h2 class="text-3xl font-bold mb-4 text-slate-800">المختبر التفاعلي</h2>
                    <p class="mb-8 text-slate-600 leading-relaxed">
                        حان وقت التطبيق العملي! هذا المختبر هو مساحتك لتجربة المفاهيم التي تعلمتها. استخدم الأدوات التفاعلية أدناه لفهم أعمق لكيفية تأثير قرارات التصميم على أداء الشبكة. ابدأ بمتخيل خطط القنوات لترى كيف يؤثر تباعد القنوات على السعة.
                    </p>
                    <div class="bg-slate-100 p-6 rounded-lg">
                        <h3 class="text-2xl font-semibold mb-4 text-center">متخيل خطط القنوات (Channel Plan Visualizer)</h3>
                        <div class="max-w-md mx-auto mb-4">
                            <label for="channel-spacing" class="block text-center mb-2 font-medium">اختر تباعد القنوات:</label>
                            <select id="channel-spacing" class="w-full p-2 border border-slate-300 rounded-md">
                                <option value="100">100 GHz (0.8 nm) - قياسي</option>
                                <option value="50">50 GHz (0.4 nm) - كثيف</option>
                                <option value="25">25 GHz (0.2 nm) - فائق الكثافة</option>
                            </select>
                        </div>
                        <div class="chart-container h-[400px] max-h-[500px]">
                            <canvas id="channel-plan-chart"></canvas>
                        </div>
                    </div>
                </div>
            </section>

        </main>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            // Tab navigation
            const tabs = document.querySelectorAll('.tab-btn');
            const panels = document.querySelectorAll('.panel');

            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    tabs.forEach(t => t.classList.remove('tab-active'));
                    tab.classList.add('tab-active');

                    panels.forEach(panel => {
                        panel.classList.remove('active');
                    });
                    
                    const targetPanel = document.getElementById(tab.dataset.tab);
                    targetPanel.classList.add('active');
                });
            });
            
            // Comparison table interaction
            const comparisonTableRows = document.querySelectorAll('#comparison-table tr');
            const detailBox = document.getElementById('comparison-detail');
            comparisonTableRows.forEach(row => {
                row.addEventListener('click', () => {
                    detailBox.textContent = row.dataset.detail;
                });
            });
            // Set initial detail
            if (comparisonTableRows.length > 0) {
                 detailBox.textContent = comparisonTableRows[0].dataset.detail;
            }

            // Component diagram interaction
            const components = document.querySelectorAll('.component');
            const infoTitle = document.getElementById('component-title');
            const infoDetail = document.getElementById('component-detail');

            components.forEach(component => {
                component.addEventListener('click', () => {
                    infoTitle.textContent = component.dataset.info;
                    infoDetail.textContent = component.dataset.detail;
                });
            });

            // Accordion for topologies
            const accordionHeaders = document.querySelectorAll('.accordion-header');
            accordionHeaders.forEach(header => {
                header.addEventListener('click', () => {
                    const content = header.nextElementSibling;
                    const icon = header.querySelector('span:last-child');
                    
                    if (content.style.maxHeight) {
                        content.style.maxHeight = null;
                        icon.style.transform = 'rotate(0deg)';
                    } else {
                        // Close other accordions
                        document.querySelectorAll('.accordion-content').forEach(c => c.style.maxHeight = null);
                         document.querySelectorAll('.accordion-header span:last-child').forEach(i => i.style.transform = 'rotate(0deg)');
                        
                        content.style.maxHeight = content.scrollHeight + 'px';
                        icon.style.transform = 'rotate(180deg)';
                    }
                });
            });

            // Power Budget Calculator
            const form = document.getElementById('power-budget-form');
            const distanceInput = document.getElementById('distance');
            const attenuationInput = document.getElementById('attenuation');
            const componentLossInput = document.getElementById('component-loss');

            const distanceVal = document.getElementById('distance-val');
            const attenuationVal = document.getElementById('attenuation-val');
            const componentLossVal = document.getElementById('component-loss-val');

            const totalLossEl = document.getElementById('total-loss');
            const systemMarginEl = document.getElementById('system-margin');
            const conclusionEl = document.getElementById('conclusion');
            
            const transceiverBudget = 23; // dB, a typical value for many transceivers

            function calculatePowerBudget() {
                const distance = parseFloat(distanceInput.value);
                const attenuation = parseFloat(attenuationInput.value);
                const componentLoss = parseFloat(componentLossInput.value);

                distanceVal.textContent = distance;
                attenuationVal.textContent = attenuation;
                componentLossVal.textContent = componentLoss.toFixed(1);

                const fiberLoss = distance * attenuation;
                const totalLoss = fiberLoss + componentLoss;
                const margin = transceiverBudget - totalLoss;

                totalLossEl.textContent = `${totalLoss.toFixed(2)} dB`;
                systemMarginEl.textContent = `${margin.toFixed(2)} dB`;
                
                if (margin >= 3) {
                    systemMarginEl.className = 'text-green-600 font-bold';
                    conclusionEl.textContent = 'ممتاز: النظام لديه هامش أمان جيد.';
                    conclusionEl.className = 'mt-2 font-semibold text-green-700';
                } else if (margin >= 0) {
                     systemMarginEl.className = 'text-yellow-600 font-bold';
                     conclusionEl.textContent = 'مقبول: النظام سيعمل، لكن هامش الأمان ضئيل.';
                     conclusionEl.className = 'mt-2 font-semibold text-yellow-700';
                } else {
                     systemMarginEl.className = 'text-red-600 font-bold';
                     conclusionEl.textContent = 'تحذير: النظام سيفشل! فقدان الرابط يتجاوز الميزانية.';
                     conclusionEl.className = 'mt-2 font-semibold text-red-700';
                }
            }

            form.addEventListener('input', calculatePowerBudget);
            calculatePowerBudget(); // Initial calculation

            // Channel Plan Visualizer
            const spacingSelect = document.getElementById('channel-spacing');
            const ctx = document.getElementById('channel-plan-chart').getContext('2d');
            let channelChart;
            const cBandStart = 1529; // nm
            const cBandEnd = 1566; // nm

            function createChannelChart(spacingGHz) {
                const spacingNm = spacingGHz === 100 ? 0.8 : (spacingGHz === 50 ? 0.4 : 0.2);
                const numChannels = Math.floor((cBandEnd - cBandStart) / spacingNm);
                
                const labels = Array.from({ length: numChannels }, (_, i) => (cBandStart + i * spacingNm).toFixed(2));
                const data = Array(numChannels).fill(10);
                
                const backgroundColors = data.map((_, i) => `hsl(${(i * 360 / numChannels)}, 70%, 60%)`);

                if (channelChart) {
                    channelChart.destroy();
                }
                
                channelChart = new Chart(ctx, {
                    type: 'bar',
                    data: {
                        labels: labels,
                        datasets: [{
                            label: `قنوات DWDM (تباعد ${spacingGHz} GHz)`,
                            data: data,
                            backgroundColor: backgroundColors,
                            borderColor: backgroundColors,
                            borderWidth: 1,
                            barPercentage: 1.0,
                            categoryPercentage: 1.0,
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: {
                                display: true,
                                labels:{
                                  font:{
                                    size: 14,
                                    family: 'Tajawal'
                                  }
                                }
                            },
                            tooltip: {
                                callbacks: {
                                    title: function(context) {
                                        return `القناة عند ${context[0].label} nm`;
                                    },
                                    label: function() {
                                        return '';
                                    }
                                }
                            }
                        },
                        scales: {
                            x: {
                                title: {
                                    display: true,
                                    text: 'الطول الموجي (nm)',
                                     font:{
                                        size: 14,
                                        family: 'Tajawal'
                                    }
                                },
                                ticks:{
                                  maxRotation: 90,
                                  minRotation: 70,
                                  font:{
                                      size: 10
                                  }
                                }
                            },
                            y: {
                                display: false,
                                beginAtZero: true
                            }
                        }
                    }
                });
            }

            spacingSelect.addEventListener('change', (e) => {
                createChannelChart(parseInt(e.target.value));
            });

            // Initial chart
            createChannelChart(100);

        });
    </script>
</body>
</html>
# raed-almsari
