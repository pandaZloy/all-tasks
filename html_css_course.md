# 🎨 HTML & CSS: ОТ ОСНОВ ДО МАСТЕРСТВА
## Курс с акцентом на сложные эффекты, анимации и нестандартную верстку

---

## 📅 **СТРУКТУРА КУРСА**

### **РАЗДЕЛ 1: ОСНОВЫ HTML/CSS** (Быстрый обзор)
- Семантический HTML5
- CSS селекторы и специфичность
- Box Model и позиционирование
- **15 задач**

### **РАЗДЕЛ 2: ПРОДВИНУТЫЙ CSS**
- Flexbox и Grid на максимум
- Custom Properties (CSS переменные)
- Calc() и математика в CSS
- **20 задач**

### **РАЗДЕЛ 3: АНИМАЦИИ И ТРАНСФОРМАЦИИ**
- CSS Transitions
- CSS Animations и @keyframes
- Transform 2D/3D
- **25 задач со сложными эффектами**

### **РАЗДЕЛ 4: НЕСТАНДАРТНЫЕ ЭЛЕМЕНТЫ**
- Кастомные формы и инпуты
- Необычные навигации
- Креативные карточки и лейауты
- **20 задач**

### **РАЗДЕЛ 5: СОВРЕМЕННЫЕ ТЕХНИКИ**
- CSS Filters и Blend Modes
- Clip-path и Masks
- Backdrop Filter
- **15 задач**

### **РАЗДЕЛ 6: ИНТЕРАКТИВНЫЕ КОМПОНЕНТЫ**
- Hover эффекты и микроанимации
- Parallax и Scroll эффекты
- Морфинг и трансформации
- **20 задач**

### **РАЗДЕЛ 7: ПРАКТИЧЕСКИЕ ПРОЕКТЫ**
- Портфолио с эффектами
- Лендинг с анимациями
- Интерактивная галерея
- **10 проектов**

---

# 📝 **РАЗДЕЛ 1: ОСНОВЫ HTML/CSS** (15 задач)

## Задача HTML-1: Семантическая структура страницы
**Уровень сложности:** ⭐  
**Концепции:** HTML5 семантика, accessibility

**Условие:**
Создайте семантически правильную структуру веб-страницы.

**Требования:**
```html
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Semantic Page</title>
</head>
<body>
    <header>
        <nav>
            <!-- Навигация -->
        </nav>
    </header>
    
    <main>
        <article>
            <header>
                <h1>Заголовок статьи</h1>
                <time datetime="2025-11-02">2 ноября 2025</time>
            </header>
            <section>
                <!-- Контент секции -->
            </section>
            <aside>
                <!-- Боковая информация -->
            </aside>
            <footer>
                <!-- Футер статьи -->
            </footer>
        </article>
    </main>
    
    <footer>
        <!-- Футер страницы -->
    </footer>
</body>
</html>
```

**Дополнительно:**
- Используйте ARIA атрибуты для доступности
- Добавьте микроразметку Schema.org

---

## Задача CSS-1: CSS Grid - Святой Грааль лейаут
**Уровень сложности:** ⭐⭐  
**Концепции:** CSS Grid, grid-template-areas

**Условие:**
Создайте классический "Holy Grail" лейаут используя CSS Grid.

**CSS:**
```css
.container {
    display: grid;
    grid-template-areas:
        "header header header"
        "nav main aside"
        "footer footer footer";
    grid-template-columns: 200px 1fr 200px;
    grid-template-rows: auto 1fr auto;
    min-height: 100vh;
    gap: 20px;
}

header { grid-area: header; }
nav { grid-area: nav; }
main { grid-area: main; }
aside { grid-area: aside; }
footer { grid-area: footer; }

@media (max-width: 768px) {
    .container {
        grid-template-areas:
            "header"
            "nav"
            "main"
            "aside"
            "footer";
        grid-template-columns: 1fr;
    }
}
```

**Требования:**
- Header, footer на всю ширину
- Nav слева, aside справа
- Main в центре с гибкой шириной
- Адаптивность для мобильных

---

## Задача CSS-2: Flexbox - сложные лейауты
**Уровень сложности:** ⭐⭐  
**Концепции:** Flexbox, flex-grow, flex-shrink, flex-basis

**Условие:**
Создайте 5 различных лейаутов используя только Flexbox.

**Лейауты:**
1. **Равные колонки** с разным контентом
2. **Sticky footer** (футер всегда внизу)
3. **Карточная сетка** с автоматическим переносом
4. **Навигация** с лого слева и меню справа
5. **Pricing таблица** с выровненными элементами

**Пример pricing таблицы:**
```css
.pricing-container {
    display: flex;
    gap: 20px;
    justify-content: center;
}

.pricing-card {
    flex: 1;
    max-width: 300px;
    display: flex;
    flex-direction: column;
}

.pricing-header,
.pricing-price,
.pricing-features {
    padding: 20px;
}

.pricing-features {
    flex-grow: 1;
}

.pricing-button {
    margin-top: auto;
}
```

---

## Задача CSS-3: Custom Properties (CSS переменные)
**Уровень сложности:** ⭐⭐  
**Концепции:** --custom-properties, var(), calc()

**Условие:**
Создайте систему дизайна с CSS переменными для тем.

**CSS:**
```css
:root {
    /* Цвета */
    --primary-color: #3498db;
    --secondary-color: #2ecc71;
    --text-color: #333;
    --bg-color: #fff;
    
    /* Размеры */
    --spacing-xs: 4px;
    --spacing-sm: 8px;
    --spacing-md: 16px;
    --spacing-lg: 32px;
    --spacing-xl: 64px;
    
    /* Типографика */
    --font-size-base: 16px;
    --font-size-sm: calc(var(--font-size-base) * 0.875);
    --font-size-lg: calc(var(--font-size-base) * 1.25);
    --font-size-xl: calc(var(--font-size-base) * 1.5);
    
    /* Тени */
    --shadow-sm: 0 2px 4px rgba(0,0,0,0.1);
    --shadow-md: 0 4px 6px rgba(0,0,0,0.1);
    --shadow-lg: 0 10px 15px rgba(0,0,0,0.1);
    
    /* Радиусы */
    --radius-sm: 4px;
    --radius-md: 8px;
    --radius-lg: 16px;
}

/* Темная тема */
[data-theme="dark"] {
    --primary-color: #2980b9;
    --text-color: #ecf0f1;
    --bg-color: #2c3e50;
}

/* Использование */
.button {
    background-color: var(--primary-color);
    color: var(--bg-color);
    padding: var(--spacing-md) var(--spacing-lg);
    border-radius: var(--radius-md);
    box-shadow: var(--shadow-md);
}
```

**Требования:**
- Создайте 2 темы (светлую и темную)
- Переключение через JavaScript
- Плавные переходы между темами
- Система отступов и типографики

---

# 🎭 **РАЗДЕЛ 3: АНИМАЦИИ И ТРАНСФОРМАЦИИ** (25 задач)

## Задача ANIM-1: Плавные переходы (Transitions)
**Уровень сложности:** ⭐⭐  
**Концепции:** transition, timing-functions

**Условие:**
Создайте галерею transition эффектов для кнопок.

**CSS:**
```css
/* Базовая кнопка */
.btn {
    padding: 15px 30px;
    border: none;
    cursor: pointer;
    position: relative;
    overflow: hidden;
}

/* 1. Простой переход цвета */
.btn-fade {
    background: #3498db;
    transition: background 0.3s ease;
}
.btn-fade:hover {
    background: #2980b9;
}

/* 2. Увеличение с тенью */
.btn-grow {
    background: #2ecc71;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}
.btn-grow:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
}

/* 3. Скольжение границы */
.btn-slide-border {
    background: transparent;
    border: 2px solid #e74c3c;
    color: #e74c3c;
    transition: all 0.4s ease;
}
.btn-slide-border::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: #e74c3c;
    transition: left 0.4s ease;
    z-index: -1;
}
.btn-slide-border:hover {
    color: white;
}
.btn-slide-border:hover::before {
    left: 0;
}

/* 4. Волновой эффект */
.btn-wave {
    background: #9b59b6;
    transition: all 0.3s ease;
}
.btn-wave::after {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    width: 0;
    height: 0;
    border-radius: 50%;
    background: rgba(255,255,255,0.5);
    transform: translate(-50%, -50%);
    transition: width 0.6s, height 0.6s;
}
.btn-wave:hover::after {
    width: 300px;
    height: 300px;
}

/* 5. Неоновое свечение */
.btn-neon {
    background: #1a1a1a;
    color: #00ffff;
    border: 2px solid #00ffff;
    transition: all 0.3s ease;
    text-shadow: 0 0 5px #00ffff;
}
.btn-neon:hover {
    box-shadow: 
        0 0 5px #00ffff,
        0 0 10px #00ffff,
        0 0 20px #00ffff,
        0 0 40px #00ffff;
    transform: translateY(-2px);
}
```

**Требования:**
- Создайте 10 различных hover эффектов
- Используйте разные timing-functions
- Комбинируйте несколько свойств
- Оптимизируйте производительность (используйте transform вместо left/top)

---

## Задача ANIM-2: CSS Animations - Loading спиннеры
**Уровень сложности:** ⭐⭐⭐  
**Концепции:** @keyframes, animation, animation-timing-function

**Условие:**
Создайте коллекцию из 10 уникальных loading индикаторов.

**Примеры:**

```css
/* 1. Вращающийся круг */
.spinner-circle {
    width: 50px;
    height: 50px;
    border: 4px solid rgba(0,0,0,0.1);
    border-left-color: #3498db;
    border-radius: 50%;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    to { transform: rotate(360deg); }
}

/* 2. Пульсирующий круг */
.spinner-pulse {
    width: 50px;
    height: 50px;
    background: #3498db;
    border-radius: 50%;
    animation: pulse 1.5s ease-in-out infinite;
}

@keyframes pulse {
    0%, 100% {
        transform: scale(1);
        opacity: 1;
    }
    50% {
        transform: scale(1.5);
        opacity: 0.5;
    }
}

/* 3. Три прыгающих точки */
.spinner-dots {
    display: flex;
    gap: 10px;
}

.spinner-dots span {
    width: 15px;
    height: 15px;
    background: #3498db;
    border-radius: 50%;
    animation: bounce 1.4s infinite ease-in-out;
}

.spinner-dots span:nth-child(1) { animation-delay: -0.32s; }
.spinner-dots span:nth-child(2) { animation-delay: -0.16s; }

@keyframes bounce {
    0%, 80%, 100% {
        transform: scale(0);
    }
    40% {
        transform: scale(1);
    }
}

/* 4. Волновой спиннер */
.spinner-wave {
    display: flex;
    gap: 5px;
}

.spinner-wave span {
    width: 6px;
    height: 40px;
    background: #3498db;
    animation: wave 1.2s ease-in-out infinite;
}

.spinner-wave span:nth-child(1) { animation-delay: 0s; }
.spinner-wave span:nth-child(2) { animation-delay: 0.1s; }
.spinner-wave span:nth-child(3) { animation-delay: 0.2s; }
.spinner-wave span:nth-child(4) { animation-delay: 0.3s; }
.spinner-wave span:nth-child(5) { animation-delay: 0.4s; }

@keyframes wave {
    0%, 40%, 100% {
        transform: scaleY(0.4);
    }
    20% {
        transform: scaleY(1);
    }
}

/* 5. Orbit спиннер */
.spinner-orbit {
    position: relative;
    width: 60px;
    height: 60px;
}

.spinner-orbit::before,
.spinner-orbit::after {
    content: '';
    position: absolute;
    width: 20px;
    height: 20px;
    background: #3498db;
    border-radius: 50%;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.spinner-orbit::before {
    animation: orbit1 2s linear infinite;
}

.spinner-orbit::after {
    animation: orbit2 2s linear infinite;
}

@keyframes orbit1 {
    from {
        transform: translate(-50%, -50%) rotate(0deg) translateX(20px);
    }
    to {
        transform: translate(-50%, -50%) rotate(360deg) translateX(20px);
    }
}

@keyframes orbit2 {
    from {
        transform: translate(-50%, -50%) rotate(180deg) translateX(20px);
    }
    to {
        transform: translate(-50%, -50%) rotate(540deg) translateX(20px);
    }
}
```

**Требования:**
- 10 уникальных спиннеров
- Разные типы анимаций
- Настройка скорости
- Паузируемые анимации

---

## Задача ANIM-3: Трансформации 3D
**Уровень сложности:** ⭐⭐⭐⭐  
**Концепции:** transform-style: preserve-3d, perspective, rotateX/Y/Z

**Условие:**
Создайте 3D карточки с эффектом переворота.

**HTML:**
```html
<div class="card-container">
    <div class="card">
        <div class="card-front">
            <h3>Front Side</h3>
        </div>
        <div class="card-back">
            <h3>Back Side</h3>
        </div>
    </div>
</div>
```

**CSS:**
```css
.card-container {
    perspective: 1000px;
    width: 300px;
    height: 400px;
}

.card {
    width: 100%;
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
    transition: transform 0.8s cubic-bezier(0.4, 0.2, 0.2, 1);
}

.card:hover {
    transform: rotateY(180deg);
}

.card-front,
.card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    border-radius: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.card-front {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.card-back {
    background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    transform: rotateY(180deg);
}

/* Вариант 2: Переворот по вертикали */
.card.flip-vertical:hover {
    transform: rotateX(180deg);
}

/* Вариант 3: 3D Куб */
.cube-container {
    perspective: 1000px;
    width: 200px;
    height: 200px;
}

.cube {
    width: 100%;
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
    animation: rotateCube 10s infinite linear;
}

@keyframes rotateCube {
    from {
        transform: rotateX(0deg) rotateY(0deg);
    }
    to {
        transform: rotateX(360deg) rotateY(360deg);
    }
}

.cube-face {
    position: absolute;
    width: 200px;
    height: 200px;
    border: 2px solid #333;
    background: rgba(255, 255, 255, 0.9);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    font-weight: bold;
}

.cube-face.front  { transform: rotateY(0deg) translateZ(100px); }
.cube-face.back   { transform: rotateY(180deg) translateZ(100px); }
.cube-face.right  { transform: rotateY(90deg) translateZ(100px); }
.cube-face.left   { transform: rotateY(-90deg) translateZ(100px); }
.cube-face.top    { transform: rotateX(90deg) translateZ(100px); }
.cube-face.bottom { transform: rotateX(-90deg) translateZ(100px); }
```

**Требования:**
- Карточки с переворотом (flip)
- 3D куб с вращением
- 3D галерея (carousel)
- Книга с переворачивающимися страницами
- Интерактивный 3D объект

---

## Задача ANIM-4: Сложные keyframe анимации
**Уровень сложности:** ⭐⭐⭐⭐  
**Концепции:** Multi-step animations, animation-fill-mode

**Условие:**
Создайте сложные многоступенчатые анимации.

**Примеры:**

```css
/* 1. Анимация появления текста */
.text-reveal {
    overflow: hidden;
}

.text-reveal span {
    display: inline-block;
    opacity: 0;
    transform: translateY(100%);
    animation: slideUp 0.8s cubic-bezier(0.4, 0, 0.2, 1) forwards;
}

.text-reveal span:nth-child(1) { animation-delay: 0.1s; }
.text-reveal span:nth-child(2) { animation-delay: 0.2s; }
.text-reveal span:nth-child(3) { animation-delay: 0.3s; }

@keyframes slideUp {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* 2. Морфинг форм */
.morphing-shape {
    width: 100px;
    height: 100px;
    background: linear-gradient(45deg, #667eea, #764ba2);
    animation: morph 4s ease-in-out infinite;
}

@keyframes morph {
    0% {
        border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
        transform: rotate(0deg);
    }
    25% {
        border-radius: 30% 60% 70% 40% / 50% 60% 30% 60%;
        transform: rotate(90deg);
    }
    50% {
        border-radius: 40% 60% 60% 40% / 60% 40% 50% 50%;
        transform: rotate(180deg);
    }
    75% {
        border-radius: 70% 30% 40% 60% / 40% 70% 60% 50%;
        transform: rotate(270deg);
    }
    100% {
        border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
        transform: rotate(360deg);
    }
}

/* 3. Частицы (конфетти) */
.particle {
    position: absolute;
    width: 10px;
    height: 10px;
    background: #fff;
    animation: fall 3s linear infinite;
}

@keyframes fall {
    0% {
        transform: translateY(-100vh) rotate(0deg);
        opacity: 1;
    }
    100% {
        transform: translateY(100vh) rotate(720deg);
        opacity: 0;
    }
}

/* Генерация случайных задержек через nth-child */
.particle:nth-child(1) { left: 10%; animation-delay: 0s; }
.particle:nth-child(2) { left: 20%; animation-delay: 0.5s; }
.particle:nth-child(3) { left: 30%; animation-delay: 1s; }
/* ...и так далее */

/* 4. Печатающийся текст */
.typing-text {
    font-family: monospace;
    white-space: nowrap;
    overflow: hidden;
    border-right: 3px solid;
    width: 0;
    animation: 
        typing 3.5s steps(40) 1s forwards,
        blink 0.75s step-end infinite;
}

@keyframes typing {
    from { width: 0; }
    to { width: 100%; }
}

@keyframes blink {
    50% { border-color: transparent; }
}

/* 5. Волновой текст */
.wave-text span {
    display: inline-block;
    animation: wave 1.5s ease-in-out infinite;
}

.wave-text span:nth-child(1) { animation-delay: 0s; }
.wave-text span:nth-child(2) { animation-delay: 0.1s; }
.wave-text span:nth-child(3) { animation-delay: 0.2s; }
.wave-text span:nth-child(4) { animation-delay: 0.3s; }
.wave-text span:nth-child(5) { animation-delay: 0.4s; }

@keyframes wave {
    0%, 100% {
        transform: translateY(0px);
    }
    50% {
        transform: translateY(-20px);
    }
}
```

**Требования:**
- 5 сложных многоступенчатых анимаций
- Синхронизация нескольких анимаций
- Использование animation-fill-mode
- Паузируемость анимаций

---

## Задача ANIM-5: Параллакс эффекты
**Уровень сложности:** ⭐⭐⭐⭐  
**Концепции:** perspective, transform, scroll-based animations

**Условие:**
Создайте многослойный параллакс эффект.

**HTML:**
```html
<div class="parallax-container">
    <div class="parallax-layer layer-bg"></div>
    <div class="parallax-layer layer-mid"></div>
    <div class="parallax-layer layer-front"></div>
    <div class="content">
        <h1>Parallax Effect</h1>
    </div>
</div>
```

**CSS:**
```css
.parallax-container {
    height: 100vh;
    overflow-x: hidden;
    overflow-y: auto;
    perspective: 1px;
}

.parallax-layer {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
}

.layer-bg {
    transform: translateZ(-2px) scale(3);
    background: url('bg.jpg') center/cover;
}

.layer-mid {
    transform: translateZ(-1px) scale(2);
    background: url('mid.png') center/cover;
}

.layer-front {
    transform: translateZ(0);
    background: url('front.png') center/cover;
}

.content {
    position: relative;
    z-index: 10;
    transform: translateZ(0);
}
```

**JavaScript для продвинутого параллакса:**
```javascript
window.addEventListener('scroll', () => {
    const scrolled = window.pageYOffset;
    
    document.querySelector('.layer-bg').style.transform = 
        `translateY(${scrolled * 0.5}px)`;
    
    document.querySelector('.layer-mid').style.transform = 
        `translateY(${scrolled * 0.25}px)`;
});
```

**Требования:**
- Многослойный параллакс (3+ слоя)
- Плавное скроллирование
- Элементы появляются при прокрутке
- Фоновые элементы двигаются с разной скоростью

---

## Задача ANIM-6: Морфинг SVG
**Уровень сложности:** ⭐⭐⭐⭐⭐  
**Концепции:** SVG, SMIL animations, CSS animations with SVG

**Условие:**
Создайте анимированные SVG иконки с морфингом.

**Пример - Морфинг меню в крестик:**
```html
<svg width="100" height="100" viewBox="0 0 100 100">
    <path class="line line1" d="M 20,29 H 80" />
    <path class="line line2" d="M 20,50 H 80" />
    <path class="line line3" d="M 20,71 H 80" />
</svg>
```

**CSS:**
```css
.line {
    fill: none;
    stroke: #000;
    stroke-width: 6;
    stroke-linecap: round;
    transition: all 0.3s ease;
}

.menu-open .line1 {
    d: path("M 20,29 L 80,71");
}

.menu-open .line2 {
    opacity: 0;
}

.menu-open .line3 {
    d: path("M 20,71 L 80,29");
}

/* Анимированная иконка загрузки */
@keyframes dash {
    to {
        stroke-dashoffset: 0;
    }
}

.loading-icon {
    stroke-dasharray: 1000;
    stroke-dashoffset: 1000;
    animation: dash 2s linear forwards;
}
```

**Требования:**
- 5 анимированных SVG иконок
- Морфинг между формами
- Интерактивные состояния
- Оптимизация производительности

---

# 🎨 **РАЗДЕЛ 4: НЕСТАНДАРТНЫЕ ЭЛЕМЕНТЫ** (20 задач)

## Задача CUSTOM-1: Кастомный чекбокс и радио кнопки
**Уровень сложности:** ⭐⭐⭐  
**Концепции:** appearance: none, ::before, ::after

**Условие:**
Создайте 5 стилей кастомных чекбоксов и радио кнопок.

**CSS:**
```css
/* Скрываем стандартный чекбокс */
input[type="checkbox"] {
    appearance: none;
    width: 20px;
    height: 20px;
    border: 2px solid #3498db;
    border-radius: 4px;
    outline: none;
    cursor: pointer;
    position: relative;
    transition: all 0.3s ease;
}

input[type="checkbox"]:checked {
    background: #3498db;
    border-color: #3498db;
}

input[type="checkbox"]:checked::after {
    content: '✓';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    font-size: 14px;
}

/* Стиль 2: Переключатель (Toggle) */
.toggle {
    position: relative;
    width: 60px;
    height: 30px;
}

.toggle input {
    opacity: 0;
    width: 0;
    height: 0;
}

.toggle-slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    transition: 0.4s;
    border-radius: 30px;
}

.toggle-slider:before {
    position: absolute;
    content: "";
    height: 22px;
    width: 22px;
    left: 4px;
    bottom: 4px;
    background-color: white;
    transition: 0.4s;
    border-radius: 50%;
}

.toggle input:checked + .toggle-slider {
    background-color: #2196F3;
}

.toggle input:checked + .toggle-slider:before {
    transform: translateX(30px);
}

/* Стиль 3: Анимированный чекбокс */
.checkbox-animated {
    appearance: none;
    width: 24px;
    height: 24px;
    border: 2px solid #3498db;
    border-radius: 4px;
    position: relative;
    cursor: pointer;
    transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.checkbox-animated::before {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    width: 0;
    height: 0;
    background: #3498db;
    border-radius: 50%;
    transform: translate(-50%, -50%);
    transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.checkbox-animated:checked::before {
    width: 40px;
    height: 40px;
    opacity: 0;
}

.checkbox-animated::after {
    content: '';
    position: absolute;
    top: 3px;
    left: 8px;
    width: 5px;
    height: 10px;
    border: solid white;
    border-width: 0 2px 2px 0;
    transform: rotate(45deg) scale(0);
    transition: transform 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55) 0.1s;
}

.checkbox-animated:checked::after {
    transform: rotate(45deg) scale(1);
}

/* Стиль 4: Радио кнопка с волной */
input[type="radio"] {
    appearance: none;
    width: 20px;
    height: 20px;
    border: 2px solid #3498db;
    border-radius: 50%;
    outline: none;
    cursor: pointer;
    position: relative;
    transition: all 0.3s ease;
}

input[type="radio"]::before {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0);
    width: 10px;
    height: 10px;
    background: #3498db;
    border-radius: 50%;
    transition: transform 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

input[type="radio"]:checked::before {
    transform: translate(-50%, -50%) scale(1);
}

input[type="radio"]::after {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 0;
    height: 0;
    background: rgba(52, 152, 219, 0.3);
    border-radius: 50%;
    transition: all 0.4s ease;
}

input[type="radio"]:checked::after {
    width: 40px;
    height: 40px;
    opacity: 0;
}
```

**Требования:**
- 5 стилей чекбоксов
- 5 стилей радио кнопок
- Анимированные переходы
- Доступность (keyboard navigation)

---

## Задача CUSTOM-2: Кастомный select (dropdown)
**Уровень сложности:** ⭐⭐⭐⭐  
**Концепции:** Custom dropdown, JavaScript interaction

**Условие:**
Создайте полностью кастомный select с поиском и мультиселектом.

**HTML:**
```html
<div class="custom-select">
    <div class="select-trigger">
        <span class="selected-value">Select option</span>
        <i class="arrow"></i>
    </div>
    <div class="select-dropdown">
        <input type="text" class="search-input" placeholder="Search...">
        <ul class="options">
            <li data-value="1">Option 1</li>
            <li data-value="2">Option 2</li>
            <li data-value="3">Option 3</li>
        </ul>
    </div>
</div>
```

**CSS:**
```css
.custom-select {
    position: relative;
    width: 300px;
}

.select-trigger {
    padding: 12px 40px 12px 15px;
    background: white;
    border: 2px solid #ddd;
    border-radius: 8px;
    cursor: pointer;
    position: relative;
    transition: all 0.3s ease;
}

.select-trigger:hover {
    border-color: #3498db;
}

.arrow {
    position: absolute;
    right: 15px;
    top: 50%;
    transform: translateY(-50%);
    width: 0;
    height: 0;
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-top: 5px solid #333;
    transition: transform 0.3s ease;
}

.custom-select.open .arrow {
    transform: translateY(-50%) rotate(180deg);
}

.select-dropdown {
    position: absolute;
    top: calc(100% + 5px);
    left: 0;
    right: 0;
    background: white;
    border: 2px solid #ddd;
    border-radius: 8px;
    opacity: 0;
    visibility: hidden;
    transform: translateY(-10px);
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    z-index: 100;
    max-height: 300px;
    overflow: hidden;
}

.custom-select.open .select-dropdown {
    opacity: 1;
    visibility: visible;
    transform: translateY(0);
}

.search-input {
    width: 100%;
    padding: 10px 15px;
    border: none;
    border-bottom: 1px solid #eee;
    outline: none;
}

.options {
    list-style: none;
    margin: 0;
    padding: 0;
    max-height: 240px;
    overflow-y: auto;
}

.options li {
    padding: 12px 15px;
    cursor: pointer;
    transition: background 0.2s ease;
}

.options li:hover {
    background: #f5f5f5;
}

.options li.selected {
    background: #3498db;
    color: white;
}

/* Анимация появления опций */
.options li {
    opacity: 0;
    transform: translateX(-20px);
    animation: slideIn 0.3s ease forwards;
}

.options li:nth-child(1) { animation-delay: 0.05s; }
.options li:nth-child(2) { animation-delay: 0.1s; }
.options li:nth-child(3) { animation-delay: 0.15s; }

@keyframes slideIn {
    to {
        opacity: 1;
        transform: translateX(0);
    }
}
```

**Требования:**
- Кастомный дизайн
- Поиск по опциям
- Мультиселект режим
- Клавиатурная навигация
- Анимации открытия/закрытия

---

## Задача CUSTOM-3: Продвинутый range slider
**Уровень сложности:** ⭐⭐⭐⭐  
**Концепции:** input[type="range"], custom styling

**Условие:**
Создайте кастомный range slider с двойным значением.

**CSS:**
```css
/* Базовый стиль */
input[type="range"] {
    -webkit-appearance: none;
    appearance: none;
    width: 100%;
    height: 8px;
    border-radius: 5px;
    background: linear-gradient(to right, 
        #ddd 0%, 
        #ddd var(--value), 
        #3498db var(--value), 
        #3498db 100%
    );
    outline: none;
}

/* Стиль ползунка (Webkit) */
input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background: #3498db;
    cursor: pointer;
    box-shadow: 0 2px 5px rgba(0,0,0,0.2);
    transition: all 0.3s ease;
}

input[type="range"]::-webkit-slider-thumb:hover {
    transform: scale(1.2);
    box-shadow: 0 0 0 8px rgba(52, 152, 219, 0.1);
}

/* Стиль ползунка (Firefox) */
input[type="range"]::-moz-range-thumb {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background: #3498db;
    cursor: pointer;
    border: none;
    box-shadow: 0 2px 5px rgba(0,0,0,0.2);
}

/* Двойной range slider */
.double-range {
    position: relative;
    width: 100%;
    height: 40px;
}

.double-range input[type="range"] {
    position: absolute;
    width: 100%;
    pointer-events: none;
    -webkit-appearance: none;
    background: transparent;
}

.double-range input[type="range"]::-webkit-slider-thumb {
    pointer-events: all;
    -webkit-appearance: none;
}

.range-track {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    width: 100%;
    height: 8px;
    background: #ddd;
    border-radius: 5px;
}

.range-fill {
    position: absolute;
    height: 100%;
    background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
    border-radius: 5px;
}

/* Значения над слайдером */
.range-value {
    position: absolute;
    top: -30px;
    transform: translateX(-50%);
    background: #333;
    color: white;
    padding: 4px 8px;
    border-radius: 4px;
    font-size: 12px;
    white-space: nowrap;
}

.range-value::after {
    content: '';
    position: absolute;
    bottom: -4px;
    left: 50%;
    transform: translateX(-50%);
    width: 0;
    height: 0;
    border-left: 4px solid transparent;
    border-right: 4px solid transparent;
    border-top: 4px solid #333;
}
```

**Требования:**
- Одиночный slider со значением
- Двойной slider (диапазон)
- Кастомные цвета и стили
- Значения над ползунком
- Шаги и метки

---

## Задача CUSTOM-4: Креативные кнопки
**Уровень сложности:** ⭐⭐⭐  
**Концепции:** Button effects, pseudo-elements, gradients

**Условие:**
Создайте коллекцию из 15 уникальных стилей кнопок.

**Примеры:**

```css
/* 1. Неоморфизм */
.btn-neomorph {
    background: #e0e5ec;
    border: none;
    padding: 15px 30px;
    border-radius: 10px;
    box-shadow: 
        9px 9px 16px rgba(163, 177, 198, 0.6),
        -9px -9px 16px rgba(255, 255, 255, 0.5);
    transition: all 0.3s ease;
}

.btn-neomorph:active {
    box-shadow: 
        inset 9px 9px 16px rgba(163, 177, 198, 0.6),
        inset -9px -9px 16px rgba(255, 255, 255, 0.5);
}

/* 2. Градиентная с анимацией */
.btn-gradient-animated {
    background: linear-gradient(45deg, #667eea, #764ba2, #f093fb, #4facfe);
    background-size: 400% 400%;
    border: none;
    color: white;
    padding: 15px 30px;
    border-radius: 50px;
    animation: gradientShift 3s ease infinite;
}

@keyframes gradientShift {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
}

/* 3. Голографическая */
.btn-holographic {
    background: linear-gradient(
        135deg,
        #667eea 0%,
        #764ba2 25%,
        #f093fb 50%,
        #4facfe 75%,
        #00f2fe 100%
    );
    border: none;
    color: white;
    padding: 15px 30px;
    border-radius: 10px;
    position: relative;
    overflow: hidden;
}

.btn-holographic::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: linear-gradient(
        45deg,
        transparent,
        rgba(255,255,255,0.3),
        transparent
    );
    transform: rotate(45deg);
    animation: shine 3s infinite;
}

@keyframes shine {
    0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
    100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
}

/* 4. Кнопка с жидким эффектом */
.btn-liquid {
    position: relative;
    padding: 15px 30px;
    background: transparent;
    border: 2px solid #3498db;
    color: #3498db;
    overflow: hidden;
    transition: color 0.5s;
}

.btn-liquid::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: #3498db;
    transition: left 0.5s;
    z-index: -1;
}

.btn-liquid:hover {
    color: white;
}

.btn-liquid:hover::before {
    left: 0;
}

/* 5. Глитч эффект */
.btn-glitch {
    background: #000;
    color: #fff;
    padding: 15px 30px;
    border: none;
    position: relative;
    overflow: hidden;
}

.btn-glitch::before,
.btn-glitch::after {
    content: attr(data-text);
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
}

.btn-glitch:hover::before {
    animation: glitch1 0.3s infinite;
    color: #0ff;
    z-index: -1;
}

.btn-glitch:hover::after {
    animation: glitch2 0.3s infinite;
    color: #f0f;
    z-index: -2;
}

@keyframes glitch1 {
    0%, 100% { transform: translate(0); }
    33% { transform: translate(-2px, 2px); }
    66% { transform: translate(2px, -2px); }
}

@keyframes glitch2 {
    0%, 100% { transform: translate(0); }
    33% { transform: translate(2px, -2px); }
    66% { transform: translate(-2px, 2px); }
}

/* 6. 3D кнопка */
.btn-3d {
    background: linear-gradient(to bottom, #3498db, #2980b9);
    border: none;
    color: white;
    padding: 15px 30px;
    border-radius: 8px;
    box-shadow: 
        0 5px 0 #21618c,
        0 10px 20px rgba(0,0,0,0.3);
    transform: translateY(0);
    transition: all 0.1s ease;
}

.btn-3d:active {
    transform: translateY(5px);
    box-shadow: 
        0 0 0 #21618c,
        0 5px 10px rgba(0,0,0,0.3);
}
```

**Требования:**
- 15 уникальных стилей
- Различные hover эффекты
- Анимации и трансформации
- Адаптивность
- Accessibility

---

## Задача CUSTOM-5: Необычная навигация
**Уровень сложности:** ⭐⭐⭐⭐  
**Концепции:** Creative navigation, hamburger menus, circular menus

**Условие:**
Создайте 5 типов необычной навигации.

**1. Круговое меню:**
```css
.circular-menu {
    position: fixed;
    bottom: 30px;
    right: 30px;
}

.menu-toggle {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    background: #3498db;
    border: none;
    cursor: pointer;
    position: relative;
    z-index: 1000;
}

.menu-items {
    position: absolute;
    bottom: 0;
    right: 0;
}

.menu-item {
    position: absolute;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background: #2ecc71;
    opacity: 0;
    transform: scale(0);
    transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.circular-menu.active .menu-item:nth-child(1) {
    transform: translate(-70px, -70px) scale(1);
    opacity: 1;
    transition-delay: 0.1s;
}

.circular-menu.active .menu-item:nth-child(2) {
    transform: translate(0, -100px) scale(1);
    opacity: 1;
    transition-delay: 0.2s;
}

.circular-menu.active .menu-item:nth-child(3) {
    transform: translate(70px, -70px) scale(1);
    opacity: 1;
    transition-delay: 0.3s;
}
```

**2. Полноэкранное меню с переходом:**
```css
.fullscreen-menu {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    clip-path: circle(0% at top right);
    transition: clip-path 0.8s cubic-bezier(0.77, 0, 0.175, 1);
}

.fullscreen-menu.active {
    clip-path: circle(150% at top right);
}

.menu-items {
    list-style: none;
    text-align: center;
}

.menu-items li {
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.5s cubic-bezier(0.77, 0, 0.175, 1);
}

.fullscreen-menu.active .menu-items li {
    opacity: 1;
    transform: translateY(0);
}

.fullscreen-menu.active .menu-items li:nth-child(1) { transition-delay: 0.2s; }
.fullscreen-menu.active .menu-items li:nth-child(2) { transition-delay: 0.3s; }
.fullscreen-menu.active .menu-items li:nth-child(3) { transition-delay: 0.4s; }
```

**Требования:**
- Круговое меню
- Полноэкранное меню с transition
- Боковое выдвижное меню
- Mega menu с анимациями
- Sticky навигация с эффектами

---

*Продолжение с остальными задачами по фильтрам, clip-path, интерактивным компонентам и практическим проектам...*

---

# 🎯 **ПРАКТИЧЕСКИЕ ПРОЕКТЫ** (10 проектов)

## Проект 1: Анимированное портфолио
**Сложность:** ⭐⭐⭐⭐  
**Требования:**
- Hero секция с параллаксом
- Плавная прокрутка по якорям
- Анимация при скролле (AOS)
- Галерея с фильтрами
- Контактная форма с валидацией
- Полная адаптивность

## Проект 2: Лендинг продукта
**Сложность:** ⭐⭐⭐⭐  
**Требования:**
- Видео-фон в hero
- Анимированные SVG иконки
- Интерактивные графики
- Pricing таблицы с эффектами
- Testimonials слайдер
- Call-to-action секции

## Проект 3: Интерактивная галерея
**Сложность:** ⭐⭐⭐⭐⭐  
**Требования:**
- Masonry layout (Pinterest style)
- Lightbox с зумом
- Фильтрация и сортировка
- Infinite scroll
- Hover эффекты на карточки
- Lazy loading изображений

---

**Курс готов к использованию!** Хотите продолжить детализацию остальных задач или создать стартовые шаблоны для проектов?