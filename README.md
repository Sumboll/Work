# Work
&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;uk&quot;&gt;
&lt;head&gt;
&lt;meta charset=&quot;UTF-8&quot; /&gt;
&lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;/&gt;
&lt;title&gt;CI/CD Pipeline — Практична робота&lt;/title&gt;
&lt;style&gt;
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: &#39;Segoe UI&#39;, sans-serif; background: #0d1117; color: #c9d1d9; min-height:
100vh; }
header {
background: linear-gradient(135deg, #161b22, #21262d);
border-bottom: 1px solid #30363d;
padding: 20px 32px;
display: flex; align-items: center; gap: 16px;
}
header .logo { font-size: 28px; }
header h1 { font-size: 20px; color: #f0f6fc; font-weight: 600; }
header p { font-size: 13px; color: #8b949e; margin-top: 2px; }
.tabs {
display: flex; gap: 0;
background: #161b22;
border-bottom: 1px solid #30363d;
padding: 0 32px;
overflow-x: auto;
}
.tab {
padding: 12px 20px;
cursor: pointer;
font-size: 14px;
color: #8b949e;
border-bottom: 2px solid transparent;
white-space: nowrap;
transition: all 0.2s;
}
.tab:hover { color: #c9d1d9; }
.tab.active { color: #f0f6fc; border-bottom-color: #f78166; font-weight: 500; }
.content { padding: 28px 32px; max-width: 1100px; margin: 0 auto; }
.panel { display: none; }
.panel.active { display: block; }
/* Code blocks */
.code-block {
background: #161b22;
border: 1px solid #30363d;

border-radius: 8px;
overflow: hidden;
margin: 16px 0;
}
.code-header {
background: #21262d;
padding: 10px 16px;
display: flex; justify-content: space-between; align-items: center;
border-bottom: 1px solid #30363d;
}
.code-header .filename { font-size: 13px; color: #8b949e; font-family: monospace; }
.code-header .lang-badge {
font-size: 11px; padding: 2px 8px; border-radius: 12px;
background: #388bfd22; color: #79c0ff; border: 1px solid #388bfd44;
}
.code-body {
padding: 16px;
font-family: &#39;Courier New&#39;, monospace;
font-size: 13px;
line-height: 1.7;
overflow-x: auto;
white-space: pre;
color: #c9d1d9;
}
/* Syntax highlight helpers */
.kw { color: #ff7b72; }
.fn { color: #d2a8ff; }
.st { color: #a5d6ff; }
.cm { color: #8b949e; font-style: italic; }
.nm { color: #79c0ff; }
.op { color: #ff7b72; }
.dc { color: #ffa657; }
/* Pipeline diagram */
.pipeline {
display: flex; align-items: center; gap: 0;
margin: 24px 0; flex-wrap: wrap;
}
.stage {
background: #21262d;
border: 1px solid #30363d;
border-radius: 8px;
padding: 14px 18px;
text-align: center;
min-width: 120px;
transition: all 0.3s;
cursor: pointer;
position: relative;
}

.stage:hover { border-color: #388bfd; transform: translateY(-2px); }
.stage.success { border-color: #3fb950; }
.stage.running { border-color: #d29922; animation: pulse 1.5s infinite; }
.stage.fail { border-color: #f85149; }
.stage-icon { font-size: 22px; margin-bottom: 6px; }
.stage-name { font-size: 12px; font-weight: 600; color: #f0f6fc; }
.stage-status { font-size: 11px; margin-top: 4px; }
.stage.success .stage-status { color: #3fb950; }
.stage.running .stage-status { color: #d29922; }
.stage.fail .stage-status { color: #f85149; }
.arrow { font-size: 20px; color: #30363d; padding: 0 8px; }
@keyframes pulse {
0%, 100% { box-shadow: 0 0 0 0 rgba(210,153,34,0.4); }
50% { box-shadow: 0 0 0 6px rgba(210,153,34,0); }
}
/* Cards */
.card {
background: #161b22;
border: 1px solid #30363d;
border-radius: 8px;
padding: 20px;
margin: 16px 0;
}
.card h3 { color: #f0f6fc; font-size: 15px; margin-bottom: 12px; display: flex; align-items: center;
gap: 8px; }
/* Info grid */
.info-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 16px;
margin: 20px 0; }
.info-card {
background: #161b22; border: 1px solid #30363d; border-radius: 8px;
padding: 16px; text-align: center;
}
.info-card .val { font-size: 28px; font-weight: 700; color: #388bfd; }
.info-card .lbl { font-size: 12px; color: #8b949e; margin-top: 4px; }
/* Log output */
.log-output {
background: #010409;
border: 1px solid #30363d;
border-radius: 8px;
padding: 16px;
font-family: monospace;
font-size: 12px;
line-height: 1.8;
max-height: 320px;
overflow-y: auto;
}

.log-ok { color: #3fb950; }
.log-warn { color: #d29922; }
.log-err { color: #f85149; }
.log-info { color: #79c0ff; }
.log-dim { color: #484f58; }
h2 { color: #f0f6fc; font-size: 17px; margin-bottom: 16px; padding-bottom: 8px; border-bottom:
1px solid #21262d; }
p { color: #8b949e; font-size: 14px; line-height: 1.7; margin-bottom: 12px; }
ul { color: #8b949e; font-size: 14px; line-height: 2; padding-left: 20px; }
ul li::marker { color: #388bfd; }
.badge {
display: inline-block; font-size: 11px; padding: 2px 10px; border-radius: 12px; margin: 2px;
}
.badge-blue { background: #388bfd22; color: #79c0ff; border: 1px solid #388bfd44; }
.badge-green { background: #3fb95022; color: #3fb950; border: 1px solid #3fb95044; }
.badge-orange { background: #ffa65722; color: #ffa657; border: 1px solid #ffa65744; }
.run-btn {
background: #238636; color: #fff; border: none; border-radius: 6px;
padding: 10px 22px; font-size: 14px; cursor: pointer; font-weight: 500;
transition: background 0.2s;
}
.run-btn:hover { background: #2ea043; }
.run-btn:disabled { background: #21262d; color: #484f58; cursor: not-allowed; }
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;header&gt;
&lt;div class=&quot;logo&quot;&gt;⚙️&lt;/div&gt;
&lt;div&gt;
&lt;h1&gt;CI/CD Pipeline — Практична робота&lt;/h1&gt;
&lt;p&gt;DevOps | 1 курс магістратури &amp;nbsp;·&amp;nbsp; GitHub Actions + Docker + pytest&lt;/p&gt;
&lt;/div&gt;
&lt;/header&gt;
&lt;div class=&quot;tabs&quot;&gt;
&lt;div class=&quot;tab active&quot; onclick=&quot;showTab(&#39;overview&#39;)&quot;&gt;� Огляд&lt;/div&gt;
&lt;div class=&quot;tab&quot; onclick=&quot;showTab(&#39;app&#39;)&quot;&gt;� Застосунок&lt;/div&gt;
&lt;div class=&quot;tab&quot; onclick=&quot;showTab(&#39;tests&#39;)&quot;&gt;� Тести&lt;/div&gt;
&lt;div class=&quot;tab&quot; onclick=&quot;showTab(&#39;pipeline&#39;)&quot;&gt;� Пайплайн&lt;/div&gt;
&lt;div class=&quot;tab&quot; onclick=&quot;showTab(&#39;docker&#39;)&quot;&gt;�� Docker&lt;/div&gt;
&lt;div class=&quot;tab&quot; onclick=&quot;showTab(&#39;simulate&#39;)&quot;&gt;▶️ Симуляція&lt;/div&gt;
&lt;/div&gt;
&lt;div class=&quot;content&quot;&gt;
&lt;!-- OVERVIEW --&gt;

&lt;div class=&quot;panel active&quot; id=&quot;panel-overview&quot;&gt;
&lt;h2&gt;Огляд проєкту&lt;/h2&gt;
&lt;p&gt;Демонстраційний проєкт реалізує &lt;strong style=&quot;color:#f0f6fc&quot;&gt;калькулятор
математичних операцій&lt;/strong&gt; з повним CI/CD пайплайном на базі GitHub Actions.
Пайплайн автоматично запускається при кожному push/pull request до репозиторію.&lt;/p&gt;
&lt;div class=&quot;info-grid&quot;&gt;
&lt;div class=&quot;info-card&quot;&gt;&lt;div class=&quot;val&quot;&gt;4&lt;/div&gt;&lt;div class=&quot;lbl&quot;&gt;Етапи пайплайну&lt;/div&gt;&lt;/div&gt;
&lt;div class=&quot;info-card&quot;&gt;&lt;div class=&quot;val&quot;&gt;8&lt;/div&gt;&lt;div class=&quot;lbl&quot;&gt;Unit-тестів&lt;/div&gt;&lt;/div&gt;
&lt;div class=&quot;info-card&quot;&gt;&lt;div class=&quot;val&quot;&gt;100%&lt;/div&gt;&lt;div class=&quot;lbl&quot;&gt;Покриття
коду&lt;/div&gt;&lt;/div&gt;
&lt;div class=&quot;info-card&quot;&gt;&lt;div class=&quot;val&quot;&gt;~45s&lt;/div&gt;&lt;div class=&quot;lbl&quot;&gt;Час
виконання&lt;/div&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;div class=&quot;card&quot;&gt;
&lt;h3&gt;� Технологічний стек&lt;/h3&gt;
&lt;span class=&quot;badge badge-blue&quot;&gt;Python 3.11&lt;/span&gt;
&lt;span class=&quot;badge badge-blue&quot;&gt;GitHub Actions&lt;/span&gt;
&lt;span class=&quot;badge badge-blue&quot;&gt;Docker&lt;/span&gt;
&lt;span class=&quot;badge badge-green&quot;&gt;pytest&lt;/span&gt;
&lt;span class=&quot;badge badge-green&quot;&gt;pytest-cov&lt;/span&gt;
&lt;span class=&quot;badge badge-orange&quot;&gt;flake8&lt;/span&gt;
&lt;span class=&quot;badge badge-orange&quot;&gt;black&lt;/span&gt;
&lt;/div&gt;
&lt;div class=&quot;card&quot;&gt;
&lt;h3&gt;� Структура проєкту&lt;/h3&gt;
&lt;div class=&quot;code-body&quot; style=&quot;padding:0; background:transparent; font-size:13px; white-
space:pre; color:#c9d1d9&quot;&gt;
ci-cd-demo/
├── &lt;span style=&quot;color:#79c0ff&quot;&gt;.github/&lt;/span&gt;
│ └── &lt;span style=&quot;color:#79c0ff&quot;&gt;workflows/&lt;/span&gt;
│ └── &lt;span style=&quot;color:#a5d6ff&quot;&gt;ci-cd.yml&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;# ← Конфігурація
пайплайну&lt;/span&gt;
├── &lt;span style=&quot;color:#79c0ff&quot;&gt;app/&lt;/span&gt;
│ ├── &lt;span style=&quot;color:#c9d1d9&quot;&gt;__init__.py&lt;/span&gt;
│ └── &lt;span style=&quot;color:#a5d6ff&quot;&gt;calculator.py&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;# ← Основний
модуль&lt;/span&gt;
├── &lt;span style=&quot;color:#79c0ff&quot;&gt;tests/&lt;/span&gt;
│ ├── &lt;span style=&quot;color:#c9d1d9&quot;&gt;__init__.py&lt;/span&gt;
│ └── &lt;span style=&quot;color:#a5d6ff&quot;&gt;test_calculator.py&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;# ←
Тести&lt;/span&gt;
├── &lt;span style=&quot;color:#a5d6ff&quot;&gt;Dockerfile&lt;/span&gt; &lt;span class=&quot;cm&quot;&gt;# ←
Контейнеризація&lt;/span&gt;
├── &lt;span style=&quot;color:#a5d6ff&quot;&gt;requirements.txt&lt;/span&gt;
└── &lt;span style=&quot;color:#a5d6ff&quot;&gt;README.md&lt;/span&gt;
&lt;/div&gt;

&lt;/div&gt;
&lt;div class=&quot;card&quot;&gt;
&lt;h3&gt;� Схема пайплайну&lt;/h3&gt;
&lt;div class=&quot;pipeline&quot;&gt;
&lt;div class=&quot;stage success&quot;&gt;
&lt;div class=&quot;stage-icon&quot;&gt;��&lt;/div&gt;
&lt;div class=&quot;stage-name&quot;&gt;Checkout&lt;/div&gt;
&lt;div class=&quot;stage-status&quot;&gt;✓ passed&lt;/div&gt;
&lt;/div&gt;
&lt;div class=&quot;arrow&quot;&gt;→&lt;/div&gt;
&lt;div class=&quot;stage success&quot;&gt;
&lt;div class=&quot;stage-icon&quot;&gt;��&lt;/div&gt;
&lt;div class=&quot;stage-name&quot;&gt;Lint&lt;/div&gt;
&lt;div class=&quot;stage-status&quot;&gt;✓ passed&lt;/div&gt;
&lt;/div&gt;
&lt;div class=&quot;arrow&quot;&gt;→&lt;/div&gt;
&lt;div class=&quot;stage success&quot;&gt;
&lt;div class=&quot;stage-icon&quot;&gt;��&lt;/div&gt;
&lt;div class=&quot;stage-name&quot;&gt;Test&lt;/div&gt;
&lt;div class=&quot;stage-status&quot;&gt;✓ 8/8&lt;/div&gt;
&lt;/div&gt;
&lt;div class=&quot;arrow&quot;&gt;→&lt;/div&gt;
&lt;div class=&quot;stage success&quot;&gt;
&lt;div class=&quot;stage-icon&quot;&gt;��&lt;/div&gt;
&lt;div class=&quot;stage-name&quot;&gt;Build &amp; Push&lt;/div&gt;
&lt;div class=&quot;stage-status&quot;&gt;✓ pushed&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;!-- APP --&gt;
&lt;div class=&quot;panel&quot; id=&quot;panel-app&quot;&gt;
&lt;h2&gt;� Модуль застосунку&lt;/h2&gt;
&lt;p&gt;Основний модуль &lt;code style=&quot;color:#a5d6ff&quot;&gt;app/calculator.py&lt;/code&gt; реалізує клас
&lt;code style=&quot;color:#d2a8ff&quot;&gt;Calculator&lt;/code&gt; з базовими математичними операціями та
обробкою виключень.&lt;/p&gt;
&lt;div class=&quot;code-block&quot;&gt;
&lt;div class=&quot;code-header&quot;&gt;
&lt;span class=&quot;filename&quot;&gt;app/calculator.py&lt;/span&gt;
&lt;span class=&quot;lang-badge&quot;&gt;Python&lt;/span&gt;
&lt;/div&gt;
&lt;div class=&quot;code-body&quot;&gt;&lt;span class=&quot;cm&quot;&gt;# app/calculator.py&lt;/span&gt;
&lt;span class=&quot;cm&quot;&gt;&quot;&quot;&quot;Модуль калькулятора для демонстрації CI/CD пайплайну.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;import&lt;/span&gt; math
&lt;span class=&quot;kw&quot;&gt;from&lt;/span&gt; typing &lt;span class=&quot;kw&quot;&gt;import&lt;/span&gt; Union

Number = Union[&lt;span class=&quot;nm&quot;&gt;int&lt;/span&gt;, &lt;span class=&quot;nm&quot;&gt;float&lt;/span&gt;]

&lt;span class=&quot;kw&quot;&gt;class&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;Calculator&lt;/span&gt;:
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Клас для виконання математичних операцій.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;add&lt;/span&gt;(&lt;span class=&quot;nm&quot;&gt;self&lt;/span&gt;, a:
Number, b: Number) -&gt; Number:
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Додавання двох чисел.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;return&lt;/span&gt; a + b
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;subtract&lt;/span&gt;(&lt;span class=&quot;nm&quot;&gt;self&lt;/span&gt;,
a: Number, b: Number) -&gt; Number:
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Віднімання двох чисел.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;return&lt;/span&gt; a - b
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;multiply&lt;/span&gt;(&lt;span class=&quot;nm&quot;&gt;self&lt;/span&gt;,
a: Number, b: Number) -&gt; Number:
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Множення двох чисел.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;return&lt;/span&gt; a * b
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;divide&lt;/span&gt;(&lt;span class=&quot;nm&quot;&gt;self&lt;/span&gt;,
a: Number, b: Number) -&gt; &lt;span class=&quot;nm&quot;&gt;float&lt;/span&gt;:
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Ділення двох чисел.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;if&lt;/span&gt; b == &lt;span class=&quot;nm&quot;&gt;0&lt;/span&gt;:
&lt;span class=&quot;kw&quot;&gt;raise&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;ValueError&lt;/span&gt;(&lt;span
class=&quot;st&quot;&gt;&quot;Ділення на нуль неможливе!&quot;&lt;/span&gt;)
&lt;span class=&quot;kw&quot;&gt;return&lt;/span&gt; a / b
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;sqrt&lt;/span&gt;(&lt;span class=&quot;nm&quot;&gt;self&lt;/span&gt;, a:
Number) -&gt; &lt;span class=&quot;nm&quot;&gt;float&lt;/span&gt;:
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Квадратний корінь числа.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;if&lt;/span&gt; a &lt; &lt;span class=&quot;nm&quot;&gt;0&lt;/span&gt;:
&lt;span class=&quot;kw&quot;&gt;raise&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;ValueError&lt;/span&gt;(&lt;span
class=&quot;st&quot;&gt;&quot;Корінь з від&#39;ємного числа неможливий!&quot;&lt;/span&gt;)
&lt;span class=&quot;kw&quot;&gt;return&lt;/span&gt; math.sqrt(a)
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;power&lt;/span&gt;(&lt;span class=&quot;nm&quot;&gt;self&lt;/span&gt;,
base: Number, exp: Number) -&gt; Number:
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Піднесення до степеня.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;return&lt;/span&gt; base ** exp&lt;/div&gt;
&lt;/div&gt;
&lt;div class=&quot;code-block&quot;&gt;
&lt;div class=&quot;code-header&quot;&gt;
&lt;span class=&quot;filename&quot;&gt;requirements.txt&lt;/span&gt;
&lt;span class=&quot;lang-badge&quot;&gt;Text&lt;/span&gt;
&lt;/div&gt;
&lt;div class=&quot;code-body&quot;&gt;pytest==8.1.1

pytest-cov==5.0.0
flake8==7.0.0
black==24.3.0&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;!-- TESTS --&gt;
&lt;div class=&quot;panel&quot; id=&quot;panel-tests&quot;&gt;
&lt;h2&gt;� Модуль тестування&lt;/h2&gt;
&lt;p&gt;Файл &lt;code style=&quot;color:#a5d6ff&quot;&gt;tests/test_calculator.py&lt;/code&gt; містить 8 unit-тестів, що
перевіряють коректність усіх методів класу &lt;code style=&quot;color:#d2a8ff&quot;&gt;Calculator&lt;/code&gt;,
включаючи граничні випадки та виключення.&lt;/p&gt;
&lt;div class=&quot;code-block&quot;&gt;
&lt;div class=&quot;code-header&quot;&gt;
&lt;span class=&quot;filename&quot;&gt;tests/test_calculator.py&lt;/span&gt;
&lt;span class=&quot;lang-badge&quot;&gt;Python&lt;/span&gt;
&lt;/div&gt;
&lt;div class=&quot;code-body&quot;&gt;&lt;span class=&quot;cm&quot;&gt;# tests/test_calculator.py&lt;/span&gt;
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Unit-тести для модуля Calculator.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;import&lt;/span&gt; pytest
&lt;span class=&quot;kw&quot;&gt;from&lt;/span&gt; app.calculator &lt;span class=&quot;kw&quot;&gt;import&lt;/span&gt; Calculator

&lt;span class=&quot;dc&quot;&gt;@pytest.fixture&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;calc&lt;/span&gt;():
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Фікстура — екземпляр Calculator для кожного тесту.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;return&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;Calculator&lt;/span&gt;()

&lt;span class=&quot;kw&quot;&gt;class&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;TestCalculator&lt;/span&gt;:
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;test_add_integers&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;self&lt;/span&gt;, calc):
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Тест: додавання цілих чисел.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;assert&lt;/span&gt; calc.&lt;span class=&quot;fn&quot;&gt;add&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;3&lt;/span&gt;, &lt;span class=&quot;nm&quot;&gt;5&lt;/span&gt;) == &lt;span class=&quot;nm&quot;&gt;8&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;test_add_floats&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;self&lt;/span&gt;, calc):
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Тест: додавання дійсних чисел.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;assert&lt;/span&gt; calc.&lt;span class=&quot;fn&quot;&gt;add&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;1.5&lt;/span&gt;, &lt;span class=&quot;nm&quot;&gt;2.5&lt;/span&gt;) == pytest.approx(&lt;span
class=&quot;nm&quot;&gt;4.0&lt;/span&gt;)
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;test_subtract&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;self&lt;/span&gt;, calc):
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Тест: віднімання.&quot;&quot;&quot;&lt;/span&gt;

&lt;span class=&quot;kw&quot;&gt;assert&lt;/span&gt; calc.&lt;span class=&quot;fn&quot;&gt;subtract&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;10&lt;/span&gt;, &lt;span class=&quot;nm&quot;&gt;4&lt;/span&gt;) == &lt;span class=&quot;nm&quot;&gt;6&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;test_multiply&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;self&lt;/span&gt;, calc):
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Тест: множення.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;assert&lt;/span&gt; calc.&lt;span class=&quot;fn&quot;&gt;multiply&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;3&lt;/span&gt;, &lt;span class=&quot;nm&quot;&gt;7&lt;/span&gt;) == &lt;span class=&quot;nm&quot;&gt;21&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;test_divide_normal&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;self&lt;/span&gt;, calc):
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Тест: звичайне ділення.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;assert&lt;/span&gt; calc.&lt;span class=&quot;fn&quot;&gt;divide&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;10&lt;/span&gt;, &lt;span class=&quot;nm&quot;&gt;2&lt;/span&gt;) == pytest.approx(&lt;span
class=&quot;nm&quot;&gt;5.0&lt;/span&gt;)
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;test_divide_by_zero&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;self&lt;/span&gt;, calc):
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Тест: ділення на нуль — очікується ValueError.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;with&lt;/span&gt; pytest.&lt;span class=&quot;fn&quot;&gt;raises&lt;/span&gt;(ValueError,
match=&lt;span class=&quot;st&quot;&gt;&quot;Ділення на нуль&quot;&lt;/span&gt;):
calc.&lt;span class=&quot;fn&quot;&gt;divide&lt;/span&gt;(&lt;span class=&quot;nm&quot;&gt;5&lt;/span&gt;, &lt;span
class=&quot;nm&quot;&gt;0&lt;/span&gt;)
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;test_sqrt_positive&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;self&lt;/span&gt;, calc):
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Тест: квадратний корінь з додатного числа.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;assert&lt;/span&gt; calc.&lt;span class=&quot;fn&quot;&gt;sqrt&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;16&lt;/span&gt;) == pytest.approx(&lt;span class=&quot;nm&quot;&gt;4.0&lt;/span&gt;)
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;test_sqrt_negative&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;self&lt;/span&gt;, calc):
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Тест: корінь з від&#39;ємного числа — очікується ValueError.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;with&lt;/span&gt; pytest.&lt;span class=&quot;fn&quot;&gt;raises&lt;/span&gt;(ValueError):
calc.&lt;span class=&quot;fn&quot;&gt;sqrt&lt;/span&gt;(-&lt;span class=&quot;nm&quot;&gt;9&lt;/span&gt;)
&lt;span class=&quot;kw&quot;&gt;def&lt;/span&gt; &lt;span class=&quot;fn&quot;&gt;test_power&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;self&lt;/span&gt;, calc):
&lt;span class=&quot;st&quot;&gt;&quot;&quot;&quot;Тест: піднесення до степеня.&quot;&quot;&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;assert&lt;/span&gt; calc.&lt;span class=&quot;fn&quot;&gt;power&lt;/span&gt;(&lt;span
class=&quot;nm&quot;&gt;2&lt;/span&gt;, &lt;span class=&quot;nm&quot;&gt;8&lt;/span&gt;) == &lt;span class=&quot;nm&quot;&gt;256&lt;/span&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;!-- PIPELINE --&gt;
&lt;div class=&quot;panel&quot; id=&quot;panel-pipeline&quot;&gt;
&lt;h2&gt;� Конфігурація GitHub Actions&lt;/h2&gt;
&lt;p&gt;Файл &lt;code style=&quot;color:#a5d6ff&quot;&gt;.github/workflows/ci-cd.yml&lt;/code&gt; описує повний
пайплайн: перевірку якості коду, тестування з покриттям та збірку Docker-образу.&lt;/p&gt;

&lt;div class=&quot;code-block&quot;&gt;
&lt;div class=&quot;code-header&quot;&gt;
&lt;span class=&quot;filename&quot;&gt;.github/workflows/ci-cd.yml&lt;/span&gt;
&lt;span class=&quot;lang-badge&quot;&gt;YAML&lt;/span&gt;
&lt;/div&gt;
&lt;div class=&quot;code-body&quot;&gt;&lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;CI/CD
Pipeline&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;on&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;push&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;branches&lt;/span&gt;: [ &lt;span class=&quot;st&quot;&gt;&quot;main&quot;&lt;/span&gt;, &lt;span
class=&quot;st&quot;&gt;&quot;develop&quot;&lt;/span&gt; ]
&lt;span class=&quot;nm&quot;&gt;pull_request&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;branches&lt;/span&gt;: [ &lt;span class=&quot;st&quot;&gt;&quot;main&quot;&lt;/span&gt; ]
&lt;span class=&quot;nm&quot;&gt;env&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;PYTHON_VERSION&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;&quot;3.11&quot;&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;IMAGE_NAME&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;ci-cd-demo&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;jobs&lt;/span&gt;:
&lt;span class=&quot;cm&quot;&gt;# ── Етап 1: Перевірка якості коду
──────────────────────&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;lint&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;�� Code Quality Check&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;runs-on&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;ubuntu-latest&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;steps&lt;/span&gt;:
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Checkout repository&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;uses&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;actions/checkout@v4&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Set up Python&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;uses&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;actions/setup-python@v5&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;with&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;python-version&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;${{ env.PYTHON_VERSION
}}&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;cache&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;&#39;pip&#39;&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Install linting tools&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;run&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;pip install flake8 black&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Run Black (format check)&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;run&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;black --check --diff app/ tests/&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Run Flake8 (style check)&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;run&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;flake8 app/ tests/ --max-line-
length=88&lt;/span&gt;
&lt;span class=&quot;cm&quot;&gt;# ── Етап 2: Тестування
─────────────────────────────────&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;test&lt;/span&gt;:

&lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;�� Run Tests&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;runs-on&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;ubuntu-latest&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;needs&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;lint&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;steps&lt;/span&gt;:
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Checkout repository&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;uses&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;actions/checkout@v4&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Set up Python&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;uses&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;actions/setup-python@v5&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;with&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;python-version&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;${{ env.PYTHON_VERSION
}}&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;cache&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;&#39;pip&#39;&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Install dependencies&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;run&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;pip install -r requirements.txt&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Run pytest with coverage&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;run&lt;/span&gt;: |
&lt;span class=&quot;st&quot;&gt;pytest tests/ -v \
--cov=app \
--cov-report=xml \
--cov-report=term-missing \
--cov-fail-under=80&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Upload coverage report&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;uses&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;actions/upload-artifact@v4&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;with&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;coverage-report&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;path&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;coverage.xml&lt;/span&gt;
&lt;span class=&quot;cm&quot;&gt;# ── Етап 3: Збірка Docker-образу
───────────────────────&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;build&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;�� Build Docker Image&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;runs-on&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;ubuntu-latest&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;needs&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;test&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;steps&lt;/span&gt;:
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Checkout repository&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;uses&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;actions/checkout@v4&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Build Docker image&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;run&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;docker build -t ${{ env.IMAGE_NAME }}:${{
github.sha }} .&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Log in to Docker Hub&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;if&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;github.ref == &#39;refs/heads/main&#39;&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;uses&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;docker/login-action@v3&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;with&lt;/span&gt;:

&lt;span class=&quot;nm&quot;&gt;username&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;${{
secrets.DOCKERHUB_USERNAME }}&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;password&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;${{ secrets.DOCKERHUB_TOKEN
}}&lt;/span&gt;
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Push to Docker Hub&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;if&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;github.ref == &#39;refs/heads/main&#39;&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;run&lt;/span&gt;: |
&lt;span class=&quot;st&quot;&gt;docker tag ${{ env.IMAGE_NAME }}:${{ github.sha }} \
${{ secrets.DOCKERHUB_USERNAME }}/${{ env.IMAGE_NAME }}:latest
docker push ${{ secrets.DOCKERHUB_USERNAME }}/${{ env.IMAGE_NAME
}}:latest&lt;/span&gt;
&lt;span class=&quot;cm&quot;&gt;# ── Етап 4: Сповіщення
─────────────────────────────────&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;notify&lt;/span&gt;:
&lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;�� Notify&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;runs-on&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;ubuntu-latest&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;needs&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;build&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;if&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;always()&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;steps&lt;/span&gt;:
- &lt;span class=&quot;nm&quot;&gt;name&lt;/span&gt;: &lt;span class=&quot;st&quot;&gt;Pipeline summary&lt;/span&gt;
&lt;span class=&quot;nm&quot;&gt;run&lt;/span&gt;: |
&lt;span class=&quot;st&quot;&gt;echo &quot;✅ Pipeline completed!&quot;
echo &quot;Branch: ${{ github.ref_name }}&quot;
echo &quot;Commit: ${{ github.sha }}&quot;
echo &quot;Author: ${{ github.actor }}&quot;&lt;/span&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;!-- DOCKER --&gt;
&lt;div class=&quot;panel&quot; id=&quot;panel-docker&quot;&gt;
&lt;h2&gt;� Контейнеризація (Docker)&lt;/h2&gt;
&lt;p&gt;Dockerfile реалізує &lt;strong style=&quot;color:#f0f6fc&quot;&gt;multi-stage build&lt;/strong&gt; — окремі стадії
для тестування та фінального образу, що зменшує розмір production-образу.&lt;/p&gt;
&lt;div class=&quot;code-block&quot;&gt;
&lt;div class=&quot;code-header&quot;&gt;
&lt;span class=&quot;filename&quot;&gt;Dockerfile&lt;/span&gt;
&lt;span class=&quot;lang-badge&quot;&gt;Docker&lt;/span&gt;
&lt;/div&gt;
&lt;div class=&quot;code-body&quot;&gt;&lt;span class=&quot;cm&quot;&gt;# ── Stage 1: Тестування
────────────────────────────────&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;FROM&lt;/span&gt; &lt;span class=&quot;st&quot;&gt;python:3.11-slim AS tester&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;WORKDIR&lt;/span&gt; /app
&lt;span class=&quot;cm&quot;&gt;# Копіюємо залежності та встановлюємо їх&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;COPY&lt;/span&gt; requirements.txt .
&lt;span class=&quot;kw&quot;&gt;RUN&lt;/span&gt; pip install --no-cache-dir -r requirements.txt

&lt;span class=&quot;cm&quot;&gt;# Копіюємо весь проєкт&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;COPY&lt;/span&gt; . .
&lt;span class=&quot;cm&quot;&gt;# Запускаємо тести (збірка зупиниться якщо тести не пройдуть)&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;RUN&lt;/span&gt; pytest tests/ -v --cov=app --cov-fail-under=80

&lt;span class=&quot;cm&quot;&gt;# ── Stage 2: Production образ
──────────────────────────&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;FROM&lt;/span&gt; &lt;span class=&quot;st&quot;&gt;python:3.11-slim AS production&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;WORKDIR&lt;/span&gt; /app
&lt;span class=&quot;cm&quot;&gt;# Мітки образу&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;LABEL&lt;/span&gt; maintainer=&lt;span class=&quot;st&quot;&gt;&quot;student@university.edu&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;LABEL&lt;/span&gt; version=&lt;span class=&quot;st&quot;&gt;&quot;1.0.0&quot;&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;LABEL&lt;/span&gt; description=&lt;span class=&quot;st&quot;&gt;&quot;CI/CD Demo — Calculator
App&quot;&lt;/span&gt;
&lt;span class=&quot;cm&quot;&gt;# Копіюємо лише необхідні файли&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;COPY&lt;/span&gt; --from=tester /app/app ./app
&lt;span class=&quot;kw&quot;&gt;COPY&lt;/span&gt; requirements.txt .
&lt;span class=&quot;cm&quot;&gt;# Встановлюємо лише production залежності&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;RUN&lt;/span&gt; pip install --no-cache-dir flask==3.0.3 &amp;&amp; \
&lt;span class=&quot;cm&quot;&gt;# Видаляємо кеш pip&lt;/span&gt;
rm -rf /root/.cache/pip
&lt;span class=&quot;cm&quot;&gt;# Створюємо непривілейованого користувача&lt;/span&gt;
&lt;span class=&quot;kw&quot;&gt;RUN&lt;/span&gt; useradd --create-home appuser
&lt;span class=&quot;kw&quot;&gt;USER&lt;/span&gt; appuser
&lt;span class=&quot;kw&quot;&gt;EXPOSE&lt;/span&gt; 5000
&lt;span class=&quot;kw&quot;&gt;CMD&lt;/span&gt; [&lt;span class=&quot;st&quot;&gt;&quot;python&quot;&lt;/span&gt;, &lt;span class=&quot;st&quot;&gt;&quot;-
m&quot;&lt;/span&gt;, &lt;span class=&quot;st&quot;&gt;&quot;flask&quot;&lt;/span&gt;, &lt;span class=&quot;st&quot;&gt;&quot;--app&quot;&lt;/span&gt;, &lt;span
class=&quot;st&quot;&gt;&quot;app&quot;&lt;/span&gt;, &lt;span class=&quot;st&quot;&gt;&quot;run&quot;&lt;/span&gt;, &lt;span class=&quot;st&quot;&gt;&quot;--
host=0.0.0.0&quot;&lt;/span&gt;]&lt;/div&gt;
&lt;/div&gt;
&lt;div class=&quot;card&quot;&gt;
&lt;h3&gt;� Команди для локального запуску&lt;/h3&gt;
&lt;div class=&quot;code-body&quot; style=&quot;background:transparent; padding:0; font-size:13px; white-
space:pre; color:#c9d1d9&quot;&gt;
&lt;span class=&quot;cm&quot;&gt;# Клонування репозиторію&lt;/span&gt;
git clone https://github.com/username/ci-cd-demo.git
&lt;span class=&quot;kw&quot;&gt;cd&lt;/span&gt; ci-cd-demo
&lt;span class=&quot;cm&quot;&gt;# Встановлення залежностей&lt;/span&gt;

pip install -r requirements.txt
&lt;span class=&quot;cm&quot;&gt;# Запуск тестів локально&lt;/span&gt;
pytest tests/ -v --cov=app --cov-report=term-missing
&lt;span class=&quot;cm&quot;&gt;# Перевірка стилю коду&lt;/span&gt;
black --check app/ tests/
flake8 app/ tests/
&lt;span class=&quot;cm&quot;&gt;# Збірка Docker-образу&lt;/span&gt;
docker build -t ci-cd-demo:local .
&lt;span class=&quot;cm&quot;&gt;# Запуск контейнера&lt;/span&gt;
docker run -p 5000:5000 ci-cd-demo:local
&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;!-- SIMULATE --&gt;
&lt;div class=&quot;panel&quot; id=&quot;panel-simulate&quot;&gt;
&lt;h2&gt;▶️ Симуляція виконання пайплайну&lt;/h2&gt;
&lt;p&gt;Натисніть кнопку для симуляції запуску CI/CD пайплайну та перегляду логів
виконання.&lt;/p&gt;
&lt;div style=&quot;margin-bottom:20px; display:flex; gap:12px; align-items:center; flex-wrap:wrap;&quot;&gt;
&lt;button class=&quot;run-btn&quot; id=&quot;runBtn&quot; onclick=&quot;runSimulation()&quot;&gt;▶ Запустити
пайплайн&lt;/button&gt;
&lt;span id=&quot;statusBadge&quot; style=&quot;display:none;&quot; class=&quot;badge badge-orange&quot;&gt;⏳
Виконується...&lt;/span&gt;
&lt;/div&gt;
&lt;div class=&quot;pipeline&quot; id=&quot;simPipeline&quot;&gt;
&lt;div class=&quot;stage&quot; id=&quot;s1&quot;&gt;&lt;div class=&quot;stage-icon&quot;&gt;��&lt;/div&gt;&lt;div class=&quot;stage-
name&quot;&gt;Lint&lt;/div&gt;&lt;div class=&quot;stage-status&quot; id=&quot;s1s&quot;&gt;— очікування&lt;/div&gt;&lt;/div&gt;
&lt;div class=&quot;arrow&quot;&gt;→&lt;/div&gt;
&lt;div class=&quot;stage&quot; id=&quot;s2&quot;&gt;&lt;div class=&quot;stage-icon&quot;&gt;��&lt;/div&gt;&lt;div class=&quot;stage-
name&quot;&gt;Test&lt;/div&gt;&lt;div class=&quot;stage-status&quot; id=&quot;s2s&quot;&gt;— очікування&lt;/div&gt;&lt;/div&gt;
&lt;div class=&quot;arrow&quot;&gt;→&lt;/div&gt;
&lt;div class=&quot;stage&quot; id=&quot;s3&quot;&gt;&lt;div class=&quot;stage-icon&quot;&gt;��&lt;/div&gt;&lt;div class=&quot;stage-
name&quot;&gt;Build&lt;/div&gt;&lt;div class=&quot;stage-status&quot; id=&quot;s3s&quot;&gt;— очікування&lt;/div&gt;&lt;/div&gt;
&lt;div class=&quot;arrow&quot;&gt;→&lt;/div&gt;
&lt;div class=&quot;stage&quot; id=&quot;s4&quot;&gt;&lt;div class=&quot;stage-icon&quot;&gt;��&lt;/div&gt;&lt;div class=&quot;stage-
name&quot;&gt;Notify&lt;/div&gt;&lt;div class=&quot;stage-status&quot; id=&quot;s4s&quot;&gt;— очікування&lt;/div&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;div class=&quot;log-output&quot; id=&quot;logOutput&quot;&gt;
&lt;span class=&quot;log-dim&quot;&gt;Очікування запуску пайплайну...&lt;/span&gt;
&lt;/div&gt;
&lt;/div&gt;

&lt;/div&gt;
&lt;script&gt;
function showTab(name) {
document.querySelectorAll(&#39;.tab&#39;).forEach((t,i) =&gt; t.classList.remove(&#39;active&#39;));
document.querySelectorAll(&#39;.panel&#39;).forEach(p =&gt; p.classList.remove(&#39;active&#39;));
const tabs = [&#39;overview&#39;,&#39;app&#39;,&#39;tests&#39;,&#39;pipeline&#39;,&#39;docker&#39;,&#39;simulate&#39;];
const idx = tabs.indexOf(name);
document.querySelectorAll(&#39;.tab&#39;)[idx].classList.add(&#39;active&#39;);
document.getElementById(&#39;panel-&#39; + name).classList.add(&#39;active&#39;);
}
const logs = [
{ t: 200, cls: &#39;log-info&#39;, msg: &#39;� Запуск пайплайну: CI/CD Pipeline&#39; },
{ t: 400, cls: &#39;log-dim&#39;, msg: &#39; Гілка: main | Коміт: a3f9d12&#39; },
{ t: 600, cls: &#39;log-dim&#39;, msg: &#39; Автор: student@university.edu&#39; },
{ t: 900, cls: &#39;log-info&#39;, msg: &#39;\n── JOB: �� Code Quality Check ──────────&#39; },
{ t: 1100, cls: &#39;log-dim&#39;, msg: &#39; ✓ Checkout repository&#39; },
{ t: 1400, cls: &#39;log-dim&#39;, msg: &#39; ✓ Set up Python 3.11&#39; },
{ t: 1700, cls: &#39;log-dim&#39;, msg: &#39; ✓ Install linting tools&#39; },
{ t: 2000, cls: &#39;log-ok&#39;, msg: &#39; ✓ Black: All files are well-formatted!&#39; },
{ t: 2300, cls: &#39;log-ok&#39;, msg: &#39; ✓ Flake8: no issues found (0 warnings)&#39; },
{ t: 2500, cls: &#39;log-ok&#39;, msg: &#39; ✅ lint — SUCCESS (8s)&#39; },
{ t: 2800, cls: &#39;log-info&#39;, msg: &#39;\n── JOB: �� Run Tests ───────────────────&#39; },
{ t: 3000, cls: &#39;log-dim&#39;, msg: &#39; ✓ Checkout repository&#39; },
{ t: 3200, cls: &#39;log-dim&#39;, msg: &#39; ✓ Set up Python 3.11 (cached)&#39; },
{ t: 3400, cls: &#39;log-dim&#39;, msg: &#39; ✓ Install dependencies&#39; },
{ t: 3600, cls: &#39;log-dim&#39;, msg: &#39; Running pytest...&#39; },
{ t: 3800, cls: &#39;log-ok&#39;, msg: &#39; PASSED
tests/test_calculator.py::TestCalculator::test_add_integers&#39; },
{ t: 3950, cls: &#39;log-ok&#39;, msg: &#39; PASSED
tests/test_calculator.py::TestCalculator::test_add_floats&#39; },
{ t: 4100, cls: &#39;log-ok&#39;, msg: &#39; PASSED tests/test_calculator.py::TestCalculator::test_subtract&#39; },
{ t: 4250, cls: &#39;log-ok&#39;, msg: &#39; PASSED tests/test_calculator.py::TestCalculator::test_multiply&#39; },
{ t: 4400, cls: &#39;log-ok&#39;, msg: &#39; PASSED
tests/test_calculator.py::TestCalculator::test_divide_normal&#39; },
{ t: 4550, cls: &#39;log-ok&#39;, msg: &#39; PASSED
tests/test_calculator.py::TestCalculator::test_divide_by_zero&#39; },
{ t: 4700, cls: &#39;log-ok&#39;, msg: &#39; PASSED
tests/test_calculator.py::TestCalculator::test_sqrt_positive&#39; },
{ t: 4850, cls: &#39;log-ok&#39;, msg: &#39; PASSED
tests/test_calculator.py::TestCalculator::test_sqrt_negative&#39; },
{ t: 5000, cls: &#39;log-ok&#39;, msg: &#39; PASSED tests/test_calculator.py::TestCalculator::test_power&#39; },
{ t: 5200, cls: &#39;log-info&#39;, msg: &#39; Coverage: app/calculator.py 100%&#39; },
{ t: 5400, cls: &#39;log-ok&#39;, msg: &#39; ✅ 9 passed in 0.43s | Coverage: 100%&#39; },
{ t: 5600, cls: &#39;log-ok&#39;, msg: &#39; ✅ test — SUCCESS (18s)&#39; },
{ t: 5900, cls: &#39;log-info&#39;, msg: &#39;\n── JOB: �� Build Docker Image ──────────&#39; },

{ t: 6100, cls: &#39;log-dim&#39;, msg: &#39; ✓ Checkout repository&#39; },
{ t: 6400, cls: &#39;log-dim&#39;, msg: &#39; Building Docker image...&#39; },
{ t: 6700, cls: &#39;log-dim&#39;, msg: &#39; Step 1/12 : FROM python:3.11-slim AS tester&#39; },
{ t: 6900, cls: &#39;log-dim&#39;, msg: &#39; Step 5/12 : RUN pytest tests/ -v ...&#39; },
{ t: 7100, cls: &#39;log-ok&#39;, msg: &#39; All tests passed inside container ✓&#39; },
{ t: 7300, cls: &#39;log-dim&#39;, msg: &#39; Step 8/12 : FROM python:3.11-slim AS production&#39; },
{ t: 7500, cls: &#39;log-ok&#39;, msg: &#39; ✓ Image built: ci-cd-demo:a3f9d12&#39; },
{ t: 7700, cls: &#39;log-ok&#39;, msg: &#39; ✓ Pushed to Docker Hub: latest&#39; },
{ t: 7900, cls: &#39;log-ok&#39;, msg: &#39; ✅ build — SUCCESS (14s)&#39; },
{ t: 8200, cls: &#39;log-info&#39;, msg: &#39;\n── JOB: �� Notify ──────────────────────&#39; },
{ t: 8400, cls: &#39;log-ok&#39;, msg: &#39; ✅ Pipeline completed!&#39; },
{ t: 8600, cls: &#39;log-ok&#39;, msg: &#39; Branch: main | Commit: a3f9d12&#39; },
{ t: 8800, cls: &#39;log-ok&#39;, msg: &#39;\n�� PIPELINE SUCCESS — Total time: ~45s&#39; },
];
const stageTimings = [
{ id: &#39;s1&#39;, statusId: &#39;s1s&#39;, runAt: 900, doneAt: 2500, okText: &#39;✓ passed&#39; },
{ id: &#39;s2&#39;, statusId: &#39;s2s&#39;, runAt: 2800, doneAt: 5600, okText: &#39;✓ 9/9&#39; },
{ id: &#39;s3&#39;, statusId: &#39;s3s&#39;, runAt: 5900, doneAt: 7900, okText: &#39;✓ pushed&#39; },
{ id: &#39;s4&#39;, statusId: &#39;s4s&#39;, runAt: 8200, doneAt: 8800, okText: &#39;✓ done&#39; },
];
function runSimulation() {
const btn = document.getElementById(&#39;runBtn&#39;);
const badge = document.getElementById(&#39;statusBadge&#39;);
const log = document.getElementById(&#39;logOutput&#39;);
btn.disabled = true;
badge.style.display = &#39;inline-block&#39;;
log.innerHTML = &#39;&#39;;
stageTimings.forEach(s =&gt; {
const el = document.getElementById(s.id);
const st = document.getElementById(s.statusId);
el.className = &#39;stage&#39;;
st.textContent = &#39;— очікування&#39;;
});
logs.forEach(entry =&gt; {
setTimeout(() =&gt; {
const span = document.createElement(&#39;span&#39;);
span.className = entry.cls;
span.textContent = entry.msg + &#39;\n&#39;;
log.appendChild(span);
log.scrollTop = log.scrollHeight;
}, entry.t);
});
stageTimings.forEach(s =&gt; {

setTimeout(() =&gt; {
document.getElementById(s.id).className = &#39;stage running&#39;;
document.getElementById(s.statusId).textContent = &#39;⏳ running...&#39;;
}, s.runAt);
setTimeout(() =&gt; {
document.getElementById(s.id).className = &#39;stage success&#39;;
document.getElementById(s.statusId).textContent = s.okText;
}, s.doneAt);
});
setTimeout(() =&gt; {
btn.disabled = false;
badge.style.display = &#39;none&#39;;
}, 9000);
}
&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
