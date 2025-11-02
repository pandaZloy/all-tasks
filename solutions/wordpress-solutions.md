# 📰 WordPress Solutions
## Детальные решения всех задач WordPress курса

---

## 📋 Содержание

- [🚀 Месяц 1: Основы WordPress](#-месяц-1-основы-wordpress)
- [🎨 Месяц 2: Темы WordPress](#-месяц-2-темы-wordpress)
- [🔧 Месяц 3: Плагины WordPress](#-месяц-3-плагины-wordpress)
- [⚡ Месяц 4: Продвинутая разработка](#-месяц-4-продвинутая-разработка)

---

# 🚀 **МЕСЯЦ 1: ОСНОВЫ WORDPRESS**

## 💡 Задача WP-1: Установка WordPress локально

### 📋 **Условие:**
Установите WordPress на локальный сервер разными способами.

### ✅ **Решение:**

#### 🔧 **Способ 1: Установка через XAMPP/MAMP**

```bash
# 1. Скачайте и установите XAMPP
# Windows: https://www.apachefriends.org/download.html
# Mac: используйте MAMP

# 2. Запустите Apache и MySQL в XAMPP Control Panel

# 3. Создайте базу данных
# Откройте http://localhost/phpmyadmin
# Создайте новую БД: wordpress_local
```

```sql
-- Создание базы данных для WordPress
CREATE DATABASE wordpress_local CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Создание пользователя (опционально)
CREATE USER 'wp_user'@'localhost' IDENTIFIED BY 'wp_password';
GRANT ALL PRIVILEGES ON wordpress_local.* TO 'wp_user'@'localhost';
FLUSH PRIVILEGES;
```

```php
<?php
// wp-config.php - базовая конфигурация

// ** MySQL настройки ** //
define( 'DB_NAME', 'wordpress_local' );
define( 'DB_USER', 'root' );  // или 'wp_user'
define( 'DB_PASSWORD', '' );  // или 'wp_password'
define( 'DB_HOST', 'localhost' );
define( 'DB_CHARSET', 'utf8mb4' );
define( 'DB_COLLATE', '' );

// Уникальные ключи и соли
define( 'AUTH_KEY',         'вставьте уникальную фразу здесь' );
define( 'SECURE_AUTH_KEY',  'вставьте уникальную фразу здесь' );
define( 'LOGGED_IN_KEY',    'вставьте уникальную фразу здесь' );
define( 'NONCE_KEY',        'вставьте уникальную фразу здесь' );
define( 'AUTH_SALT',        'вставьте уникальную фразу здесь' );
define( 'SECURE_AUTH_SALT', 'вставьте уникальную фразу здесь' );
define( 'LOGGED_IN_SALT',   'вставьте уникальную фразу здесь' );
define( 'NONCE_SALT',       'вставьте уникальную фразу здесь' );

// Префикс таблиц
$table_prefix = 'wp_';

// Режим отладки
define( 'WP_DEBUG', true );
define( 'WP_DEBUG_LOG', true );
define( 'WP_DEBUG_DISPLAY', false );

// Дополнительные настройки для разработки
define( 'WP_ENVIRONMENT_TYPE', 'local' );
define( 'DISALLOW_FILE_EDIT', true );
define( 'WP_POST_REVISIONS', 3 );
define( 'AUTOSAVE_INTERVAL', 300 );

if ( ! defined( 'ABSPATH' ) ) {
    define( 'ABSPATH', __DIR__ . '/' );
}

require_once ABSPATH . 'wp-settings.php';
?>
```

#### 🐳 **Способ 2: Установка через Docker**

```yaml
# docker-compose.yml
version: '3.8'

services:
  wordpress:
    image: wordpress:latest
    container_name: wp_site
    restart: always
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress_password
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DEBUG: 1
    volumes:
      - ./wp-content:/var/www/html/wp-content
      - ./uploads.ini:/usr/local/etc/php/conf.d/uploads.ini
    depends_on:
      - db

  db:
    image: mysql:8.0
    container_name: wp_database
    restart: always
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress_password
      MYSQL_ROOT_PASSWORD: root_password
    volumes:
      - db_data:/var/lib/mysql
    ports:
      - "3306:3306"

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    container_name: wp_phpmyadmin
    restart: always
    ports:
      - "8081:80"
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: root_password

volumes:
  db_data:
```

```ini
# uploads.ini - увеличение лимитов PHP
file_uploads = On
memory_limit = 256M
upload_max_filesize = 64M
post_max_size = 64M
max_execution_time = 300
```

```bash
# Команды для запуска
docker-compose up -d

# Проверка статуса
docker-compose ps

# Просмотр логов
docker-compose logs wordpress

# Остановка
docker-compose down
```

#### 🌐 **Способ 3: Local by Flywheel**

```bash
# 1. Скачайте Local by Flywheel с https://localwp.com/
# 2. Установите приложение
# 3. Создайте новый сайт через интерфейс

# Преимущества Local:
# - Простая установка в один клик
# - Управление несколькими сайтами
# - Встроенный SSL
# - Легкий доступ к файлам и БД
# - Автоматические бэкапы
```

### 🎯 **Структура файлов WordPress:**

```
wordpress/
├── wp-admin/              # Административная панель
├── wp-content/            # Пользовательский контент
│   ├── themes/           # Темы
│   ├── plugins/          # Плагины
│   ├── uploads/          # Загруженные файлы
│   └── mu-plugins/       # Обязательные плагины
├── wp-includes/          # Основные файлы WordPress
├── wp-config.php         # Конфигурация
├── .htaccess             # Настройки сервера
└── index.php             # Точка входа
```

### 🔧 **Продвинутая конфигурация:**

```php
<?php
// wp-config.php - расширенная конфигурация

// Многосайтовая сеть
define( 'WP_ALLOW_MULTISITE', true );

// Настройки памяти
define( 'WP_MEMORY_LIMIT', '256M' );

// Настройки кэширования
define( 'WP_CACHE', true );
define( 'ENABLE_CACHE', true );

// Безопасность
define( 'FORCE_SSL_ADMIN', true );
define( 'DISALLOW_FILE_MODS', false ); // для разработки

// Автоматические обновления
define( 'WP_AUTO_UPDATE_CORE', 'minor' );

// Настройки для разработки
if ( WP_DEBUG ) {
    define( 'SCRIPT_DEBUG', true );
    define( 'CONCATENATE_SCRIPTS', false );
    define( 'COMPRESS_SCRIPTS', false );
    define( 'COMPRESS_CSS', false );
    
    // Логирование запросов к БД
    define( 'SAVEQUERIES', true );
}

// Пользовательские константы
define( 'WP_DEFAULT_THEME', 'twentytwentyfour' );
define( 'UPLOADS', 'wp-content/uploads' );
?>
```

---

## 💡 Задача WP-2: Панель администратора

### 📋 **Условие:**
Освойте навигацию и основные функции админ-панели WordPress.

### ✅ **Решение:**

#### 🎛️ **Настройка Settings (Настройки)**

```php
<?php
// functions.php - кастомизация админ-панели

// Удаление ненужных виджетов с Dashboard
function remove_dashboard_widgets() {
    global $wp_meta_boxes;
    
    unset($wp_meta_boxes['dashboard']['side']['core']['dashboard_quick_press']);
    unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_incoming_links']);
    unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_right_now']);
    unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_plugins']);
    unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_recent_drafts']);
    unset($wp_meta_boxes['dashboard']['normal']['core']['dashboard_recent_comments']);
    unset($wp_meta_boxes['dashboard']['side']['core']['dashboard_primary']);
    unset($wp_meta_boxes['dashboard']['side']['core']['dashboard_secondary']);
}
add_action('wp_dashboard_setup', 'remove_dashboard_widgets');

// Добавление кастомного виджета на Dashboard
function add_custom_dashboard_widget() {
    wp_add_dashboard_widget(
        'custom_dashboard_widget',
        'Информация о сайте',
        'custom_dashboard_widget_content'
    );
}
add_action('wp_dashboard_setup', 'add_custom_dashboard_widget');

function custom_dashboard_widget_content() {
    $theme = wp_get_theme();
    $users_count = count_users();
    $posts_count = wp_count_posts();
    $pages_count = wp_count_posts('page');
    
    echo '<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 15px;">';
    echo '<div>';
    echo '<h4>Информация о теме</h4>';
    echo '<p><strong>Активная тема:</strong> ' . $theme->get('Name') . '</p>';
    echo '<p><strong>Версия:</strong> ' . $theme->get('Version') . '</p>';
    echo '<p><strong>Автор:</strong> ' . $theme->get('Author') . '</p>';
    echo '</div>';
    
    echo '<div>';
    echo '<h4>Статистика контента</h4>';
    echo '<p><strong>Пользователей:</strong> ' . $users_count['total_users'] . '</p>';
    echo '<p><strong>Записей:</strong> ' . $posts_count->publish . '</p>';
    echo '<p><strong>Страниц:</strong> ' . $pages_count->publish . '</p>';
    echo '</div>';
    echo '</div>';
    
    echo '<h4>Последние действия</h4>';
    echo '<ul>';
    echo '<li>Последний вход: ' . date('d.m.Y H:i') . '</li>';
    echo '<li>WordPress версия: ' . get_bloginfo('version') . '</li>';
    echo '<li>PHP версия: ' . phpversion() . '</li>';
    echo '</ul>';
}

// Кастомизация футера админки
function custom_admin_footer() {
    echo '<span id="footer-thankyou">Создано с ❤️ для ' . get_bloginfo('name') . '</span>';
}
add_filter('admin_footer_text', 'custom_admin_footer');

// Удаление версии WordPress из футера
function remove_wordpress_version() {
    return '';
}
add_filter('update_footer', 'remove_wordpress_version', 9999);

// Кастомное приветствие
function custom_howdy($translated, $text, $domain) {
    $new_message = str_replace('Howdy', 'Добро пожаловать', $text);
    return $new_message;
}
add_filter('gettext', 'custom_howdy', 10, 3);
?>
```

#### 🔐 **Управление пользователями и ролями**

```php
<?php
// Создание кастомной роли
function add_custom_roles() {
    // Роль "Редактор контента"
    add_role(
        'content_editor',
        'Редактор контента',
        [
            'read' => true,
            'edit_posts' => true,
            'edit_others_posts' => true,
            'publish_posts' => true,
            'edit_pages' => true,
            'edit_others_pages' => true,
            'publish_pages' => true,
            'edit_published_posts' => true,
            'edit_published_pages' => true,
            'delete_posts' => true,
            'delete_others_posts' => true,
            'delete_published_posts' => true,
            'upload_files' => true,
            'manage_categories' => true,
            'moderate_comments' => true
        ]
    );
    
    // Роль "SEO Специалист"
    add_role(
        'seo_specialist',
        'SEO Специалист',
        [
            'read' => true,
            'edit_posts' => true,
            'edit_pages' => true,
            'edit_published_posts' => true,
            'edit_published_pages' => true,
            'manage_categories' => true,
            'manage_options' => false // Ограниченный доступ к настройкам
        ]
    );
}
add_action('init', 'add_custom_roles');

// Добавление кастомных возможностей к существующим ролям
function modify_user_capabilities() {
    $role = get_role('editor');
    if ($role) {
        $role->add_cap('edit_theme_options');
        $role->add_cap('customize');
    }
}
add_action('admin_init', 'modify_user_capabilities');

// Ограничение доступа к определенным разделам админки
function restrict_admin_access() {
    if (defined('DOING_AJAX') && DOING_AJAX) {
        return;
    }
    
    if (!current_user_can('manage_options')) {
        if (in_array($GLOBALS['pagenow'], ['themes.php', 'plugins.php', 'users.php'])) {
            wp_die('У вас нет доступа к этой странице.');
        }
    }
}
add_action('admin_init', 'restrict_admin_access');

// Кастомизация профиля пользователя
function add_custom_user_fields($user) {
    ?>
    <h3>Дополнительная информация</h3>
    <table class="form-table">
        <tr>
            <th><label for="phone">Телефон</label></th>
            <td>
                <input type="text" name="phone" id="phone" 
                       value="<?php echo esc_attr(get_user_meta($user->ID, 'phone', true)); ?>" 
                       class="regular-text" />
            </td>
        </tr>
        <tr>
            <th><label for="position">Должность</label></th>
            <td>
                <input type="text" name="position" id="position" 
                       value="<?php echo esc_attr(get_user_meta($user->ID, 'position', true)); ?>" 
                       class="regular-text" />
            </td>
        </tr>
        <tr>
            <th><label for="department">Отдел</label></th>
            <td>
                <select name="department" id="department">
                    <option value="">Выберите отдел</option>
                    <option value="marketing" <?php selected(get_user_meta($user->ID, 'department', true), 'marketing'); ?>>Маркетинг</option>
                    <option value="sales" <?php selected(get_user_meta($user->ID, 'department', true), 'sales'); ?>>Продажи</option>
                    <option value="development" <?php selected(get_user_meta($user->ID, 'department', true), 'development'); ?>>Разработка</option>
                    <option value="support" <?php selected(get_user_meta($user->ID, 'department', true), 'support'); ?>>Поддержка</option>
                </select>
            </td>
        </tr>
    </table>
    <?php
}
add_action('show_user_profile', 'add_custom_user_fields');
add_action('edit_user_profile', 'add_custom_user_fields');

// Сохранение кастомных полей
function save_custom_user_fields($user_id) {
    if (!current_user_can('edit_user', $user_id)) {
        return;
    }
    
    update_user_meta($user_id, 'phone', sanitize_text_field($_POST['phone']));
    update_user_meta($user_id, 'position', sanitize_text_field($_POST['position']));
    update_user_meta($user_id, 'department', sanitize_text_field($_POST['department']));
}
add_action('personal_options_update', 'save_custom_user_fields');
add_action('edit_user_profile_update', 'save_custom_user_fields');
?>
```

#### 🔗 **Настройка ЧПУ (Permalinks)**

```php
<?php
// Кастомные правила перезаписи URL
function add_custom_rewrite_rules() {
    // Правило для архива продуктов
    add_rewrite_rule(
        '^products/([^/]*)/page/?([0-9]{1,})/?$',
        'index.php?post_type=product&product_category=$matches[1]&paged=$matches[2]',
        'top'
    );
    
    // Правило для отдельного продукта
    add_rewrite_rule(
        '^product/([^/]*)/?',
        'index.php?post_type=product&name=$matches[1]',
        'top'
    );
    
    // Правило для пользовательских профилей
    add_rewrite_rule(
        '^profile/([^/]*)/?',
        'index.php?pagename=profile&user_slug=$matches[1]',
        'top'
    );
}
add_action('init', 'add_custom_rewrite_rules');

// Добавление кастомных query vars
function add_custom_query_vars($vars) {
    $vars[] = 'user_slug';
    $vars[] = 'product_category';
    return $vars;
}
add_filter('query_vars', 'add_custom_query_vars');

// Принудительное обновление правил перезаписи (выполнить один раз)
function flush_rewrite_rules_on_activation() {
    add_custom_rewrite_rules();
    flush_rewrite_rules();
}
// Раскомментировать и выполнить один раз для активации
// add_action('init', 'flush_rewrite_rules_on_activation');
?>
```

### ⚡ **Полезные сниппеты для админки:**

```php
<?php
// Скрытие обновлений для не-администраторов
function hide_update_notice_to_all_but_admin() {
    if (!current_user_can('update_core')) {
        remove_action('admin_notices', 'update_nag', 3);
    }
}
add_action('admin_head', 'hide_update_notice_to_all_but_admin', 1);

// Добавление кастомного CSS в админку
function custom_admin_css() {
    echo '<style>
        .dashboard-widget-content {
            padding: 20px;
        }
        #dashboard-widgets .meta-box-sortables {
            min-height: 0;
        }
        .custom-admin-notice {
            border-left: 4px solid #007cba;
            background: #f0f6fc;
            padding: 12px;
            margin: 15px 0;
        }
    </style>';
}
add_action('admin_head', 'custom_admin_css');

// Кастомные уведомления в админке
function show_custom_admin_notice() {
    $screen = get_current_screen();
    if ($screen->id === 'dashboard') {
        echo '<div class="notice custom-admin-notice">
            <p><strong>Добро пожаловать!</strong> Вы находитесь в панели управления сайтом.</p>
        </div>';
    }
}
add_action('admin_notices', 'show_custom_admin_notice');

// Добавление колонки в список постов
function add_post_columns($columns) {
    $columns['post_views'] = 'Просмотры';
    $columns['word_count'] = 'Слов';
    return $columns;
}
add_filter('manage_posts_columns', 'add_post_columns');

function populate_post_columns($column, $post_id) {
    switch ($column) {
        case 'post_views':
            $views = get_post_meta($post_id, 'post_views', true);
            echo $views ? $views : '0';
            break;
        case 'word_count':
            $content = get_post_field('post_content', $post_id);
            $word_count = str_word_count(strip_tags($content));
            echo $word_count;
            break;
    }
}
add_action('manage_posts_custom_column', 'populate_post_columns', 10, 2);

// Сортировка колонок
function make_post_columns_sortable($columns) {
    $columns['post_views'] = 'post_views';
    $columns['word_count'] = 'word_count';
    return $columns;
}
add_filter('manage_edit-post_sortable_columns', 'make_post_columns_sortable');
?>
```

---

## 💡 Задача WP-3: Работа с постами

### ✅ **Решение:**

```php
<?php
// Создание постов программно (для тестирования)
function create_sample_posts() {
    // Проверяем, что посты еще не созданы
    if (get_option('sample_posts_created')) {
        return;
    }
    
    $categories = [
        'Технологии' => 'technology',
        'Дизайн' => 'design',
        'Маркетинг' => 'marketing',
        'Разработка' => 'development',
        'Бизнес' => 'business'
    ];
    
    // Создаем категории
    $category_ids = [];
    foreach ($categories as $name => $slug) {
        $term = wp_insert_term($name, 'category', ['slug' => $slug]);
        if (!is_wp_error($term)) {
            $category_ids[$slug] = $term['term_id'];
        }
    }
    
    // Создаем теги
    $tags = ['веб-разработка', 'JavaScript', 'PHP', 'WordPress', 'CSS', 'HTML', 'React', 'Vue.js', 'SEO', 'UX/UI'];
    
    // Примеры постов
    $sample_posts = [
        [
            'title' => 'Введение в современную веб-разработку',
            'content' => 'Веб-разработка сегодня требует знания множества технологий. В этой статье мы рассмотрим основные инструменты и подходы, которые должен знать каждый разработчик...',
            'category' => 'development',
            'tags' => ['веб-разработка', 'JavaScript', 'PHP'],
            'featured_image' => 'https://via.placeholder.com/800x400/3498db/ffffff?text=Web+Development'
        ],
        [
            'title' => 'Основы дизайна пользовательских интерфейсов',
            'content' => 'Хороший UX/UI дизайн - это основа успешного продукта. Разберем принципы создания интуитивно понятных интерфейсов...',
            'category' => 'design',
            'tags' => ['UX/UI', 'дизайн'],
            'featured_image' => 'https://via.placeholder.com/800x400/e74c3c/ffffff?text=UI+Design'
        ],
        [
            'title' => 'SEO оптимизация для WordPress сайтов',
            'content' => 'Поисковая оптимизация критически важна для видимости вашего сайта. Рассмотрим лучшие практики SEO для WordPress...',
            'category' => 'marketing',
            'tags' => ['SEO', 'WordPress', 'маркетинг'],
            'featured_image' => 'https://via.placeholder.com/800x400/2ecc71/ffffff?text=SEO'
        ],
        [
            'title' => 'Создание адаптивных сайтов с CSS Grid',
            'content' => 'CSS Grid революционизировал способ создания макетов. Изучим, как создавать современные адаптивные дизайны...',
            'category' => 'development',
            'tags' => ['CSS', 'веб-разработка'],
            'featured_image' => 'https://via.placeholder.com/800x400/9b59b6/ffffff?text=CSS+Grid'
        ],
        [
            'title' => 'Тренды в веб-дизайне 2025',
            'content' => 'Какие тренды будут актуальны в веб-дизайне в 2025 году? Обзор самых интересных направлений...',
            'category' => 'design',
            'tags' => ['дизайн', 'тренды'],
            'featured_image' => 'https://via.placeholder.com/800x400/f39c12/ffffff?text=Design+Trends'
        ]
    ];
    
    foreach ($sample_posts as $i => $post_data) {
        $post_args = [
            'post_title' => $post_data['title'],
            'post_content' => $post_data['content'] . "\n\n" . 
                            'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
            'post_status' => 'publish',
            'post_type' => 'post',
            'post_category' => [$category_ids[$post_data['category']]],
            'tags_input' => $post_data['tags'],
            'meta_input' => [
                'post_views' => rand(10, 1000),
                '_yoast_wpseo_metadesc' => 'SEO описание для поста: ' . $post_data['title']
            ]
        ];
        
        $post_id = wp_insert_post($post_args);
        
        if ($post_id && !is_wp_error($post_id)) {
            // Добавляем изображение записи (placeholder)
            if (isset($post_data['featured_image'])) {
                $attachment_id = media_sideload_image($post_data['featured_image'], $post_id, '', 'id');
                if (!is_wp_error($attachment_id)) {
                    set_post_thumbnail($post_id, $attachment_id);
                }
            }
            
            // Добавляем кастомные поля
            update_post_meta($post_id, 'reading_time', rand(3, 15) . ' мин');
            update_post_meta($post_id, 'difficulty_level', ['Новичок', 'Средний', 'Продвинутый'][rand(0, 2)]);
            update_post_meta($post_id, 'author_note', 'Дополнительные материалы доступны по ссылке в конце статьи.');
        }
    }
    
    // Отмечаем, что посты созданы
    update_option('sample_posts_created', true);
}

// Раскомментировать для создания тестовых постов
// add_action('init', 'create_sample_posts');

// Добавление кастомных мета-полей к постам
function add_custom_post_meta_fields() {
    add_meta_box(
        'post_additional_info',
        'Дополнительная информация',
        'post_additional_info_callback',
        'post',
        'side',
        'default'
    );
}
add_action('add_meta_boxes', 'add_custom_post_meta_fields');

function post_additional_info_callback($post) {
    wp_nonce_field('save_post_additional_info', 'post_additional_info_nonce');
    
    $reading_time = get_post_meta($post->ID, 'reading_time', true);
    $difficulty_level = get_post_meta($post->ID, 'difficulty_level', true);
    $author_note = get_post_meta($post->ID, 'author_note', true);
    $is_featured = get_post_meta($post->ID, 'is_featured', true);
    ?>
    <table style="width: 100%;">
        <tr>
            <td><label for="reading_time">Время чтения:</label></td>
            <td><input type="text" id="reading_time" name="reading_time" value="<?php echo esc_attr($reading_time); ?>" placeholder="5 мин" /></td>
        </tr>
        <tr>
            <td><label for="difficulty_level">Уровень сложности:</label></td>
            <td>
                <select id="difficulty_level" name="difficulty_level">
                    <option value="">Выберите уровень</option>
                    <option value="Новичок" <?php selected($difficulty_level, 'Новичок'); ?>>Новичок</option>
                    <option value="Средний" <?php selected($difficulty_level, 'Средний'); ?>>Средний</option>
                    <option value="Продвинутый" <?php selected($difficulty_level, 'Продвинутый'); ?>>Продвинутый</option>
                </select>
            </td>
        </tr>
        <tr>
            <td colspan="2">
                <label for="author_note">Заметка автора:</label><br>
                <textarea id="author_note" name="author_note" rows="3" style="width: 100%;"><?php echo esc_textarea($author_note); ?></textarea>
            </td>
        </tr>
        <tr>
            <td colspan="2">
                <label>
                    <input type="checkbox" name="is_featured" value="1" <?php checked($is_featured, 1); ?> />
                    Рекомендуемая статья
                </label>
            </td>
        </tr>
    </table>
    <?php
}

function save_post_additional_info($post_id) {
    if (!isset($_POST['post_additional_info_nonce']) || 
        !wp_verify_nonce($_POST['post_additional_info_nonce'], 'save_post_additional_info')) {
        return;
    }
    
    if (defined('DOING_AUTOSAVE') && DOING_AUTOSAVE) {
        return;
    }
    
    if (!current_user_can('edit_post', $post_id)) {
        return;
    }
    
    update_post_meta($post_id, 'reading_time', sanitize_text_field($_POST['reading_time']));
    update_post_meta($post_id, 'difficulty_level', sanitize_text_field($_POST['difficulty_level']));
    update_post_meta($post_id, 'author_note', sanitize_textarea_field($_POST['author_note']));
    update_post_meta($post_id, 'is_featured', isset($_POST['is_featured']) ? 1 : 0);
}
add_action('save_post', 'save_post_additional_info');

// Подсчет просмотров постов
function track_post_views($post_id) {
    if (!is_single()) return;
    if (empty($post_id)) {
        global $post;
        $post_id = $post->ID;
    }
    
    $count = get_post_meta($post_id, 'post_views', true);
    $count = $count ? $count + 1 : 1;
    update_post_meta($post_id, 'post_views', $count);
}
add_action('wp_head', function() {
    if (is_single()) {
        global $post;
        track_post_views($post->ID);
    }
});

// Вывод дополнительной информации в постах
function display_post_additional_info($content) {
    if (!is_single()) {
        return $content;
    }
    
    global $post;
    
    $reading_time = get_post_meta($post->ID, 'reading_time', true);
    $difficulty_level = get_post_meta($post->ID, 'difficulty_level', true);
    $author_note = get_post_meta($post->ID, 'author_note', true);
    $views = get_post_meta($post->ID, 'post_views', true);
    $is_featured = get_post_meta($post->ID, 'is_featured', true);
    
    $additional_info = '<div class="post-additional-info" style="background: #f8f9fa; padding: 20px; margin: 20px 0; border-radius: 8px; border-left: 4px solid #007cba;">';
    
    if ($is_featured) {
        $additional_info .= '<div style="background: #007cba; color: white; padding: 5px 10px; border-radius: 4px; display: inline-block; margin-bottom: 10px; font-size: 12px;">⭐ РЕКОМЕНДУЕМАЯ СТАТЬЯ</div>';
    }
    
    $additional_info .= '<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 15px; margin-bottom: 15px;">';
    
    if ($reading_time) {
        $additional_info .= '<div><strong>⏱ Время чтения:</strong><br>' . esc_html($reading_time) . '</div>';
    }
    
    if ($difficulty_level) {
        $additional_info .= '<div><strong>📊 Уровень:</strong><br>' . esc_html($difficulty_level) . '</div>';
    }
    
    if ($views) {
        $additional_info .= '<div><strong>👁 Просмотров:</strong><br>' . number_format($views) . '</div>';
    }
    
    $additional_info .= '<div><strong>📅 Опубликовано:</strong><br>' . get_the_date() . '</div>';
    
    $additional_info .= '</div>';
    
    if ($author_note) {
        $additional_info .= '<div style="font-style: italic; color: #666; border-top: 1px solid #ddd; padding-top: 15px;">';
        $additional_info .= '<strong>💡 От автора:</strong> ' . esc_html($author_note);
        $additional_info .= '</div>';
    }
    
    $additional_info .= '</div>';
    
    return $additional_info . $content;
}
add_filter('the_content', 'display_post_additional_info');
?>
```

### ⚡ **Лучшие практики WordPress:**
- ✅ Всегда проверяйте права доступа (`current_user_can()`)
- ✅ Используйте nonce для безопасности форм
- ✅ Санитизируйте и валидируйте входные данные
- ✅ Применяйте хуки и фильтры вместо изменения core файлов
- ✅ Создавайте резервные копии перед изменениями

---

## 📊 **Итоги WordPress решений**

### 🎯 **Изученные концепции:**
- ✅ Установка и настройка WordPress
- ✅ Кастомизация админ-панели
- ✅ Управление пользователями и ролями
- ✅ Работа с постами и мета-полями
- ✅ Хуки и фильтры WordPress

### 🔧 **Применяемые техники:**
- Docker контейнеризация
- Кастомные роли и возможности
- Программное создание контента
- Безопасная обработка данных

### 🚀 **Следующий шаг:**
Переходите к [Месяцу 2: Темы WordPress](#-месяц-2-темы-wordpress)