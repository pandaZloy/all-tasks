# 🎨 SCSS/SASS: МАСТЕР-КУРС ПРЕПРОЦЕССОРА
## От основ до продвинутых техник и архитектуры

---

## 📅 **СТРУКТУРА КУРСА**

### **РАЗДЕЛ 1: ОСНОВЫ SCSS** (15 задач)
- Переменные и типы данных
- Вложенность (Nesting)
- Родительский селектор (&)
- Импорты иPartialFiles

### **РАЗДЕЛ 2: ФУНКЦИИ И МИКСИНЫ** (20 задач)
- @mixin и @include
- Параметры и значения по умолчанию
- @function и @return
- Встроенные функции SCSS

### **РАЗДЕЛ 3: УПРАВЛЯЮЩИЕ ДИРЕКТИВЫ** (15 задач)
- @if, @else if, @else
- @for, @each, @while
- Условная логика
- Циклы для генерации классов

### **РАЗДЕЛ 4: ПРОДВИНУТЫЕ ТЕХНИКИ** (20 задач)
- @extend и placeholders
- Maps и списки
- Интерполация
- @content директива

### **РАЗДЕЛ 5: АРХИТЕКТУРА И ОРГАНИЗАЦИЯ** (15 задач)
- 7-1 Pattern
- BEM + SCSS
- ITCSS методология
- Модульная структура

### **РАЗДЕЛ 6: ПРАКТИЧЕСКИЕ ПРОЕКТЫ** (10 проектов)
- UI Kit с компонентами
- Адаптивная сетка
- Система тем
- Utility классы генератор

---

# 📝 **РАЗДЕЛ 1: ОСНОВЫ SCSS** (15 задач)

## Задача SCSS-1: Переменные и типы данных
**Уровень сложности:** ⭐  
**Концепции:** $variables, типы данных

**Условие:**
Создайте систему переменных для цветовой палитры проекта.

**SCSS:**
```scss
// Цвета
$primary-color: #3498db;
$secondary-color: #2ecc71;
$danger-color: #e74c3c;
$warning-color: #f39c12;
$success-color: #27ae60;

// Оттенки серого
$gray-100: #f8f9fa;
$gray-200: #e9ecef;
$gray-300: #dee2e6;
$gray-400: #ced4da;
$gray-500: #adb5bd;
$gray-600: #6c757d;
$gray-700: #495057;
$gray-800: #343a40;
$gray-900: #212529;

// Типографика
$font-family-base: 'Roboto', sans-serif;
$font-family-heading: 'Montserrat', sans-serif;
$font-size-base: 16px;
$font-weight-light: 300;
$font-weight-normal: 400;
$font-weight-bold: 700;

// Отступы
$spacing-unit: 8px;
$spacing-xs: $spacing-unit * 0.5;    // 4px
$spacing-sm: $spacing-unit;           // 8px
$spacing-md: $spacing-unit * 2;       // 16px
$spacing-lg: $spacing-unit * 4;       // 32px
$spacing-xl: $spacing-unit * 8;       // 64px

// Breakpoints
$breakpoint-xs: 0;
$breakpoint-sm: 576px;
$breakpoint-md: 768px;
$breakpoint-lg: 992px;
$breakpoint-xl: 1200px;
$breakpoint-xxl: 1400px;

// Z-index слои
$z-index-dropdown: 1000;
$z-index-sticky: 1020;
$z-index-fixed: 1030;
$z-index-modal-backdrop: 1040;
$z-index-modal: 1050;
$z-index-popover: 1060;
$z-index-tooltip: 1070;

// Тени
$shadow-sm: 0 2px 4px rgba(0, 0, 0, 0.1);
$shadow-md: 0 4px 6px rgba(0, 0, 0, 0.1);
$shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1);
$shadow-xl: 0 20px 25px rgba(0, 0, 0, 0.15);

// Радиусы
$border-radius-sm: 4px;
$border-radius-md: 8px;
$border-radius-lg: 16px;
$border-radius-full: 9999px;

// Переходы
$transition-base: all 0.3s ease;
$transition-fast: all 0.15s ease;
$transition-slow: all 0.5s ease;

// Использование
.button {
  background-color: $primary-color;
  padding: $spacing-md $spacing-lg;
  border-radius: $border-radius-md;
  box-shadow: $shadow-md;
  transition: $transition-base;
  font-family: $font-family-base;
  font-size: $font-size-base;
}
```

**Требования:**
- Создайте полную систему переменных
- Логическая группировка
- Использование математических операций
- Комментарии для секций

---

## Задача SCSS-2: Вложенность (Nesting)
**Уровень сложности:** ⭐⭐  
**Концепции:** Nested selectors, избегание глубокой вложенности

**Условие:**
Используйте вложенность для стилизации навигации.

**SCSS:**
```scss
.navigation {
  background-color: $gray-900;
  padding: $spacing-md 0;
  
  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .logo {
    font-size: 24px;
    font-weight: $font-weight-bold;
    color: white;
    text-decoration: none;
    
    &:hover {
      color: $primary-color;
    }
  }
  
  .nav-menu {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
    gap: $spacing-lg;
    
    li {
      position: relative;
    }
    
    a {
      color: $gray-300;
      text-decoration: none;
      padding: $spacing-sm $spacing-md;
      display: block;
      transition: $transition-base;
      
      &:hover {
        color: white;
        background-color: rgba(255, 255, 255, 0.1);
        border-radius: $border-radius-sm;
      }
      
      &.active {
        color: $primary-color;
        font-weight: $font-weight-bold;
      }
    }
    
    // Dropdown
    .dropdown {
      position: absolute;
      top: 100%;
      left: 0;
      background: $gray-800;
      min-width: 200px;
      border-radius: $border-radius-md;
      box-shadow: $shadow-lg;
      opacity: 0;
      visibility: hidden;
      transform: translateY(-10px);
      transition: $transition-base;
      
      a {
        padding: $spacing-md;
        border-radius: 0;
        
        &:first-child {
          border-radius: $border-radius-md $border-radius-md 0 0;
        }
        
        &:last-child {
          border-radius: 0 0 $border-radius-md $border-radius-md;
        }
      }
    }
    
    li:hover .dropdown {
      opacity: 1;
      visibility: visible;
      transform: translateY(0);
    }
  }
}

// ❌ Плохая практика - слишком глубокая вложенность
.bad-example {
  .level-1 {
    .level-2 {
      .level-3 {
        .level-4 {
          .level-5 {
            // Слишком глубоко! Избегайте этого
          }
        }
      }
    }
  }
}

// ✅ Хорошая практика - максимум 3-4 уровня
.good-example {
  .item {
    .title {
      // Оптимальная глубина
    }
  }
}
```

**Требования:**
- Используйте вложенность для структуры
- Максимум 3-4 уровня вложенности
- Псевдо-классы через &
- Дочерние элементы логично сгруппированы

---

## Задача SCSS-3: Родительский селектор (&)
**Уровень сложности:** ⭐⭐  
**Концепции:** Parent selector, модификаторы, состояния

**Условие:**
Создайте систему кнопок с модификаторами используя &.

**SCSS:**
```scss
.btn {
  display: inline-block;
  padding: $spacing-md $spacing-lg;
  border: none;
  border-radius: $border-radius-md;
  font-size: $font-size-base;
  font-weight: $font-weight-bold;
  text-align: center;
  cursor: pointer;
  transition: $transition-base;
  
  // Состояния
  &:hover {
    transform: translateY(-2px);
    box-shadow: $shadow-lg;
  }
  
  &:active {
    transform: translateY(0);
    box-shadow: $shadow-sm;
  }
  
  &:focus {
    outline: 3px solid rgba($primary-color, 0.3);
    outline-offset: 2px;
  }
  
  &:disabled {
    opacity: 0.5;
    cursor: not-allowed;
    pointer-events: none;
  }
  
  // Модификаторы цвета
  &--primary {
    background-color: $primary-color;
    color: white;
    
    &:hover {
      background-color: darken($primary-color, 10%);
    }
  }
  
  &--secondary {
    background-color: $secondary-color;
    color: white;
    
    &:hover {
      background-color: darken($secondary-color, 10%);
    }
  }
  
  &--danger {
    background-color: $danger-color;
    color: white;
    
    &:hover {
      background-color: darken($danger-color, 10%);
    }
  }
  
  &--outline {
    background-color: transparent;
    border: 2px solid $primary-color;
    color: $primary-color;
    
    &:hover {
      background-color: $primary-color;
      color: white;
    }
    
    // Комбинация модификаторов
    &.btn--danger {
      border-color: $danger-color;
      color: $danger-color;
      
      &:hover {
        background-color: $danger-color;
        color: white;
      }
    }
  }
  
  // Модификаторы размера
  &--small {
    padding: $spacing-sm $spacing-md;
    font-size: 14px;
  }
  
  &--large {
    padding: $spacing-lg $spacing-xl;
    font-size: 18px;
  }
  
  // Модификаторы формы
  &--rounded {
    border-radius: $border-radius-full;
  }
  
  &--block {
    display: block;
    width: 100%;
  }
  
  // Иконка в кнопке
  &__icon {
    margin-right: $spacing-sm;
    
    // Иконка справа
    .btn--icon-right & {
      margin-right: 0;
      margin-left: $spacing-sm;
    }
  }
  
  // Loading состояние
  &--loading {
    position: relative;
    color: transparent;
    
    &::after {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 20px;
      height: 20px;
      border: 2px solid white;
      border-top-color: transparent;
      border-radius: 50%;
      animation: spin 0.6s linear infinite;
    }
  }
}

@keyframes spin {
  to { transform: translate(-50%, -50%) rotate(360deg); }
}

// Использование
// <button class="btn btn--primary btn--large btn--rounded">Click me</button>
```

**Требования:**
- BEM naming с использованием &
- Состояния элементов
- Модификаторы размеров и цветов
- Комбинации модификаторов
- Вложенные элементы с &

---

## Задача SCSS-4: Импорты и Partials
**Уровень сложности:** ⭐⭐  
**Концепции:** @import, @use, partials (_file.scss)

**Условие:**
Организуйте структуру проекта с использованием partials.

**Структура файлов:**
```
styles/
├── main.scss
├── abstracts/
│   ├── _variables.scss
│   ├── _functions.scss
│   ├── _mixins.scss
│   └── _placeholders.scss
├── base/
│   ├── _reset.scss
│   ├── _typography.scss
│   └── _animations.scss
├── components/
│   ├── _buttons.scss
│   ├── _cards.scss
│   ├── _forms.scss
│   └── _modals.scss
├── layout/
│   ├── _header.scss
│   ├── _footer.scss
│   ├── _sidebar.scss
│   └── _grid.scss
├── pages/
│   ├── _home.scss
│   ├── _about.scss
│   └── _contact.scss
└── themes/
    ├── _dark.scss
    └── _light.scss
```

**main.scss:**
```scss
// Abstracts (не генерируют CSS)
@import 'abstracts/variables';
@import 'abstracts/functions';
@import 'abstracts/mixins';
@import 'abstracts/placeholders';

// Base
@import 'base/reset';
@import 'base/typography';
@import 'base/animations';

// Layout
@import 'layout/grid';
@import 'layout/header';
@import 'layout/footer';
@import 'layout/sidebar';

// Components
@import 'components/buttons';
@import 'components/cards';
@import 'components/forms';
@import 'components/modals';

// Pages
@import 'pages/home';
@import 'pages/about';
@import 'pages/contact';

// Themes
@import 'themes/light';
@import 'themes/dark';
```

**abstracts/_variables.scss:**
```scss
// Цвета
$colors: (
  'primary': #3498db,
  'secondary': #2ecc71,
  'danger': #e74c3c,
  'warning': #f39c12,
  'success': #27ae60
);

// Размеры
$sizes: (
  'xs': 0.5rem,
  'sm': 1rem,
  'md': 2rem,
  'lg': 4rem,
  'xl': 8rem
);

// Breakpoints
$breakpoints: (
  'sm': 576px,
  'md': 768px,
  'lg': 992px,
  'xl': 1200px,
  'xxl': 1400px
);
```

**abstracts/_mixins.scss:**
```scss
// Responsive mixin
@mixin respond-to($breakpoint) {
  @if map-has-key($breakpoints, $breakpoint) {
    @media (min-width: map-get($breakpoints, $breakpoint)) {
      @content;
    }
  }
}

// Flex center
@mixin flex-center {
  display: flex;
  align-items: center;
  justify-content: center;
}

// Position absolute center
@mixin absolute-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

**Использование @use (современный способ):**
```scss
// main.scss с @use
@use 'abstracts/variables' as vars;
@use 'abstracts/mixins' as mix;

.button {
  background-color: map-get(vars.$colors, 'primary');
  
  @include mix.respond-to('md') {
    padding: 2rem;
  }
}
```

**Требования:**
- Организуйте файловую структуру
- Используйте partials (начинаются с _)
- Логическое разделение на папки
- Правильный порядок импортов
- Попробуйте @use вместо @import

---

# 🔧 **РАЗДЕЛ 2: ФУНКЦИИ И МИКСИНЫ** (20 задач)

## Задача MIXIN-1: Базовые миксины
**Уровень сложности:** ⭐⭐  
**Концепции:** @mixin, @include, параметры

**Условие:**
Создайте библиотеку полезных миксинов.

**SCSS:**
```scss
// 1. Размеры элемента
@mixin size($width, $height: $width) {
  width: $width;
  height: $height;
}

// Использование
.square {
  @include size(100px);
}

.rectangle {
  @include size(200px, 100px);
}

// 2. Позиционирование
@mixin position($position, $top: null, $right: null, $bottom: null, $left: null) {
  position: $position;
  top: $top;
  right: $right;
  bottom: $bottom;
  left: $left;
}

.overlay {
  @include position(absolute, 0, 0, 0, 0);
}

// 3. Truncate текст
@mixin truncate($lines: 1) {
  @if $lines == 1 {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  } @else {
    display: -webkit-box;
    -webkit-line-clamp: $lines;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }
}

.single-line {
  @include truncate;
}

.multi-line {
  @include truncate(3);
}

// 4. Clearfix
@mixin clearfix {
  &::after {
    content: '';
    display: table;
    clear: both;
  }
}

// 5. Gradient
@mixin gradient($direction, $color-stops...) {
  background: linear-gradient($direction, $color-stops);
}

.gradient-box {
  @include gradient(to right, #667eea, #764ba2);
}

// 6. Triangle (CSS треугольник)
@mixin triangle($direction, $size, $color) {
  width: 0;
  height: 0;
  border-style: solid;
  
  @if $direction == up {
    border-width: 0 ($size / 2) $size ($size / 2);
    border-color: transparent transparent $color transparent;
  } @else if $direction == down {
    border-width: $size ($size / 2) 0 ($size / 2);
    border-color: $color transparent transparent transparent;
  } @else if $direction == left {
    border-width: ($size / 2) $size ($size / 2) 0;
    border-color: transparent $color transparent transparent;
  } @else if $direction == right {
    border-width: ($size / 2) 0 ($size / 2) $size;
    border-color: transparent transparent transparent $color;
  }
}

.arrow {
  @include triangle(down, 10px, $primary-color);
}

// 7. Placeholder стили
@mixin placeholder {
  &::placeholder {
    @content;
  }
  &::-webkit-input-placeholder {
    @content;
  }
  &::-moz-placeholder {
    @content;
  }
  &:-ms-input-placeholder {
    @content;
  }
}

input {
  @include placeholder {
    color: $gray-400;
    font-style: italic;
  }
}

// 8. Hardware acceleration
@mixin hardware-accelerate {
  transform: translateZ(0);
  backface-visibility: hidden;
  perspective: 1000px;
}

// 9. Visually hidden (доступность)
@mixin visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}

// 10. Aspect ratio
@mixin aspect-ratio($width, $height) {
  position: relative;
  
  &::before {
    content: '';
    display: block;
    padding-top: ($height / $width) * 100%;
  }
  
  > * {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}

.video-container {
  @include aspect-ratio(16, 9);
}
```

**Требования:**
- Создайте 15 полезных миксинов
- Параметры с значениями по умолчанию
- Условная логика внутри миксинов
- @content для гибкости
- Комментарии с примерами использования

---

## Задача MIXIN-2: Медиа-запросы миксины
**Уровень сложности:** ⭐⭐⭐  
**Концепции:** Responsive mixins, breakpoints

**Условие:**
Создайте систему адаптивных миксинов.

**SCSS:**
```scss
// Breakpoints map
$breakpoints: (
  'xs': 0,
  'sm': 576px,
  'md': 768px,
  'lg': 992px,
  'xl': 1200px,
  'xxl': 1400px
);

// 1. Базовый media query mixin
@mixin media($breakpoint) {
  @if map-has-key($breakpoints, $breakpoint) {
    $value: map-get($breakpoints, $breakpoint);
    @media (min-width: $value) {
      @content;
    }
  } @else {
    @warn "Invalid breakpoint: #{$breakpoint}";
  }
}

// 2. Максимальная ширина
@mixin media-max($breakpoint) {
  @if map-has-key($breakpoints, $breakpoint) {
    $value: map-get($breakpoints, $breakpoint);
    @media (max-width: $value - 1px) {
      @content;
    }
  }
}

// 3. Диапазон
@mixin media-between($min, $max) {
  $min-value: map-get($breakpoints, $min);
  $max-value: map-get($breakpoints, $max);
  
  @media (min-width: $min-value) and (max-width: $max-value - 1px) {
    @content;
  }
}

// 4. Retina display
@mixin retina {
  @media (-webkit-min-device-pixel-ratio: 2),
         (min-resolution: 192dpi) {
    @content;
  }
}

// 5. Orientation
@mixin landscape {
  @media (orientation: landscape) {
    @content;
  }
}

@mixin portrait {
  @media (orientation: portrait) {
    @content;
  }
}

// 6. Dark mode
@mixin dark-mode {
  @media (prefers-color-scheme: dark) {
    @content;
  }
}

// 7. Motion preference
@mixin reduce-motion {
  @media (prefers-reduced-motion: reduce) {
    @content;
  }
}

// Использование
.container {
  padding: $spacing-md;
  
  @include media('md') {
    padding: $spacing-lg;
  }
  
  @include media('lg') {
    padding: $spacing-xl;
  }
}

.sidebar {
  display: none;
  
  @include media('lg') {
    display: block;
  }
}

.tablet-only {
  display: none;
  
  @include media-between('md', 'lg') {
    display: block;
  }
}

.image {
  background-image: url('image.jpg');
  
  @include retina {
    background-image: url('image@2x.jpg');
  }
}

.animated-element {
  animation: slideIn 0.5s ease;
  
  @include reduce-motion {
    animation: none;
  }
}

// 8. Генератор responsive классов
@mixin generate-responsive-classes($property, $values) {
  @each $name, $value in $values {
    .#{$property}-#{$name} {
      #{$property}: $value;
    }
    
    @each $bp-name, $bp-value in $breakpoints {
      @include media($bp-name) {
        .#{$property}-#{$name}-#{$bp-name} {
          #{$property}: $value;
        }
      }
    }
  }
}

// Генерация margin классов
$spacings: (
  '0': 0,
  '1': 0.25rem,
  '2': 0.5rem,
  '3': 1rem,
  '4': 1.5rem,
  '5': 3rem
);

@include generate-responsive-classes('margin', $spacings);
// Создаст: .margin-0, .margin-1-md, .margin-2-lg и т.д.
```

**Требования:**
- Mobile-first подход
- Миксины для всех сценариев
- Генерация responsive классов
- Поддержка retina, dark mode, motion
- Валидация входных данных

---

## Задача FUNC-1: Функции SCSS
**Уровень сложности:** ⭐⭐⭐  
**Концепции:** @function, @return, математика

**Условие:**
Создайте библиотеку полезных функций.

**SCSS:**
```scss
// 1. Конвертация px в rem
@function rem($pixels, $base: 16) {
  @return ($pixels / $base) * 1rem;
}

.element {
  font-size: rem(18); // 1.125rem
  padding: rem(24);   // 1.5rem
}

// 2. Работа с цветами
@function tint($color, $percentage) {
  @return mix(white, $color, $percentage);
}

@function shade($color, $percentage) {
  @return mix(black, $color, $percentage);
}

.box {
  background: $primary-color;
  border-color: shade($primary-color, 20%);
  
  &:hover {
    background: tint($primary-color, 20%);
  }
}

// 3. Генерация палитры цветов
@function generate-palette($base-color) {
  $palette: ();
  
  @for $i from 1 through 9 {
    $lightness: 10% * $i;
    $palette: map-merge($palette, (
      #{$i * 100}: if($i <= 5, 
        tint($base-color, 100% - $lightness * 2),
        shade($base-color, $lightness * 2 - 100%)
      )
    ));
  }
  
  @return $palette;
}

$blue-palette: generate-palette(#3498db);
// Результат: (100: #lightest, 500: #3498db, 900: #darkest)

// 4. Контрастный цвет текста
@function contrast-color($background) {
  $luminance: (
    red($background) * 0.299 +
    green($background) * 0.587 +
    blue($background) * 0.114
  ) / 255;
  
  @return if($luminance > 0.5, #000, #fff);
}

.auto-contrast {
  background: $primary-color;
  color: contrast-color($primary-color);
}

// 5. Fluid typography
@function fluid-size($min-size, $max-size, $min-vw: 320px, $max-vw: 1200px) {
  $slope: ($max-size - $min-size) / ($max-vw - $min-vw);
  $y-intercept: $min-size - $slope * $min-vw;
  
  @return clamp(#{$min-size}, #{$y-intercept} + #{$slope * 100}vw, #{$max-size});
}

h1 {
  font-size: fluid-size(24px, 48px);
}

// 6. Безопасное деление (SCSS 2.0+)
@use "sass:math";

@function divide($a, $b) {
  @return math.div($a, $b);
}

// 7. Strip unit (удалить единицу измерения)
@function strip-unit($number) {
  @return math.div($number, $number * 0 + 1);
}

$value: strip-unit(20px); // 20

// 8. Map deep get
@function map-deep-get($map, $keys...) {
  @each $key in $keys {
    $map: map-get($map, $key);
  }
  @return $map;
}

$config: (
  'colors': (
    'primary': (
      'base': #3498db,
      'dark': #2980b9
    )
  )
);

$primary-dark: map-deep-get($config, 'colors', 'primary', 'dark');

// 9. Генерация случайного цвета
@function random-color() {
  @return rgb(random(255), random(255), random(255));
}

// 10. Z-index функция
$z-layers: (
  'modal': 9000,
  'dropdown': 8000,
  'header': 7000,
  'default': 1
);

@function z($layer) {
  @if map-has-key($z-layers, $layer) {
    @return map-get($z-layers, $layer);
  }
  @warn "No z-index found for #{$layer}";
  @return map-get($z-layers, 'default');
}

.modal {
  z-index: z('modal');
}

// 11. Сумма значений списка
@function sum($list) {
  $result: 0;
  @each $item in $list {
    $result: $result + $item;
  }
  @return $result;
}

// 12. Среднее значение
@function average($list) {
  @return divide(sum($list), length($list));
}
```

**Требования:**
- 15 полезных функций
- Работа с цветами, размерами, списками
- Математические вычисления
- Валидация входных данных
- Возврат правильных типов данных

---

# 🎯 **РАЗДЕЛ 3: УПРАВЛЯЮЩИЕ ДИРЕКТИВЫ** (15 задач)

## Задача CONTROL-1: @if, @else условия
**Уровень сложности:** ⭐⭐  
**Концепции:** Conditional logic, @if/@else

**Условие:**
Создайте миксины с условной логикой.

**SCSS:**
```scss
// 1. Theme mixin с условием
@mixin theme-aware($property, $light-value, $dark-value, $theme: 'light') {
  @if $theme == 'light' {
    #{$property}: $light-value;
  } @else if $theme == 'dark' {
    #{$property}: $dark-value;
  } @else {
    @warn "Unknown theme: #{$theme}";
  }
}

.box {
  @include theme-aware('background', white, #1a1a1a, 'dark');
}

// 2. Кнопка с размерами
@mixin button-size($size) {
  @if $size == 'small' {
    padding: 0.5rem 1rem;
    font-size: 0.875rem;
  } @else if $size == 'medium' {
    padding: 0.75rem 1.5rem;
    font-size: 1rem;
  } @else if $size == 'large' {
    padding: 1rem 2rem;
    font-size: 1.25rem;
  } @else {
    @error "Invalid size: #{$size}. Use small, medium, or large.";
  }
}

.btn-small {
  @include button-size('small');
}

// 3. Responsive font size
@mixin responsive-font($min-size, $max-size, $min-width: 320px, $max-width: 1200px) {
  font-size: $min-size;
  
  @if $min-size != $max-size {
    @media (min-width: $min-width) {
      font-size: calc(#{$min-size} + (#{strip-unit($max-size)} - #{strip-unit($min-size)}) * ((100vw - #{$min-width}) / #{strip-unit($max-width) - strip-unit($min-width)}));
    }
    
    @media (min-width: $max-width) {
      font-size: $max-size;
    }
  }
}

// 4. Grid columns с проверкой
@mixin grid-columns($columns) {
  @if $columns <= 0 {
    @error "Columns must be greater than 0";
  } @else if $columns > 12 {
    @warn "Using more than 12 columns";
  }
  
  width: percentage(divide($columns, 12));
}

// 5. Контрастный border
@mixin smart-border($bg-color, $width: 1px) {
  $luminance: lightness($bg-color);
  
  @if $luminance > 90% {
    border: $width solid darken($bg-color, 10%);
  } @else if $luminance < 10% {
    border: $width solid lighten($bg-color, 10%);
  } @else {
    border: $width solid rgba(black, 0.1);
  }
}

// 6. Truncate с проверкой
@mixin smart-truncate($width: null, $lines: 1) {
  @if $width {
    max-width: $width;
  }
  
  @if $lines == 1 {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  } @else if $lines > 1 {
    display: -webkit-box;
    -webkit-line-clamp: $lines;
    -webkit-box-orient: vertical;
    overflow: hidden;
  } @else {
    @error "Lines must be 1 or greater";
  }
}

// 7. Direction-aware padding
@mixin padding-direction($direction, $amount) {
  @if $direction == 'horizontal' {
    padding-left: $amount;
    padding-right: $amount;
  } @else if $direction == 'vertical' {
    padding-top: $amount;
    padding-bottom: $amount;
  } @else if $direction == 'all' {
    padding: $amount;
  } @else {
    @error "Invalid direction: #{$direction}";
  }
}
```

**Требования:**
- Используйте @if/@else для вариаций
- Валидация входных параметров
- @warn для предупреждений
- @error для критических ошибок
- Логичные условия

---

## Задача CONTROL-2: @for циклы
**Уровень сложности:** ⭐⭐⭐  
**Концепции:** @for loops, генерация классов

**Условие:**
Генерируйте utility классы с помощью циклов.

**SCSS:**
```scss
// 1. Margin классы
@for $i from 0 through 10 {
  .m-#{$i} {
    margin: #{$i * 0.5}rem;
  }
  
  .mt-#{$i} {
    margin-top: #{$i * 0.5}rem;
  }
  
  .mr-#{$i} {
    margin-right: #{$i * 0.5}rem;
  }
  
  .mb-#{$i} {
    margin-bottom: #{$i * 0.5}rem;
  }
  
  .ml-#{$i} {
    margin-left: #{$i * 0.5}rem;
  }
  
  .mx-#{$i} {
    margin-left: #{$i * 0.5}rem;
    margin-right: #{$i * 0.5}rem;
  }
  
  .my-#{$i} {
    margin-top: #{$i * 0.5}rem;
    margin-bottom: #{$i * 0.5}rem;
  }
}

// 2. Grid columns
@for $i from 1 through 12 {
  .col-#{$i} {
    width: percentage(divide($i, 12));
  }
  
  .offset-#{$i} {
    margin-left: percentage(divide($i, 12));
  }
}

// 3. Z-index utility
@for $i from 1 through 10 {
  .z-#{$i * 10} {
    z-index: $i * 10;
  }
}

// 4. Opacity classes
@for $i from 0 through 10 {
  .opacity-#{$i * 10} {
    opacity: divide($i, 10);
  }
}

// 5. Font weight
$weights: 100, 200, 300, 400, 500, 600, 700, 800, 900;
@for $i from 1 through length($weights) {
  .font-#{nth($weights, $i)} {
    font-weight: nth($weights, $i);
  }
}

// 6. Loading animation с задержками
@for $i from 1 through 5 {
  .loading-dot:nth-child(#{$i}) {
    animation-delay: #{$i * 0.1}s;
  }
}

// 7. Staggered animations
@for $i from 1 through 20 {
  .fade-in:nth-child(#{$i}) {
    animation-delay: #{$i * 0.05}s;
  }
}

// 8. Color shades
$base-colors: (
  'blue': #3498db,
  'red': #e74c3c,
  'green': #2ecc71
);

@each $name, $color in $base-colors {
  @for $i from 1 through 9 {
    .text-#{$name}-#{$i}00 {
      @if $i < 5 {
        color: lighten($color, (5 - $i) * 10%);
      } @else if $i == 5 {
        color: $color;
      } @else {
        color: darken($color, ($i - 5) * 10%);
      }
    }
  }
}

// 9. Responsive text sizes
@for $i from 1 through 6 {
  h#{$i}, .h#{$i} {
    font-size: #{3 - ($i * 0.25)}rem;
    line-height: 1.2;
    margin-bottom: 1rem;
  }
}

// 10. Grid gap utilities
@for $i from 0 through 8 {
  .gap-#{$i} {
    gap: #{$i * 0.25}rem;
  }
}

// 11. Border radius
@for $i from 0 through 4 {
  .rounded-#{$i} {
    border-radius: #{$i * 0.25}rem;
  }
}

// 12. Rotation utilities
@for $i from 0 through 36 {
  .rotate-#{$i * 10} {
    transform: rotate(#{$i * 10}deg);
  }
}

// 13. Aspect ratios
$ratios: (1, 1), (16, 9), (4, 3), (21, 9);

@for $i from 1 through length($ratios) {
  $ratio: nth($ratios, $i);
  .aspect-#{nth($ratio, 1)}-#{nth($ratio, 2)} {
    aspect-ratio: #{nth($ratio, 1)} / #{nth($ratio, 2)};
  }
}
```

**Требования:**
- Генерация spacing utilities
- Grid системы
- Color variations
- Animation delays
- Responsive utilities

---

## Задача CONTROL-3: @each циклы
**Уровень сложности:** ⭐⭐⭐  
**Концепции:** @each with lists and maps

**Условие:**
Используйте @each для итерации по данным.

**SCSS:**
```scss
// 1. Social media colors
$social-colors: (
  'facebook': #3b5998,
  'twitter': #1da1f2,
  'instagram': #e4405f,
  'linkedin': #0077b5,
  'youtube': #ff0000,
  'github': #333,
  'pinterest': #bd081c
);

@each $network, $color in $social-colors {
  .btn-#{$network} {
    background-color: $color;
    color: white;
    
    &:hover {
      background-color: darken($color, 10%);
    }
  }
  
  .text-#{$network} {
    color: $color;
  }
  
  .border-#{$network} {
    border-color: $color;
  }
}

// 2. Button variants
$button-variants: (
  'primary': #3498db,
  'secondary': #2ecc71,
  'danger': #e74c3c,
  'warning': #f39c12,
  'info': #3498db,
  'success': #27ae60
);

@each $variant, $color in $button-variants {
  .btn-#{$variant} {
    background-color: $color;
    border-color: darken($color, 5%);
    color: white;
    
    &:hover {
      background-color: darken($color, 10%);
      border-color: darken($color, 15%);
    }
    
    &:active {
      background-color: darken($color, 15%);
    }
    
    &.btn-outline {
      background-color: transparent;
      color: $color;
      border-color: $color;
      
      &:hover {
        background-color: $color;
        color: white;
      }
    }
    
    &.btn-ghost {
      background-color: transparent;
      color: $color;
      border: none;
      
      &:hover {
        background-color: rgba($color, 0.1);
      }
    }
  }
}

// 3. Text alignment
$alignments: left, center, right, justify;

@each $align in $alignments {
  .text-#{$align} {
    text-align: $align;
  }
}

// 4. Display utilities
$displays: block, inline, inline-block, flex, grid, none;

@each $display in $displays {
  .d-#{$display} {
    display: $display;
  }
}

// 5. Flex utilities
$flex-props: (
  'row': row,
  'row-reverse': row-reverse,
  'column': column,
  'column-reverse': column-reverse
);

@each $name, $value in $flex-props {
  .flex-#{$name} {
    flex-direction: $value;
  }
}

$justify-content: (
  'start': flex-start,
  'end': flex-end,
  'center': center,
  'between': space-between,
  'around': space-around,
  'evenly': space-evenly
);

@each $name, $value in $justify-content {
  .justify-#{$name} {
    justify-content: $value;
  }
}

// 6. Breakpoints + utilities
$breakpoints: (
  'sm': 576px,
  'md': 768px,
  'lg': 992px,
  'xl': 1200px
);

$utilities: (
  'hidden': (display: none),
  'block': (display: block),
  'flex': (display: flex)
);

@each $bp-name, $bp-value in $breakpoints {
  @media (min-width: $bp-value) {
    @each $util-name, $properties in $utilities {
      .#{$util-name}-#{$bp-name} {
        @each $prop, $value in $properties {
          #{$prop}: $value;
        }
      }
    }
  }
}

// 7. Background patterns
$patterns: stripes, dots, grid, checkerboard;

@each $pattern in $patterns {
  .bg-#{$pattern} {
    @if $pattern == stripes {
      background-image: repeating-linear-gradient(
        45deg,
        transparent,
        transparent 10px,
        rgba(0,0,0,0.05) 10px,
        rgba(0,0,0,0.05) 20px
      );
    } @else if $pattern == dots {
      background-image: radial-gradient(circle, rgba(0,0,0,0.1) 1px, transparent 1px);
      background-size: 20px 20px;
    } @else if $pattern == grid {
      background-image: 
        linear-gradient(rgba(0,0,0,0.05) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,0,0,0.05) 1px, transparent 1px);
      background-size: 20px 20px;
    } @else if $pattern == checkerboard {
      background-image: 
        linear-gradient(45deg, rgba(0,0,0,0.05) 25%, transparent 25%),
        linear-gradient(-45deg, rgba(0,0,0,0.05) 25%, transparent 25%),
        linear-gradient(45deg, transparent 75%, rgba(0,0,0,0.05) 75%),
        linear-gradient(-45deg, transparent 75%, rgba(0,0,0,0.05) 75%);
      background-size: 20px 20px;
      background-position: 0 0, 0 10px, 10px -10px, -10px 0px;
    }
  }
}

// 8. Animation types
$animations: (
  'fade': (
    '0%': (opacity: 0),
    '100%': (opacity: 1)
  ),
  'slide-up': (
    '0%': (transform: translateY(20px), opacity: 0),
    '100%': (transform: translateY(0), opacity: 1)
  ),
  'scale': (
    '0%': (transform: scale(0.8), opacity: 0),
    '100%': (transform: scale(1), opacity: 1)
  )
);

@each $name, $keyframes in $animations {
  @keyframes #{$name} {
    @each $step, $props in $keyframes {
      #{$step} {
        @each $prop, $value in $props {
          #{$prop}: $value;
        }
      }
    }
  }
  
  .animate-#{$name} {
    animation: #{$name} 0.3s ease;
  }
}
```

**Требования:**
- Итерация по maps для вариантов
- Генерация utility классов
- Комбинация @each с breakpoints
- Nested loops для сложных структур
- DRY принцип

---

*Продолжение со следующими разделами: продвинутые техники, архитектура, практические проекты...*

---

# 🎯 **ПРАКТИЧЕСКИЕ ПРОЕКТЫ** (10 проектов)

## Проект 1: UI Component Library
**Сложность:** ⭐⭐⭐⭐  
**Требования:**
- Кнопки (10 вариантов)
- Формы (inputs, selects, checkboxes)
- Карточки
- Модальные окна
- Alerts и toasts
- Navigation компоненты
- Grid система
- Typography система
- Utility классы
- Темизация

**Структура:**
```scss
components/
├── _buttons.scss
├── _forms.scss
├── _cards.scss
├── _modals.scss
├── _alerts.scss
├── _navigation.scss
└── _typography.scss
```

---

## Проект 2: Responsive Grid System
**Сложность:** ⭐⭐⭐⭐  
**Требования:**
- 12-колоночная сетка
- Breakpoints система
- Gutters и spacing
- Offset классы
- Order классы
- Auto layout
- Вложенные grid'ы

---

**Курс готов!** Продолжить с остальными проектами или добавить больше задач?