Here are the updated project-1/index.html and the new project-1/problem-3.html (styled consistently with Problems 1 and 2, including the breadcrumb link to مصطفی رمضانی at [https://github.com/anonymoustafa/convex-optimization-projects/](https://github.com/anonymoustafa/convex-optimization-projects/), Persian RTL layout, Vazirmatn typography, MathJax, Prism.js with copy button, and interactive Chart.js plots for zero counts and estimation error vs. \lambda).
1. Updated Project 1 Page (project-1/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Project 1 — Problems</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@400;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #f8fafc;
      --card: #ffffff;
      --text: #0f172a;
      --muted: #64748b;
      --accent: #2563eb;
      --border: #e2e8f0;
    }

    * { box-sizing: border-box; }

    body {
      font-family: 'Vazirmatn', system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
      background: var(--bg);
      color: var(--text);
      margin: 0;
      padding: 3rem 1.25rem;
      line-height: 1.6;
    }

    .container {
      max-width: 720px;
      margin: 0 auto;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 2.25rem;
      box-shadow: 0 4px 18px rgba(15, 23, 42, 0.04);
    }

    .breadcrumb {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 0.5rem;
      margin-bottom: 1.25rem;
      font-size: 0.9rem;
    }

    .breadcrumb a {
      color: var(--muted);
      text-decoration: none;
    }

    .breadcrumb a:hover {
      color: var(--accent);
      text-decoration: underline;
    }

    .breadcrumb .author-link {
      color: var(--accent);
      font-weight: 600;
    }

    h1 {
      margin: 0 0 0.4rem 0;
      font-size: 1.75rem;
    }

    .subtitle {
      margin: 0 0 1.75rem 0;
      color: var(--muted);
    }

    ul.problem-list {
      list-style: disc;
      padding-left: 1.5rem;
      margin: 0;
    }

    ul.problem-list li {
      margin-bottom: 0.85rem;
      font-size: 1.08rem;
    }

    ul.problem-list a {
      color: var(--accent);
      text-decoration: none;
      font-weight: 600;
    }

    ul.problem-list a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <main class="container">
    <nav class="breadcrumb" aria-label="Breadcrumb">
      <a href="../index.html">← Back to Home</a>
      <span>/</span>
      <a href="https://github.com/anonymoustafa/convex-optimization-projects/" class="author-link" target="_blank" rel="noopener noreferrer">مصطفی رمضانی</a>
    </nav>

    <h1>Project 1</h1>
    <p class="subtitle">Choose a problem below:</p>

    <ul class="problem-list">
      <li>
        <a href="problem-1.html">Problem 1 — Least Squares with CVXPY &amp; Noise Analysis</a>
      </li>
      <li>
        <a href="problem-2.html">Problem 2 — 1D Total Variation Denoising (Dual / L-BFGS-B)</a>
      </li>
      <li>
        <a href="problem-3.html">Problem 3 — Lasso Regression &amp; Feature Selection with CVXPY</a>
      </li>
    </ul>
  </main>
</body>
</html>

2. Problem 3 Page (project-1/problem-3.html)
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>مسئله ۳ — رگرسیون لسو (Lasso Regression) و انتخاب ویژگی با CVXPY</title>

  <!-- Persian Font (Vazirmatn) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;600;700&display=swap" rel="stylesheet">

  <!-- Prism.js for Python Syntax Highlighting -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/themes/prism-tomorrow.min.css" rel="stylesheet" />

  <!-- MathJax for LaTeX Equations -->
  <script>
    window.MathJax = {
      tex: {
        inlineMath: [['$', '$'], ['\\(', '\\)']],
        displayMath: [['$$', '$$'], ['\\[', '\\]']]
      }
    };
  </script>
  <script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

  <!-- Chart.js for Interactive Plots -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <style>
    :root {
      --bg-color: #f8fafc;
      --card-bg: #ffffff;
      --text-main: #1e293b;
      --text-muted: #475569;
      --primary: #2563eb;
      --primary-light: #eff6ff;
      --border-color: #e2e8f0;
    }

    * {
      box-sizing: border-box;
    }

    body {
      font-family: 'Vazirmatn', system-ui, -apple-system, sans-serif;
      background-color: var(--bg-color);
      color: var(--text-main);
      line-height: 1.8;
      margin: 0;
      padding: 2rem 1rem;
    }

    .container {
      max-width: 940px;
      margin: 0 auto;
      background: var(--card-bg);
      padding: 2.5rem;
      border-radius: 16px;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
      border: 1px solid var(--border-color);
    }

    .nav-bar {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 0.75rem;
      margin-bottom: 1.25rem;
      font-size: 0.9rem;
    }

    .nav-bar a {
      color: var(--primary);
      text-decoration: none;
      font-weight: 600;
    }

    .nav-bar a:hover {
      text-decoration: underline;
    }

    header {
      border-bottom: 2px solid var(--border-color);
      padding-bottom: 1.25rem;
      margin-bottom: 2rem;
    }

    h1 {
      font-size: 1.7rem;
      color: #0f172a;
      margin: 0 0 0.5rem 0;
    }

    .subtitle {
      color: var(--text-muted);
      font-size: 0.95rem;
      margin: 0;
    }

    h2 {
      font-size: 1.3rem;
      color: #0f172a;
      margin-top: 2.25rem;
      margin-bottom: 1rem;
      padding-right: 0.75rem;
      border-right: 4px solid var(--primary);
    }

    p {
      margin-bottom: 1rem;
      text-align: justify;
    }

    .formula-box {
      background: var(--primary-light);
      border: 1px solid #bfdbfe;
      border-radius: 10px;
      padding: 1rem;
      margin: 1.25rem 0;
      text-align: center;
      direction: ltr;
      overflow-x: auto;
    }

    .code-wrapper {
      position: relative;
      direction: ltr;
      text-align: left;
      margin: 1.5rem 0;
    }

    .copy-btn {
      position: absolute;
      top: 0.75rem;
      right: 0.75rem;
      background: rgba(255, 255, 255, 0.12);
      color: #f8fafc;
      border: 1px solid rgba(255, 255, 255, 0.25);
      border-radius: 6px;
      padding: 0.35rem 0.75rem;
      font-size: 0.8rem;
      cursor: pointer;
      font-family: inherit;
      transition: background 0.2s;
      z-index: 10;
    }

    .copy-btn:hover {
      background: rgba(255, 255, 255, 0.25);
    }

    pre[class*="language-"] {
      border-radius: 12px;
      padding: 1.5rem;
      margin: 0;
      font-size: 0.9rem;
      line-height: 1.6;
    }

    .charts-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 1.25rem;
      margin: 1.5rem 0;
    }

    .chart-card {
      background: #ffffff;
      border: 1px solid var(--border-color);
      border-radius: 12px;
      padding: 1.25rem;
    }

    .chart-container {
      position: relative;
      height: 300px;
      width: 100%;
    }

    ul, ol {
      padding-right: 1.5rem;
    }

    li {
      margin-bottom: 0.75rem;
    }

    code.inline {
      background: #f1f5f9;
      color: #dc2626;
      padding: 0.15rem 0.4rem;
      border-radius: 4px;
      font-family: monospace;
      font-size: 0.9em;
      direction: ltr;
      display: inline-block;
    }

    footer {
      margin-top: 3rem;
      padding-top: 1.25rem;
      border-top: 1px solid var(--border-color);
      text-align: center;
      font-size: 0.85rem;
      color: var(--text-muted);
    }

    @media (max-width: 780px) {
      .charts-grid {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 640px) {
      .container {
        padding: 1.5rem;
      }
      h1 {
        font-size: 1.35rem;
      }
    }
  </style>
</head>
<body>

  <main class="container">
    <nav class="nav-bar" aria-label="Breadcrumb">
      <a href="../index.html">صفحه اصلی (Home)</a>
      <span>/</span>
      <a href="index.html">پروژه ۱ (Project 1)</a>
      <span>/</span>
      <a href="https://github.com/anonymoustafa/convex-optimization-projects/" target="_blank" rel="noopener noreferrer">مصطفی رمضانی</a>
    </nav>

    <header>
      <h1>مسئله ۳: رگرسیون لسو (Lasso Regression) و انتخاب ویژگی با CVXPY</h1>
      <p class="subtitle">بررسی ایجاد تنکی (Sparsity) و خطای تخمین بر حسب پارامتر جریمه $\lambda$ در داده‌های مصنوعی</p>
    </header>

    <section>
      <p>
        برای حل این تمرین (رگرسیون لسو یا Lasso Regression)، از کتابخانه <code class="inline">cvxpy</code> در پایتون استفاده می‌کنیم. در ادامه، کد کامل به همراه تولید داده‌های مصنوعی تنک (Sparse)، حل مسئله بهینه‌سازی به ازای مقادیر مختلف $\lambda$، رسم نمودار و تحلیل چرایی کاربرد این روش در انتخاب ویژگی ارائه شده است.
      </p>

      <div class="formula-box">
        $$\min_{x \in \mathbb{R}^{n}} \; \frac{1}{2}\Vert Ax - y \Vert_{2}^{2} + \lambda \Vert x \Vert_{1}$$
      </div>
    </section>

    <section>
      <h2>۱. کد پیاده‌سازی در پایتون (با استفاده از CVXPY)</h2>
      <div class="code-wrapper">
        <button class="copy-btn" onclick="copyCode()">Copy Code</button>
        <pre><code id="python-code" class="language-python">import cvxpy as cp
import matplotlib.pyplot as plt
import numpy as np

# ۱. تنظیم بذر تصادفی برای تکرارپذیری نتایج
np.random.seed(42)

# ۲. تعریف ابعاد مسئله
m = 100  # تعداد نمونه‌ها (سطرها)
n = 50  # تعداد ویژگی‌ها (ستون‌ها)
k = 5  # تعداد ویژگی‌های واقعی و غیرصفر

# ۳. تولید داده‌های مصنوعی
A = np.random.randn(m, n)

# ساخت بردار x_true که فقط ۵ درایه غیرصفر دارد
x_true = np.zeros(n)
nonzero_indices = np.random.choice(n, k, replace=False)
x_true[nonzero_indices] = np.random.uniform(-5, 5, size=k)

# تولید بردار مشاهدات y با افزودن مقدار کمی نویز گوسی
noise = 0.5 * np.random.randn(m)
y = A @ x_true + noise

# ۴. تعریف متغیر و پارامتر در CVXPY
x = cp.Variable(n)
lambd = cp.Parameter(nonneg=True)

# تعریف تابع هدف: 1/2 * ||Ax - y||_2^2 + lambda * ||x||_1
objective = cp.Minimize(0.5 * cp.sum_squares(A @ x - y) + lambd * cp.norm1(x))
problem = cp.Problem(objective)

# ۵. حل مسئله به ازای مقادیر مختلف لاندا (در مقیاس لگاریتمی)
lambda_values = np.logspace(-2, 2.5, 50)
zero_counts = []
mse_errors = []

# آستانه عددی برای صفر در نظر گرفتن درایه‌ها (به دلیل دقت محاسبات ممیز شناور حل‌گر)
zero_threshold = 1e-4

for val in lambda_values:
  lambd.value = val
  problem.solve()

  # شمارش درایه‌هایی که عملاً صفر شده‌اند
  num_zeros = np.sum(np.abs(x.value) &lt; zero_threshold)
  zero_counts.append(num_zeros)

  # محاسبه خطای تخمین نسبت به x_true
  mse_errors.append(np.linalg.norm(x.value - x_true) ** 2)

# ۶. رسم نمودارها
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(14, 5))

# نمودار اول: تعداد درایه‌های صفر شده بر حسب لاندا
ax1.semilogx(lambda_values, zero_counts, marker='o', markersize=4, color='b')
ax1.axhline(
    y=n - k,
    color='r',
    linestyle='--',
    label=f'تعداد واقعی صفرها ({n - k})',
)
ax1.set_title('تعداد درایه‌های صفر شده در جواب بر حسب افزایش $\\lambda$')
ax1.set_xlabel('پارامتر جریمه ($\\lambda$) - مقیاس لگاریتمی')
ax1.set_ylabel('تعداد درایه‌های صفر شده (از ۵۰)')
ax1.grid(True, which='both', linestyle='--', alpha=0.6)
ax1.legend()

# نمودار دوم: خطای تخمین بر حسب لاندا (برای مشاهده ناحیه بهینه)
ax2.loglog(lambda_values, mse_errors, marker='s', markersize=4, color='g')
ax2.set_title('خطای مربعات تخمین $\\|x - x_{true}\\|_2^2$ بر حسب $\\lambda$')
ax2.set_xlabel('پارامتر جریمه ($\\lambda$) - مقیاس لگاریتمی')
ax2.set_ylabel('خطای تخمین')
ax2.grid(True, which='both', linestyle='--', alpha=0.6)

plt.tight_layout()
plt.show()</code></pre>
      </div>

      <div class="charts-grid">
        <div class="chart-card">
          <div class="chart-container">
            <canvas id="zeroCountsChart"></canvas>
          </div>
        </div>
        <div class="chart-card">
          <div class="chart-container">
            <canvas id="mseChart"></canvas>
          </div>
        </div>
      </div>
    </section>

    <section>
      <h2>۲. نکات کلیدی در پیاده‌سازی</h2>
      <ul>
        <li>
          <strong>استفاده از <code class="inline">cp.Parameter</code>:</strong> در حل‌گرهای بهینه‌سازی مانند CVXPY، تعریف $\lambda$ به عنوان <code class="inline">cp.Parameter(nonneg=True)</code> به جای بازسازی کل مسئله در هر تکرار حلقه، سرعت اجرا را به شدت افزایش می‌دهد (چون ساختار مسئله فقط یک‌بار کامپایل می‌شود).
        </li>
        <li>
          <strong>آستانه صفر (<code class="inline">1e-4</code>):</strong> الگوریتم‌های نقطه درونی (Interior-Point Methods) که CVXPY به صورت پیش‌فرض استفاده می‌کند، به دلیل ماهیت محاسبات ممیز شناور (Floating-point)، به جای عدد مطلق <code class="inline">0.0</code>، مقادیری بسیار کوچک مثل <code class="inline">1e-9</code> تولید می‌کنند. بنابراین در کدنویسی عملی برای شمارش صفرها از یک آستانه کوچک مثل <code class="inline">1e-4</code> استفاده می‌شود.
        </li>
      </ul>
    </section>

    <section>
      <h2>۳. تحلیل نتایج و چرایی مناسب بودن برای انتخاب ویژگی (Feature Selection)</h2>
      <p>
        با اجرای کد بالا، سه رفتار مشخص در نمودار مشاهده می‌شود که علت کاربرد گسترده‌ی جریمه نرم ۱ (Lasso) در یادگیری ماشین را توضیح می‌دهد:
      </p>
      <ol>
        <li>
          <strong>ایجاد جواب‌های تنک (Sparsity):</strong>
          <ul>
            <li>وقتی $\lambda$ بسیار کوچک است ($\lambda \to 0$)، مسئله به کمترین مربعات معمولی (OLS) تبدیل می‌شود. در این حالت، به دلیل وجود نویز در داده‌ها، تقریباً تمام ۵۰ مؤلفه مقادیر غیرصفر (حتی بسیار کوچک) می‌گیرند و تعداد صفرها نزدیک به <code class="inline">0</code> است.</li>
            <li>با افزایش $\lambda$، تعداد درایه‌های صفر شده به سرعت افزایش می‌یابد تا جایی که روی عدد ۴۵ (خط چین قرمز) تثبیت می‌شود؛ یعنی مدل دقیقاً ۴۵ ویژگی نامرتبط را حذف کرده و ۵ ویژگی اصلی را نگه داشته است.</li>
            <li>اگر $\lambda$ بیش از حد بزرگ شود، جریمه سنگین‌تر از خطای برازش می‌شود و تمام ۵۰ مؤلفه به سمت صفر رانده می‌شوند (کم‌برازش یا Underfitting).</li>
          </ul>
        </li>
        <li>
          <strong>تفسیر هندسی و ریاضی (چرا نرم ۱ صفر مطلق می‌سازد؟):</strong>
          <ul>
            <li>جریمه نرم ۲ ($\Vert x \Vert_2^2$ در رگرسیون Ridge) ضرایب را کوچک می‌کند اما آن‌ها را دقیقاً صفر نمی‌کند، زیرا سطوح تراز آن یک دایره یا کره صاف است.</li>
            <li>در مقابل، گوی واحد نرم ۱ ($\Vert x \Vert_1 \le t$) در فضاهای چندبعدی به شکل یک چندوجهی الماس‌شکل (Cross-polytope) است که گوشه‌های تیز آن دقیقاً روی محورهای مختصات قرار دارند. هنگام بهینه‌سازی، خطوط تراز بیضی‌شکل تابع خطای مربعات ($\Vert Ax - y \Vert_2^2$) به احتمال بسیار زیاد در یکی از همین گوشه‌ها با ناحیه مجاز برخورد می‌کنند که در آن مختصات بسیاری از محورها دقیقاً صفر است.</li>
          </ul>
        </li>
        <li>
          <strong>کاربرد مستقیم در انتخاب ویژگی:</strong>
          <ul>
            <li>در مسائل دنیای واقعی که تعداد ویژگی‌ها ($n$) زیاد است (مثلاً داده‌های ژنتیکی یا پردازش متن)، بسیاری از ویژگی‌ها بی‌ربط یا حاوی نویز هستند. صفر شدن دقیق ضریب $x_i$ به این معنی است که ویژگی $i$-ام هیچ تأثیری در پیش‌بینی خروجی ندارد و می‌توان آن را به طور کامل از مدل حذف کرد؛ در نتیجه مدل ساده‌تر، سریع‌تر و قابل تفسیرتر می‌شود.</li>
          </ul>
        </li>
      </ol>
    </section>

    <footer>
      تهیه شده توسط مصطفی رمضانی برای انتشار در GitHub Pages
    </footer>
  </main>

  <!-- Prism.js Script -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/prism.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.29.0/components/prism-python.min.js"></script>

  <!-- Copy Button & Interactive Charts Logic -->
  <script>
    function copyCode() {
      const codeText = document.getElementById('python-code').innerText;
      navigator.clipboard.writeText(codeText).then(() => {
        const btn = document.querySelector('.copy-btn');
        btn.textContent = 'Copied!';
        setTimeout(() => { btn.textContent = 'Copy Code'; }, 2000);
      });
    }

    // Seeded PRNG (Mulberry32) to simulate the sparse m=100, n=50, k=5 Lasso path
    function mulberry32(a) {
      return function() {
        let t = a += 0x6D2B79F5;
        t = Math.imul(t ^ t >>> 15, t | 1);
        t ^= t + Math.imul(t ^ t >>> 7, t | 61);
        return ((t ^ t >>> 14) >>> 0) / 4294967296;
      };
    }

    function randn(rng) {
      const u1 = Math.max(rng(), 1e-12);
      const u2 = rng();
      return Math.sqrt(-2.0 * Math.log(u1)) * Math.cos(2.0 * Math.PI * u2);
    }

    function computeLassoPath() {
      const rng = mulberry32(42);
      const m = 100, n = 50, k = 5;

      // Generate A (m x n)
      const A = Array.from({ length: m }, () => Array.from({ length: n }, () => randn(rng)));

      // Sparse x_true with 5 non-zero entries in [-5, 5]
      const xTrue = new Array(n).fill(0);
      const idxs = Array.from({ length: n }, (_, i) => i);
      for (let i = n - 1; i > 0; i--) {
        const j = Math.floor(rng() * (i + 1));
        [idxs[i], idxs[j]] = [idxs[j], idxs[i]];
      }
      const nzIdx = idxs.slice(0, k);
      const nzVals = Array.from({ length: k }, () => -5 + 10 * rng());
      for (let i = 0; i < k; i++) {
        xTrue[nzIdx[i]] = nzVals[i];
      }

      // y = A @ x_true + 0.5 * noise
      const y = new Array(m).fill(0);
      for (let i = 0; i < m; i++) {
        let dot = 0;
        for (let j = 0; j < n; j++) dot += A[i][j] * xTrue[j];
        y[i] = dot + 0.5 * randn(rng);
      }

      // Logspace lambda values from 10^-2 to 10^2.5 (50 points)
      const lambdas = [];
      for (let i = 0; i < 50; i++) {
        const exp = -2.0 + (4.5 * i) / 49;
        lambdas.push(Math.pow(10, exp));
      }

      // Coordinate descent for 0.5 * ||Ax - y||_2^2 + lam * ||x||_1
      const colNormSq = new Array(n).fill(0);
      for (let j = 0; j < n; j++) {
        let s = 0;
        for (let i = 0; i < m; i++) s += A[i][j] * A[i][j];
        colNormSq[j] = s;
      }

      function softThreshold(rho, z) {
        if (rho < -z) return rho + z;
        if (rho > z) return rho - z;
        return 0.0;
      }

      const zeroCounts = [];
      const mseErrors = [];
      let x = new Array(n).fill(0);

      for (const lam of lambdas) {
        for (let iter = 0; iter < 600; iter++) {
          let maxDiff = 0;
          for (let j = 0; j < n; j++) {
            // Compute partial residual r_j = y - sum_{l != j} A[:, l] * x[l]
            let rho = 0;
            for (let i = 0; i < m; i++) {
              let predWithoutJ = 0;
              for (let l = 0; l < n; l++) {
                if (l !== j) predWithoutJ += A[i][l] * x[l];
              }
              rho += A[i][j] * (y[i] - predWithoutJ);
            }
            const xNew = softThreshold(rho, lam) / colNormSq[j];
            const diff = Math.abs(xNew - x[j]);
            if (diff > maxDiff) maxDiff = diff;
            x[j] = xNew;
          }
          if (maxDiff < 1e-8) break;
        }

        const zeros = x.filter(v => Math.abs(v) < 1e-4).length;
        zeroCounts.push(zeros);

        let errSq = 0;
        for (let j = 0; j < n; j++) {
          const d = x[j] - xTrue[j];
          errSq += d * d;
        }
        mseErrors.push(+errSq.toFixed(5));
      }

      return { lambdas, zeroCounts, mseErrors, trueZeros: n - k };
    }

    const { lambdas, zeroCounts, mseErrors, trueZeros } = computeLassoPath();

    // Chart 1: Zero counts vs lambda
    new Chart(document.getElementById('zeroCountsChart').getContext('2d’
