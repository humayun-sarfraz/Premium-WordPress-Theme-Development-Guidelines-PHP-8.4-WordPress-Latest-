## WordPress Theme Review & Pre-Launch Checklist

This file provides a final checklist to follow before submitting your theme to ThemeForest, selling on marketplaces, or launching publicly.

---

### ✅ General Review

* [ ] WordPress Core Compatibility (latest version)
* [ ] PHP Compatibility (7.4 – 8.4+)
* [ ] Gutenberg Compatibility
* [ ] Elementor Compatibility (widgets, templates)
* [ ] WooCommerce Compatibility (shop, single, cart, checkout)
* [ ] RTL Support
* [ ] Translation Ready with `.pot` file

---

### 🧪 Functionality Testing

* [ ] All theme options working (Customizer/Redux)
* [ ] All menus register/display correctly
* [ ] Sidebars and widgets render as expected
* [ ] Header/Footer builder (if applicable) works properly
* [ ] Breadcrumbs, search, pagination, 404 pages function
* [ ] Blog, archive, single pages load correctly
* [ ] WooCommerce loop, filters, sorting, product pages

---

### 🔒 Security Checklist

* [ ] All inputs sanitized before save
* [ ] All outputs escaped with appropriate `esc_*()`
* [ ] All forms have nonces and nonce verification
* [ ] No debug code or hardcoded credentials
* [ ] No base64, eval, or PHP `exec()` functions
* [ ] Custom user input areas tested for XSS & SQLi

---

### 🎨 UI/UX Design Review

* [ ] Theme is mobile responsive (desktop, tablet, mobile)
* [ ] Minimum WCAG AA color contrast
* [ ] Font sizes, spacing, and button click areas are accessible
* [ ] Smooth scroll, animations, transitions reviewed
* [ ] Sticky header, modals, dropdowns work across devices

---

### 🌐 Internationalization

* [ ] All static text wrapped with `__()`, `_e()`, etc.
* [ ] `.pot` file included and tested in Poedit/Loco Translate
* [ ] WPML/Polylang tested if multilingual support advertised

---

### ⚙️ Code Quality

* [ ] All functions/classes are prefixed
* [ ] `function_exists()` and `class_exists()` used where needed
* [ ] Theme passes **Theme Check** with no critical issues
* [ ] No PHP errors/warnings on front-end or back-end
* [ ] Clean browser console (no JS errors or warnings)

---

### 📁 Packaging

* [ ] Includes `style.css`, `functions.php`, `screenshot.png`
* [ ] Includes `readme.txt` with setup instructions
* [ ] Includes sample XML demo import + widget data (if applicable)
* [ ] Includes ready-to-use child theme ZIP
* [ ] Includes licensing for bundled assets/plugins
* [ ] Folder zipped and named correctly (e.g., `mytheme.zip`)

---

### 🧰 Bonus (Optional but Recommended)

* [ ] One-click demo importer tested
* [ ] Basic onboarding wizard or welcome page
* [ ] Sample Elementor templates included
* [ ] Performance tested (Lighthouse, GTmetrix, etc.)
* [ ] Accessibility scanned using WAVE or axe

---

This checklist ensures your theme is production-ready, user-friendly, and passes both technical and visual inspections during review.

End of Checklist
