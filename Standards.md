## WordPress Theme Development Standards (Compliance Checklist)

This file outlines the core **standards and principles** you must adhere to when developing a premium WordPress theme. These are aligned with the **WordPress Coding Standards**, **ThemeForest submission guidelines**, and **PHP 8.4+ compatibility**.

---

### 🧱 Code Structure Standards

* Every file begins with:

```php
if ( ! defined( 'ABSPATH' ) ) {
    exit; // Exit if accessed directly
}
```

* Use **OOP where possible**; keep procedural functions in `functions.php` only
* Separate logic from templates (`inc/`, `template-parts/`)
* Follow **WordPress file naming conventions** (lowercase, dash-separated)

---

### 🔒 Security Standards

* **Escape all output**:

  * `esc_html()`, `esc_attr()`, `esc_url()`, `esc_js()`
* **Sanitize all input**:

  * `sanitize_text_field()`, `sanitize_email()`, `absint()`, `intval()`
* **Use nonces** for all forms and AJAX:

```php
wp_nonce_field( 'action_name', 'nonce_name' );
```

* Validate with `check_admin_referer()` or `wp_verify_nonce()`

---

### 🏷️ Naming Standards

* Prefix everything with your theme slug (e.g., `mytheme_`, `MyTheme_`)
* Do not use global functions or class names without prefixing
* Example:

```php
function mytheme_register_post_type() {}
class MyTheme_Breadcrumb {}
```

---

### 🎨 Styling Standards

* Enqueue styles via `wp_enqueue_style()`
* Do **not** hardcode `<style>` tags in templates
* Use `style.css` for global styling and `assets/css/` for modules
* Use proper versioning and dependencies

---

### ⚙️ Script Standards

* Enqueue JS files in footer using:

```php
wp_enqueue_script( 'mytheme-main', get_template_directory_uri() . '/assets/js/main.js', [ 'jquery' ], '1.0', true );
```

* Avoid inline scripts unless localized with `wp_localize_script()`
* Minimize and defer heavy scripts where applicable

---

### 🌐 Internationalization Standards

* All strings must use translation functions: `__()`, `_e()`, `_x()`, `_n()`
* Load text domain in `after_setup_theme`
* Store `.pot`, `.po`, `.mo` files in `/languages/`

---

### 🛍️ WooCommerce & Plugin Compatibility

* Declare `add_theme_support( 'woocommerce' )`
* Use `woocommerce/` override folder for template changes
* Do not break default plugin styling (use `.theme-` prefixed overrides)

---

### 🧪 Testing & Validation Standards

* Run with **DEBUG mode enabled**
* Pass **Theme Check Plugin** with zero errors
* Test with **Theme Unit Test Data**
* Check responsiveness on all breakpoints
* Check accessibility (ARIA, contrast, keyboard nav)

---

### 📄 File Naming & Location

* Template parts: `template-parts/content-single.php`
* Custom files: `inc/class-mytheme-header.php`
* Assets:

  * `assets/js/`, `assets/css/`, `assets/fonts/`
* Language: `languages/mytheme.pot`

---

These standards ensure compatibility, maintainability, and pass review on professional platforms like ThemeForest, WordPress.org, and premium marketplaces.

End of Standards
