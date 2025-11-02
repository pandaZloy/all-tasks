# 🎨 HTML/CSS Solutions
## Детальные решения всех задач HTML/CSS курса

---

## 📋 Содержание

- [📝 Раздел 1: Основы HTML/CSS](#-раздел-1-основы-htmlcss)
- [📦 Раздел 2: Продвинутый CSS](#-раздел-2-продвинутый-css)
- [✨ Раздел 3: Анимации и трансформации](#-раздел-3-анимации-и-трансформации)
- [🎯 Раздел 4: Нестандартные элементы](#-раздел-4-нестандартные-элементы)
- [🔮 Раздел 5: Современные техники](#-раздел-5-современные-техники)

---

# 📝 **РАЗДЕЛ 1: ОСНОВЫ HTML/CSS**

## 💡 Задача HTML-1: Семантическая структура страницы

### 📋 **Условие:**
Создайте семантически правильную структуру веб-страницы.

### ✅ **Решение:**

```html
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Описание страницы для SEO">
    <meta name="keywords" content="ключевые, слова">
    <title>Семантическая страница</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Шапка сайта -->
    <header role="banner">
        <nav role="navigation" aria-label="Главная навигация">
            <ul>
                <li><a href="#home" aria-current="page">Главная</a></li>
                <li><a href="#about">О нас</a></li>
                <li><a href="#services">Услуги</a></li>
                <li><a href="#contact">Контакты</a></li>
            </ul>
        </nav>
        
        <h1>Заголовок сайта</h1>
        <p>Краткое описание или слоган</p>
    </header>

    <!-- Основной контент -->
    <main role="main">
        <!-- Главная секция -->
        <section id="home" aria-labelledby="home-heading">
            <h2 id="home-heading">Добро пожаловать</h2>
            <p>Основной контент страницы</p>
            
            <!-- Статья -->
            <article>
                <header>
                    <h3>Заголовок статьи</h3>
                    <time datetime="2025-11-02">2 ноября 2025</time>
                    <address>Автор: <a href="mailto:author@example.com">Имя Автора</a></address>
                </header>
                
                <p>Содержание статьи...</p>
                
                <footer>
                    <p>Теги: <a href="#tag1" rel="tag">HTML</a>, <a href="#tag2" rel="tag">CSS</a></p>
                </footer>
            </article>
        </section>

        <!-- Боковая панель -->
        <aside role="complementary" aria-labelledby="sidebar-heading">
            <h2 id="sidebar-heading">Дополнительная информация</h2>
            
            <!-- Виджет поиска -->
            <section aria-labelledby="search-heading">
                <h3 id="search-heading">Поиск</h3>
                <form role="search">
                    <label for="search-input">Поиск по сайту:</label>
                    <input type="search" id="search-input" name="q" placeholder="Введите запрос">
                    <button type="submit">Найти</button>
                </form>
            </section>
            
            <!-- Последние посты -->
            <section aria-labelledby="recent-posts">
                <h3 id="recent-posts">Последние посты</h3>
                <ul>
                    <li><a href="#post1">Заголовок поста 1</a></li>
                    <li><a href="#post2">Заголовок поста 2</a></li>
                    <li><a href="#post3">Заголовок поста 3</a></li>
                </ul>
            </section>
        </aside>
    </main>

    <!-- Подвал -->
    <footer role="contentinfo">
        <section aria-labelledby="contact-info">
            <h2 id="contact-info">Контактная информация</h2>
            <address>
                <p>Email: <a href="mailto:info@example.com">info@example.com</a></p>
                <p>Телефон: <a href="tel:+71234567890">+7 (123) 456-78-90</a></p>
            </address>
        </section>
        
        <p>&copy; 2025 Название компании. Все права защищены.</p>
        
        <!-- Социальные сети -->
        <nav aria-label="Социальные сети">
            <ul>
                <li><a href="#" aria-label="Facebook">FB</a></li>
                <li><a href="#" aria-label="Twitter">TW</a></li>
                <li><a href="#" aria-label="Instagram">IG</a></li>
            </ul>
        </nav>
    </footer>
</body>
</html>
```

```css
/* Базовые стили для семантической структуры */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    color: #333;
}

/* Шапка */
header {
    background: #2c3e50;
    color: white;
    padding: 1rem;
}

header nav ul {
    list-style: none;
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
}

header nav a {
    color: white;
    text-decoration: none;
    padding: 0.5rem;
    border-radius: 4px;
    transition: background-color 0.3s ease;
}

header nav a:hover,
header nav a[aria-current="page"] {
    background-color: rgba(255, 255, 255, 0.2);
}

/* Основной контент */
main {
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 2rem;
    padding: 2rem;
    max-width: 1200px;
    margin: 0 auto;
}

/* Статьи */
article {
    background: #f9f9f9;
    padding: 1.5rem;
    border-radius: 8px;
    margin: 1rem 0;
}

article header {
    background: transparent;
    color: #333;
    padding: 0 0 1rem 0;
    border-bottom: 1px solid #eee;
    margin-bottom: 1rem;
}

article h3 {
    color: #2c3e50;
    margin-bottom: 0.5rem;
}

time {
    font-style: italic;
    color: #666;
}

/* Боковая панель */
aside {
    background: #ecf0f1;
    padding: 1.5rem;
    border-radius: 8px;
    height: fit-content;
}

aside section {
    margin-bottom: 1.5rem;
}

aside ul {
    list-style: none;
}

aside li {
    margin-bottom: 0.5rem;
}

/* Формы */
form {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

label {
    font-weight: bold;
}

input, button {
    padding: 0.5rem;
    border: 1px solid #ddd;
    border-radius: 4px;
}

button {
    background: #3498db;
    color: white;
    border: none;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

button:hover {
    background: #2980b9;
}

/* Подвал */
footer {
    background: #34495e;
    color: white;
    padding: 2rem;
    text-align: center;
}

footer nav ul {
    list-style: none;
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-top: 1rem;
}

footer nav a {
    color: white;
    text-decoration: none;
    padding: 0.5rem;
    background: #2c3e50;
    border-radius: 4px;
    transition: background-color 0.3s ease;
}

footer nav a:hover {
    background: #1a252f;
}

/* Адаптивность */
@media (max-width: 768px) {
    main {
        grid-template-columns: 1fr;
    }
    
    header nav ul {
        flex-direction: column;
    }
    
    footer nav ul {
        flex-direction: column;
        align-items: center;
    }
}

/* Улучшение доступности */
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
}

/* Фокус для клавиатурной навигации */
a:focus,
button:focus,
input:focus {
    outline: 2px solid #3498db;
    outline-offset: 2px;
}
```

### 🎯 **Объяснение решения:**

#### 📱 **HTML5 Семантические элементы:**
- `<header>` - шапка сайта с навигацией
- `<main>` - основной контент страницы
- `<nav>` - навигационные меню
- `<section>` - тематические разделы
- `<article>` - самостоятельный контент
- `<aside>` - дополнительный контент
- `<footer>` - подвал сайта
- `<address>` - контактная информация

#### ♿ **Доступность (Accessibility):**
- `role` атрибуты для ясности структуры
- `aria-label` и `aria-labelledby` для экранных читалок
- `aria-current` для текущей страницы
- Правильная иерархия заголовков (h1 → h2 → h3)
- `lang` атрибут для языка

#### 🎨 **CSS лучшие практики:**
- CSS Grid для макета
- Flexbox для навигации
- Адаптивный дизайн
- Фокус-состояния для доступности
- Плавные переходы

### 🔧 **Альтернативные подходы:**

```html
<!-- Прогрессивное улучшение с microdata -->
<article itemscope itemtype="https://schema.org/Article">
    <header>
        <h3 itemprop="headline">Заголовок статьи</h3>
        <time itemprop="datePublished" datetime="2025-11-02">2 ноября 2025</time>
        <div itemprop="author" itemscope itemtype="https://schema.org/Person">
            <span itemprop="name">Имя Автора</span>
        </div>
    </header>
    <div itemprop="articleBody">
        <p>Содержание статьи...</p>
    </div>
</article>
```

### ⚡ **Лучшие практики:**
- ✅ Всегда используйте семантические элементы
- ✅ Добавляйте ARIA атрибуты для улучшения доступности
- ✅ Соблюдайте иерархию заголовков
- ✅ Тестируйте с экранными читалками
- ✅ Валидируйте HTML код

---

# 📦 **РАЗДЕЛ 2: ПРОДВИНУТЫЙ CSS**

## 💡 Задача CSS-1: Современный CSS Grid Layout

### 📋 **Условие:**
Создайте адаптивный макет с использованием CSS Grid для современного дизайна.

### ✅ **Решение:**

```html
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Grid Layout</title>
    <link rel="stylesheet" href="grid-layout.css">
</head>
<body>
    <div class="container">
        <header class="header">Header</header>
        
        <nav class="sidebar">
            <ul>
                <li><a href="#">Ссылка 1</a></li>
                <li><a href="#">Ссылка 2</a></li>
                <li><a href="#">Ссылка 3</a></li>
            </ul>
        </nav>
        
        <main class="content">
            <section class="hero">
                <h1>Герой секция</h1>
                <p>Основной контент страницы</p>
            </section>
            
            <section class="cards">
                <div class="card">Карточка 1</div>
                <div class="card">Карточка 2</div>
                <div class="card">Карточка 3</div>
                <div class="card">Карточка 4</div>
            </section>
        </main>
        
        <aside class="widget">
            <h3>Виджет</h3>
            <p>Дополнительная информация</p>
        </aside>
        
        <footer class="footer">Footer</footer>
    </div>
</body>
</html>
```

```css
/* CSS Grid Layout */
.container {
    display: grid;
    grid-template-columns: 200px 1fr 300px;
    grid-template-rows: auto 1fr auto;
    grid-template-areas: 
        "header  header  header"
        "sidebar content widget"
        "footer  footer  footer";
    min-height: 100vh;
    gap: 1rem;
    padding: 1rem;
    max-width: 1400px;
    margin: 0 auto;
}

/* Размещение элементов по областям */
.header {
    grid-area: header;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 2rem;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.5rem;
    font-weight: bold;
}

.sidebar {
    grid-area: sidebar;
    background: #f8f9fa;
    padding: 1.5rem;
    border-radius: 8px;
    border-left: 4px solid #667eea;
}

.sidebar ul {
    list-style: none;
    padding: 0;
    margin: 0;
}

.sidebar li {
    margin-bottom: 0.5rem;
}

.sidebar a {
    display: block;
    padding: 0.75rem;
    text-decoration: none;
    color: #333;
    border-radius: 4px;
    transition: all 0.3s ease;
}

.sidebar a:hover {
    background: #667eea;
    color: white;
    transform: translateX(5px);
}

.content {
    grid-area: content;
    display: grid;
    gap: 2rem;
}

.hero {
    background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    color: white;
    padding: 3rem;
    border-radius: 12px;
    text-align: center;
}

.hero h1 {
    margin: 0 0 1rem 0;
    font-size: 2.5rem;
}

.cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
}

.card {
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    border: 1px solid #e9ecef;
    transition: all 0.3s ease;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 150px;
    font-weight: 500;
    color: #495057;
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
    border-color: #667eea;
}

.widget {
    grid-area: widget;
    background: #fff3cd;
    padding: 1.5rem;
    border-radius: 8px;
    border: 1px solid #ffeaa7;
    height: fit-content;
}

.widget h3 {
    margin: 0 0 1rem 0;
    color: #856404;
}

.widget p {
    margin: 0;
    color: #856404;
    line-height: 1.6;
}

.footer {
    grid-area: footer;
    background: #343a40;
    color: white;
    padding: 2rem;
    border-radius: 8px;
    text-align: center;
    font-weight: 500;
}

/* Адаптивность */
@media (max-width: 1024px) {
    .container {
        grid-template-columns: 1fr 300px;
        grid-template-areas: 
            "header header"
            "content widget"
            "sidebar sidebar"
            "footer footer";
    }
}

@media (max-width: 768px) {
    .container {
        grid-template-columns: 1fr;
        grid-template-areas: 
            "header"
            "content"
            "sidebar"
            "widget"
            "footer";
        padding: 0.5rem;
        gap: 0.5rem;
    }
    
    .cards {
        grid-template-columns: 1fr;
    }
    
    .hero {
        padding: 2rem 1rem;
    }
    
    .hero h1 {
        font-size: 2rem;
    }
}

/* Продвинутые CSS техники */
@supports (display: subgrid) {
    .cards {
        display: subgrid;
        grid-template-rows: subgrid;
    }
}

/* CSS Custom Properties для темизации */
:root {
    --primary-color: #667eea;
    --secondary-color: #764ba2;
    --accent-color: #f093fb;
    --text-color: #333;
    --bg-color: #ffffff;
    --border-radius: 8px;
    --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    --transition: all 0.3s ease;
}

/* Темная тема */
@media (prefers-color-scheme: dark) {
    :root {
        --text-color: #f8f9fa;
        --bg-color: #212529;
    }
    
    body {
        background: var(--bg-color);
        color: var(--text-color);
    }
    
    .card {
        background: #343a40;
        color: var(--text-color);
        border-color: #495057;
    }
}
```

### 🎯 **Объяснение решения:**

#### 🎛️ **CSS Grid возможности:**
- `grid-template-areas` - именованные области для интуитивного размещения
- `repeat(auto-fit, minmax())` - адаптивные колонки без медиа-запросов
- `grid-area` - размещение элементов по именованным областям
- Подложка (subgrid) для сложных макетов

#### 📱 **Адаптивный дизайн:**
- Мобильный подход (mobile-first)
- Переопределение grid-template-areas для разных экранов
- Гибкие размеры с minmax() и fr единицами

#### 🎨 **Современные CSS техники:**
- CSS Custom Properties (переменные)
- `prefers-color-scheme` для автоматической темной темы
- `@supports` для прогрессивного улучшения
- Плавные анимации и трансформации

### ⚡ **Лучшие практики:**
- ✅ Используйте именованные grid-области для читаемости
- ✅ Применяйте CSS переменные для консистентности
- ✅ Тестируйте на разных размерах экранов
- ✅ Используйте `fr` единицы для гибкости
- ✅ Добавляйте fallback для старых браузеров

---

## 📊 **Итоги HTML/CSS решений**

### 🎯 **Изученные концепции:**
- ✅ Семантическая HTML5 разметка
- ✅ CSS Grid и Flexbox макеты
- ✅ Доступность и ARIA атрибуты
- ✅ Адаптивный дизайн
- ✅ CSS переменные и современные техники
- ✅ Анимации и переходы

### 🔧 **Применяемые техники:**
- Мобильный подход (mobile-first)
- Прогрессивное улучшение
- Кроссбраузерная совместимость
- SEO оптимизация

### 🚀 **Следующий шаг:**
Изучайте [Анимации и трансформации](#-раздел-3-анимации-и-трансформации)