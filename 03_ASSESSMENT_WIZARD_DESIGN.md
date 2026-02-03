# Assessment (Q&A Wizard): Complete Design Specification

## 🎯 Purpose & Success Metrics

**Primary Goal**: Convert 65%+ of starters to completion  
**Secondary Goal**: Capture qualified leads at 35%+ rate  
**Strategic Goal**: Position Spencer Risk AI to relevant personas

**Key Metrics**:
- Start rate (clicks from homepage)
- Question 1 → 2 progression (should be >90%)
- Question 2 → 3 progression (should be >85%)
- Question 3 → Results (should be >80%)
- Results → Lead form submission (should be >35%)

---

## 📐 Page Layout & Flow

### URL Structure
```
/assessment (main page)
/assessment/results (after completion, shareable URL with query params)
```

### Page States
1. **Intro screen** (welcome + value prop)
2. **Question 1** (Persona selection)
3. **Question 2** (Goal selection, dynamic based on Q1)
4. **Question 3** (Bottleneck selection, dynamic based on Q1+Q2)
5. **Results** (Product recommendations + case studies)
6. **Lead form** (inline on results, not separate page)

---

## 🎨 Visual Design

### Layout (Desktop)
```
┌────────────────────────────────────────────────┐
│  [← Back to Home]            [X] Close         │  ← Header (minimal)
│                                                │
│  ┌──────────────────────────────────────────┐ │
│  │                                          │ │
│  │         CONTENT AREA                     │ │
│  │      (centered, max-width 800px)         │ │
│  │                                          │ │
│  └──────────────────────────────────────────┘ │
│                                                │
│     [Progress: ▓▓▓▒▒ 60%]                     │  ← Bottom
└────────────────────────────────────────────────┘
```

### Design Principles
- **Clean**: White background, no distractions
- **Focused**: One question per screen
- **Visual**: Use icons + color-coded chips (not boring dropdowns)
- **Progress**: Always show progress bar (reduces anxiety)
- **Mobile-first**: Large touch targets (min 48px height)

---

## 📝 Screen-by-Screen Specifications

### SCREEN 0: Intro

**Headline** (H1, centered):
```
Find the right trading technology 
for your business in 3 questions
```

**Subheadline** (gray text, centered):
```
We'll recommend a combination of Spencer Logic products 
that fits your situation—and you can talk to an expert right away.
```

**Visual** (optional):
- Simple illustration of 3 steps
- OR: Clean icon showing "diagnosis"

**CTA** (Large button, centered):
```
Start Assessment
```

**Disclaimer** (small text below button):
```
Takes less than 2 minutes • No email required to see results
```

**Design Notes**:
- Ample white space (padding: 80px top/bottom)
- Button should be prominent (16px padding, Spencer blue)
- On click, fade transition to Question 1 (not jarring)

---

### SCREEN 1: Persona Selection

**Progress Bar**: ▓▓▒▒▒ (20%)

**Question Label** (small, uppercase, gray):
```
QUESTION 1 OF 3
```

**Question** (H2):
```
What best describes you?
```

**Options** (Visual chips, 3 columns on desktop, stack on mobile):

#### Option 1: Multi-Asset Broker
```
Icon: 📊 (or line chart icon)
Label: Multi-Asset Broker
Subtext: FX, CFDs, stocks, crypto
```

#### Option 2: Crypto Exchange
```
Icon: ₿ (or crypto symbol)
Label: Crypto Exchange
Subtext: Spot, derivatives, or both
```

#### Option 3: Prop Trading Firm
```
Icon: 🎯 (or target icon)
Label: Prop Trading Firm
Subtext: Funded traders, challenges
```

#### Option 4: Asset Manager
```
Icon: 💼 (or briefcase icon)
Label: Asset Manager
Subtext: Institutional, fund management
```

#### Option 5: Introducing Broker
```
Icon: 🤝 (or handshake icon)
Label: Introducing Broker (IB)
Subtext: White label, revenue share
```

#### Option 6: Entrepreneur / Influencer
```
Icon: ⚡ (or lightning icon)
Label: Entrepreneur / Influencer
Subtext: Starting a trading community
```

#### Option 7: Technology / Ops Lead
```
Icon: ⚙️ (or gear icon)
Label: Technology / Ops Lead
Subtext: Evaluating for a firm
```

#### Option 8: Other
```
Icon: ❓ (or question mark)
Label: Other
Subtext: Tell us more later
```

**Chip Design**:
```
Width: 250px (desktop), full-width (mobile)
Height: 100px
Border: 2px solid #E2E8F0
Border-radius: 8px
Padding: 16px
Hover: Border color changes to Spencer blue, lift effect
Selected: Background Spencer blue (light), border Spencer blue (dark)
```

**Behavior**:
- On click, chip animates (checkmark appears)
- After 300ms delay, auto-advance to Question 2
- User can click "Back" to change selection

**Analytics**:
```javascript
gtag('event', 'assessment_q1_answer', {
  'persona': 'multi-asset-broker'
});
```

---

### SCREEN 2: Goal Selection

**Progress Bar**: ▓▓▓▒▒ (40%)

**Question Label**:
```
QUESTION 2 OF 3
```

**Question** (H2, personalized):
```
What's your main goal for the next 6-12 months?
```

**Options** (Dynamic based on Question 1):

#### IF Persona = Multi-Asset Broker:
```
✓ Launch a new brand or white label
✓ Improve execution quality & spreads
✓ Add crypto or more asset classes
✓ Offer social / copy trading
✓ Modernize platforms or back office
✓ Replace an existing vendor
✓ Scale to handle more volume
```

#### IF Persona = Crypto Exchange:
```
✓ Launch a new crypto exchange
✓ Improve order book depth & liquidity
✓ Add new trading pairs or derivatives
✓ Reduce infrastructure costs
✓ Meet regulatory requirements
✓ Replace an existing vendor
```

#### IF Persona = Prop Firm:
```
✓ Launch a new prop firm or challenge
✓ Scale to more funded traders
✓ Improve risk monitoring & controls
✓ Offer multi-asset trading
✓ Reduce manual operations
✓ Improve trader experience (platform)
```

#### IF Persona = IB / Influencer:
```
✓ Launch a white label platform
✓ Offer copy trading to my community
✓ Generate more revenue per client
✓ Automate client onboarding
```

#### IF Persona = Asset Manager / Tech Lead / Other:
```
✓ Launch a new trading platform
✓ Improve execution & connectivity
✓ Add new asset classes
✓ Modernize infrastructure
✓ Evaluate vendors / build vs buy
```

**Chip Design** (Similar to Q1, but smaller):
```
Width: 350px (desktop), full-width (mobile)
Height: 60px
Single-line text (no subtext)
Icon: ✓ (checkmark on selected)
```

**Behavior**:
- Same as Question 1: auto-advance after selection
- "Back" button visible (top-left)

**Analytics**:
```javascript
gtag('event', 'assessment_q2_answer', {
  'persona': 'multi-asset-broker',
  'goal': 'improve-execution'
});
```

---

### SCREEN 3: Bottleneck Selection

**Progress Bar**: ▓▓▓▓▒ (60%)

**Question Label**:
```
QUESTION 3 OF 3
```

**Question** (H2):
```
What's your biggest bottleneck right now?
```

**Options** (Dynamic based on Persona + Goal):

#### Common Bottlenecks (appear for most personas):
```
✓ Poor execution quality (wide spreads, slippage)
✓ Traders don't like the current platform UI
✓ Too much manual work in back office & reporting
✓ Can't launch new brands quickly enough
✓ Hard to scale (infrastructure limitations)
✓ Risk monitoring is too slow or manual
✓ MT4/MT5 limitations (for brokers)
✓ Vendor rigidity or high costs
✓ Regulatory / compliance challenges
```

#### Crypto-Specific Bottlenecks:
```
✓ Thin order books
✓ Wallet integration issues
✓ High infrastructure costs
✓ Slow settlement times
```

#### Prop Firm-Specific:
```
✓ Can't monitor risk across all traders in real time
✓ Trader onboarding is too manual
✓ Platform crashes during high volume
```

**Chip Design** (Same as Q2)

**Behavior**:
- Same as Q1/Q2: auto-advance after selection
- BUT this time, transition to **Results screen** (not another question)
- Slightly longer delay (500ms) to build anticipation

**Analytics**:
```javascript
gtag('event', 'assessment_q3_answer', {
  'persona': 'multi-asset-broker',
  'goal': 'improve-execution',
  'bottleneck': 'poor-execution-quality'
});
```

---

### SCREEN 4: Results

**Progress Bar**: ▓▓▓▓▓ (100%)

**Layout**:
```
┌─────────────────────────────────────────────────┐
│  Based on your answers, we recommend:           │  ← Intro
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  [Product Card 1]  [Product Card 2]             │  ← Recommended Products
│  [Product Card 3]  [Product Card 4 (optional)]  │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  Related Case Studies                            │  ← Social Proof
│  [Case Study 1]  [Case Study 2]                 │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  Want a detailed plan?                           │  ← Lead Capture
│  [Lead Form - inline]                           │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  [Start Over] [Share Results]                   │  ← Actions
└─────────────────────────────────────────────────┘
```

#### Section 1: Intro Text

**Headline** (H2):
```
Based on your answers, we recommend:
```

**Summary** (personalized based on answers):
```
As a [Persona] looking to [Goal] but facing [Bottleneck], 
here's a combination of Spencer Logic products that can help:
```

**Example**:
> "As a **multi-asset broker** looking to **improve execution quality** but facing **poor spreads and slippage**, here's a combination of Spencer Logic products that can help:"

---

#### Section 2: Recommended Product Cards

**Layout**: 2 columns (desktop), stack (mobile)

**Product Card Design**:
```
┌──────────────────────────────────────┐
│  [Badge: RECOMMENDED PRODUCT]        │
│                                      │
│  [Product Icon/Image]                │
│                                      │
│  Product Name                        │
│  One-sentence value prop             │
│                                      │
│  Key features:                       │
│  • Feature 1                         │
│  • Feature 2                         │
│  • Feature 3                         │
│                                      │
│  [Learn more →]                      │
└──────────────────────────────────────┘
```

**Badge Styling**:
- Background: Spencer blue (light)
- Text: Spencer blue (dark)
- Font size: 12px, uppercase, bold
- Position: Top-right corner

---

### Product Recommendation Logic

#### Scenario 1: Multi-Asset Broker + Improve Execution + Poor Spreads
**Recommended Products**:
1. **Liquidity Aggregation** (PRIMARY)
   - Access multiple liquidity pools
   - Competitive pricing & deep liquidity
   - Reduce slippage

2. **Bridging Engine** (SUPPORTING)
   - Seamless MT4/MT5 integration
   - Sub-millisecond execution
   - Full transparency

3. **Spencer Trader** (OPTIONAL)
   - Modern web trading interface
   - TradingView charts
   - Better client experience

4. **Spencer Risk AI** (NEW - if risk mentioned)
   - Real-time exposure monitoring
   - Pattern detection
   - Multi-brand risk aggregation

---

#### Scenario 2: Crypto Exchange + Launch New Exchange + Infrastructure
**Recommended Products**:
1. **Spencer Exchange** (PRIMARY)
   - Full CLOB (central limit order book)
   - Wallet integration
   - KYC/compliance built-in

2. **Liquidity Aggregation** (SUPPORTING)
   - Connect to top crypto liquidity providers
   - Market making tools
   - Competitive spreads

3. **Spencer Core** (OPTIONAL)
   - Back office & reporting
   - Multi-currency accounting
   - API for integrations

---

#### Scenario 3: Prop Firm + Scale Traders + Risk Monitoring
**Recommended Products**:
1. **Spencer Risk AI** (PRIMARY) ⭐
   - Real-time trader exposure monitoring
   - Abnormal pattern detection
   - Dealing desk dashboards

2. **Spencer Core** (SUPPORTING)
   - Automated trader onboarding
   - Performance reporting
   - Multi-account management

3. **Spencer Trader** (OPTIONAL)
   - Web-based trading platform
   - Mobile-friendly
   - Customizable UI

---

#### Scenario 4: IB/Influencer + Copy Trading + Launch Platform
**Recommended Products**:
1. **Invest Social** (PRIMARY)
   - Social feeds & rankings
   - One-click copy trading
   - Revenue share for influencers

2. **Spencer Broker Hub** (SUPPORTING)
   - Client portal
   - Account management
   - Onboarding tools

3. **Spencer Trader** (OPTIONAL)
   - Modern trading interface
   - Mobile app
   - White label ready

---

### CRITICAL RULE:
**If any of these appear in answers → ALWAYS include Spencer Risk AI:**
- Bottleneck: "Risk monitoring is too slow"
- Bottleneck: "Can't monitor risk across traders"
- Bottleneck: "MT4/MT5 limitations" (MT limitations often = risk issues)
- Goal: "Scale to more traders/volume" (scale = risk)
- Persona: Prop Firm (any goal + any bottleneck)

---

#### Section 3: Related Case Studies

**Headline** (H3):
```
See how others solved similar challenges:
```

**Case Study Cards** (2 cards, horizontal):

**Card Design** (Compact):
```
┌─────────────────────────────────────┐
│ [Segment Badge]                     │
│                                     │
│ Headline (result-focused)           │
│ "Cut manual work by 40%"            │
│                                     │
│ Short description (2 lines)         │
│                                     │
│ [Read the story →]                  │
└─────────────────────────────────────┘
```

**Case Study Selection Logic**:
- Pick case studies that match recommended products
- If Spencer Risk AI recommended → show (future) "Spencer Risk AI beta results"
- If Liquidity Aggregation → show "Execution quality improvement"
- If Spencer Exchange → show "Crypto launch in 6 weeks"
- If Spencer Core → show "Back office efficiency"

---

#### Section 4: Lead Capture Form

**Headline** (H3):
```
Want a detailed plan tailored to your business?
```

**Subheadline** (gray text):
```
Share a few details and we'll send you:
• A personalized product roadmap
• Pricing & implementation timeline
• Access to relevant case studies
```

**Form Fields**:

```html
<form>
  <!-- Visible Fields -->
  <label>First Name *</label>
  <input type="text" name="first_name" required>

  <label>Work Email *</label>
  <input type="email" name="email" required pattern="^[^@]+@(?!gmail|yahoo|hotmail|outlook|live)">

  <label>Company *</label>
  <input type="text" name="company" required>

  <label>Phone / WhatsApp (Optional)</label>
  <input type="tel" name="phone">

  <!-- Hidden Fields (captured from Assessment) -->
  <input type="hidden" name="persona" value="multi-asset-broker">
  <input type="hidden" name="goal" value="improve-execution">
  <input type="hidden" name="bottleneck" value="poor-execution-quality">
  <input type="hidden" name="recommended_products" value="liquidity-aggregation,bridging-engine,spencer-risk-ai">
  <input type="hidden" name="source" value="assessment">
  <input type="hidden" name="utm_source" value="">
  <input type="hidden" name="utm_campaign" value="">

  <!-- Checkboxes -->
  <label>
    <input type="checkbox" name="want_call" value="yes">
    I'd like a 20-minute call to walk through this plan
  </label>

  <label>
    <input type="checkbox" name="subscribe" value="yes" checked>
    Send me occasional product updates & insights
  </label>

  <!-- Submit Button -->
  <button type="submit">Email me this plan</button>
</form>
```

**Form Design**:
- Light blue background (to separate from rest of page)
- Padding: 32px
- Border-radius: 8px
- Fields stack vertically
- Button: Full-width on mobile, auto-width on desktop

**Email Validation**:
- Must be work email (not Gmail, Yahoo, Hotmail, etc.)
- Show inline error: "Please use your work email"

**Submit Behavior**:
- On submit, show loading spinner (prevent double-submit)
- Send to CRM (HubSpot, Salesforce, or custom endpoint)
- Redirect to /assessment/thank-you

---

#### Section 5: Action Buttons

**Layout** (centered, side-by-side on desktop):

```
[← Start Over]    [Share Results →]
```

**Start Over**:
- Ghost button (outline)
- On click, reset all answers and return to Question 1
- Confirm dialog: "Are you sure? This will reset your answers."

**Share Results**:
- Secondary button
- Generates shareable URL: `/assessment/results?p=multi-asset-broker&g=improve-execution&b=poor-spreads`
- Opens share modal with:
  - Copy link button
  - Email link
  - LinkedIn share (pre-filled text: "I just used Spencer Logic's assessment tool to find the right trading tech for my business. Check it out:")

---

## 🔗 URL Parameters for Shareable Results

**Format**:
```
/assessment/results?persona=multi-asset-broker&goal=improve-execution&bottleneck=poor-spreads
```

**Behavior**:
- If user lands on this URL directly, show results immediately (skip questions)
- Pre-fill persona/goal/bottleneck values in hidden form fields
- Still require email to get detailed plan

**Benefits**:
- Shareable (user can send to colleague)
- Trackable (see which results pages get most traffic)
- Retargetable (pixel visitors who see results but don't convert)

---

## 📊 Analytics & Tracking

### Event Tracking:

```javascript
// Assessment started
gtag('event', 'assessment_started', {
  'source': 'homepage_hero' // or 'homepage_final_cta', 'solution_page', etc.
});

// Each question answered
gtag('event', 'assessment_q1_answer', {
  'persona': 'multi-asset-broker'
});
gtag('event', 'assessment_q2_answer', {
  'persona': 'multi-asset-broker',
  'goal': 'improve-execution'
});
gtag('event', 'assessment_q3_answer', {
  'persona': 'multi-asset-broker',
  'goal': 'improve-execution',
  'bottleneck': 'poor-execution-quality'
});

// Results viewed
gtag('event', 'assessment_completed', {
  'persona': 'multi-asset-broker',
  'goal': 'improve-execution',
  'bottleneck': 'poor-execution-quality',
  'recommended_products': 'liquidity-aggregation,bridging-engine,spencer-risk-ai'
});

// Product card clicks from results
gtag('event', 'product_click', {
  'product': 'liquidity-aggregation',
  'source': 'assessment_results'
});

// Lead form submitted
gtag('event', 'lead_captured', {
  'source': 'assessment',
  'persona': 'multi-asset-broker',
  'recommended_products': 'liquidity-aggregation,bridging-engine,spencer-risk-ai'
});
```

### Conversion Funnel:
```
Started → Q1 → Q2 → Q3 → Results Viewed → Lead Submitted
```

**Goal**: Minimize drop-off at each stage

---

## 🧪 A/B Test Variations

### Test 1: Number of Questions
**Control**: 3 questions  
**Variation**: 2 questions (combine Goal + Bottleneck into single multi-select)

**Hypothesis**: Fewer questions = higher completion rate

---

### Test 2: Results Page Layout
**Control**: Product cards first, then lead form  
**Variation**: Lead form first (above the fold), then product cards

**Hypothesis**: Earlier lead capture = higher conversion (but may reduce quality)

---

### Test 3: Lead Form Fields
**Control**: Name, Email, Company, Phone (4 fields)  
**Variation**: Email only (1 field)

**Hypothesis**: Less friction = higher submission rate (but may reduce lead quality)

---

### Test 4: Spencer Risk AI Placement
**Control**: Include Risk AI only when risk-related bottleneck selected  
**Variation**: Always include Risk AI in results (with "Beta" badge)

**Hypothesis**: More exposure = more beta applications

---

## 🎨 Mobile Responsiveness

### Mobile Adjustments:

**Intro Screen**:
- Reduce headline font size
- Stack CTA buttons vertically
- Increase touch target size (min 48px height)

**Question Screens**:
- Chips stack vertically (full-width)
- Increase chip height to 80px (for readability)
- Progress bar sticky at top (always visible)

**Results Screen**:
- Product cards stack vertically (1 column)
- Lead form full-width
- Case study cards stack vertically

**Navigation**:
- "Back" button always visible (top-left, sticky)
- Swipe gesture support (swipe right = back)

---

## 🔒 Privacy & Compliance

**GDPR Compliance**:
- Checkbox for "Subscribe to updates" must be opt-in (not pre-checked for EU visitors)
- Privacy policy link below form
- "We respect your privacy. No spam, unsubscribe anytime."

**Data Storage**:
- Assessment answers stored in session (not cookies)
- After lead submission, store in CRM
- Option to delete data on request

---

## ✅ Pre-Launch Checklist

- [ ] All question logic tested (all persona/goal/bottleneck combinations)
- [ ] Product recommendation logic verified (spot-check 10 scenarios)
- [ ] Spencer Risk AI appears in relevant scenarios
- [ ] Lead form connected to CRM (test submission)
- [ ] Email validation working (reject Gmail, etc.)
- [ ] Thank you page created (/assessment/thank-you)
- [ ] Shareable URLs working (URL parameters populate results)
- [ ] Mobile responsive (test on iPhone, Android)
- [ ] Analytics events firing (verify in Google Analytics)
- [ ] Load time < 2 seconds (each screen)
- [ ] Back button functional (all screens)
- [ ] "Start Over" resets all state correctly

---

**Document Version**: 1.0  
**Last Updated**: 2026-02-03  
**Owner**: Product & UX Team
