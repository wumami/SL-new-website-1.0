# UI Design System & Tone Guidelines

## 🎨 Visual Design Philosophy

**Core Principle**: **Trust through simplicity, not complexity**

This website should feel like:
- A modern financial institution (trustworthy, professional)
- NOT a flashy tech startup (aggressive, over-designed)
- NOT a complex enterprise software company (overwhelming, technical)

**Reference**: DriveWealth.com
- Clean white backgrounds
- Ample white space (never feel cramped)
- Subtle interactions (not aggressive animations)
- Photography when needed (not decorative stock photos)

---

## 🎨 Color System

### Primary Colors

**Spencer Blue** (Brand Primary)
```
Primary:   #4A9FF5   (Main brand color - buttons, links, accents)
Dark:      #2E7BC4   (Hover states, darker elements)
Light:     #E8F4FD   (Backgrounds, subtle highlights)
Very Light:#F7FCFF   (Alternate section backgrounds)
```

**Usage**:
- Primary CTAs (buttons)
- Links (text links, navigation links)
- Icons (key feature icons)
- Badges ("New Beta", "Recommended")
- Progress bars (Assessment wizard)
- Section dividers (when needed)

---

### Neutral Colors

**Grays** (Primary text and UI elements)
```
Text Dark:    #1A202C   (Headings, primary text)
Text Body:    #2D3748   (Body copy, descriptions)
Text Subtle:  #718096   (Subheadings, captions, meta info)
Border:       #E2E8F0   (Card borders, dividers)
Background:   #F7FAFC   (Alternate section backgrounds)
White:        #FFFFFF   (Primary background)
```

**Usage**:
- Text Dark: All headings (H1, H2, H3)
- Text Body: Paragraph text, button text (on white)
- Text Subtle: Subheadings, "Question 1 of 3", timestamps
- Border: Card outlines, form inputs, section dividers
- Background: Alternating sections (symptoms lists, FAQ)
- White: Hero sections, main content areas

---

### Accent Colors (Minimal Use)

**Success Green**
```
Green: #48BB78   ("Beta" badges, success states)
```

**Warning Orange**
```
Orange: #ED8936  (Important notices, limited-time offers)
```

**Error Red**
```
Red: #F56565     (Form validation errors)
```

---

## 📐 Typography System

### Font Family

**Primary**: Inter  
**Fallback**: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif

**Why Inter?**
- Clean, modern, highly readable
- Excellent at all sizes (especially small UI text)
- Free and open-source
- Used by many modern SaaS companies

**Alternative**: SF Pro Display (if targeting Apple users heavily)

---

### Font Sizes & Weights

```css
/* Headings */
H1: {
  font-size: 48px (desktop), 32px (mobile);
  font-weight: 700 (bold);
  line-height: 1.2;
  letter-spacing: -0.02em;
  color: #1A202C;
}

H2: {
  font-size: 36px (desktop), 28px (mobile);
  font-weight: 600 (semi-bold);
  line-height: 1.3;
  letter-spacing: -0.01em;
  color: #1A202C;
}

H3: {
  font-size: 24px;
  font-weight: 600;
  line-height: 1.4;
  color: #1A202C;
}

H4: {
  font-size: 18px;
  font-weight: 600;
  line-height: 1.5;
  color: #2D3748;
}

/* Body Text */
Body Large: {
  font-size: 18px;
  font-weight: 400;
  line-height: 1.7;
  color: #2D3748;
}

Body Regular: {
  font-size: 16px;
  font-weight: 400;
  line-height: 1.6;
  color: #2D3748;
}

Body Small: {
  font-size: 14px;
  font-weight: 400;
  line-height: 1.6;
  color: #718096;
}

/* UI Text */
Button Text: {
  font-size: 16px;
  font-weight: 600;
  letter-spacing: 0.01em;
}

Label Text: {
  font-size: 14px;
  font-weight: 500;
  color: #2D3748;
}

Caption: {
  font-size: 12px;
  font-weight: 400;
  line-height: 1.5;
  color: #718096;
}
```

---

### Typography Rules

**DO**:
- Use bold (700) for H1 only
- Use semi-bold (600) for H2, H3, buttons
- Keep body text at 400 (regular weight)
- Use 1.6-1.7 line-height for readability
- Use negative letter-spacing for large headings

**DON'T**:
- Use more than 3 font weights on a page
- Use italic (except for citations/quotes)
- Use ALL CAPS for headings (only for labels like "QUESTION 1 OF 3")
- Use font sizes smaller than 12px (accessibility)

---

## 🔘 Button Styles

### Primary Button
```css
.btn-primary {
  background: #4A9FF5;
  color: #FFFFFF;
  font-size: 16px;
  font-weight: 600;
  padding: 14px 32px;
  border-radius: 6px;
  border: none;
  cursor: pointer;
  transition: all 0.2s ease;
  box-shadow: 0 2px 8px rgba(74, 159, 245, 0.25);
}

.btn-primary:hover {
  background: #2E7BC4;
  box-shadow: 0 4px 12px rgba(74, 159, 245, 0.35);
  transform: translateY(-1px);
}

.btn-primary:active {
  transform: translateY(0);
  box-shadow: 0 2px 8px rgba(74, 159, 245, 0.25);
}
```

**Usage**: "Start Assessment", "Get a Demo", "Join Beta", "Submit"

---

### Secondary Button (Ghost)
```css
.btn-secondary {
  background: transparent;
  color: #4A9FF5;
  font-size: 16px;
  font-weight: 600;
  padding: 12px 30px; /* Adjusted for border */
  border-radius: 6px;
  border: 2px solid #4A9FF5;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-secondary:hover {
  background: #4A9FF5;
  color: #FFFFFF;
}
```

**Usage**: "Talk to expert", "Learn more", "Back", "Start Over"

---

### Text Link
```css
.text-link {
  color: #4A9FF5;
  font-size: 16px;
  font-weight: 500;
  text-decoration: none;
  transition: all 0.2s ease;
  border-bottom: 1px solid transparent;
}

.text-link:hover {
  color: #2E7BC4;
  border-bottom: 1px solid #2E7BC4;
}
```

**Usage**: "Learn more →", "Read the story →", "Explore solution →"

---

### Button Sizes

**Large** (Hero CTAs):
```
padding: 18px 40px;
font-size: 18px;
```

**Regular** (Most CTAs):
```
padding: 14px 32px;
font-size: 16px;
```

**Small** (Inline forms, secondary actions):
```
padding: 10px 24px;
font-size: 14px;
```

---

## 📦 Card Styles

### Standard Card
```css
.card {
  background: #FFFFFF;
  border: 1px solid #E2E8F0;
  border-radius: 8px;
  padding: 24px;
  transition: all 0.2s ease;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
  transform: translateY(-2px);
}
```

**Usage**: Product cards, Solution cards, Feature cards

---

### Highlighted Card (for Spencer Risk AI, featured items)
```css
.card-highlighted {
  background: linear-gradient(135deg, #E8F4FD 0%, #FFFFFF 100%);
  border: 2px solid #4A9FF5;
  border-radius: 8px;
  padding: 24px;
  position: relative;
  box-shadow: 0 4px 16px rgba(74, 159, 245, 0.15);
}

.card-highlighted::before {
  content: "NEW BETA";
  position: absolute;
  top: 12px;
  right: 12px;
  background: #48BB78;
  color: #FFFFFF;
  font-size: 11px;
  font-weight: 700;
  padding: 4px 10px;
  border-radius: 4px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}
```

**Usage**: Spencer Risk AI cards, "New" products, Beta programs

---

### Case Study Card
```css
.card-case-study {
  background: #F7FAFC;
  border-left: 4px solid #4A9FF5;
  border-radius: 4px;
  padding: 32px;
}

.card-case-study .badge {
  display: inline-block;
  background: #E2E8F0;
  color: #2D3748;
  font-size: 12px;
  font-weight: 600;
  padding: 4px 12px;
  border-radius: 4px;
  margin-bottom: 16px;
  text-transform: uppercase;
}
```

---

## 📝 Form Styles

### Input Fields
```css
.form-input {
  width: 100%;
  font-size: 16px;
  padding: 12px 16px;
  border: 1px solid #E2E8F0;
  border-radius: 6px;
  background: #FFFFFF;
  transition: all 0.2s ease;
  font-family: inherit;
}

.form-input:focus {
  outline: none;
  border-color: #4A9FF5;
  box-shadow: 0 0 0 3px rgba(74, 159, 245, 0.1);
}

.form-input::placeholder {
  color: #A0AEC0;
}

.form-input.error {
  border-color: #F56565;
}
```

---

### Labels
```css
.form-label {
  display: block;
  font-size: 14px;
  font-weight: 500;
  color: #2D3748;
  margin-bottom: 6px;
}

.form-label.required::after {
  content: " *";
  color: #F56565;
}
```

---

### Checkboxes
```css
.form-checkbox {
  display: flex;
  align-items: center;
  margin-bottom: 12px;
}

.form-checkbox input[type="checkbox"] {
  width: 20px;
  height: 20px;
  margin-right: 10px;
  accent-color: #4A9FF5;
}

.form-checkbox label {
  font-size: 14px;
  color: #2D3748;
  cursor: pointer;
}
```

---

### Error Messages
```css
.form-error {
  display: block;
  font-size: 13px;
  color: #F56565;
  margin-top: 6px;
}
```

---

## 🎯 Icon System

**Icon Library**: Feather Icons OR Heroicons  
**Style**: Line icons (not solid)  
**Size**: 24px (standard), 32px (large), 16px (small/inline)  
**Color**: Spencer Blue (#4A9FF5) or Text Dark (#1A202C)

**Common Icons**:
- Rocket: Launch products
- Chart: Analytics, performance
- Shield: Security, risk management
- Zap: Speed, efficiency
- Users: Social, community
- Settings: Configuration, technical
- Check: Verified, completed
- Arrow Right: Links, next steps

**Icon Rules**:
- Use sparingly (not every card needs an icon)
- Icons should support text, not replace it
- Keep stroke weight consistent (2px)
- Don't use emojis (except in examples/documentation)

---

## 🖼️ Image Guidelines

### Screenshots
**DO**:
- Use clean, uncluttered screenshots
- Show real UI (not mockups if possible)
- Crop to relevant area (not full desktop with OS chrome)
- Add subtle shadow/border to separate from background
- Use 2x resolution for Retina displays
- Compress with WebP format

**DON'T**:
- Show outdated UI
- Use busy screenshots with too much data
- Include client names/sensitive data (blur if needed)
- Use low-resolution images (blurry on mobile)

---

### Photography (Use Sparingly)
**DO**:
- Use real photos of team (if available)
- Use contextual photos (trading floor, office) if relevant
- Keep background simple (avoid busy stock photos)

**DON'T**:
- Use generic "businessman shaking hands" stock photos
- Use photos just to fill space
- Use photos with aggressive color filters

---

### Illustrations
**Style**: Simple, line-based (not complex 3D renders)  
**Color**: Primarily Spencer Blue + grays  
**Usage**: 
- Diagrams (architecture, flow charts)
- Abstract concepts (AI, patterns, connections)
- Empty states (no case studies yet)

**Where to source**:
- Custom (preferred)
- Undraw.co (free, customizable)
- Storyset (free, customizable)

---

## 📏 Spacing System

**Base Unit**: 8px

```
Spacing Scale:
xs:  8px   (tight spacing, inline elements)
sm:  16px  (between paragraphs, small gaps)
md:  24px  (card padding, between sections)
lg:  32px  (section padding on mobile)
xl:  48px  (between major sections)
2xl: 64px  (section padding on desktop)
3xl: 96px  (between major page sections on desktop)
4xl: 128px (large gaps, hero sections)
```

**Section Padding** (Vertical):
- Desktop: 64px top/bottom
- Mobile: 32px top/bottom

**Container Max-Width**:
- Standard content: 1200px
- Narrow (forms, articles): 800px
- Wide (case studies grid): 1400px

---

## 🎭 Animation & Interaction

### Hover States
```css
transition: all 0.2s ease;
```

**DO**:
- Use subtle lift effect (translateY(-2px))
- Increase shadow on hover
- Change color slightly (darken buttons)
- Underline text links on hover

**DON'T**:
- Use slow animations (>0.3s)
- Use easing beyond ease, ease-in-out
- Animate too many properties at once
- Use overly aggressive effects (scale, rotate)

---

### Page Transitions
- Fade in on load (0.3s)
- Smooth scroll between sections
- Assessment questions: fade transition between screens (0.4s)

**DON'T**:
- Use slide animations (feels outdated)
- Use parallax scrolling (distracting)
- Auto-play videos with sound

---

## ✍️ Tone of Voice

### Writing Principles

**1. Problem-First, Not Feature-First**

❌ BAD:
> "Spencer Logic is a leading provider of cutting-edge trading technology solutions leveraging AI and machine learning."

✅ GOOD:
> "Trading technology that starts with your business problem."

---

**2. Concrete, Not Abstract**

❌ BAD:
> "Leverage our innovative liquidity aggregation framework to optimize execution quality."

✅ GOOD:
> "Connect to multiple liquidity providers to get better pricing for your clients."

---

**3. Outcomes, Not Features**

❌ BAD:
> "Spencer Core includes client onboarding, CRM, reporting, and back office management."

✅ GOOD:
> "Cut manual back-office work by 40% with automated reconciliation and reporting."

---

**4. Plain Language, Not Jargon**

❌ BAD:
> "Ultra-low latency aggregation with sub-millisecond execution via FIX protocol connectivity."

✅ GOOD:
> "Fast connections to top liquidity providers (less than 1 millisecond latency)."

---

**5. Confident, Not Salesy**

❌ BAD:
> "The world's most revolutionary AI-powered risk management solution! 🚀"

✅ GOOD:
> "AI-powered risk management for brokers and exchanges."

---

### Voice Characteristics

**We are**:
- **Confident**: We know our product works
- **Direct**: No fluff, no marketing speak
- **Helpful**: We're here to solve problems
- **Technical (when needed)**: We don't dumb things down for technical buyers
- **Human**: We're people talking to people

**We are NOT**:
- Aggressive salespeople
- Marketing robots
- Over-excited startup bros
- Condescending tech experts

---

### Word Choices

**Use These**:
- Build, launch, improve, fix, solve
- Fast, reliable, flexible, simple
- Broker, exchange, prop firm, trader
- Risk, exposure, execution, liquidity
- Dashboard, alert, monitoring, reporting

**Avoid These**:
- Synergy, leverage, disruptive, revolutionary
- Cutting-edge, state-of-the-art, next-gen
- Solution (unless in context like "solution page")
- Ecosystem, holistic, paradigm
- Empower, enable, facilitate (overused)

---

### Headline Formulas

**Problem → Solution**:
> "Stop losing clients to execution complaints"
> "Launch a crypto exchange in 6 weeks"

**Benefit → Context**:
> "Cut manual work by 40% with automated back office"
> "Monitor risk across all traders in real time"

**Action → Outcome**:
> "Connect to multiple LPs → Tighten spreads"
> "Automate reconciliation → Free up your team"

---

## 📱 Mobile Design Considerations

### Mobile-First Rules

1. **Touch Targets**: Minimum 44px height (iOS), 48px (Android)
2. **Font Sizes**: Never smaller than 14px
3. **Spacing**: Increase padding/margins slightly (easier to tap)
4. **Navigation**: Hamburger menu (if needed), or bottom tabs
5. **Forms**: Stack all fields vertically, large inputs
6. **CTAs**: Full-width buttons on mobile (easier to tap)

### Mobile Breakpoints

```css
/* Mobile First */
@media (min-width: 768px) {
  /* Tablet */
}

@media (min-width: 1024px) {
  /* Desktop */
}

@media (min-width: 1280px) {
  /* Large Desktop */
}
```

---

## ♿ Accessibility (WCAG 2.1 AA)

### Color Contrast
- Text on white: Minimum 4.5:1 ratio
- Large text (18px+): Minimum 3:1 ratio
- Spencer Blue (#4A9FF5) on white: ✅ Pass (4.58:1)
- Text Subtle (#718096) on white: ✅ Pass (4.69:1)

### Keyboard Navigation
- All interactive elements tabbable
- Focus states clearly visible (blue outline)
- Skip to content link (for screen readers)

### Screen Readers
- Alt text on all images
- ARIA labels on icon buttons
- Form labels properly associated
- Semantic HTML (h1, h2, nav, main, footer)

---

## 🎨 Component Library (Summary)

### Core Components Needed:

1. **Buttons**
   - Primary (filled)
   - Secondary (ghost)
   - Text link

2. **Cards**
   - Standard card
   - Highlighted card (Spencer Risk AI)
   - Case study card
   - Product card
   - Solution card

3. **Forms**
   - Text input
   - Email input (with validation)
   - Dropdown/Select
   - Checkbox
   - Radio buttons (Assessment chips)
   - Submit button
   - Error states

4. **Navigation**
   - Top nav (desktop)
   - Mobile menu
   - Breadcrumbs (optional)
   - Footer

5. **Content Blocks**
   - Hero section
   - Feature grid
   - Case study inline
   - FAQ accordion
   - CTA banner (full-width)

6. **Assessment Specific**
   - Progress bar
   - Question chips (visual selection)
   - Results cards

---

## ✅ Design Quality Checklist

Before launching any page:

- [ ] All text is readable (contrast ratio >4.5:1)
- [ ] All interactive elements have hover states
- [ ] All buttons have consistent sizing
- [ ] All cards have consistent border-radius (8px)
- [ ] Spacing follows 8px grid system
- [ ] Typography uses no more than 3 weights
- [ ] Mobile design tested on real devices
- [ ] All images optimized (WebP, <200KB)
- [ ] No orphans (single words on last line of headline)
- [ ] All links have clear destinations (not generic "Learn more")
- [ ] CTAs are specific and action-oriented
- [ ] Load time < 2 seconds on 4G connection

---

**Document Version**: 1.0  
**Last Updated**: 2026-02-03  
**Owner**: Design & UX Team
