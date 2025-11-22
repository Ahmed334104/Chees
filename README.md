# Chees
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>شطرنجي - تعلم الشطرنج من الصفر للاحتراف</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/chess.js/0.10.3/chess.min.js"></script>
    <style>
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --light-color: #ecf0f1;
            --dark-color: #2c3e50;
            --success-color: #2ecc71;
            --warning-color: #f39c12;
            --border-radius: 8px;
            --box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f5f5f5;
            color: var(--dark-color);
            line-height: 1.6;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* رأس الصفحة */
        header {
            background-color: var(--primary-color);
            color: white;
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: var(--box-shadow);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }

        .logo i {
            margin-left: 10px;
            color: var(--secondary-color);
        }

        nav ul {
            display: flex;
            list-style: none;
        }

        nav ul li {
            margin-right: 20px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: var(--transition);
            padding: 5px 10px;
            border-radius: var(--border-radius);
        }

        nav ul li a:hover {
            color: var(--secondary-color);
            background-color: rgba(255, 255, 255, 0.1);
        }

        .auth-buttons {
            display: flex;
            gap: 10px;
        }

        .btn {
            padding: 8px 16px;
            border: none;
            border-radius: var(--border-radius);
            cursor: pointer;
            font-weight: 500;
            transition: var(--transition);
        }

        .btn-primary {
            background-color: var(--secondary-color);
            color: white;
        }

        .btn-primary:hover {
            background-color: #2980b9;
            transform: translateY(-2px);
        }

        .btn-outline {
            background-color: transparent;
            color: white;
            border: 1px solid white;
        }

        .btn-outline:hover {
            background-color: white;
            color: var(--primary-color);
        }

        .btn-success {
            background-color: var(--success-color);
            color: white;
        }

        .btn-warning {
            background-color: var(--warning-color);
            color: white;
        }

        .btn-danger {
            background-color: var(--accent-color);
            color: white;
        }

        /* قسم البطل */
        .hero {
            background: linear-gradient(135deg, var(--primary-color), #1a2530);
            color: white;
            padding: 4rem 0;
            text-align: center;
        }

        .hero-content h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .hero-content p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
        }

        .hero-buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 2rem;
        }

        .btn-large {
            padding: 12px 24px;
            font-size: 1.1rem;
        }

        /* الأقسام الرئيسية */
        section {
            padding: 4rem 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }

        .section-title h2 {
            font-size: 2rem;
            color: var(--primary-color);
            display: inline-block;
            padding-bottom: 10px;
        }

        .section-title h2::after {
            content: '';
            position: absolute;
            width: 80px;
            height: 3px;
            background-color: var(--secondary-color);
            bottom: 0;
            right: 50%;
            transform: translateX(50%);
        }

        /* قسم المستويات */
        .levels {
            background-color: white;
        }

        .levels-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .level-card {
            background-color: white;
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
            transition: var(--transition);
        }

        .level-card:hover {
            transform: translateY(-10px);
        }

        .level-header {
            padding: 20px;
            color: white;
            text-align: center;
        }

        .beginner .level-header {
            background-color: var(--success-color);
        }

        .intermediate .level-header {
            background-color: var(--warning-color);
        }

        .advanced .level-header {
            background-color: var(--secondary-color);
        }

        .expert .level-header {
            background-color: var(--accent-color);
        }

        .level-body {
            padding: 20px;
        }

        .level-body ul {
            list-style: none;
            margin-bottom: 20px;
        }

        .level-body ul li {
            padding: 8px 0;
            border-bottom: 1px solid #eee;
            position: relative;
            padding-right: 25px;
        }

        .level-body ul li::before {
            content: '✓';
            position: absolute;
            right: 0;
            color: var(--success-color);
            font-weight: bold;
        }

        /* قسم الميزات */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
        }

        .feature-card {
            background-color: white;
            padding: 30px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            text-align: center;
            transition: var(--transition);
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }

        .feature-icon {
            font-size: 3rem;
            color: var(--secondary-color);
            margin-bottom: 20px;
        }

        /* قسم لوحة الشطرنج التفاعلية */
        .chess-board-section {
            background-color: white;
        }

        .chess-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
        }

        .chess-board-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .chess-board {
            width: 400px;
            height: 400px;
            display: grid;
            grid-template-columns: repeat(8, 1fr);
            grid-template-rows: repeat(8, 1fr);
            border: 2px solid var(--dark-color);
            box-shadow: var(--box-shadow);
            margin-bottom: 20px;
        }

        .chess-square {
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 30px;
            cursor: pointer;
            transition: var(--transition);
            position: relative;
        }

        .white {
            background-color: #f0d9b5;
        }

        .black {
            background-color: #b58863;
        }

        .chess-square.selected {
            background-color: rgba(52, 152, 219, 0.5);
        }

        .chess-square.valid-move::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background-color: rgba(46, 204, 113, 0.5);
        }

        .chess-square.capture::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            border: 3px solid rgba(231, 76, 60, 0.7);
            border-radius: 50%;
        }

        .chess-controls {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-bottom: 20px;
        }

        .chess-info {
            background-color: white;
            padding: 20px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            width: 400px;
            max-height: 400px;
            overflow-y: auto;
        }

        .move-history {
            margin-bottom: 20px;
        }

        .move-list {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 5px;
            margin-top: 10px;
        }

        .move-item {
            padding: 5px;
            border-radius: 4px;
            cursor: pointer;
        }

        .move-item:hover {
            background-color: #f0f0f0;
        }

        .move-item.current {
            background-color: var(--secondary-color);
            color: white;
        }

        .analysis-result {
            background-color: #f8f9fa;
            padding: 15px;
            border-radius: var(--border-radius);
            margin-top: 15px;
        }

        /* قسم الدروس التفاعلية */
        .interactive-lessons {
            background-color: #f9f9f9;
        }

        .lessons-container {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 30px;
        }

        .lessons-sidebar {
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            padding: 20px;
            max-height: 500px;
            overflow-y: auto;
        }

        .lesson-item {
            padding: 15px;
            border-bottom: 1px solid #eee;
            cursor: pointer;
            transition: var(--transition);
        }

        .lesson-item:hover {
            background-color: #f0f0f0;
        }

        .lesson-item.active {
            background-color: var(--secondary-color);
            color: white;
        }

        .lesson-content {
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            padding: 30px;
        }

        .lesson-title {
            margin-bottom: 20px;
            color: var(--primary-color);
        }

        .lesson-video {
            width: 100%;
            height: 300px;
            background-color: #ddd;
            border-radius: var(--border-radius);
            margin-bottom: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #777;
        }

        .lesson-exercises {
            margin-top: 30px;
        }

        .exercise-item {
            background-color: #f8f9fa;
            padding: 15px;
            border-radius: var(--border-radius);
            margin-bottom: 15px;
            cursor: pointer;
            transition: var(--transition);
        }

        .exercise-item:hover {
            background-color: #e9ecef;
        }

        /* قسم نظام المستخدم */
        .user-system {
            background-color: white;
        }

        .user-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

        .user-form {
            background-color: white;
            padding: 30px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: var(--border-radius);
            font-size: 1rem;
        }

        .user-stats {
            background-color: white;
            padding: 30px;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
            margin-top: 20px;
        }

        .stat-card {
            background-color: #f8f9fa;
            padding: 20px;
            border-radius: var(--border-radius);
            text-align: center;
        }

        .stat-value {
            font-size: 2rem;
            font-weight: bold;
            color: var(--secondary-color);
        }

        .progress-bar {
            height: 10px;
            background-color: #e9ecef;
            border-radius: 5px;
            margin-top: 10px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background-color: var(--success-color);
            border-radius: 5px;
        }

        /* قسم المدونة */
        .blog-preview {
            background-color: #f9f9f9;
        }

        .blog-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .blog-card {
            background-color: white;
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
        }

        .blog-image {
            height: 200px;
            background-color: #ddd;
            background-size: cover;
            background-position: center;
        }

        .blog-content {
            padding: 20px;
        }

        .blog-content h3 {
            margin-bottom: 10px;
            color: var(--primary-color);
        }

        .blog-meta {
            display: flex;
            justify-content: space-between;
            color: #777;
            font-size: 0.9rem;
            margin-bottom: 15px;
        }

        /* تذييل الصفحة */
        footer {
            background-color: var(--primary-color);
            color: white;
            padding: 3rem 0 1rem;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            margin-bottom: 2rem;
        }

        .footer-column h3 {
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
        }

        .footer-column h3::after {
            content: '';
            position: absolute;
            width: 40px;
            height: 2px;
            background-color: var(--secondary-color);
            bottom: 0;
            right: 0;
        }

        .footer-column ul {
            list-style: none;
        }

        .footer-column ul li {
            margin-bottom: 10px;
        }

        .footer-column ul li a {
            color: #ddd;
            text-decoration: none;
            transition: var(--transition);
        }

        .footer-column ul li a:hover {
            color: var(--secondary-color);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* تصميم متجاوب */
        @media (max-width: 992px) {
            .lessons-container, .user-container {
                grid-template-columns: 1fr;
            }
            
            .chess-info {
                width: 100%;
                max-width: 400px;
            }
        }

        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }

            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }

            .hero-content h1 {
                font-size: 2rem;
            }

            .hero-buttons {
                flex-direction: column;
                align-items: center;
            }

            .chess-board {
                width: 300px;
                height: 300px;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
        }

        /* نمط الإشعارات */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            background-color: var(--success-color);
            color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            z-index: 1100;
            transform: translateX(150%);
            transition: transform 0.3s ease;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.error {
            background-color: var(--accent-color);
        }

        .notification.warning {
            background-color: var(--warning-color);
        }
    </style>
</head>
<body>
    <!-- رأس الصفحة -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <i class="fas fa-chess-knight"></i>
                <span>شطرنجي</span>
            </div>
            <nav>
                <ul>
                    <li><a href="#home">الرئيسية</a></li>
                    <li><a href="#levels">المستويات</a></li>
                    <li><a href="#lessons">الدروس</a></li>
                    <li><a href="#practice">التدريب</a></li>
                    <li><a href="#user">حسابي</a></li>
                    <li><a href="#blog">المدونة</a></li>
                </ul>
            </nav>
            <div class="auth-buttons">
                <button class="btn btn-outline" id="loginBtn">تسجيل الدخول</button>
                <button class="btn btn-primary" id="registerBtn">إنشاء حساب</button>
            </div>
        </div>
    </header>

    <!-- قسم البطل -->
    <section class="hero" id="home">
        <div class="container hero-content">
            <h1>ارتقِ بمهاراتك في الشطرنج من الصفر إلى الاحتراف</h1>
            <p>موقع متكامل لتعلم الشطرنج خطوة بخطوة، مع دروس تفاعلية، تمارين عملية، وتحديات تناسب جميع المستويات.</p>
            <div class="hero-buttons">
                <button class="btn btn-primary btn-large" id="startJourneyBtn">ابدأ رحلتك الآن</button>
                <button class="btn btn-outline btn-large" id="exploreLessonsBtn">استكشاف الدروس</button>
            </div>
        </div>
    </section>

    <!-- قسم المستويات -->
    <section class="levels" id="levels">
        <div class="container">
            <div class="section-title">
                <h2>مستويات التعلم</h2>
            </div>
            <div class="levels-grid">
                <div class="level-card beginner">
                    <div class="level-header">
                        <h3>المبتدئ</h3>
                    </div>
                    <div class="level-body">
                        <p>ابدأ رحلتك في عالم الشطرنج بتعلم الأساسيات</p>
                        <ul>
                            <li>تعرف على قطع الشطرنج وحركاتها</li>
                            <li>فهم قواعد اللعبة الأساسية</li>
                            <li>مبادئ الافتتاحيات البسيطة</li>
                            <li>تعلم كيفية كش ملك</li>
                            <li>تمارين على المبتدئين</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;">ابدأ المستوى</button>
                    </div>
                </div>
                <div class="level-card intermediate">
                    <div class="level-header">
                        <h3>المتوسط</h3>
                    </div>
                    <div class="level-body">
                        <p>تطوير مهاراتك وفهمك الاستراتيجي للعبة</p>
                        <ul>
                            <li>استراتيجيات الافتتاحيات المتقدمة</li>
                            <li>التكتيكات والهجمات المزدوجة</li>
                            <li>مبادئ وسط اللعبة</li>
                            <li>الأسس الأساسية لنهاية اللعبة</li>
                            <li>تحليل الأخطاء الشائعة</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;">ابدأ المستوى</button>
                    </div>
                </div>
                <div class="level-card advanced">
                    <div class="level-header">
                        <h3>المتقدم</h3>
                    </div>
                    <div class="level-body">
                        <p>احتراف التخطيط الاستراتيجي والتنفيذ التكتيكي</p>
                        <ul>
                            <li>استراتيجيات متقدمة للافتتاحيات</li>
                            <li>التخطيط طويل المدى</li>
                            <li>تقنيات نهاية اللعبة المعقدة</li>
                            <li>دراسة مباريات الأساتذة الكبار</li>
                            <li>تحليل المواقف المعقدة</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;">ابدأ المستوى</button>
                    </div>
                </div>
                <div class="level-card expert">
                    <div class="level-header">
                        <h3>المحترف</h3>
                    </div>
                    <div class="level-body">
                        <p>إتقان فن الشطرنج والمنافسة على أعلى المستويات</p>
                        <ul>
                            <li>إعداد الافتتاحيات الشخصية</li>
                            <li>التكتيكات المتقدمة والتركيبات</li>
                            <li>التحضير للمنافسات</li>
                            <li>علم النفس في الشطرنج</li>
                            <li>تحليل مبارياتك باستخدام المحركات</li>
                        </ul>
                        <button class="btn btn-primary" style="width: 100%;">ابدأ المستوى</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- قسم الدروس التفاعلية -->
    <section class="interactive-lessons" id="lessons">
        <div class="container">
            <div class="section-title">
                <h2>الدروس التفاعلية</h2>
            </div>
            <div class="lessons-container">
                <div class="lessons-sidebar">
                    <div class="lesson-item active" data-lesson="1">
                        <h4>مقدمة في الشطرنج</h4>
                        <p>تعرف على أساسيات اللعبة</p>
                    </div>
                    <div class="lesson-item" data-lesson="2">
                        <h4>حركات القطع</h4>
                        <p>كيف تتحرك كل قطعة على الرقعة</p>
                    </div>
                    <div class="lesson-item" data-lesson="3">
                        <h4>الاستراتيجيات الأساسية</h4>
                        <p>مبادئ التخطيط في الشطرنج</p>
                    </div>
                    <div class="lesson-item" data-lesson="4">
                        <h4>الافتتاحيات الشهيرة</h4>
                        <p>أشهر استراتيجيات بداية اللعبة</p>
                    </div>
                    <div class="lesson-item" data-lesson="5">
                        <h4>نهاية اللعبة</h4>
                        <p>تقنيات إنهاء المباراة بفوز</p>
                    </div>
                </div>
                <div class="lesson-content">
                    <h3 class="lesson-title" id="currentLessonTitle">مقدمة في الشطرنج</h3>
                    <div class="lesson-video" id="lessonVideo">
                        <i class="fas fa-play-circle" style="font-size: 4rem; color: #777;"></i>
                        <p>في النسخة الكاملة، سيكون هنا فيديو تعليمي</p>
                    </div>
                    <div class="lesson-text" id="lessonText">
                        <p>الشطرنج هي لعبة استراتيجية تلعب على رقعة مربعة مقسمة إلى 64 مربعًا بلونين متبادلين. يلعبها لاعبان، يتحكمان بمجموعة من القطع، كل لاعب يملك 16 قطعة: ملك، وزير، قلعتان، حصانان، فيلان، وثمانية جنود.</p>
                        <p>الهدف من اللعبة هو إماتة ملك الخصم، أي وضعه في وضعية لا يستطيع فيها الهروب من التهديد (كش ملك).</p>
                    </div>
                    <div class="lesson-exercises">
                        <h4>تمارين الدرس</h4>
                        <div class="exercise-item" data-exercise="1">
                            <p>تمرين 1: تحديد مواقع القطع على الرقعة</p>
                        </div>
                        <div class="exercise-item" data-exercise="2">
                            <p>تمرين 2: فهم حركات القطع الأساسية</p>
                        </div>
                        <div class="exercise-item" data-exercise="3">
                            <p>تمرين 3: التعرف على وضعية كش ملك</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- قسم لوحة الشطرنج التفاعلية -->
    <section class="chess-board-section" id="practice">
        <div class="container">
            <div class="section-title">
                <h2>لوحة شطرنج تفاعلية</h2>
            </div>
            <div class="chess-container">
                <div class="chess-board-container">
                    <div class="chess-controls">
                        <button class="btn btn-primary" id="resetBoard">إعادة الضبط</button>
                        <button class="btn btn-success" id="hintBtn">تلميح</button>
                        <button class="btn btn-warning" id="analyzeBtn">تحليل النقلة</button>
                        <button class="btn btn-danger" id="undoBtn">تراجع</button>
                        <button class="btn btn-outline" id="flipBoard">قلب الرقعة</button>
                    </div>
                    <div class="chess-board" id="chessBoard">
                        <!-- سيتم إنشاء لوحة الشطرنج بالجافاسكريبت -->
                    </div>
                    <div class="game-status" id="gameStatus">
                        <p>حالة اللعبة: <span id="statusText">جاهز للعب</span></p>
                    </div>
                </div>
                <div class="chess-info">
                    <div class="move-history">
                        <h4>سجل النقلات</h4>
                        <div class="move-list" id="moveList">
                            <!-- سجل النقلات سيتم إنشاؤه ديناميكيًا -->
                        </div>
                    </div>
                    <div class="analysis-result" id="analysisResult">
                        <h4>نتيجة التحليل</h4>
                        <p id="analysisText">سيظهر هنا تحليل للنقلة الحالية</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- قسم نظام المستخدم -->
    <section class="user-system" id="user">
        <div class="container">
            <div class="section-title">
                <h2>نظام المستخدم</h2>
            </div>
            <div class="user-container">
                <div class="user-form">
                    <h3>إنشاء حساب جديد</h3>
                    <form id="registerForm">
                        <div class="form-group">
                            <label for="username">اسم المستخدم</label>
                            <input type="text" id="username" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="email">البريد الإلكتروني</label>
                            <input type="email" id="email" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="password">كلمة المرور</label>
                            <input type="password" id="password" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="confirmPassword">تأكيد كلمة المرور</label>
                            <input type="password" id="confirmPassword" class="form-control" required>
                        </div>
                        <button type="submit" class="btn btn-primary" style="width: 100%;">إنشاء حساب</button>
                    </form>
                    <div class="login-link" style="margin-top: 20px; text-align: center;">
                        <p>هل لديك حساب بالفعل؟ <a href="#" id="showLoginForm">تسجيل الدخول</a></p>
                    </div>
                </div>
                <div class="user-stats">
                    <h3>إحصائياتك</h3>
                    <p>تابع تقدمك في تعلم الشطرنج</p>
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-value" id="completedLessons">0</div>
                            <div class="stat-label">دروس مكتملة</div>
                            <div class="progress-bar">
                                <div class="progress-fill" style="width: 0%;" id="lessonsProgress"></div>
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="solvedExercises">0</div>
                            <div class="stat-label">تمارين محلولة</div>
                            <div class="progress-bar">
                                <div class="progress-fill" style="width: 0%;" id="exercisesProgress"></div>
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="gamesPlayed">0</div>
                            <div class="stat-label">مباريات ملعوبة</div>
                            <div class="progress-bar">
                                <div class="progress-fill" style="width: 0%;" id="gamesProgress"></div>
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="currentLevel">مبتدئ</div>
                            <div class="stat-label">مستواك الحالي</div>
                            <div class="progress-bar">
                                <div class="progress-fill" style="width: 25%;" id="levelProgress"></div>
                            </div>
                        </div>
                    </div>
                    <div class="achievements" style="margin-top: 30px;">
                        <h4>إنجازاتك</h4>
                        <div id="achievementsList">
                            <p>لا توجد إنجازات حتى الآن. استمر في التعلم لكسب الإنجازات!</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- قسم المدونة -->
    <section class="blog-preview" id="blog">
        <div class="container">
            <div class="section-title">
                <h2>أحدث المقالات</h2>
            </div>
            <div class="blog-grid">
                <div class="blog-card">
                    <div class="blog-image" style="background-color: #3498db;"></div>
                    <div class="blog-content">
                        <h3>أفضل 5 افتتاحيات للمبتدئين في الشطرنج</h3>
                        <div class="blog-meta">
                            <span>بواسطة: أحمد الشطرنجي</span>
                            <span>15 مايو 2023</span>
                        </div>
                        <p>اكتشف أفضل الافتتاحيات التي يمكن للمبتدئين تعلمها لبناء أساس قوي في لعبة الشطرنج.</p>
                        <button class="btn btn-outline" style="margin-top: 15px;">اقرأ المزيد</button>
                    </div>
                </div>
                <div class="blog-card">
                    <div class="blog-image" style="background-color: #e74c3c;"></div>
                    <div class="blog-content">
                        <h3>كيف تتجنب الأخطاء الشائعة في نهاية اللعبة</h3>
                        <div class="blog-meta">
                            <span>بواسطة: فاطمة المحترفة</span>
                            <span>22 أبريل 2023</span>
                        </div>
                        <p>تعرف على الأخطاء الشائعة التي يرتكبها اللاعبون في نهاية اللعبة وكيفية تجنبها.</p>
                        <button class="btn btn-outline" style="margin-top: 15px;">اقرأ المزيد</button>
                    </div>
                </div>
                <div class="blog-card">
                    <div class="blog-image" style="background-color: #2ecc71;"></div>
                    <div class="blog-content">
                        <h3>أسرار التخطيط الاستراتيجي في وسط اللعبة</h3>
                        <div class="blog-meta">
                            <span>بواسطة: خالد الأستاذ</span>
                            <span>10 مارس 2023</span>
                        </div>
                        <p>تعلم كيفية تطوير خطط استراتيجية فعالة خلال مرحلة وسط اللعبة لتحقيق الأفضلية.</p>
                        <button class="btn btn-outline" style="margin-top: 15px;">اقرأ المزيد</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- تذييل الصفحة -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>شطرنجي</h3>
                    <p>منصة متكاملة لتعلم الشطرنج من الصفر إلى الاحتراف، نقدم دروسًا تفاعلية، تمارين عملية، ومجتمعًا نشطًا للاعبي الشطرنج.</p>
                </div>
                <div class="footer-column">
                    <h3>روابط سريعة</h3>
                    <ul>
                        <li><a href="#home">الرئيسية</a></li>
                        <li><a href="#levels">المستويات</a></li>
                        <li><a href="#lessons">الدروس</a></li>
                        <li><a href="#practice">التدريب</a></li>
                        <li><a href="#user">حسابي</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>الدعم</h3>
                    <ul>
                        <li><a href="#">الأسئلة الشائعة</a></li>
                        <li><a href="#">اتصل بنا</a></li>
                        <li><a href="#">الشروط والأحكام</a></li>
                        <li><a href="#">سياسة الخصوصية</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>تابعنا</h3>
                    <ul>
                        <li><a href="#"><i class="fab fa-facebook"></i> فيسبوك</a></li>
                        <li><a href="#"><i class="fab fa-twitter"></i> تويتر</a></li>
                        <li><a href="#"><i class="fab fa-instagram"></i> إنستغرام</a></li>
                        <li><a href="#"><i class="fab fa-youtube"></i> يوتيوب</a></li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <p>© 2023 شطرنجي. جميع الحقوق محفوظة.</p>
            </div>
        </div>
    </footer>

    <!-- إشعارات -->
    <div class="notification" id="notification">
        <span id="notificationText">هذا إشعار تجريبي</span>
    </div>

    <script>
        // نظام الإشعارات
        function showNotification(message, type = 'success') {
            const notification = document.getElementById('notification');
            const notificationText = document.getElementById('notificationText');
            
            notificationText.textContent = message;
            notification.className = 'notification ' + type;
            notification.classList.add('show');
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }

        // نظام المستخدمين
        document.getElementById('registerForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;
            const confirmPassword = document.getElementById('confirmPassword').value;
            
            if (password !== confirmPassword) {
                showNotification('كلمات المرور غير متطابقة!', 'error');
                return;
            }
            
            // في التطبيق الحقيقي، هنا سيتم إرسال البيانات للخادم
            showNotification('تم إنشاء حسابك بنجاح!', 'success');
            
            // تحديث إحصائيات المستخدم
            updateUserStats({
                completedLessons: 3,
                solvedExercises: 15,
                gamesPlayed: 8,
                currentLevel: 'مبتدئ'
            });
        });

        document.getElementById('showLoginForm').addEventListener('click', function(e) {
            e.preventDefault();
            showNotification('سيتم فتح نموذج تسجيل الدخول في النسخة الكاملة', 'warning');
        });

        // تحديث إحصائيات المستخدم
        function updateUserStats(stats) {
            document.getElementById('completedLessons').textContent = stats.completedLessons;
            document.getElementById('solvedExercises').textContent = stats.solvedExercises;
            document.getElementById('gamesPlayed').textContent = stats.gamesPlayed;
            document.getElementById('currentLevel').textContent = stats.currentLevel;
            
            // تحديث أشرطة التقدم
            document.getElementById('lessonsProgress').style.width = '30%';
            document.getElementById('exercisesProgress').style.width = '25%';
            document.getElementById('gamesProgress').style.width = '20%';
        }

        // نظام الدروس التفاعلية
        const lessonItems = document.querySelectorAll('.lesson-item');
        lessonItems.forEach(item => {
            item.addEventListener('click', function() {
                // إزالة النشاط من جميع الدروس
                lessonItems.forEach(i => i.classList.remove('active'));
                // إضافة النشاط للدرس المحدد
                this.classList.add('active');
                
                const lessonId = this.getAttribute('data-lesson');
                loadLesson(lessonId);
            });
        });

        function loadLesson(lessonId) {
            const lessonTitles = {
                1: 'مقدمة في الشطرنج',
                2: 'حركات القطع',
                3: 'الاستراتيجيات الأساسية',
                4: 'الافتتاحيات الشهيرة',
                5: 'نهاية اللعبة'
            };
            
            const lessonTexts = {
                1: '<p>الشطرنج هي لعبة استراتيجية تلعب على رقعة مربعة مقسمة إلى 64 مربعًا بلونين متبادلين. يلعبها لاعبان، يتحكمان بمجموعة من القطع، كل لاعب يملك 16 قطعة: ملك، وزير، قلعتان، حصانان، فيلان، وثمانية جنود.</p><p>الهدف من اللعبة هو إماتة ملك الخصم، أي وضعه في وضعية لا يستطيع فيها الهروب من التهديد (كش ملك).</p>',
                2: '<p>كل قطعة في الشطرنج تتحرك بطريقة مختلفة:</p><ul><li>الملك: يتححرك مربع واحد في أي اتجاه</li><li>الوزير: يتحرك أي عدد من المربعات في أي اتجاه</li><li>القلعة: تتحرك أي عدد من المربعات أفقياً أو عمودياً</li><li>الفيل: يتحرك أي عدد من المربعات قطرياً</li><li>الحصان: يتحرك على شكل حرف L</li><li>الجندي: يتحرك للأمام مربع واحد، ويأكل قطرياً</li></ul>',
                3: '<p>الاستراتيجيات الأساسية في الشطرنج تشمل:</p><ul><li>السيطرة على مركز الرقعة</li><li>تطوير القطع بسرعة</li><li>حماية الملك</li><li>إنشاء هيكل بيادق قوي</li><li>التخطيط طويل المدى</li></ul>',
                4: '<p>الافتتاحيات هي مجموعة النقلات الأولى في المباراة. من أشهر الافتتاحيات:</p><ul><li>الافتتاح الإسباني</li><li>دفاع صقلية</li><li>افتتاح الوزير</li><li>الدفاع الفرنسي</li><li>افتتاح الفيل</li></ul>',
                5: '<p>نهاية اللعبة هي المرحلة التي تبقى فيها عدد قليل من القطع على الرقعة. من أهم تقنيات نهاية اللعبة:</p><ul><li>تبييت الملك</li><li>ترقية البيادق</li><li>إنشاء ممر للبيادق</li><li>تقنية المربعات الرئيسية</li><li>التضحية بالقطع لتحقيق الفوز</li></ul>'
            };
            
            document.getElementById('currentLessonTitle').textContent = lessonTitles[lessonId];
            document.getElementById('lessonText').innerHTML = lessonTexts[lessonId];
            
            showNotification(تم تحميل درس: ${lessonTitles[lessonId]}, 'success');
        }

        // نظام لوحة الشطرنج
        document.addEventListener('DOMContentLoaded', function() {
            const chessBoard = document.getElementById('chessBoard');
            const files = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'];
            const initialPosition = [
                ['r', 'n', 'b', 'q', 'k', 'b', 'n', 'r'],
                ['p', 'p', 'p', 'p', 'p', 'p', 'p', 'p'],
                ['', '', '', '', '', '', '', ''],
                ['', '', '', '', '', '', '', ''],
                ['', '', '', '', '', '', '', ''],
                ['', '', '', '', '', '', '', ''],
                ['P', 'P', 'P', 'P', 'P', 'P', 'P', 'P'],
                ['R', 'N', 'B', 'Q', 'K', 'B', 'N', 'R']
            ];

            const pieceSymbols = {
                'r': '♜', 'n': '♞', 'b': '♝', 'q': '♛', 'k': '♚', 'p': '♟',
                'R': '♖', 'N': '♘', 'B': '♗', 'Q': '♕', 'K': '♔', 'P': '♙'
            };

            // إنشاء لوحة الشطرنج
            for (let row = 0; row < 8; row++) {
                for (let col = 0; col < 8; col++) {
                    const square = document.createElement('div');
                    square.className = chess-square ${(row + col) % 2 === 0 ? 'white' : 'black'};
                    square.dataset.row = row;
                    square.dataset.col = col;
                    
                    const piece = initialPosition[row][col];
                    if (piece) {
                        square.textContent = pieceSymbols[piece];
                        square.dataset.piece = piece;
                    }
                    
                    square.addEventListener('click', handleSquareClick);
                    chessBoard.appendChild(square);
                }
            }

            let selectedSquare = null;
            let moveHistory = [];
            let currentMoveIndex = -1;

            function handleSquareClick(event) {
                const square = event.currentTarget;
                const row = parseInt(square.dataset.row);
                const col = parseInt(square.dataset.col);
                
                if (selectedSquare) {
                    // إذا كان هناك مربع محدد مسبقًا، حاول نقل القطعة
                    const fromRow = parseInt(selectedSquare.dataset.row);
                    const fromCol = parseInt(selectedSquare.dataset.col);
                    const toRow = row;
                    const toCol = col;
                    
                    // محاكاة نقلة صحيحة (في التطبيق الحقيقي، نستخدم chess.js للتحقق)
                    if (isValidMove(fromRow, fromCol, toRow, toCol)) {
                        movePiece(selectedSquare, square);
                        
                        // تحديث سجل النقلات
                        const moveNotation = ${files[fromCol]}${8-fromRow} → ${files[toCol]}${8-toRow};
                        addMoveToHistory(moveNotation);
                        
                        // محاكاة رد الخصم (الكمبيوتر)
                        setTimeout(makeComputerMove, 500);
                    }
                    
                    selectedSquare.classList.remove('selected');
                    selectedSquare = null;
                    clearValidMoves();
                } else if (square.dataset.piece) {
                    // إذا لم يكن هناك مربع محدد وكان هناك قطعة في المربع الحالي، حدده
                    square.classList.add('selected');
                    selectedSquare = square;
                    
                    // عرض النقلات المتاحة (في التطبيق الحقيقي، نستخدم chess.js)
                    showValidMoves(row, col);
                }
            }

            function isValidMove(fromRow, fromCol, toRow, toCol) {
                // في التطبيق الحقيقي، نستخدم chess.js للتحقق من صحة النقلات
                // هنا نستخدم محاكاة بسيطة
                const piece = initialPosition[fromRow][fromCol];
                if (!piece) return false;
                
                // السماح بجميع النقلات للمحاكاة
                return true;
            }

            function showValidMoves(row, col) {
                // في التطبيق الحقيقي، نستخدم chess.js للحصول على النقلات المتاحة
                // هنا نعرض بعض النقلات العشوائية للمحاكاة
                for (let i = 0; i < 3; i++) {
                    const randomRow = Math.floor(Math.random() * 8);
                    const randomCol = Math.floor(Math.random() * 8);
                    
                    const square = document.querySelector(.chess-square[data-row="${randomRow}"][data-col="${randomCol}"]);
                    if (square && !square.dataset.piece) {
                        square.classList.add('valid-move');
                    } else if (square && square.dataset.piece && square.dataset.piece !== selectedSquare.dataset.piece) {
                        square.classList.add('capture');
                    }
                }
            }

            function clearValidMoves() {
                document.querySelectorAll('.chess-square.valid-move, .chess-square.capture').forEach(square => {
                    square.classList.remove('valid-move');
                    square.classList.remove('capture');
                });
            }

            function movePiece(fromSquare, toSquare) {
                const fromRow = parseInt(fromSquare.dataset.row);
                const fromCol = parseInt(fromSquare.dataset.col);
                const toRow = parseInt(toSquare.dataset.row);
                const toCol = parseInt(toSquare.dataset.col);
                
                // تحديث الموقع الابتدائي للذاكرة
                initialPosition[toRow][toCol] = initialPosition[fromRow][fromCol];
                initialPosition[fromRow][fromCol] = '';
                
                // تحديث العرض
                toSquare.textContent = fromSquare.textContent;
                toSquare.dataset.piece = fromSquare.dataset.piece;
                
                fromSquare.textContent = '';
                delete fromSquare.dataset.piece;
                
                // تحديث حالة اللعبة
                updateGameStatus();
            }

            function makeComputerMove() {
                // محاكاة نقلة الكمبيوتر
                const emptySquares = [];
                const computerPieces = [];
                
                // جمع القطع والمربعات الفارغة
                for (let row = 0; row < 8; row++) {
                    for (let col = 0; col < 8; col++) {
                        const piece = initialPosition[row][col];
                        if (piece && piece === piece.toLowerCase()) { // قطع الكمبيوتر (الأحرف الصغيرة)
                            computerPieces.push({row, col, piece});
                        } else if (!piece) {
                            emptySquares.push({row, col});
                        }
                    }
                }
                
                if (computerPieces.length > 0 && emptySquares.length > 0) {
                    // اختيار قطعة عشوائية ونقلها
                    const randomPiece = computerPieces[Math.floor(Math.random() * computerPieces.length)];
                    const randomSquare = emptySquares[Math.floor(Math.random() * emptySquares.length)];
                    
                    const fromSquare = document.querySelector(.chess-square[data-row="${randomPiece.row}"][data-col="${randomPiece.col}"]);
                    const toSquare = document.querySelector(.chess-square[data-row="${randomSquare.row}"][data-col="${randomSquare.col}"]);
                    
                    if (fromSquare && toSquare) {
                        movePiece(fromSquare, toSquare);
                        
                        // تحديث سجل النقلات
                        const moveNotation = ${files[randomPiece.col]}${8-randomPiece.row} → ${files[randomSquare.col]}${8-randomSquare.row};
                        addMoveToHistory(moveNotation, true);
                    }
                }
            }

            function addMoveToHistory(moveNotation, isComputer = false) {
                moveHistory.push({move: moveNotation, isComputer});
                currentMoveIndex = moveHistory.length - 1;
                updateMoveHistory();
            }

            function updateMoveHistory() {
                const moveList = document.getElementById('moveList');
                moveList.innerHTML = '';
                
                moveHistory.forEach((moveObj, index) => {
                    const moveItem = document.createElement('div');
                    moveItem.className = move-item ${index === currentMoveIndex ? 'current' : ''};
                    moveItem.textContent = ${moveObj.isComputer ? 'الكمبيوتر' : 'أنت'}: ${moveObj.move};
                    moveItem.addEventListener('click', () => goToMove(index));
                    moveList.appendChild(moveItem);
                });
            }

            function goToMove(index) {
                // في التطبيق الحقيقي، نعيد اللعبة إلى النقلة المحددة
                showNotification(الانتقال إلى النقلة ${index + 1}, 'success');
                currentMoveIndex = index;
                updateMoveHistory();
            }

            function updateGameStatus() {
                // في التطبيق الحقيقي، نستخدم chess.js للتحقق من حالة اللعبة
                document.getElementById('statusText').textContent = 'في تقدم';
            }

            // إعادة ضبط اللوحة
            document.getElementById('resetBoard').addEventListener('click', function() {
                if (confirm('هل تريد إعادة ضبط اللوحة إلى الوضع الابتدائي؟')) {
                    resetBoard();
                }
            });

            function resetBoard() {
                const squares = document.querySelectorAll('.chess-square');
                squares.forEach(square => {
                    const row = parseInt(square.dataset.row);
                    const col = parseInt(square.dataset.col);
                    const piece = initialPosition[row][col];
                    
                    if (piece) {
                        square.textContent = pieceSymbols[piece];
                        square.dataset.piece = piece;
                    } else {
                        square.textContent = '';
                        delete square.dataset.piece;
                    }
                    
                    square.classList.remove('selected');
                });
                
                selectedSquare = null;
                moveHistory = [];
                currentMoveIndex = -1;
                updateMoveHistory();
                document.getElementById('statusText').textContent = 'جاهز للعب';
                showMessage('تم إعادة ضبط اللوحة');
            }

            // زر التلميح
            document.getElementById('hintBtn').addEventListener('click', function() {
                showNotification('في النسخة الكاملة، ستحصل هنا على تلميح للنقلة التالية بناءً على تحليل المحرك!', 'warning');
            });

            // زر التحليل
            document.getElementById('analyzeBtn').addEventListener('click', function() {
                document.getElementById('analysisText').textContent = 'المحرك يوصي بنقلة الفيل إلى c4. هذه النقلة تساعد في السيطرة على المركز وتطوير القطعة.';
                showNotification('تم تحليل النقلة الحالية', 'success');
            });

            // زر التراجع
            document.getElementById('undoBtn').addEventListener('click', function() {
                if (moveHistory.length > 0) {
                    showNotification('في النسخة الكاملة، سيتم التراجع عن النقلة الأخيرة', 'warning');
                } else {
                    showNotification('لا توجد نقلات للتراجع عنها', 'error');
                }
            });

            // قلب الرقعة
            document.getElementById('flipBoard').addEventListener('click', function() {
                showNotification('في النسخة الكاملة، سيتم قلب اتجاه الرقعة', 'warning');
            });

            function showMessage(message) {
                showNotification(message, 'success');
            }
        });

        // أحداث الأزرار الرئيسية
        document.getElementById('startJourneyBtn').addEventListener('click', function() {
            showNotification('مرحبًا بك في رحلة تعلم الشطرنج! نتمنى لك تجربة تعلم ممتعة.', 'success');
            document.getElementById('levels').scrollIntoView({behavior: 'smooth'});
        });

        document.getElementById('exploreLessonsBtn').addEventListener('click', function() {
            document.getElementById('lessons').scrollIntoView({behavior: 'smooth'});
        });

        document.getElementById('loginBtn').addEventListener('click', function() {
            showNotification('سيتم فتح نافذة تسجيل الدخول في النسخة الكاملة', 'warning');
        });

        document.getElementById('registerBtn').addEventListener('click', function() {
            document.getElementById('user').scrollIntoView({behavior: 'smooth'});
        });

        // محاكاة بيانات المستخدم الأولية
        updateUserStats({
            completedLessons: 3,
            solvedExercises: 15,
            gamesPlayed: 8,
            currentLevel: 'مبتدئ'
        });
    </script>
</body>
</html>
