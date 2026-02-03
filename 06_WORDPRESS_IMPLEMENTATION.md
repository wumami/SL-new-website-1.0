# WordPress Implementation Guide

## 🎯 Technical Stack

**Platform**: WordPress 6.4+  
**Page Builder**: Elementor Pro (required for Assessment wizard)  
**Form Plugin**: WPForms Pro (for lead capture with hidden fields)  
**Custom Fields**: Advanced Custom Fields (ACF) Pro  
**Performance**: WP Rocket + CDN (Cloudflare)  
**Analytics**: Google Analytics 4 + Google Tag Manager

---

## 📦 Required Plugins

### Essential Plugins:

1. **Elementor Pro** (v3.18+)
   - Purpose: Visual page building, Assessment wizard
   - Features needed: Form widget, custom CSS, popup builder
   - License: Required ($59/year for 1 site)

2. **WPForms Pro** (v1.8+)
   - Purpose: Lead forms with hidden fields, conditional logic
   - Features needed: Hidden fields, webhooks (for CRM), email notifications
   - License: Required ($199/year for Basic)

3. **Advanced Custom Fields (ACF) Pro** (v6.2+)
   - Purpose: Case study templates, product metadata
   - Features needed: Flexible content, repeater fields, relationship fields
   - License: Required ($49/year for 1 site)

4. **Yoast SEO** (Free or Premium)
   - Purpose: SEO optimization, sitemap generation
   - Features: Title/meta templates, schema markup

5. **WP Rocket** (v3.15+)
   - Purpose: Page caching, performance optimization
   - Features: Page caching, minification, lazy loading
   - License: Required ($49/year for 1 site)

6. **Safe SVG** (Free)
   - Purpose: Allow SVG uploads for icons

---

### Optional but Recommended:

7. **Code Snippets** (Free)
   - Purpose: Add custom PHP code without editing functions.php
   
8. **WP Mail SMTP** (Free)
   - Purpose: Reliable email delivery for form submissions

9. **Redirection** (Free)
   - Purpose: Manage 301 redirects from old site

10. **Duplicate Page** (Free)
    - Purpose: Clone templates quickly

---

## 🗂️ Custom Post Types

### 1. Case Studies

**Post Type**: `case_study`  
**Slug**: `/case-studies/[slug]`

**ACF Fields**:
```php
Segment: Select (dropdown)
  - Multi-Asset Broker
  - Crypto Exchange
  - Prop Trading Firm
  - Asset Manager
  - Introducing Broker

Related Products: Relationship (multi-select)
  - Links to Products post type

Challenge: Textarea (rich text)
Situation: Textarea (rich text)
Solution: Textarea (rich text)
Results: Repeater
  - Metric Label (text): "Execution complaints reduced"
  - Metric Value (text): "70%"
  - Metric Icon (image upload)

Client Name: Text (optional, can be anonymized)
Client Logo: Image Upload (optional)
Implementation Timeline: Text (e.g., "4 weeks")
Featured: Checkbox (show on homepage)
```

**Template**: `single-case_study.php`

---

### 2. Products

**Post Type**: `product`  
**Slug**: `/products/[slug]`

**ACF Fields**:
```php
Product Category: Select
  - Platforms
  - Infrastructure
  - AI & Risk

Product Badge: Text (e.g., "NEW BETA", "POPULAR")
Badge Color: Color Picker

One-Line Value Prop: Text (100 chars)
Short Description: Textarea (250 chars)

Key Features: Repeater
  - Feature Icon (image upload or icon class)
  - Feature Title (text)
  - Feature Description (textarea)

Who This Is For: Repeater
  - Persona (text)
  - Use Case (textarea)

Integration Diagram: Image Upload
Supported Platforms: Checkbox
  - MT4/MT5
  - Spencer Core
  - Third-party APIs

Technical Specs: Flexible Content
  - Section Title (text)
  - Section Content (WYSIWYG)

Related Solutions: Relationship (multi-select)
  - Links to Solutions post type

Case Study Featured: Relationship (single)
  - Links to Case Studies post type

CTA Text: Text (default: "Request Demo")
CTA URL: URL (can link to form or external)
Beta Form: Checkbox (show beta application form instead)
```

**Template**: `single-product.php`

---

### 3. Solutions

**Post Type**: `solution`  
**Slug**: `/solutions/[slug]`

**ACF Fields**:
```php
Problem Statement: Text (headline)
Who This Is For: Repeater
  - Persona Badge (text)

Symptoms: Repeater
  - Symptom Text (text)

Business Impact: Repeater
  - Impact Icon (image)
  - Impact Metric (text, e.g., "+25-40%")
  - Impact Description (text)

How It Works Steps: Repeater
  - Step Icon (image)
  - Step Title (text)
  - Step Description (textarea)
  - Technology Used (text, links to product)

Products Used: Repeater
  - Product (relationship to Products post type)
  - Role in Solution (text, e.g., "PRIMARY", "SUPPORTING")
  - Role Description (textarea)

Featured Case Study: Relationship (single)
  - Links to Case Studies post type

FAQ: Repeater
  - Question (text)
  - Answer (textarea)

CTA Text: Text
CTA URL: URL
```

**Template**: `single-solution.php`

---

## 📄 Custom Page Templates

### Template 1: Homepage
**File**: `page-templates/template-homepage.php`

**Built With**: Elementor

**Sections** (each is an Elementor section):
1. Hero (built in Elementor)
2. Trust Bar (HTML widget)
3. Solution Path Cards (Icon Box widget × 6)
4. Stack Diagram (Image or custom HTML)
5. Featured Products (Loop Grid pulling from Products CPT)
6. Case Studies Preview (Loop Grid pulling from Case Studies CPT where Featured = true)
7. Final CTA (built in Elementor)

**No ACF fields needed** (all content built in Elementor)

---

### Template 2: Assessment Wizard
**File**: `page-templates/template-assessment.php`

**Built With**: Elementor + Custom JavaScript

**Structure**:
```html
<!-- Section: Intro Screen -->
<div id="assessment-intro" class="assessment-screen active">
  [Elementor content]
  <button onclick="startAssessment()">Start Assessment</button>
</div>

<!-- Section: Question 1 -->
<div id="assessment-q1" class="assessment-screen">
  <div class="progress-bar">
    <div class="progress" style="width: 20%"></div>
  </div>
  <p class="question-label">QUESTION 1 OF 3</p>
  <h2>What best describes you?</h2>
  <div class="chips-container">
    <div class="chip" data-value="multi-asset-broker">
      <span class="icon">📊</span>
      <span class="label">Multi-Asset Broker</span>
      <span class="subtext">FX, CFDs, stocks, crypto</span>
    </div>
    <!-- More chips -->
  </div>
</div>

<!-- Section: Question 2 (dynamic based on Q1) -->
<div id="assessment-q2" class="assessment-screen">
  [Similar structure]
</div>

<!-- Section: Question 3 (dynamic based on Q1+Q2) -->
<div id="assessment-q3" class="assessment-screen">
  [Similar structure]
</div>

<!-- Section: Results -->
<div id="assessment-results" class="assessment-screen">
  <h2>Based on your answers, we recommend:</h2>
  <div id="recommended-products-container">
    <!-- Populated via JavaScript -->
  </div>
  
  <!-- Lead Capture Form -->
  [WPForms shortcode with hidden fields]
</div>
```

**JavaScript File**: `/js/assessment-wizard.js`
- Handles screen transitions
- Stores answers in sessionStorage
- Dynamically shows Q2/Q3 options based on previous answers
- Populates results screen with product recommendations
- Pre-fills hidden form fields

**PHP Function** (in functions.php):
```php
function get_product_recommendations($persona, $goal, $bottleneck) {
  // Logic to return array of product IDs
  // Based on mapping table from Assessment design doc
  return [123, 456, 789]; // Product post IDs
}
```

**WPForms Setup**:
- Form ID: assessment-results-form
- Visible fields: First Name, Email, Company, Phone (optional)
- Hidden fields: persona, goal, bottleneck, recommended_products, utm_source, utm_campaign
- Submit button text: "Email me this plan"
- Redirect after submit: `/assessment/thank-you`

---

### Template 3: Solution Page
**File**: `page-templates/template-solution.php`

**Built With**: Elementor + ACF fields

**ACF Field Group**: "Solution Page Fields" (attached to Solutions post type)

**Elementor Sections** (pulling from ACF):
1. Hero
   - Headline: `[acf field="problem_statement"]`
   - Who This Is For: Loop `[acf field="who_this_is_for"]`

2. Symptoms
   - Loop `[acf field="symptoms"]`

3. Business Impact
   - Loop `[acf field="business_impact"]`

4. How It Works
   - Loop `[acf field="how_it_works_steps"]`

5. Products Used
   - Loop `[acf field="products_used"]`
   - Each product links to single-product.php

6. Case Study
   - Pull from `[acf field="featured_case_study"]` (relationship field)

7. FAQ
   - Accordion widget, loop `[acf field="faq"]`

8. Final CTA
   - Button: `[acf field="cta_text"]` → `[acf field="cta_url"]`

---

### Template 4: Product Page
**File**: `page-templates/template-product.php`

**Built With**: Elementor + ACF fields

**Similar structure to Solution page, pulling from Product CPT ACF fields**

---

### Template 5: Case Study Page
**File**: `single-case_study.php`

**Built With**: Elementor + ACF fields

**Sections**:
1. Hero
   - Segment badge
   - Client name/logo (if available)

2. Challenge
   - `[acf field="challenge"]`

3. Solution
   - `[acf field="solution"]`
   - Show related products (relationship field)

4. Results
   - Loop `[acf field="results"]` (repeater with metrics)
   - Display as stat cards

5. Related Case Studies
   - Query case studies with same segment or related products

---

## 🧩 Reusable Elementor Templates

### 1. Product Card Component
**Type**: Elementor Template (Saved as "Product Card")

**Structure**:
```
┌─────────────────────────┐
│ [Badge: Dynamic]        │
│ [Image: Featured]       │
│ [Title: Post Title]     │
│ [Description: ACF]      │
│ • Feature 1             │
│ • Feature 2             │
│ • Feature 3             │
│ [Learn more →]          │
└─────────────────────────┘
```

**Usage**: Insert via Elementor Template widget, filter by Product CPT

---

### 2. Case Study Card Component
**Type**: Elementor Template

**Structure**:
```
┌─────────────────────────┐
│ [Segment Badge]         │
│ [Headline: Post Title]  │
│ [Subtext: Excerpt]      │
│ [Read story →]          │
└─────────────────────────┘
```

---

### 3. Solution Path Card Component
**Type**: Elementor Template

**Structure**:
```
┌─────────────────────────┐
│ [Icon]                  │
│ [Title]                 │
│ [Description]           │
│ [Explore solution →]    │
└─────────────────────────┘
```

---

### 4. Lead Form Inline Component
**Type**: WPForms template

**Fields**:
- First Name (text, required)
- Work Email (email, required, validate domain)
- Company (text, required)
- Phone/WhatsApp (text, optional)
- Hidden fields: source, utm_source, utm_campaign
- Checkboxes: Call me, Subscribe to updates
- Submit button: Customizable text

**Usage**: Insert via `[wpforms id="123"]` shortcode

---

## 🎨 Custom CSS (Additional Styles)

**File**: `style.css` or Elementor Custom CSS

```css
/* Assessment Wizard Specific */
.assessment-screen {
  display: none;
  opacity: 0;
  transition: opacity 0.4s ease;
}

.assessment-screen.active {
  display: block;
  opacity: 1;
}

.progress-bar {
  width: 100%;
  height: 4px;
  background: #E2E8F0;
  border-radius: 2px;
  margin-bottom: 24px;
}

.progress-bar .progress {
  height: 100%;
  background: #4A9FF5;
  transition: width 0.3s ease;
}

.chips-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 16px;
  margin-top: 32px;
}

.chip {
  border: 2px solid #E2E8F0;
  border-radius: 8px;
  padding: 20px;
  cursor: pointer;
  transition: all 0.2s ease;
  text-align: left;
}

.chip:hover {
  border-color: #4A9FF5;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(74, 159, 245, 0.15);
}

.chip.selected {
  border-color: #4A9FF5;
  background: #E8F4FD;
}

.chip .icon {
  font-size: 32px;
  display: block;
  margin-bottom: 8px;
}

.chip .label {
  font-size: 18px;
  font-weight: 600;
  color: #1A202C;
  display: block;
  margin-bottom: 4px;
}

.chip .subtext {
  font-size: 14px;
  color: #718096;
}

/* Product Card Hover Effect */
.product-card {
  transition: all 0.2s ease;
}

.product-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
}

/* Spencer Risk AI Highlighted Card */
.card-risk-ai {
  border: 2px solid #4A9FF5;
  background: linear-gradient(135deg, #E8F4FD 0%, #FFFFFF 100%);
  position: relative;
}

.card-risk-ai::before {
  content: "NEW BETA";
  position: absolute;
  top: 12px;
  right: 12px;
  background: #48BB78;
  color: white;
  font-size: 11px;
  font-weight: 700;
  padding: 4px 10px;
  border-radius: 4px;
  text-transform: uppercase;
}

/* Mobile Responsive Adjustments */
@media (max-width: 768px) {
  .chips-container {
    grid-template-columns: 1fr;
  }
  
  .chip {
    min-height: 80px;
  }
}
```

---

## ⚙️ Custom JavaScript Functions

**File**: `/js/custom-functions.js`

```javascript
// Assessment Wizard Logic
let assessmentData = {
  persona: null,
  goal: null,
  bottleneck: null
};

function startAssessment() {
  document.getElementById('assessment-intro').classList.remove('active');
  document.getElementById('assessment-q1').classList.add('active');
  updateProgress(20);
}

function selectChip(screen, value) {
  // Store answer
  if (screen === 'q1') assessmentData.persona = value;
  if (screen === 'q2') assessmentData.goal = value;
  if (screen === 'q3') assessmentData.bottleneck = value;
  
  // Update sessionStorage
  sessionStorage.setItem('assessmentData', JSON.stringify(assessmentData));
  
  // Visual feedback
  document.querySelectorAll('.chip').forEach(chip => {
    chip.classList.remove('selected');
  });
  event.target.closest('.chip').classList.add('selected');
  
  // Auto-advance after 400ms
  setTimeout(() => {
    if (screen === 'q1') showScreen('q2');
    if (screen === 'q2') showScreen('q3');
    if (screen === 'q3') showResults();
  }, 400);
}

function showScreen(screenId) {
  document.querySelectorAll('.assessment-screen').forEach(screen => {
    screen.classList.remove('active');
  });
  document.getElementById(`assessment-${screenId}`).classList.add('active');
  
  if (screenId === 'q2') updateProgress(40);
  if (screenId === 'q3') updateProgress(60);
}

function showResults() {
  // Hide questions
  document.querySelectorAll('.assessment-screen').forEach(screen => {
    screen.classList.remove('active');
  });
  document.getElementById('assessment-results').classList.add('active');
  updateProgress(100);
  
  // Fetch product recommendations via AJAX
  fetch('/wp-json/spencer/v1/recommendations', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(assessmentData)
  })
  .then(response => response.json())
  .then(data => {
    displayRecommendedProducts(data.products);
    prefillLeadForm(assessmentData, data.productIds);
  });
  
  // Analytics
  gtag('event', 'assessment_completed', {
    persona: assessmentData.persona,
    goal: assessmentData.goal,
    bottleneck: assessmentData.bottleneck
  });
}

function displayRecommendedProducts(products) {
  const container = document.getElementById('recommended-products-container');
  container.innerHTML = '';
  
  products.forEach(product => {
    const card = `
      <div class="product-card">
        <span class="badge">RECOMMENDED PRODUCT</span>
        <img src="${product.image}" alt="${product.title}">
        <h3>${product.title}</h3>
        <p>${product.description}</p>
        <ul>
          ${product.features.map(f => `<li>${f}</li>`).join('')}
        </ul>
        <a href="${product.url}">Learn more →</a>
      </div>
    `;
    container.innerHTML += card;
  });
}

function prefillLeadForm(answers, productIds) {
  // Prefill hidden fields in WPForms
  document.querySelector('[name="wpforms[fields][persona]"]').value = answers.persona;
  document.querySelector('[name="wpforms[fields][goal]"]').value = answers.goal;
  document.querySelector('[name="wpforms[fields][bottleneck]"]').value = answers.bottleneck;
  document.querySelector('[name="wpforms[fields][recommended_products]"]').value = productIds.join(',');
}

function updateProgress(percent) {
  document.querySelector('.progress').style.width = percent + '%';
}

// Track CTA clicks
document.querySelectorAll('[data-track-cta]').forEach(button => {
  button.addEventListener('click', function() {
    gtag('event', 'cta_click', {
      location: this.dataset.location,
      cta_text: this.innerText
    });
  });
});

// Email validation (reject Gmail, Yahoo, etc. for lead forms)
document.querySelectorAll('.wpforms-field-email input').forEach(input => {
  input.addEventListener('blur', function() {
    const email = this.value.toLowerCase();
    const freeProviders = ['gmail.com', 'yahoo.com', 'hotmail.com', 'outlook.com', 'live.com'];
    const domain = email.split('@')[1];
    
    if (freeProviders.includes(domain)) {
      this.setCustomValidity('Please use your work email');
      this.reportValidity();
    } else {
      this.setCustomValidity('');
    }
  });
});
```

---

## 🔌 Custom REST API Endpoints

**File**: `functions.php` or custom plugin

```php
<?php
// Register custom REST API endpoint for product recommendations
add_action('rest_api_init', function () {
  register_rest_route('spencer/v1', '/recommendations', array(
    'methods' => 'POST',
    'callback' => 'get_assessment_recommendations',
    'permission_callback' => '__return_true'
  ));
});

function get_assessment_recommendations($request) {
  $persona = $request['persona'];
  $goal = $request['goal'];
  $bottleneck = $request['bottleneck'];
  
  // Mapping logic (based on Assessment design doc)
  $product_ids = [];
  
  // Example logic
  if ($persona === 'multi-asset-broker' && $bottleneck === 'poor-execution-quality') {
    $product_ids = [
      get_product_id_by_slug('liquidity-aggregation'),
      get_product_id_by_slug('bridging-engine'),
      get_product_id_by_slug('spencer-risk-ai')
    ];
  }
  
  // ... more conditions
  
  // Fetch product details
  $products = array_map(function($id) {
    $post = get_post($id);
    return [
      'id' => $id,
      'title' => $post->post_title,
      'description' => get_field('short_description', $id),
      'features' => array_slice(get_field('key_features', $id), 0, 3),
      'image' => get_the_post_thumbnail_url($id, 'medium'),
      'url' => get_permalink($id)
    ];
  }, $product_ids);
  
  return [
    'products' => $products,
    'productIds' => $product_ids
  ];
}

function get_product_id_by_slug($slug) {
  $query = new WP_Query([
    'post_type' => 'product',
    'name' => $slug,
    'posts_per_page' => 1
  ]);
  return $query->posts[0]->ID ?? null;
}
?>
```

---

## 📊 Analytics Setup (Google Tag Manager)

### GTM Container Configuration:

**Tags**:
1. Google Analytics 4 (config)
2. Assessment Started (event)
3. Assessment Question Answered (event)
4. Assessment Completed (event)
5. Lead Form Submitted (event)
6. CTA Clicked (event)

**Triggers**:
1. Page View (All Pages)
2. Custom Event: assessment_started
3. Custom Event: assessment_q1_answer, q2_answer, q3_answer
4. Custom Event: assessment_completed
5. Form Submission (WPForms)
6. Click - All Elements (data-track-cta attribute)

**Variables**:
1. Persona (dataLayer variable)
2. Goal (dataLayer variable)
3. Bottleneck (dataLayer variable)
4. CTA Location (dataLayer variable)
5. CTA Text (dataLayer variable)

---

## 🚀 Deployment Checklist

### Pre-Launch:
- [ ] All plugins installed and licensed
- [ ] Custom post types registered
- [ ] ACF field groups created
- [ ] Elementor templates built
- [ ] Assessment wizard tested (all paths)
- [ ] WPForms connected to CRM (webhook or Zapier)
- [ ] Analytics tracking verified
- [ ] Mobile responsive tested (iPhone, Android)
- [ ] Load time < 2 seconds (GTMetrix test)
- [ ] SSL certificate installed
- [ ] 301 redirects from old site (if applicable)

### Post-Launch:
- [ ] Submit sitemap to Google Search Console
- [ ] Set up Google Analytics goals (Assessment completion, Lead submission)
- [ ] Configure email notifications for form submissions
- [ ] Test lead flow end-to-end (form → CRM → sales team)
- [ ] Set up weekly analytics reporting

---

## 🔧 Maintenance & Updates

### Weekly:
- Check form submissions (any spam?)
- Review Analytics (bounce rate, conversion rate)
- Test Assessment wizard (ensure no broken links)

### Monthly:
- Update plugins (test on staging first)
- Review and update case studies (add new ones)
- A/B test one element (see A/B test roadmap)

### Quarterly:
- Review product/solution content (still accurate?)
- Update Spencer Risk AI beta status (when it goes live)
- Add new case studies (aim for 1 per product)

---

**Document Version**: 1.0  
**Last Updated**: 2026-02-03  
**Owner**: Development & Implementation Team
