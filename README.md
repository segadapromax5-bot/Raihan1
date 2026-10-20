<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rihana Ashraf | Data Analyst</title>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&family=Poppins:wght@300;400;600;700;800&display=swap" rel="stylesheet">
<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  :root {
    --primary: #6366f1;
    --secondary: #ec4899;
    --accent: #06b6d4;
    --dark: #0f172a;
    --darker: #020617;
    --light: #f8fafc;
    --gray: #94a3b8;
  }

  body {
    font-family: 'Cairo', 'Poppins', sans-serif;
    background: var(--darker);
    color: var(--light);
    overflow-x: hidden;
    line-height: 1.6;
  }

  /* Animated background */
  .bg-animation {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    overflow: hidden;
  }

  .bg-animation::before,
  .bg-animation::after {
    content: '';
    position: absolute;
    width: 500px;
    height: 500px;
    border-radius: 50%;
    filter: blur(120px);
    opacity: 0.4;
    animation: float 15s ease-in-out infinite;
  }

  .bg-animation::before {
    background: var(--primary);
    top: -200px;
    right: -100px;
  }

  .bg-animation::after {
    background: var(--secondary);
    bottom: -200px;
    left: -100px;
    animation-delay: -7s;
  }

  @keyframes float {
    0%, 100% { transform: translate(0, 0) scale(1); }
    50% { transform: translate(100px, 100px) scale(1.2); }
  }

  /* Navbar */
  nav {
    position: fixed;
    top: 0;
    width: 100%;
    padding: 20px 8%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(2, 6, 23, 0.7);
    backdrop-filter: blur(20px);
    z-index: 1000;
    border-bottom: 1px solid rgba(99, 102, 241, 0.2);
  }

  .logo {
    font-size: 24px;
    font-weight: 900;
    background: linear-gradient(135deg, var(--primary), var(--secondary), var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  nav ul {
    display: flex;
    list-style: none;
    gap: 35px;
  }

  nav a {
    color: var(--light);
    text-decoration: none;
    font-weight: 600;
    position: relative;
    transition: color 0.3s;
  }

  nav a::after {
    content: '';
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--primary), var(--secondary));
    transition: width 0.3s;
  }

  nav a:hover::after { width: 100%; }
  nav a:hover { color: var(--primary); }

  /* Hero */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 120px 8% 60px;
    gap: 60px;
    position: relative;
  }

  .hero-text { flex: 1; }

  .hero-text .greet {
    display: inline-block;
    padding: 8px 20px;
    background: rgba(99, 102, 241, 0.15);
    border: 1px solid var(--primary);
    border-radius: 50px;
    color: var(--primary);
    font-weight: 600;
    margin-bottom: 20px;
    font-size: 14px;
    animation: fadeIn 1s;
  }

  .hero-text h1 {
    font-size: clamp(40px, 6vw, 72px);
    font-weight: 900;
    line-height: 1.1;
    margin-bottom: 20px;
    animation: slideRight 1s;
  }

  .hero-text h1 span {
    background: linear-gradient(135deg, var(--primary), var(--secondary), var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    background-size: 200% 200%;
    animation: gradientMove 4s ease infinite;
  }

  @keyframes gradientMove {
    0%, 100% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
  }

  .hero-text p {
    font-size: 18px;
    color: var(--gray);
    max-width: 550px;
    margin-bottom: 35px;
    animation: fadeIn 1.2s;
  }

  .hero-buttons {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
    animation: fadeIn 1.4s;
  }

  .btn {
    padding: 15px 35px;
    border-radius: 50px;
    font-family: inherit;
    font-weight: 700;
    font-size: 16px;
    text-decoration: none;
    transition: all 0.3s;
    cursor: pointer;
    border: none;
    display: inline-block;
  }

  .btn-primary {
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    color: white;
    box-shadow: 0 10px 30px rgba(99, 102, 241, 0.4);
  }

  .btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 15px 40px rgba(99, 102, 241, 0.6);
  }

  .btn-outline {
    background: transparent;
    color: var(--light);
    border: 2px solid var(--primary);
  }

  .btn-outline:hover {
    background: var(--primary);
    transform: translateY(-3px);
  }

  /* Profile picture */
  .hero-image {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }

  .photo-frame {
    width: 380px;
    height: 380px;
    border-radius: 50%;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    animation: fadeIn 1.5s;
  }

  .photo-frame::before {
    content: '';
    position: absolute;
    inset: -10px;
    border-radius: 50%;
    background: conic-gradient(from 0deg, var(--primary), var(--secondary), var(--accent), var(--primary));
    animation: rotate 4s linear infinite;
    z-index: -1;
  }

  .photo-frame::after {
    content: '';
    position: absolute;
    inset: 0;
    border-radius: 50%;
    background: var(--darker);
    z-index: -1;
  }

  @keyframes rotate {
    to { transform: rotate(360deg); }
  }

  .photo-frame img,
  .photo-placeholder {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    object-fit: cover;
    border: 8px solid var(--darker);
    background: linear-gradient(135deg, #1e293b, #334155);
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    color: var(--gray);
    gap: 10px;
    font-size: 14px;
  }

  .photo-placeholder svg {
    width: 80px;
    height: 80px;
    opacity: 0.5;
  }

  /* Floating badges */
  .badge {
    position: absolute;
    padding: 12px 20px;
    background: rgba(15, 23, 42, 0.9);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(99, 102, 241, 0.3);
    border-radius: 15px;
    font-weight: 600;
    font-size: 14px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
    animation: bounce 3s ease-in-out infinite;
  }

  .badge-1 { top: 10%; right: -20px; color: var(--accent); animation-delay: 0s; }
  .badge-2 { bottom: 15%; left: -30px; color: var(--secondary); animation-delay: 1s; }
  .badge-3 { top: 40%; left: -50px; color: var(--primary); animation-delay: 2s; }

  @keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-15px); }
  }

  /* Sections */
  section {
    padding: 100px 8%;
  }

  .section-title {
    text-align: center;
    margin-bottom: 60px;
  }

  .section-title h2 {
    font-size: clamp(32px, 4vw, 48px);
    font-weight: 900;
    margin-bottom: 15px;
  }

  .section-title h2 span {
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .section-title p {
    color: var(--gray);
    font-size: 16px;
  }

  /* Skills */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 25px;
  }

  .skill-card {
    padding: 35px 30px;
    background: rgba(15, 23, 42, 0.6);
    border: 1px solid rgba(99, 102, 241, 0.2);
    border-radius: 20px;
    transition: all 0.4s;
    position: relative;
    overflow: hidden;
    cursor: default;
  }

  .skill-card::before {
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    width: 100px;
    height: 100px;
    background: radial-gradient(circle, rgba(99, 102, 241, 0.3), transparent);
    transition: all 0.4s;
  }

  .skill-card:hover {
    transform: translateY(-10px);
    border-color: var(--primary);
    box-shadow: 0 20px 40px rgba(99, 102, 241, 0.3);
  }

  .skill-card:hover::before {
    width: 200px;
    height: 200px;
  }

  .skill-icon {
    width: 60px;
    height: 60px;
    border-radius: 15px;
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 20px;
    font-size: 28px;
  }

  .skill-card h3 {
    font-size: 20px;
    margin-bottom: 10px;
  }

  .skill-card p {
    color: var(--gray);
    font-size: 14px;
  }

  /* Projects */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 30px;
  }

  .project-card {
    background: rgba(15, 23, 42, 0.6);
    border: 1px solid rgba(99, 102, 241, 0.2);
    border-radius: 20px;
    overflow: hidden;
    transition: all 0.4s;
  }

  .project-card:hover {
    transform: translateY(-10px);
    border-color: var(--secondary);
    box-shadow: 0 20px 40px rgba(236, 72, 153, 0.3);
  }

  .project-image {
    height: 200px;
    background: linear-gradient(135deg, var(--primary), var(--secondary));
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 60px;
    position: relative;
    overflow: hidden;
  }

  .project-image::after {
    content: '';
    position: absolute;
    inset: 0;
    background: repeating-linear-gradient(
      45deg,
      transparent,
      transparent 10px,
      rgba(255, 255, 255, 0.05) 10px,
      rgba(255, 255, 255, 0.05) 20px
    );
  }

  .project-body {
    padding: 25px;
  }

  .project-body h3 {
    font-size: 20px;
    margin-bottom: 10px;
  }

  .project-body p {
    color: var(--gray);
    font-size: 14px;
    margin-bottom: 20px;
  }

  .tags {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
  }

  .tag {
    padding: 5px 14px;
    background: rgba(99, 102, 241, 0.15);
    border: 1px solid rgba(99, 102, 241, 0.4);
    color: var(--primary);
    border-radius: 50px;
    font-size: 12px;
    font-weight: 600;
  }

  /* Contact */
  .contact-container {
    max-width: 700px;
    margin: 0 auto;
    text-align: center;
  }

  .contact-links {
    display: flex;
    justify-content: center;
    gap: 25px;
    flex-wrap: wrap;
    margin-top: 40px;
  }

  .contact-link {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 15px 30px;
    background: rgba(15, 23, 42, 0.6);
    border: 1px solid rgba(99, 102, 241, 0.3);
    border-radius: 50px;
    color: var(--light);
    text-decoration: none;
    transition: all 0.3s;
    font-weight: 600;
  }

  .contact-link:hover {
    background: var(--primary);
    transform: translateY(-5px);
    box-shadow: 0 10px 30px rgba(99, 102, 241, 0.5);
  }

  footer {
    text-align: center;
    padding: 40px;
    color: var(--gray);
    border-top: 1px solid rgba(99, 102, 241, 0.1);
    font-size: 14px;
  }

  /* Animations */
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  @keyframes slideRight {
    from { opacity: 0; transform: translateX(50px); }
    to { opacity: 1; transform: translateX(0); }
  }

  /* Responsive */
  @media (max-width: 900px) {
    nav ul { display: none; }
    .hero { flex-direction: column-reverse; text-align: center; }
    .hero-buttons { justify-content: center; }
    .hero-text p { margin-left: auto; margin-right: auto; }
    .photo-frame { width: 300px; height: 300px; }
    .badge { font-size: 12px; padding: 8px 14px; }
    .badge-3 { display: none; }
  }
</style>
</head>
<body>

<div class="bg-animation"></div>

<nav>
  <div class="logo">Rihana ✨</div>
  <ul>
    <li><a href="#home">الرئيسية</a></li>
    <li><a href="#skills">المهارات</a></li>
    <li><a href="#projects">المشاريع</a></li>
    <li><a href="#contact">تواصل</a></li>
  </ul>
</nav>

<section class="hero" id="home">
  <div class="hero-text">
    <span class="greet">👋 أهلاً بك</span>
    <h1>أنا <span>ريحانة أشرف</span><br>Data Analyst</h1>
    <p>محللة بيانات شغوفة بتحويل الأرقام إلى قصص وقرارات ذكية. أحب اكتشاف الأنماط الخفية في البيانات وتحويلها إلى رؤى قيمة تساعد في اتخاذ قرارات أفضل.</p>
    <div class="hero-buttons">
      <a href="#projects" class="btn btn-primary">شوف شغلي 🚀</a>
      <a href="#contact" class="btn btn-outline">تواصل معايا</a>
    </div>
  </div>
  <div class="photo-frame">
   <img src="Mypicc.jpg">
      
    <div class="badge badge-1">📊 Python</div>
    <div class="badge badge-2">📈 SQL</div>
    <div class="badge badge-3">🎯 Power BI</div>
  </div>
</section>

<section id="skills">
  <div class="section-title">
    <h2>مهاراتي <span>الاحترافية</span></h2>
    <p>الأدوات والتقنيات التي أستخدمها في تحليل البيانات</p>
  </div>

  <div class="skills-grid">
    <div class="skill-card">
      <div class="skill-icon">🐍</div>
      <h3>Python</h3>
      <p>Pandas, NumPy, Matplotlib, Seaborn لتحليل وتصوير البيانات</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">🗄️</div>
      <h3>SQL</h3>
      <p>كتابة استعلامات معقدة واستخراج البيانات من قواعد البيانات</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">📊</div>
      <h3>Power BI & Tableau</h3>
      <p>إنشاء لوحات تحكم تفاعلية وتقارير احترافية</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">📗</div>
      <h3>Excel المتقدم</h3>
      <p>Pivot Tables, Power Query, والمعادلات المتقدمة</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">📈</div>
      <h3>Statistics</h3>
      <p>التحليل الإحصائي واختبار الفرضيات وفهم الأنماط</p>
    </div>
    <div class="skill-card">
      <div class="skill-icon">🤖</div>
      <h3>Machine Learning</h3>
      <p>بناء نماذج تنبؤية باستخدام Scikit-learn</p>
    </div>
  </div>
</section>

<section id="projects">
  <div class="section-title">
    <h2>أحدث <span>المشاريع</span></h2>
    <p>بعض الأعمال التي أفتخر بها في مجال تحليل البيانات</p>
  </div>

  <div class="projects-grid">
    <div class="project-card">
      <div class="project-image">🛒</div>
      <div class="project-body">
        <h3>تحليل مبيعات المتجر</h3>
        <p>تحليل بيانات مبيعات متجر إلكتروني لاكتشاف المنتجات الأكثر ربحية وسلوك العملاء.</p>
        <div class="tags">
          <span class="tag">Python</span>
          <span class="tag">Pandas</span>
          <span class="tag">Power BI</span>
        </div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-image">🎬</div>
      <div class="project-body">
        <h3>تحليل بيانات الأفلام</h3>
        <p>استكشاف بيانات IMDb لتحليل العوامل المؤثرة على نجاح الأفلام وتقييماتها.</p>
        <div class="tags">
          <span class="tag">SQL</span>
          <span class="tag">Python</span>
          <span class="tag">Matplotlib</span>
        </div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-image">💳</div>
      <div class="project-body">
        <h3>كشف الاحتيال البنكي</h3>
        <p>نموذج تعلم آلي لكشف المعاملات المشبوهة بدقة عالية باستخدام تقنيات ML.</p>
        <div class="tags">
          <span class="tag">Scikit-learn</span>
          <span class="tag">Pandas</span>
          <span class="tag">ML</span>
        </div>
      </div>
    </div>
  </div>
</section>

<section id="contact">
  <div class="section-title">
    <h2>خليك <span>على تواصل</span></h2>
    <p>عندك مشروع أو فرصة عمل؟ أنا دايماً متاحة!</p>
  </div>

  <div class="contact-container">
    <div class="contact-links">
      <a href="mailto:rihana@example.com" class="contact-link">📧 إيميل</a>
      <a href="https://linkedin.com" target="_blank" class="contact-link">💼 LinkedIn</a>
      <a href="https://github.com" target="_blank" class="contact-link">💻 GitHub</a>
      <a href="https://wa.me/20xxxxxxxxxx" target="_blank" class="contact-link">💬 WhatsApp</a>
    </div>
  </div>
</section>

<footer>
  <p>© 2025 Rihana Ashraf — صُنع بـ ❤️ وشغف بالبيانات</p>
</footer>

<script>
  // Smooth scroll
  document.querySelectorAll('a[href^="#"]').forEach(link => {
    link.addEventListener('click', e => {
      e.preventDefault();
      const target = document.querySelector(link.getAttribute('href'));
      if (target) target.scrollIntoView({ behavior: 'smooth' });
    });
  });

  // Animation on scroll
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.skill-card, .project-card').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(30px)';
    el.style.transition = 'all 0.6s ease';
    observer.observe(el);
  });
</script>

</body>
</html>
