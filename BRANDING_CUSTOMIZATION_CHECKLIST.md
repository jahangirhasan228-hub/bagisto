# Bagisto Bangladesh eCommerce Platform - Branding Customization Checklist

**Project:** Bangladesh-focused eCommerce Platform (Bagisto Fork)
**Status:** Ready for Implementation (Awaiting Approval)
**Date:** 2026-07-08

---

## SECTION 1: LOGO & FAVICON FILES
These files need to be replaced with your Bangladesh platform branding.

### Admin Panel Logos
- [ ] `/vercel/share/v0-project/packages/Webkul/Admin/src/Resources/assets/images/logo.svg` - Admin light logo
- [ ] `/vercel/share/v0-project/packages/Webkul/Admin/src/Resources/assets/images/dark-logo.svg` - Admin dark logo
- [ ] `/vercel/share/v0-project/packages/Webkul/Admin/src/Resources/assets/images/favicon.ico` - Admin favicon

### Shop/Storefront Logos
- [ ] `/vercel/share/v0-project/packages/Webkul/Shop/src/Resources/assets/images/logo.svg` - Shop logo
- [ ] `/vercel/share/v0-project/packages/Webkul/Shop/src/Resources/assets/images/favicon.ico` - Shop favicon

### Installer Logos
- [ ] `/vercel/share/v0-project/packages/Webkul/Installer/src/Resources/assets/images/installer/bagisto-logo.svg` - Installation page logo
- [ ] `/vercel/share/v0-project/packages/Webkul/Installer/src/Resources/assets/images/installer/favicon.ico` - Installation favicon

### Root Public Assets
- [ ] `/vercel/share/v0-project/public/favicon.ico` - Root favicon (used throughout app)

**Impact:** Pure visual changes. No functional impact. Logos are displayed in:
- Admin dashboard header
- Shop homepage and header
- Installation wizard
- Browser tabs and bookmarks

---

## SECTION 2: LOCALE & LANGUAGE CONFIGURATION
Set Bengali as default language and configure language files.

### File: `/vercel/share/v0-project/packages/Webkul/Installer/src/Database/Seeders/Core/LocalesTableSeeder.php`
**Current Behavior:**
- Seeds default locale based on `$parameters['default_locale']` or `config('app.locale')`
- Supported locales: `en`, `ar`, `bn`, `ca`, `de`, `es`, `fa`, `fr`, `he`, `hi_IN`, `id`, `it`, `ja`, `nl`, `pl`, `pt_BR`, `ro`, `ru`, `sin`, `tr`
- Bengali (`bn`) is already fully supported

**Changes Needed:**
- [ ] Ensure default locale is set to `bn` (Bengali)
- [ ] Ensure `allowed_locales` includes `bn` 
- [ ] Verify locale direction is set to `ltr` (Bengali uses left-to-right)
- [ ] Bengali flag logo will be loaded from: `/vercel/share/v0-project/packages/Webkul/Installer/src/Resources/assets/images/seeders/locales/bn.png`

**Impact:** Language configuration. **NO CORE FUNCTIONALITY BROKEN** - existing multi-language system intact.

---

## SECTION 3: CURRENCY CONFIGURATION
Set Bangladeshi Taka (BDT) as primary currency.

### File: `/vercel/share/v0-project/packages/Webkul/Installer/src/Database/Seeders/Core/CurrencyTableSeeder.php`
**Current Behavior:**
- Seeds available currencies from seeder
- Default currency for channels is based on `base_currency_id`

**Changes Needed:**
- [ ] Verify BDT (Bangladeshi Taka) is in the supported currencies list
- [ ] Set BDT as the primary/base currency in channel configuration
- [ ] Symbol for BDT: `৳` or `TK` (configurable)

**Impact:** Currency display and pricing. **NO CORE FUNCTIONALITY BROKEN** - existing multi-currency system intact.

---

## SECTION 4: CHANNEL CONFIGURATION
Set up the primary sales channel with Bangladesh defaults.

### File: `/vercel/share/v0-project/packages/Webkul/Installer/src/Database/Seeders/Core/ChannelTableSeeder.php`
**Current Behavior:**
- Creates single `default` channel
- Channel name/description are translatable from language files
- Channel SEO metadata pulled from translations

**Fields That Can Be Customized:**
- [ ] Channel code: `default` (can change but not recommended)
- [ ] Channel name (via language file): Change to your Bangladesh platform name
- [ ] Hostname: `config('app.url')` - Set via `.env` file
- [ ] Root category: Default is category ID 1
- [ ] Default locale: Set to `bn` (Bengali)
- [ ] Base currency: Set to BDT
- [ ] Channel translations (SEO metadata) - **MUST EDIT LANGUAGE FILES**

**Impact:** Core channel configuration. **SAFE TO CHANGE** - doesn't affect Bagisto core features.

---

## SECTION 5: TRANSLATOR/LANGUAGE FILES - BRANDING STRINGS
Files containing translatable strings for Bagisto branding.

### Admin Language Files
- [ ] `/vercel/share/v0-project/packages/Webkul/Admin/src/Resources/lang/en/app.php` - Admin English translations
- [ ] `/vercel/share/v0-project/packages/Webkul/Admin/src/Resources/lang/bn/app.php` - Admin Bengali translations

### Shop Language Files
- [ ] `/vercel/share/v0-project/packages/Webkul/Shop/src/Resources/lang/en/app.php` - Shop English translations
- [ ] `/vercel/share/v0-project/packages/Webkul/Shop/src/Resources/lang/bn/app.php` - Shop Bengali translations

### Core Language Files
- [ ] `/vercel/share/v0-project/packages/Webkul/Core/src/Resources/lang/en/app.php` - Core English
- [ ] `/vercel/share/v0-project/packages/Webkul/Core/src/Resources/lang/bn/app.php` - Core Bengali

### Installer Language Files
- [ ] `/vercel/share/v0-project/packages/Webkul/Installer/src/Resources/lang/en/app.php` - Installer English
- [ ] `/vercel/share/v0-project/packages/Webkul/Installer/src/Resources/lang/bn/app.php` - Installer Bengali

**Strings to Search & Update:**
- Search for "Bagisto" → Replace with your platform name
- Search for generic company/contact information → Replace with Bangladesh platform details
- Update all greeting, footer, and policy text to match your brand voice

**Impact:** User-visible text. **SAFE TO CHANGE** - doesn't affect functionality, only translations.

---

## SECTION 6: EMAIL TEMPLATES & FOOTER BRANDING
Email templates that display company branding and copyright.

### Admin Email Template
- [ ] `/vercel/share/v0-project/packages/Webkul/Admin/src/Resources/views/emails/layout.blade.php`
  - **Uses:** Admin logo from config `general.design.admin_logo.logo_image`
  - **Contains:** "Thanks" message with contact email
  - **Can Update:** Email styling, copyright text, footer links

### Shop Email Template
- [ ] `/vercel/share/v0-project/packages/Webkul/Shop/src/Resources/views/emails/layout.blade.php`
  - **Uses:** Shop channel logo from `core()->getCurrentChannel()->logo_url`
  - **Contains:** "Thanks" message with contact email
  - **Can Update:** Email styling, copyright text, footer links

**Impact:** Emails sent to customers and admins. **SAFE TO CHANGE** - only affects email appearance and messages.

---

## SECTION 7: CMS PAGES (PLACEHOLDER CONTENT TO REMOVE OR CUSTOMIZE)
Demo/placeholder pages that should be customized for Bangladesh market.

### File: `/vercel/share/v0-project/packages/Webkul/Installer/src/Database/Seeders/CMS/CMSPagesTableSeeder.php`
**Current Demo Pages (10 total):**
1. [ ] `about-us` - About Us page (customize with your Bangladesh company info)
2. [ ] `return-policy` - Return Policy (update with your policies)
3. [ ] `refund-policy` - Refund Policy (update with your policies)
4. [ ] `terms-conditions` - Terms & Conditions (required for Bangladesh market - update)
5. [ ] `terms-of-use` - Terms of Use (update)
6. [ ] `customer-service` - Customer Service page (add Bangladesh support details)
7. [ ] `whats-new` - What's New (can delete or update)
8. [ ] `payment-policy` - Payment Policy (update with BDT payment methods)
9. [ ] `shipping-policy` - Shipping Policy (update for Bangladesh shipping)
10. [ ] `privacy-policy` - Privacy Policy (REQUIRED - update with Bangladesh data protection compliance)

**Action Options:**
- **Option A (RECOMMENDED):** Keep structure, update content in Admin UI after installation
- **Option B:** Modify seeder to include Bangladesh-specific content before database seed
- **Option C:** Delete seeder entries and create CMS pages manually in Admin

**Impact:** Database content seeding. **SAFE TO CHANGE** - these are just content pages, no core logic affected.

---

## SECTION 8: DEMO PRODUCTS & CATEGORIES
Demo product data that should be removed or replaced for Bangladesh platform.

### File: `/vercel/share/v0-project/packages/Webkul/Installer/src/Database/Seeders/ProductTableSeeder.php`
**Current Behavior:**
- Loads demo products from JSON file: `/vercel/share/v0-project/packages/Webkul/Installer/src/Data/demo-products.json`
- Imports product images to storage
- Creates product variants with attributes (size, color, brand, etc.)

### File: `/vercel/share/v0-project/packages/Webkul/Installer/src/Database/Seeders/Category/CategoryTableSeeder.php`
**Current Behavior:**
- Seeds demo product categories
- Creates category hierarchy

**Action Options:**
- [ ] **Option A (RECOMMENDED):** Keep seeders but modify to skip demo products (empty/minimal data)
- [ ] **Option B:** Delete product seeder entirely (users add products manually in Admin)
- [ ] **Option C:** Replace demo products with Bangladesh-relevant products

**Impact:** Removes sample data. **SAFE TO CHANGE** - doesn't affect eCommerce core features.

---

## SECTION 9: THEME CUSTOMIZATION & STORE FRONT SETTINGS
Demo theme settings and homepage customizations.

### File: `/vercel/share/v0-project/packages/Webkul/Installer/src/Database/Seeders/Shop/ThemeCustomizationTableSeeder.php`
**Current Demo Elements (11 total):**
- Image carousel (homepage banner)
- Offer information (static content)
- Top collections (category display)
- Bold collections (category display)
- Game container (static content)
- Service content (static content)
- Footer links
- Category carousel
- Product carousel

**Changes Needed:**
- [ ] Remove/disable demo carousel images
- [ ] Update offer information with Bangladesh-specific messages
- [ ] Update service content descriptions
- [ ] Customize footer links for Bangladesh platform
- [ ] Add Bangladesh-specific category recommendations

**Impact:** Frontend appearance. **SAFE TO CHANGE** - these are visual elements only, core features intact.

---

## SECTION 10: COUNTRY & STATE CONFIGURATION
Configure Bangladesh as primary market with all states/districts.

### File: `/vercel/share/v0-project/packages/Webkul/Installer/src/Database/Seeders/Core/CountriesTableSeeder.php`
**Current Behavior:**
- Seeds all countries and their states
- Bangladesh is fully included with all 64 districts

**Changes Needed:**
- [ ] Verify Bangladesh (BD) country is seeded
- [ ] Verify all 64 Bangladesh districts/states are present:
  - Dhaka, Chittagong, Khulna, Rajshahi, Sylhet, Barisal, Rangpur, Mymensingh (8 divisions)
  - Plus all districts within each division
- [ ] Set Bangladesh as default country (optional, can be done in Admin)

**Impact:** Shipping and address configuration. **NO CORE FUNCTIONALITY BROKEN** - existing location system intact.

---

## SECTION 11: ADMIN SETTINGS & CONFIGURATION SEEDER
Core application settings that affect branding.

### File: `/vercel/share/v0-project/packages/Webkul/Installer/src/Database/Seeders/Core/ConfigTableSeeder.php`
**Current Settings That Can Be Modified:**
- [ ] General settings (app name, timezone, etc.) - via `.env`
- [ ] Admin email settings - via `.env`
- [ ] Store contact information - via Admin UI or config
- [ ] Tax configuration - via Admin UI
- [ ] Payment methods - via Admin UI
- [ ] Shipping methods - via Admin UI
- [ ] Email templates - can customize in Admin UI

**Note:** Most settings are configurable through Admin UI, no seeder changes needed unless you want to pre-populate specific values.

**Impact:** Application configuration. **SAFE TO CHANGE** - configuration-only, no core logic modified.

---

## SECTION 12: CORE FUNCTIONALITY TO PRESERVE
**These should NEVER be modified or broken:**

### Absolute No-Touch Areas
- ❌ Don't modify: `/vercel/share/v0-project/packages/Webkul/Core/src/` - Core Bagisto system
- ❌ Don't modify: `/vercel/share/v0-project/packages/Webkul/Shop/src/Http/` - Shop controller logic
- ❌ Don't modify: `/vercel/share/v0-project/packages/Webkul/Admin/src/Http/` - Admin controller logic
- ❌ Don't modify: Database migrations (except through new migrations for new features)
- ❌ Don't modify: Core models and relationships
- ❌ Don't modify: API endpoints and responses
- ❌ Don't modify: Authentication and authorization logic

### Safe Modification Areas
- ✅ DO modify: Language/translation files (`/lang/`)
- ✅ DO modify: Views and templates (`/views/`)
- ✅ DO modify: Assets (logos, images, stylesheets)
- ✅ DO modify: Seeder data (demo content)
- ✅ DO modify: Configuration values (via `.env` or Admin UI)

---

## PHASE-BY-PHASE IMPLEMENTATION PLAN

### Phase 1: Logo & Visual Branding (LOWEST RISK)
**Timeline:** ~15 minutes
**Files:** 8 image files
- Replace all logo and favicon files with Bangladesh platform branding
- **Risk Level:** ZERO - Pure visual replacement, no code changes
- **Testing:** Visual verification only

### Phase 2: Locale & Language Configuration (LOW RISK)
**Timeline:** ~20 minutes
**Files:** Seeder + language files
- Set Bengali (`bn`) as default language
- Update language files with Bangladesh platform name
- **Risk Level:** LOW - Configuration only, no logic changes
- **Testing:** Verify language displays correctly

### Phase 3: Currency & Store Configuration (LOW RISK)
**Timeline:** ~15 minutes
**Files:** Currency seeder + channel seeder
- Set BDT (Bangladeshi Taka) as primary currency
- Configure channel name and contact details
- **Risk Level:** LOW - Configuration only
- **Testing:** Verify currency displays as BDT

### Phase 4: CMS Pages & Content (LOW RISK)
**Timeline:** ~30 minutes
**Files:** CMS seeder + language files
- Update CMS page content for Bangladesh market
- Add Bangladesh-specific policies (Privacy, Terms, etc.)
- **Risk Level:** LOW - Content only, no logic changes
- **Testing:** Verify pages display correctly

### Phase 5: Remove Demo Products & Categories (LOW RISK)
**Timeline:** ~20 minutes
**Files:** Product seeder + category seeder
- Disable demo product seeding (or replace with Bangladesh products)
- Clean up demo categories
- **Risk Level:** LOW - Just removing demo data
- **Testing:** Verify no demo products appear

### Phase 6: Theme Customization & Homepage (MEDIUM RISK)
**Timeline:** ~30 minutes
**Files:** Theme customization seeder + language files
- Customize homepage banners and content
- Update service descriptions
- Configure footer links
- **Risk Level:** MEDIUM - Affects frontend UX
- **Testing:** Visual verification of homepage

### Phase 7: Email Templates & Communication (LOW RISK)
**Timeline:** ~15 minutes
**Files:** Email templates
- Update email logos and copyright information
- Customize email footer with Bangladesh contact details
- **Risk Level:** LOW - Template customization only
- **Testing:** Send test emails, verify appearance

### Phase 8: Admin Settings & Final Configuration (LOW RISK)
**Timeline:** ~20 minutes
**Files:** Config seeder + Admin UI
- Set store timezone (Asia/Dhaka)
- Configure contact information
- Set up default country as Bangladesh
- **Risk Level:** LOW - Configuration only
- **Testing:** Verify settings display in Admin

---

## REQUIRED INFORMATION FROM YOU

Before proceeding with Phase-by-Phase Implementation, please provide:

1. **Platform Branding**
   - [ ] Platform/Store name (to replace "Bagisto")
   - [ ] Logo file (SVG or PNG recommended)
   - [ ] Favicon file (ICO format)
   - [ ] Primary brand color
   - [ ] Secondary brand color

2. **Store Details**
   - [ ] Store display name
   - [ ] Store email address
   - [ ] Store phone number (Bangladesh format)
   - [ ] Store address in Bangladesh
   - [ ] Store website URL
   - [ ] Company registration number (if applicable)

3. **Default Configuration**
   - [ ] Default timezone: (Recommended: `Asia/Dhaka`)
   - [ ] Default currency: (Confirmed: `BDT`)
   - [ ] Default language: (Confirmed: `bn` - Bengali)
   - [ ] Default country: (Confirmed: `BD` - Bangladesh)

4. **Policies & Legal**
   - [ ] About Us content (for About Us CMS page)
   - [ ] Return Policy content
   - [ ] Refund Policy content
   - [ ] Terms & Conditions content
   - [ ] Privacy Policy content (REQUIRED for Bangladesh compliance)
   - [ ] Payment Policy content
   - [ ] Shipping Policy content
   - [ ] Customer Service information

5. **Payment & Shipping**
   - [ ] Preferred payment gateways (PhonePe, Razorpay, PayPal, Stripe, etc.)
   - [ ] Shipping methods to enable
   - [ ] Shipping cost configuration (by region/district)

6. **Products & Categories** (if you want to seed data)
   - [ ] Initial product categories (or keep empty and add manually)
   - [ ] Sample products (or keep empty and add manually)
   - [ ] Product attributes to support (size, color, brand, etc.)

---

## IMPLEMENTATION CHECKLIST TEMPLATE

Once you approve, we'll use this checklist during implementation:

### Pre-Implementation
- [ ] Backup current database
- [ ] Backup current codebase
- [ ] Create feature branch in Git

### Phase Implementation
- [ ] Complete Phase 1: Logos
- [ ] Test Phase 1: Visual verification
- [ ] Complete Phase 2: Locale & Language
- [ ] Test Phase 2: Language display
- [ ] Complete Phase 3: Currency & Store
- [ ] Test Phase 3: Currency display
- [ ] Complete Phase 4: CMS Pages
- [ ] Test Phase 4: CMS page display
- [ ] Complete Phase 5: Demo Products
- [ ] Test Phase 5: No demo products visible
- [ ] Complete Phase 6: Theme Customization
- [ ] Test Phase 6: Homepage appearance
- [ ] Complete Phase 7: Email Templates
- [ ] Test Phase 7: Email appearance
- [ ] Complete Phase 8: Admin Settings
- [ ] Test Phase 8: Settings configured correctly

### Post-Implementation
- [ ] Verify all core features still work (checkout, cart, auth, etc.)
- [ ] Verify no console errors in browser
- [ ] Verify no PHP errors in logs
- [ ] Run Bagisto system checks
- [ ] Commit changes to Git
- [ ] Push to repository

---

## SUMMARY

**Total Branding Files to Modify:** 50+  
**Core Bagisto Features at Risk:** ZERO (if following this plan)  
**Estimated Total Implementation Time:** 2-3 hours  
**Complexity Level:** LOW TO MEDIUM  

**Status:** ⏳ AWAITING YOUR APPROVAL & INPUT

---

**Next Step:** Please provide the information requested in **"REQUIRED INFORMATION FROM YOU"** section above, and I will proceed with phase-by-phase implementation while ensuring all Bagisto core functionality remains intact and operational.
