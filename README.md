## Premium WordPress Theme Development Guidelines (PHP 8.4+, WordPress Latest)

This document outlines all the necessary standards and best practices to develop a premium WordPress theme that is secure, performance-optimized, ThemeForest-ready, and compatible with the latest versions of PHP (8.4+) and WordPress.

---

### ✅ Core Compatibility Requirements

* Must support **latest WordPress Core**
* Fully compatible with **PHP 8.4+**
* Built for **Gutenberg**, **Elementor**, **WooCommerce**, **Redux**, **WPML**, **RTL**
* 100% **translation ready** and **child-theme friendly**
* Follows **ThemeForest WordPress Theme Submission Requirements**

---

### 🧠 Coding Standards and Practices

#### Prefixing

* All functions, classes, constants, and hooks must be **prefixed** to avoid naming conflicts.
* Example: `mytheme_register_menus()`, `MyTheme_Breadcrumb`, `MYTHEME_VERSION`

#### File Guards

* Every PHP file must begin with:

```php
if ( ! defined( 'ABSPATH' ) ) {
    exit; // Exit if accessed directly
}
```

#### Function/Class Existence Check

* Wrap all functions and classes in `function_exists()` and `class_exists()` respectively:

```php
if ( ! function_exists( 'mytheme_custom_function' ) ) {
    function mytheme_custom_function() {
        // code
    }
}
```

---

### 🎯 Theme Structure (Recommended)

```
mytheme/
├── assets/
│   ├── css/
│   ├── js/
│   └── images/
├── inc/
│   ├── class-mytheme-loader.php
│   └── class-mytheme-header.php
├── template-parts/
│   ├── header/
│   ├── footer/
│   └── content/
├── languages/
├── functions.php
├── style.css
├── screenshot.png
└── readme.txt
```

---

### 🧩 Theme Features and Setup

#### Theme Supports

```php
add_theme_support( 'title-tag' );
add_theme_support( 'post-thumbnails' );
add_theme_support( 'woocommerce' );
add_theme_support( 'custom-logo' );
add_theme_support( 'automatic-feed-links' );
add_theme_support( 'html5', array( 'search-form', 'comment-form', 'comment-list', 'gallery', 'caption' ) );
```

#### Menus & Sidebars

```php
register_nav_menus( array(
    'primary' => __( 'Primary Menu', 'mytheme' )
) );

register_sidebar( array(
    'name'          => __( 'Main Sidebar', 'mytheme' ),
    'id'            => 'main-sidebar',
    'before_widget' => '<div class="widget %2$s">',
    'after_widget'  => '</div>',
    'before_title'  => '<h3 class="widget-title">',
    'after_title'   => '</h3>',
) );
```

---

### 🛡️ Security & Data Handling

#### Escaping Output (Always!)

* `esc_html()` – For text
* `esc_attr()` – For attributes
* `esc_url()` – For URLs
* `esc_js()` – For JS output
* `wp_kses()` – For safe HTML filtering

#### Sanitizing Input

* `sanitize_text_field()` – For text inputs
* `sanitize_email()` – For emails
* `sanitize_key()` – For keys/slugs
* `intval()` or `absint()` – For numbers

#### Nonces

* Use `wp_nonce_field()` in forms
* Validate using `check_admin_referer()` or `wp_verify_nonce()`

#### Database Access

* Use `$wpdb->prepare()`
* Avoid raw SQL queries unless absolutely necessary

---

### 🌐 Internationalization

#### Load Text Domain

```php
function mytheme_load_textdomain() {
    load_theme_textdomain( 'mytheme', get_template_directory() . '/languages' );
}
add_action( 'after_setup_theme', 'mytheme_load_textdomain' );
```

* All strings must be wrapped with `__()`, `_e()`, `_n()`, `_x()` functions
* Translation files in `/languages/`

---

### 📦 Enqueue Scripts & Styles

```php
function mytheme_enqueue_assets() {
    wp_enqueue_style( 'mytheme-style', get_stylesheet_uri(), [], '1.0' );
    wp_enqueue_script( 'mytheme-main', get_template_directory_uri() . '/assets/js/main.js', [ 'jquery' ], '1.0', true );
}
add_action( 'wp_enqueue_scripts', 'mytheme_enqueue_assets' );
```

* Use versioning to avoid cache issues
* Load non-critical scripts in footer

---

### ⚙️ Performance

* Combine and minify CSS/JS assets
* Lazy load images
* Use `async`/`defer` for scripts when needed
* Optimize images and reduce HTTP requests
* Use `wp_localize_script()` for AJAX localization

---

### 🛒 WooCommerce Support

* Declare support with `add_theme_support( 'woocommerce' );`
* Override Woo templates in `woocommerce/` folder
* Follow WooCommerce coding standards

---

### 🔍 ThemeForest Submission Checklist

* ✅ Pass Theme Check plugin (no warnings/errors)
* ✅ Theme includes:

  * `style.css` with proper headers
  * `functions.php`
  * Working `screenshot.png`
  * `readme.txt`
  * `languages/` folder with `.pot`
  * Sample demo content
  * Child theme support
* ✅ No admin notices, nags, or external calls
* ✅ No hard-coded URLs or credentials

---

### 📘 Documentation

* Include `readme.txt`
* Instructions for:

  * Installing the theme
  * Importing demo
  * Using theme options (Redux, etc.)
  * Translating the theme

---

### 🧪 QA & Testing

* Test on:

  * WordPress Latest
  * PHP 7.4 to 8.4+
  * WooCommerce latest
  * Elementor, Gutenberg, Classic Editor
* Browser Compatibility: Chrome, Firefox, Safari, Edge
* Mobile Responsiveness

  
