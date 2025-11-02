# 🐘 PHP Solutions
## Детальные решения всех задач PHP курса

---

## 📋 Содержание

- [📝 Тема 1: Основы PHP](#-тема-1-основы-php)
- [🔄 Тема 2: Функции и массивы](#-тема-2-функции-и-массивы)
- [🌐 Тема 3: Веб-разработка](#-тема-3-веб-разработка)
- [💾 Тема 4: Базы данных](#-тема-4-базы-данных)
- [🏗️ Тема 5: ООП](#-тема-5-ооп)

---

# 📝 **ТЕМА 1: ОСНОВЫ PHP**

## 💡 Задача 1.1: Hello, PHP!

### 📋 **Условие:**
Создайте файл `index.php`, выведите "Hello, PHP!" и текущую дату/время.

### ✅ **Решение:**

```php
<?php
// index.php

// Установка локали для русского языка
setlocale(LC_TIME, 'ru_RU.UTF-8');

// Установка временной зоны
date_default_timezone_set('Europe/Moscow');

// Короткий синтаксис echo
echo "Hello, PHP!<br>";

// Длинный синтаксис print
print "Добро пожаловать в мир PHP!<br>";

// Текущая дата и время разными способами
echo "Текущая дата: " . date('d.m.Y') . "<br>";
echo "Текущее время: " . date('H:i:s') . "<br>";
echo "Полная дата: " . date('d.m.Y H:i:s') . "<br>";

// Используя DateTime класс (современный подход)
$now = new DateTime();
echo "DateTime: " . $now->format('d.m.Y H:i:s') . "<br>";

// Форматированный вывод с русскими названиями
$months = [
    1 => 'января', 'февраля', 'марта', 'апреля', 'мая', 'июня',
    'июля', 'августа', 'сентября', 'октября', 'ноября', 'декабря'
];

$day = date('j');
$month = $months[(int)date('n')];
$year = date('Y');

echo "Сегодня: {$day} {$month} {$year} года<br>";

// Timestamp
echo "Unix timestamp: " . time() . "<br>";

// Разные форматы
echo "ISO 8601: " . date('c') . "<br>";
echo "RFC 2822: " . date('r') . "<br>";
?>

<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello PHP</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 40px; }
        .highlight { color: #3498db; font-weight: bold; }
    </style>
</head>
<body>
    <h1 class="highlight">
        <?php echo "Hello, PHP!"; ?>
    </h1>
    
    <p>
        Страница сгенерирована: 
        <span class="highlight">
            <?= $now->format('d.m.Y в H:i:s') ?>
        </span>
    </p>
</body>
</html>
```

### 🎯 **Объяснение решения:**

1. **Синтаксис PHP:**
   - `<?php` - открывающий тег
   - `echo` vs `print` - разные способы вывода
   - `<?=` - короткий синтаксис для echo

2. **Работа с датой:**
   - `date()` - функция для форматирования
   - `DateTime` - объектно-ориентированный подход
   - `time()` - Unix timestamp

3. **Настройки:**
   - `setlocale()` - локализация
   - `date_default_timezone_set()` - часовой пояс

### 🔧 **Продвинутая версия:**

```php
<?php
class DateTimeHelper {
    private $timezone;
    private $locale;
    
    public function __construct($timezone = 'Europe/Moscow', $locale = 'ru_RU.UTF-8') {
        $this->timezone = new DateTimeZone($timezone);
        $this->locale = $locale;
        setlocale(LC_TIME, $locale);
    }
    
    public function getCurrentDateTime() {
        return new DateTime('now', $this->timezone);
    }
    
    public function formatRussian(DateTime $date) {
        $months = [
            1 => 'января', 'февраля', 'марта', 'апреля', 'мая', 'июня',
            'июля', 'августа', 'сентября', 'октября', 'ноября', 'декабря'
        ];
        
        $day = $date->format('j');
        $month = $months[(int)$date->format('n')];
        $year = $date->format('Y');
        $time = $date->format('H:i:s');
        
        return "{$day} {$month} {$year} года в {$time}";
    }
}

$helper = new DateTimeHelper();
$now = $helper->getCurrentDateTime();

echo "Hello, PHP!<br>";
echo "Сейчас: " . $helper->formatRussian($now);
?>
```

---

## 💡 Задача 1.2: Переменные и типы

### 📋 **Условие:**
Объявите переменные разных типов и используйте `var_dump()` и `gettype()`.

### ✅ **Решение:**

```php
<?php
// Переменные разных типов
$string_var = "Привет, мир!";
$integer_var = 42;
$float_var = 3.14159;
$boolean_true = true;
$boolean_false = false;
$null_var = null;
$array_var = [1, 2, 3, "четыре", 5.5];
$assoc_array = [
    'name' => 'Иван',
    'age' => 25,
    'city' => 'Москва'
];

// Создание объекта
$object_var = new stdClass();
$object_var->property = "значение";

// Создание ресурса
$resource_var = fopen('php://memory', 'r+');

echo "<h2>Анализ типов данных в PHP</h2>";
echo "<table border='1' cellpadding='10'>";
echo "<tr><th>Переменная</th><th>Значение</th><th>gettype()</th><th>var_dump()</th></tr>";

$variables = [
    'string_var' => $string_var,
    'integer_var' => $integer_var,
    'float_var' => $float_var,
    'boolean_true' => $boolean_true,
    'boolean_false' => $boolean_false,
    'null_var' => $null_var,
    'array_var' => $array_var,
    'assoc_array' => $assoc_array,
    'object_var' => $object_var,
    'resource_var' => $resource_var
];

foreach ($variables as $var_name => $var_value) {
    echo "<tr>";
    echo "<td>\${$var_name}</td>";
    echo "<td>";
    
    // Безопасный вывод значения
    if (is_array($var_value)) {
        echo "Array(" . count($var_value) . ")";
    } elseif (is_object($var_value)) {
        echo "Object(" . get_class($var_value) . ")";
    } elseif (is_resource($var_value)) {
        echo "Resource(" . get_resource_type($var_value) . ")";
    } elseif (is_bool($var_value)) {
        echo $var_value ? 'true' : 'false';
    } elseif (is_null($var_value)) {
        echo 'NULL';
    } else {
        echo htmlspecialchars($var_value);
    }
    
    echo "</td>";
    echo "<td>" . gettype($var_value) . "</td>";
    echo "<td><pre>";
    var_dump($var_value);
    echo "</pre></td>";
    echo "</tr>";
}

echo "</table>";

// Дополнительные функции проверки типов
echo "<h3>Функции проверки типов:</h3>";

$test_var = "123.45";
echo "<p>Переменная: \$test_var = '$test_var'</p>";
echo "<ul>";
echo "<li>is_string(\$test_var): " . (is_string($test_var) ? 'true' : 'false') . "</li>";
echo "<li>is_numeric(\$test_var): " . (is_numeric($test_var) ? 'true' : 'false') . "</li>";
echo "<li>is_int(\$test_var): " . (is_int($test_var) ? 'true' : 'false') . "</li>";
echo "<li>is_float(\$test_var): " . (is_float($test_var) ? 'true' : 'false') . "</li>";
echo "</ul>";

// Проверка на пустоту
echo "<h3>Проверка на пустоту:</h3>";
$empty_tests = [
    '""' => "",
    '"0"' => "0",
    '0' => 0,
    'false' => false,
    'null' => null,
    'array()' => array()
];

foreach ($empty_tests as $description => $value) {
    echo "<p>{$description}: empty() = " . (empty($value) ? 'true' : 'false') . 
         ", isset() = " . (isset($value) ? 'true' : 'false') . "</p>";
}

// Закрываем ресурс
fclose($resource_var);
?>
```

### 🎯 **Объяснение решения:**

1. **Основные типы PHP:**
   - `string` - строки
   - `integer` - целые числа
   - `float` (double) - числа с плавающей точкой
   - `boolean` - логические значения
   - `null` - пустое значение
   - `array` - массивы
   - `object` - объекты
   - `resource` - ресурсы

2. **Функции проверки:**
   - `gettype()` - возвращает тип переменной
   - `var_dump()` - подробная информация о переменной
   - `is_*()` - семейство функций для проверки типов

3. **Особенности:**
   - `empty()` vs `isset()` - разные подходы к проверке
   - Автоматическое приведение типов

---

## 💡 Задача 1.3: Приведение типов

### ✅ **Решение:**

```php
<?php
echo "<h2>Приведение типов в PHP</h2>";

// Исходные данные
$string_number = "123";
$string_float = "45.67";
$string_mixed = "89abc";
$string_non_numeric = "hello";
$boolean_true = true;
$boolean_false = false;
$null_value = null;

echo "<h3>1. Приведение к integer</h3>";
echo "<table border='1' cellpadding='5'>";
echo "<tr><th>Исходное значение</th><th>Тип</th><th>(int)</th><th>intval()</th></tr>";

$test_values = [
    '"123"' => $string_number,
    '"45.67"' => $string_float,
    '"89abc"' => $string_mixed,
    '"hello"' => $string_non_numeric,
    'true' => $boolean_true,
    'false' => $boolean_false,
    'null' => $null_value
];

foreach ($test_values as $description => $value) {
    echo "<tr>";
    echo "<td>{$description}</td>";
    echo "<td>" . gettype($value) . "</td>";
    echo "<td>" . (int)$value . "</td>";
    echo "<td>" . intval($value) . "</td>";
    echo "</tr>";
}
echo "</table>";

echo "<h3>2. Приведение к float</h3>";
echo "<table border='1' cellpadding='5'>";
echo "<tr><th>Исходное значение</th><th>Тип</th><th>(float)</th><th>floatval()</th></tr>";

foreach ($test_values as $description => $value) {
    echo "<tr>";
    echo "<td>{$description}</td>";
    echo "<td>" . gettype($value) . "</td>";
    echo "<td>" . (float)$value . "</td>";
    echo "<td>" . floatval($value) . "</td>";
    echo "</tr>";
}
echo "</table>";

echo "<h3>3. Приведение к string</h3>";
echo "<table border='1' cellpadding='5'>";
echo "<tr><th>Исходное значение</th><th>Тип</th><th>(string)</th><th>strval()</th></tr>";

$more_values = array_merge($test_values, [
    '123' => 123,
    '45.67' => 45.67,
    'array(1,2,3)' => [1, 2, 3]
]);

foreach ($more_values as $description => $value) {
    echo "<tr>";
    echo "<td>{$description}</td>";
    echo "<td>" . gettype($value) . "</td>";
    echo "<td>" . (string)$value . "</td>";
    echo "<td>" . strval($value) . "</td>";
    echo "</tr>";
}
echo "</table>";

echo "<h3>4. Строгое и нестрогое сравнение</h3>";

$comparisons = [
    ['0', '""', 'string vs string'],
    ['0', 'false', 'int vs bool'],
    ['"0"', 'false', 'string vs bool'],
    ['null', 'false', 'null vs bool'],
    ['"123"', '123', 'string vs int']
];

echo "<table border='1' cellpadding='5'>";
echo "<tr><th>Значение 1</th><th>Значение 2</th><th>== (нестрогое)</th><th>=== (строгое)</th><th>Примечание</th></tr>";

foreach ($comparisons as $comp) {
    eval("\$val1 = {$comp[0]};");
    eval("\$val2 = {$comp[1]};");
    
    echo "<tr>";
    echo "<td>{$comp[0]}</td>";
    echo "<td>{$comp[1]}</td>";
    echo "<td>" . ($val1 == $val2 ? 'true' : 'false') . "</td>";
    echo "<td>" . ($val1 === $val2 ? 'true' : 'false') . "</td>";
    echo "<td>{$comp[2]}</td>";
    echo "</tr>";
}
echo "</table>";

// Демонстрация автоматического приведения
echo "<h3>5. Автоматическое приведение типов</h3>";

$examples = [
    '"5" + 3' => "5" + 3,
    '"5.5" + 2' => "5.5" + 2,
    '"10abc" + 5' => "10abc" + 5,
    'true + 5' => true + 5,
    'false + 5' => false + 5
];

echo "<ul>";
foreach ($examples as $expression => $result) {
    echo "<li>{$expression} = {$result} (" . gettype($result) . ")</li>";
}
echo "</ul>";

// Функции для безопасного приведения
echo "<h3>6. Безопасное приведение типов</h3>";

function safeIntval($value, $default = 0) {
    if (is_numeric($value)) {
        return (int)$value;
    }
    return $default;
}

function safeFloatval($value, $default = 0.0) {
    if (is_numeric($value)) {
        return (float)$value;
    }
    return $default;
}

$unsafe_values = ["123", "45.67", "hello", "89abc"];

echo "<table border='1' cellpadding='5'>";
echo "<tr><th>Значение</th><th>safeIntval()</th><th>safeFloatval()</th></tr>";

foreach ($unsafe_values as $value) {
    echo "<tr>";
    echo "<td>\"{$value}\"</td>";
    echo "<td>" . safeIntval($value) . "</td>";
    echo "<td>" . safeFloatval($value) . "</td>";
    echo "</tr>";
}
echo "</table>";
?>
```

---

## 💡 Задача 1.4: Арифметика и факториал

### ✅ **Решение:**

```php
<?php
echo "<h2>Арифметические операции и факториал</h2>";

// Основные арифметические операции
$a = 15;
$b = 4;

echo "<h3>Базовые операции</h3>";
echo "<p>a = {$a}, b = {$b}</p>";
echo "<ul>";
echo "<li>a + b = " . ($a + $b) . "</li>";
echo "<li>a - b = " . ($a - $b) . "</li>";
echo "<li>a * b = " . ($a * $b) . "</li>";
echo "<li>a / b = " . ($a / $b) . "</li>";
echo "<li>a % b = " . ($a % $b) . " (остаток от деления)</li>";
echo "<li>a ** b = " . ($a ** $b) . " (возведение в степень, PHP 5.6+)</li>";
echo "</ul>";

// Операторы инкремента и декремента
echo "<h3>Инкремент и декремент</h3>";

$x = 5;
echo "<p>Начальное значение x = {$x}</p>";

echo "<table border='1' cellpadding='5'>";
echo "<tr><th>Операция</th><th>Результат</th><th>Значение x после</th></tr>";

// Префиксный инкремент
$x = 5;
$result = ++$x;
echo "<tr><td>++x (префиксный)</td><td>{$result}</td><td>{$x}</td></tr>";

// Постфиксный инкремент
$x = 5;
$result = $x++;
echo "<tr><td>x++ (постфиксный)</td><td>{$result}</td><td>{$x}</td></tr>";

// Префиксный декремент
$x = 5;
$result = --$x;
echo "<tr><td>--x (префиксный)</td><td>{$result}</td><td>{$x}</td></tr>";

// Постфиксный декремент
$x = 5;
$result = $x--;
echo "<tr><td>x-- (постфиксный)</td><td>{$result}</td><td>{$x}</td></tr>";

echo "</table>";

// Составные операторы присваивания
echo "<h3>Составные операторы</h3>";
$x = 10;
echo "<p>Начальное значение x = {$x}</p>";

$operations = [
    'x += 5' => function(&$x) { return $x += 5; },
    'x -= 3' => function(&$x) { return $x -= 3; },
    'x *= 2' => function(&$x) { return $x *= 2; },
    'x /= 4' => function(&$x) { return $x /= 4; },
    'x %= 3' => function(&$x) { return $x %= 3; }
];

echo "<table border='1' cellpadding='5'>";
echo "<tr><th>Операция</th><th>Результат</th></tr>";

foreach ($operations as $op_name => $operation) {
    $result = $operation($x);
    echo "<tr><td>{$op_name}</td><td>{$result}</td></tr>";
}
echo "</table>";

// Функции для вычисления факториала
echo "<h3>Вычисление факториала</h3>";

// Итеративная версия
function factorial_iterative($n) {
    if ($n < 0) {
        throw new InvalidArgumentException("Факториал не определен для отрицательных чисел");
    }
    
    if ($n <= 1) {
        return 1;
    }
    
    $result = 1;
    for ($i = 2; $i <= $n; $i++) {
        $result *= $i;
    }
    
    return $result;
}

// Рекурсивная версия
function factorial_recursive($n) {
    if ($n < 0) {
        throw new InvalidArgumentException("Факториал не определен для отрицательных чисел");
    }
    
    if ($n <= 1) {
        return 1;
    }
    
    return $n * factorial_recursive($n - 1);
}

// Версия с мемоизацией для оптимизации
class FactorialCalculator {
    private static $cache = [0 => 1, 1 => 1];
    
    public static function calculate($n) {
        if ($n < 0) {
            throw new InvalidArgumentException("Факториал не определен для отрицательных чисел");
        }
        
        if (!isset(self::$cache[$n])) {
            self::$cache[$n] = $n * self::calculate($n - 1);
        }
        
        return self::$cache[$n];
    }
    
    public static function getCache() {
        return self::$cache;
    }
}

// Тестирование функций
echo "<table border='1' cellpadding='5'>";
echo "<tr><th>n</th><th>Итеративно</th><th>Рекурсивно</th><th>С кэшем</th><th>Время (итер.)</th></tr>";

for ($n = 0; $n <= 10; $n++) {
    // Измерение времени выполнения
    $start_time = microtime(true);
    $iterative_result = factorial_iterative($n);
    $iterative_time = microtime(true) - $start_time;
    
    $recursive_result = factorial_recursive($n);
    $cached_result = FactorialCalculator::calculate($n);
    
    echo "<tr>";
    echo "<td>{$n}</td>";
    echo "<td>{$iterative_result}</td>";
    echo "<td>{$recursive_result}</td>";
    echo "<td>{$cached_result}</td>";
    echo "<td>" . number_format($iterative_time * 1000000, 2) . " мкс</td>";
    echo "</tr>";
}

echo "</table>";

// Большие числа (используем bcmath для точности)
if (extension_loaded('bcmath')) {
    echo "<h4>Факториал больших чисел (с использованием bcmath)</h4>";
    
    function factorial_big($n) {
        if ($n < 0) {
            throw new InvalidArgumentException("Факториал не определен для отрицательных чисел");
        }
        
        $result = '1';
        for ($i = 2; $i <= $n; $i++) {
            $result = bcmul($result, (string)$i);
        }
        
        return $result;
    }
    
    echo "<ul>";
    for ($n = 20; $n <= 25; $n++) {
        echo "<li>{$n}! = " . factorial_big($n) . "</li>";
    }
    echo "</ul>";
}

// Математические функции PHP
echo "<h3>Полезные математические функции</h3>";

$number = 15.7;
echo "<p>Число: {$number}</p>";
echo "<ul>";
echo "<li>abs(-{$number}) = " . abs(-$number) . "</li>";
echo "<li>round({$number}) = " . round($number) . "</li>";
echo "<li>ceil({$number}) = " . ceil($number) . "</li>";
echo "<li>floor({$number}) = " . floor($number) . "</li>";
echo "<li>sqrt({$number}) = " . sqrt($number) . "</li>";
echo "<li>pow({$number}, 2) = " . pow($number, 2) . "</li>";
echo "<li>log({$number}) = " . log($number) . "</li>";
echo "<li>sin({$number}) = " . sin($number) . "</li>";
echo "<li>cos({$number}) = " . cos($number) . "</li>";
echo "<li>max(1, 5, 3, {$number}) = " . max(1, 5, 3, $number) . "</li>";
echo "<li>min(1, 5, 3, {$number}) = " . min(1, 5, 3, $number) . "</li>";
echo "<li>rand(1, 100) = " . rand(1, 100) . "</li>";
echo "<li>mt_rand(1, 100) = " . mt_rand(1, 100) . " (лучший генератор)</li>";
echo "</ul>";
?>
```

### ⚡ **Лучшие практики:**
- ✅ Используйте строгую типизацию (`declare(strict_types=1)`)
- ✅ Проверяйте входные данные перед вычислениями
- ✅ Используйте `bcmath` для работы с большими числами
- ✅ Мемоизация для оптимизации рекурсивных вычислений
- ✅ Обрабатывайте исключения для некорректных данных

---

## 📊 **Итоги PHP решений**

### 🎯 **Изученные концепции:**
- ✅ Основы синтаксиса PHP
- ✅ Типы данных и их приведение
- ✅ Арифметические операции
- ✅ Функции и рекурсия
- ✅ Обработка ошибок

### 🔧 **Применяемые техники:**
- Объектно-ориентированное программирование
- Мемоизация и оптимизация
- Работа с большими числами
- Измерение производительности

### 🚀 **Следующий шаг:**
Переходите к [Теме 2: Функции и массивы](#-тема-2-функции-и-массивы)