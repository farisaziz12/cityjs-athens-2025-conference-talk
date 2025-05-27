---
title: "Engineering Without a Safety Net: Where It Works and Where It Hurts"
author: "Faris Aziz"
date: "May 20, 2025"
theme: "default"
marp: true
paginate: true
backgroundColor: "#0F172A"
transition: "slide"
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=JetBrains+Mono:wght@400;700&family=Fira+Code:wght@400;500;600&display=swap');

:root {
  --primary: #38BDF8;
  --secondary: #F471B5;
  --accent: #FCD34D;
  --background: #0F172A;
  --background-accent: #1E293B;
  --text: #F1F5F9;
  --code-bg: #1E293B;
  --code-text: #38BDF8;
  --success: #4ADE80;
  --warning: #FB923C;
  --danger: #F43F5E;
}

section {
  font-family: 'Inter', system-ui, sans-serif;
  background: var(--background);
  color: var(--text);
  padding: 2.5rem;
  background-opacity: 0.1;
  line-height: 1.5;
  letter-spacing: -0.01em;
}

section::after {
  font-size: 0.7rem;
  content: attr(data-marpit-pagination) '/' attr(data-marpit-pagination-total);
  color: rgba(255, 255, 255, 0.4);
}

h1, h2, h3 {
  font-family: 'Inter', system-ui, sans-serif;
  font-weight: 700;
  letter-spacing: -0.03em;
}

h1 {
  font-size: 2.5em;
  color: var(--primary);
  margin-bottom: 0.5em;
  background: linear-gradient(90deg, var(--primary), var(--secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

h2 {
  color: var(--primary);
  font-size: 2em;
  margin-bottom: 1em;
}

h3 {
  color: var(--secondary);
  font-size: 1.5em;
  margin-top: 1.5em;
}

a {
  color: var(--primary);
  text-decoration: none;
  border-bottom: 1px dashed var(--primary);
  padding-bottom: 0.1em;
}

ul, ol {
  margin-left: 1.5rem;
}

li {
  margin-bottom: 0.7em;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin: 1em 0;
  border-radius: 8px;
  overflow: hidden;
}

th {
  background-color: var(--background-accent);
  color: var(--primary);
  padding: 12px;
  text-align: left;
  font-weight: 600;
}

td {
  padding: 10px;
  border-bottom: 1px solid var(--background-accent);
}

code {
  font-family: 'JetBrains Mono', monospace;
  background-color: var(--code-bg);
  color: var(--code-text);
  padding: 2px 5px;
  border-radius: 4px;
  font-size: 0.9em;
}

pre {
  background-color: var(--code-bg);
  border-radius: 8px;
  padding: 1em;
  margin: 1em 0;
  overflow: auto;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.2);
}

pre code {
  background: transparent;
  padding: 0;
  font-size: 0.9em;
  line-height: 1.5;
}

blockquote {
  border-left: 4px solid var(--primary);
  background-color: var(--background-accent);
  padding: 1em;
  margin: 1em 0;
  border-radius: 0 8px 8px 0;
  font-style: italic;
  color: rgba(255, 255, 255, 0.9);
}

.highlight {
  color: var(--accent);
  font-weight: 600;
}

.success {
  color: var(--success);
}

.warning {
  color: var(--warning);
}

.danger {
  color: var(--danger);
}

.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

.footer {
  position: absolute;
  bottom: 1em;
  left: 2.5em;
  right: 2.5em;
  text-align: center;
  font-size: 0.8em;
  color: rgba(255, 255, 255, 0.4);
}

/* Programming Icons */
.icon-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1.25rem;
  margin-top: 1.5rem;
}

.icon-card {
  background-color: var(--background-accent);
  border-radius: 8px;
  padding: 1.25rem;
  text-align: center;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.2);
  transition: transform 0.2s ease-in-out;
}

.icon-card:hover {
  transform: translateY(-5px);
}

/* Lead slides for major sections */
section.lead {
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

section.lead h1 {
  font-size: 3em;
  margin-bottom: 0.3em;
}

section.lead h2 {
  color: var(--secondary);
  font-weight: 600;
  font-size: 1.5em;
  margin-bottom: 2em;
}

/* New special containers */
.info-box {
  background-color: var(--background-accent);
  border-radius: 8px;
  padding: 1.25rem;
  margin: 1.5rem 0;
  border-left: 4px solid var(--primary);
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}

.split-screen {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
  align-items: center;
}

/* Case study styling */
.case-study {
  background-color: var(--background-accent);
  border-radius: 8px;
  padding: 1.5rem;
  margin: 1rem 0;
  border-top: 4px solid var(--secondary);
}

.case-study h3 {
  margin-top: 0;
  margin-bottom: 1rem;
}

/* Tech stack logos */
.tech-logo {
  height: 2.5rem;
  margin: 0 0.75rem;
  opacity: 0.9;
  filter: grayscale(30%);
  transition: all 0.2s ease;
}

.tech-logo:hover {
  opacity: 1;
  filter: grayscale(0%);
  transform: scale(1.1);
}

/* Terminal-style profile section */
.terminal-profile {
  font-family: 'Fira Code', 'JetBrains Mono', monospace;
  line-height: 1.7;
  position: relative;
}

.terminal-profile ul {
  list-style-type: none;
  margin-left: 0;
  padding-left: 0;
}

.terminal-profile li {
  font-size: 1.2em;
  margin-bottom: 0.8em;
  letter-spacing: -0.02em;
}

.profile-photo {
  position: absolute;
  right: 2rem;
  bottom: 8rem;
  width: 150px;
  height: 150px;
  border-radius: 50%;
  border: 4px solid var(--primary);
  box-shadow: 0 4px 20px rgba(56, 189, 248, 0.3);
}

.company-logos {
  position: absolute;
  bottom: 2rem;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1.5rem;
  padding: 1rem;
  background-color: rgba(15, 23, 42, 0.8);
}

.company-logo {
  height: 2.5rem;
  filter: grayscale(30%) brightness(1.5);
  opacity: 0.8;
  transition: all 0.2s ease;
}

.company-logo:hover {
  filter: grayscale(0%) brightness(1.5);
  opacity: 1;
  transform: scale(1.1);
}

/* New profile card styling */
.profile-grid {
  display: grid;
  grid-template-columns: 1fr 200px;
  gap: 1.5rem;
  height: 80%;
}

.profile-cards {
  display: flex;
  flex-direction: column;
}

.profile-card {
  background-color: rgba(30, 41, 59, 0.7);
  padding: 1.5rem;
  border-radius: 0 8px 8px 0;
  margin-bottom: 1.5rem;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.2);
}

.card-primary {
  border-left: 4px solid var(--primary);
}

.card-secondary {
  border-left: 4px solid var(--secondary);
}

.card-accent {
  border-left: 4px solid var(--accent);
}

.card-title {
  margin-top: 0;
  margin-bottom: 0.75rem;
}

.card-title-primary {
  color: var(--primary);
}

.card-title-secondary {
  color: var(--secondary);
}

.card-title-accent {
  color: var(--accent);
}

.emoji-list {
  list-style-type: none;
  padding-left: 0;
  margin-top: 0.5rem;
  font-family: 'Fira Code', monospace;
}

.emoji-item {
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
}

.emoji-icon {
  display: inline-block;
  width: 28px;
  text-align: center;
  margin-right: 10px;
}

.photo-container {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  overflow: hidden;
  border: 4px solid var(--primary);
  box-shadow: 0 0 30px rgba(56, 189, 248, 0.4);
  margin: 0 auto;
}

.profile-photo {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.profile-sidebar {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}

.companies-card {
  background-color: rgba(30, 41, 59, 0.7);
  padding: 0.75rem;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.2);
  margin-top: 1rem;
}

.companies-title {
  font-family: 'Fira Code', monospace;
  font-size: 0.8rem;
  margin-bottom: 0.5rem;
  color: var(--secondary);
}

.companies-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.75rem;
}

.company-logo {
  height: 20px;
  filter: brightness(1.5);
}

.twitter-handle {
  text-align: center;
  font-family: 'Fira Code', monospace;
  font-size: 0.8rem;
  background-color: rgba(30, 41, 59, 0.7);
  padding: 0.5rem 1rem;
  border-radius: 4px;
  color: var(--primary);
  margin-top: 1rem;
}
</style>

<!-- _class: lead -->
<!-- _backgroundImage: "radial-gradient(circle at 80% 80%, rgba(56, 189, 248, 0.15), transparent)" -->

# Engineering Without a Safety Net
## Where It Works and Where It Hurts

Faris Aziz  
Staff Engineer @ Smallpdf
---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(244, 63, 94, 0.1), rgba(30, 41, 59, 0.9))" -->

## "We'll Fix It Later"

<div class="info-box">
  <span class="highlight">The Developer's Safety Net Bypass</span>
</div>

```javascript
// Things we tell ourselves (and others)
const excuses = [
  "I'll add tests in a separate ticket",
  "It's QA's problem now",
  "Just update the snapshot tests",
  "git commit --no-verify",
  "It works on my machine",
  "We can refactor this later",
  "Just ship it, Friday at 4:30pm",
  "We don't have time for tests right now",
  "Let's make it work first, then make it right"
];

// But at what cost?
```

<!-- Speaker notes: Start with relatable developer shortcuts we all use to bypass safety measures. This frames the talk as practical advice for real situations, not an idealistic lecture. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## The Real Question

<div style="display: flex; justify-content: center; align-items: center; position: absolute; top: 0; bottom: 0; left: 0; right: 0; margin: auto; height: auto; padding-top: 2rem;">
  <div class="info-box" style="padding: 3.5rem; text-align: center; background: linear-gradient(135deg, rgba(56, 189, 248, 0.1), rgba(244, 113, 181, 0.1)); border-left: 4px solid transparent; border-image: linear-gradient(to bottom, #38BDF8, #F471B5) 1 100%; max-width: 90%;">
    <h3 style="font-size: 2.4em; line-height: 1.4; background: linear-gradient(90deg, #38BDF8, #F471B5); -webkit-background-clip: text; -webkit-text-fill-color: transparent; margin: 0;">When is bypassing safety measures the right call,<br>and what are the long-term costs?</h3>
  </div>
</div>

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## My Journey Through Safety Nets

<div class="info-box">
  <span class="highlight">From zero users to tens of millions</span> — I've experienced the full spectrum
</div>

```javascript
// My career has exposed me to:
const safetyNetExperiences = [
  "Enterprise products with formal QA processes",
  "Startups obsessed with test coverage metrics",
  "Products with visual & E2E testing only",
  "High-traffic platforms with no safety nets"
];
```

<!-- Speaker notes: Frame that these slides are sharing observations from my career, not prescribing solutions. I've seen what works in different contexts. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## Connected TV Applications

### The Scale
- Streaming the Tokyo Olympics in 2020
- 1.3 billion minutes streamed
- Several hundred engineers
- Hundreds of millions of users

### Manual QA Processes
- **Smoke Testing**: Verifying critical functionality works (login, playback, navigation)
- **Sanity Testing**: Quick verification of new builds before deeper testing
- **Regression Testing**: Ensuring new features don't break existing functionality

<!-- Speaker notes: This was a massive platform where failures during live events would be catastrophic. The formal QA process was necessary given the scale and high-stakes nature of live sports broadcasting. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## Early-Stage Startup

### The Context
- Pre-seed startup with no users yet
- Sub-30 engineers on the team
- Quality gates set by management

### Coverage-Focused Approach
- Unit test coverage benchmarks (90%+)
- Static analysis metrics as gates

<!-- Speaker notes: This startup was building a foundation before having users. Management enforced test coverage as a proxy for quality, often without considering real-world usage scenarios. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## User-Experience Focused Platform

<div class="split-screen">
<div>

### Visual & Functional Testing
- Storybook for UI components
- Snapshot testing for interfaces
- E2E tests for critical flows
- Minimal unit testing

</div>
<div>

<div class="info-box">
  <span class="highlight">Approach</span>: Testing what users experience
</div>

<div class="case-study">
  <p>This team focused on testing user interfaces and journeys rather than implementation details.</p>
</div>

</div>
</div>

<!-- Speaker notes: Consumer web application with rapid UI iterations, feature-driven development, and direct user feedback loops. Describe an approach that prioritized testing the user-facing aspects of the product without suggesting this is inherently better or worse. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## High-Scale, Low-Safety Platform

### The Reality
- Platform generating tens of millions in ARR
- Tens of millions of users per month
- No automated testing suite
- No dedicated QA resources

### Approach
- Developer-led verification
- Product knowledge as primary safety net
- Careful deployment practices

<!-- Speaker notes: Despite the lack of formal safety practices, this platform was highly successful financially. The team relied on deep product knowledge and careful releases, though this approach did come with hidden costs and stress. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(244, 63, 94, 0.05), rgba(30, 41, 59, 0.2))" -->

## Hard Truth: Sometimes It's The Right Call

<div class="icon-grid">
  <div class="icon-card">⏰ Time to market</div>
  <div class="icon-card">💰 Limited resources</div>
  <div class="icon-card">🧪 Validating ideas</div>
  <div class="icon-card">🚀 Startup survival</div>
</div>

<div class="info-box">
"Perfect is the enemy of shipped."
</div>

<!-- Speaker notes: This is the controversial part - sometimes skipping safety nets IS the right business decision. We need to acknowledge this reality before we can have a nuanced conversation about when it makes sense and when it doesn't. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Who Am I?

<div style="position: absolute; top: 20px; right: 20px; max-width: 650px;">
  <img src="https://i.postimg.cc/9MbDYNpZ/Screenshot-2025-05-27-at-22-58-19.png" alt="Company Logos" style="width: 100%;">
</div>

<div style="position: absolute; top: 200px; right: 60px; width: 200px; height: 200px; border-radius: 50%; overflow: hidden; border: 4px solid var(--primary); box-shadow: 0 4px 20px rgba(56, 189, 248, 0.3);">
  <img src="https://i.postimg.cc/Pq5tyLRJ/voxxed-days-zurich-square-pic-profile.jpg" alt="Faris Aziz" style="width: 100%; height: 100%; object-fit: cover;">
</div>

<div style="position: absolute; top: 410px; right: 110px; text-align: center;">
  <strong style="color: var(--primary);">@farisaziz12</strong>
</div>

<div style="padding: 0 300px 0 20px;">

<h3 style="margin-bottom: 0rem;">Current Adventure</h3>
<ul style="margin-top: 0; margin-bottom: 0.7rem; line-height: 1.3;">
  <li>👨‍💻 Staff Software Engineer @ Smallpdf</li>
  <li>🧾 Focus: Payments infrastructure & monetization</li>
</ul>

<h3 style="margin-bottom: 0rem; margin-top: 0.7rem;">Background</h3>
<ul style="margin-top: 0; margin-bottom: 0.7rem; line-height: 1.3;">
  <li>🌐 Connected TV, Monetization/Growth, FinTech, Fitness Tech</li>
  <li>📚 Web performance & engineering leadership</li>
</ul>

<h3 style="margin-bottom: 0rem; margin-top: 0.7rem;">Community</h3>
<ul style="margin-top: 0; margin-bottom: 0.7rem; line-height: 1.3;">
  <li>💌 Open source contributor: Raycast extensions</li>
  <li>🚀 Founder of ZurichJS - premier JavaScript meetup in the Swiss German region</li>
</ul>

</div>

<!-- Speaker notes: Brief intro - emphasize experience with both rapid shipping and stable systems -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## What Is a Safety Net?

<blockquote>
Anything that gives you <strong>confidence</strong> when shipping code
</blockquote>

<div class="icon-grid">
  <div class="icon-card">🧪 <span class="highlight">Testing</span><br>Verifies expected behavior</div>
  <div class="icon-card">📊 <span class="highlight">Metrics</span><br>Measures system health</div>
  <div class="icon-card">🔍 <span class="highlight">Observability</span><br>Provides system visibility</div>
  <div class="icon-card">🛡️ <span class="highlight">Resilience</span><br>Handles unexpected conditions</div>
</div>

<!-- Speaker notes: A safety net is anything that gives us confidence to ship and maintain code. It's a comprehensive system beyond just individual components. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## Safety Net: Automated Testing

<div class="split-screen">
<div style="line-height: 1.1;">

### Test Pyramid
- **Unit**: Isolated functions, pure logic
- **Integration**: Service interactions
- **Component**: UI in isolation
- **E2E**: Complete user flows 
- **System**: Platform with mocks

</div>
<div>

```typescript
// What are we trying to verify?
test('payment processing handles network timeouts', async () => {
  // Arrange: Setup mock payment gateway that times out
  const gateway = mockPaymentGateway({ simulateTimeout: true });
  
  // Act: Process a payment
  const result = await processPayment(gateway, validOrder);
  
  // Assert: Payment is marked for retry, not failed
  expect(result.status).toBe('pending_retry');
  expect(result.error).toContain('timeout');
});
```

</div>
</div>

<!-- Speaker notes: Automated tests provide a safety net that catches issues early and enables confident changes. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## Safety Net: Manual Testing

<div class="split-screen">
<div style="line-height: 1.1;">

### Key Test Types
- **Smoke**: Verify critical paths
- **Sanity**: Quick assessment post-build
- **Regression**: Ensure existing features work
- **Exploratory**: Discover unexpected issues

### When to Apply
- Complex UX flows
- High-risk features
- Pre-release validation

</div>
<div style="line-height: 1.1;">

### Smoke Test Checklist
```
✓ User login
✓ View dashboard
✓ Product listing
✓ Add to cart
✓ Checkout
```

### Regression Focus
```
• Existing features still work
• Edge cases handled
• UI rendering consistent
• Third-party integrations functional
```

</div>
</div>

<!-- Speaker notes: Manual testing complements automation with human judgment and exploratory capabilities. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## Safety Net: Metrics

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1rem;">
  <div>
    <h3 style="margin-top: 0; color: var(--primary);">Core Metrics</h3>
    <ul style="margin-top: 0.5rem;">
      <li><strong>Traffic</strong>: Requests/sec</li>
      <li><strong>Errors</strong>: Rate, distribution</li>
      <li><strong>Latency</strong>: P50, P95, P99</li>
      <li><strong>Saturation</strong>: Resources</li>
      <li><strong>Business</strong>: Conversions</li>
    </ul>
  </div>
  <div>
    <h3 style="margin-top: 0; color: var(--primary);">Key Aspects</h3>
    <ul style="margin-top: 0.5rem;">
      <li>Trend analysis</li>
      <li>Alert thresholds</li>
      <li>Historical baselines</li>
      <li>Correlation</li>
    </ul>
  </div>
</div>

<div style="margin-top: 1rem;">
```javascript
app.use((req, res, next) => {
  const start = Date.now();
  metrics.count('req', {path: req.path});
  res.once('finish', () => metrics.time('resp', Date.now() - start));
  next();
});
```
</div>

<!-- Speaker notes: Metrics provide quantifiable measurements of system behavior and performance. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## Safety Net: Observability

<div class="split-screen">
<div style="line-height: 1.1;">

### Components
- **Logs**: Event records
- **Traces**: Request paths
- **Metrics**: System measurements
- **Context**: Business data correlation

### Value
- Unknown-unknowns detection
- Production debugging
- Root cause analysis

</div>
<div>

```javascript
// Structured logging
logger.info('payment_processed', {
  // Technical context
  request_id: '1234-abcd',
  duration_ms: 342,
  
  // Business context
  user_id: 'user_123',
  amount: 99.99,
  payment_method: 'credit_card',
  
  // Impact data
  is_first_payment: true,
  days_since_signup: 7
});

// Tracing
const span = tracer.startSpan('process_payment');
span.setAttribute('payment_id', id);
// ...processing...
span.end();
```

</div>
</div>

<!-- Speaker notes: Observability answers "why is this happening?" rather than just "what is happening?" -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.9))" -->

## Safety Net: Resilience Patterns

<div class="split-screen">
<div style="line-height: 1.1;">

### Key Patterns
- **Circuit Breakers**: Fail fast
- **Retry with Backoff**: Increasing delays
- **Rate Limiting**: Prevent overload
- **Timeouts**: Don't wait forever
- **Bulkheads**: Isolate failures
- **Fallbacks**: Degraded functionality

</div>
<div>

```javascript
// Circuit breaker example
class PaymentService {
  constructor() {
    this.circuitBreaker = new CircuitBreaker({
      failureThreshold: 5,
      resetTimeout: 30000
    });
  }
  
  async processPayment(order) {
    try {
      return await this.circuitBreaker.execute(
        () => this.gateway.charge(order)
      );
    } catch (error) {
      if (error.type === 'OPEN_CIRCUIT') {
        // Use fallback when circuit open
        return this.queueForLater(order);
      }
      throw error;
    }
  }
}
```

</div>
</div>

<!-- Speaker notes: Resilience patterns help handle failures gracefully and prevent cascading failures. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Pillars of Confidence

<div class="icon-grid">
  <div class="icon-card">🧪 <span class="highlight">Testing</span><br>Verifies behavior matches expectations</div>
  <div class="icon-card">📊 <span class="highlight">Observability</span><br>Makes system behavior visible</div>
  <div class="icon-card">🛡️ <span class="highlight">Resilience</span><br>Handles unexpected conditions</div>
  <div class="icon-card">🔄 <span class="highlight">Feedback</span><br>Accelerates learning cycles</div>
</div>

<div class="info-box">
These pillars work together to create a <span class="highlight">comprehensive safety system</span> - the absence of any one weakens your overall confidence when shipping.
</div>

<!-- Speaker notes: These four pillars work together to create confidence. Each pillar has different appropriate implementations depending on context, and they all complement each other. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Building Complete Confidence

<div class="split-screen">
<div>

### Individual Components
<div class="info-box warning">
  <span class="highlight">Tests Alone</span> ➡️ Know if it works, but not in production
</div>
<div class="info-box warning">
  <span class="highlight">Metrics Alone</span> ➡️ Know something's wrong, but not why
</div>
<div class="info-box warning">
  <span class="highlight">Resilience Alone</span> ➡️ Survive failures, but not learn from them
</div>

</div>
<div>

### Combined Effect
<div class="info-box success">
  <span class="highlight">Comprehensive Safety</span> ➡️ Confidence to ship and evolve
  <ul style="margin-top: 0.5rem;">
    <li>Verify behavior</li>
    <li>Detect issues quickly</li>
    <li>Recover gracefully</li>
    <li>Learn and improve</li>
  </ul>
</div>

</div>
</div>

<!-- Speaker notes: Individual safety practices are insufficient alone. Complete confidence comes from combining multiple approaches based on your specific context and needs. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Pillar 1: Automated Testing

```typescript
// What are we trying to verify?
test('payment processing handles network timeouts', async () => {
  // Arrange: Setup mock payment gateway that times out
  const gateway = mockPaymentGateway({ simulateTimeout: true });
  
  // Act: Process a payment
  const result = await processPayment(gateway, validOrder);
  
  // Assert: Payment is marked for retry, not failed
  expect(result.status).toBe('pending_retry');
  expect(result.error).toContain('timeout');
});
```

<!-- Speaker notes: Testing isn't about coverage percentage - it's about verification of critical paths and behavior under different conditions. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Tests Are Insurance Policies

| Test Type | Setup Cost | Maintenance | Value | When to Skip |
|-----------|------------|-------------|-------|--------------|
| Unit      | Low        | Low         | Medium | Non-critical business logic |
| Integration | Medium   | Medium      | High  | Simple CRUD operations |
| E2E       | High       | High        | Highest | Early prototypes |

<!-- Speaker notes: Different types of tests have different ROI. Tests are investments with returns based on criticality. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Pillar 2: Observability

<div class="split-screen">
<div>

* <span class="highlight">Logs</span>: What happened
* <span class="highlight">Metrics</span>: How many & how often  
* <span class="highlight">Traces</span>: Request path & dependencies

</div>
<div>

```javascript
// Structured logging with context
logger.info({
  event: 'payment_processed',
  orderId: order.id,
  userId: user.id,
  amount: payment.amount,
  processor: payment.gateway,
  durationMs: timer.elapsed()
});
```

</div>
</div>

<!-- Speaker notes: Observability is about understanding your system's internal state through its outputs. It goes beyond monitoring to answer the question "why is this happening?" rather than just "what is happening?" -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(244, 63, 94, 0.05), rgba(30, 41, 59, 0.2))" -->

## The Cost of Flying Blind

<div class="info-box">
  <span class="danger">⏱️ Average incident detection: 3 hours</span><br>
  <span class="warning">🔍 Time to root cause: 2.5x longer</span><br>
  <span class="danger">👥 Customer-reported issues: 68% higher</span>
</div>

```javascript
// Debugging without observability
function handleError(error) {
  console.error("Something went wrong");
  // What went wrong? Who was affected?
  // When did it start? Why did it happen?
}
```

<!-- Speaker notes: These numbers are industry averages for systems without proper observability. The cost compounds with each incident. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Pillar 3: Resilience Patterns

```javascript
// Circuit breaker pattern
class PaymentGateway {
  async processPayment(order) {
    if (this.circuitBreaker.isOpen()) {
      return this.fallbackPaymentProcessor(order);
    }
    
    try {
      const result = await this.makePaymentRequest(order);
      this.circuitBreaker.recordSuccess();
      return result;
    } catch (error) {
      this.circuitBreaker.recordFailure();
      throw error;
    }
  }
}
```

<!-- Speaker notes: Resilience patterns are about designing for failure. They're the safety net when things inevitably break. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Common Resilience Patterns

<div class="icon-grid">
  <div class="icon-card">⏱️ Retry with backoff</div>
  <div class="icon-card">🔌 Circuit breakers</div>
  <div class="icon-card">🔄 Fallbacks</div>
  <div class="icon-card">🔒 Bulkheads</div>
</div>

<!-- Speaker notes: These patterns are fundamental but often skipped in initial implementation. They're much harder to add later. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Pillar 4: Fast Feedback Loops

<div class="split-screen">
<div>

* Local dev environment 
* CI pipeline speed
* Feature flags
* Canary deployments

</div>
<div>

```javascript
// Feature flag for controlled rollout
if (featureFlag.isEnabled('new-payment-flow', user.id)) {
  return renderNewPaymentUI();
} else {
  return renderExistingPaymentUI();
}
```

</div>
</div>

<!-- Speaker notes: Fast feedback loops let you detect and fix issues quickly. They're the difference between a 5-minute fix and a 5-hour crisis. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Context Matters

<div class="icon-grid">
  <div class="icon-card">🔑 <span class="highlight">Feature criticality</span></div>
  <div class="icon-card">👥 <span class="highlight">User impact</span></div>
  <div class="icon-card">💰 <span class="highlight">Business impact</span></div>
  <div class="icon-card">🚀 <span class="highlight">Platform maturity</span></div>
</div>

<!-- Speaker notes: Not all code is created equal. Context determines how much safety is needed. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Decision Matrix

|                | Low Impact         | High Impact                |
|----------------|--------------------|-----------------------------|
| **Low Risk**   | <span class="success">Minimal safety</span> | <span class="warning">Moderate safety</span> |
| **High Risk**  | <span class="warning">Moderate safety</span> | <span class="danger">Maximum safety</span> |

<!-- Speaker notes: This simple matrix helps teams decide where to invest in safety nets. High risk + high impact demands maximum safety. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(74, 222, 128, 0.05), rgba(30, 41, 59, 0.2))" -->

## Where You Can Cut Corners (Safely)

<div class="split-screen">
<div>

* Internal admin tools
* Early-stage experiments
* Non-critical user flows
* Static content
* Infrequently used features

</div>
<div>

```javascript
// Acceptable for low-risk features
function experimentalFeature() {
  try {
    // New code with minimal testing
    return newImplementation();
  } catch (error) {
    // Fallback to old behavior
    return existingImplementation();
  }
}
```

</div>
</div>

<!-- Speaker notes: These are areas where the blast radius is limited and detection/recovery is straightforward. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(244, 63, 94, 0.05), rgba(30, 41, 59, 0.2))" -->

## Where It Hurts (Fast)

<div class="info-box danger">
  <span class="highlight">Payment processing</span> •
  <span class="highlight">Authentication systems</span> •
  <span class="highlight">Data migrations</span> •
  <span class="highlight">Core business workflows</span> •
  <span class="highlight">High-volume API endpoints</span>
</div>

```javascript
// Don't skip tests here!
async function processPayment(order, paymentDetails) {
  // Critical business logic
  // Affects revenue directly
  // Hard to debug issues
  // Customer trust at stake
}
```

<!-- Speaker notes: These are critical paths where failures have immediate, severe consequences. Skimping on safety nets here is extremely costly. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## What Is Technical Debt, Really?

<blockquote>
Technical debt is the <span class="highlight">accumulated cost</span> of shortcuts that seemed reasonable at the time
</blockquote>

* Not all debt is bad
* Some debt is strategic
* Compound interest applies

<!-- Speaker notes: Technical debt isn't just "bad code" - it's the increased cost of change over time due to past decisions. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Debt Accumulation Timeline

```
Time →
│
├─ Day 1: Skip tests to ship faster (+1 debt)
│
├─ Month 3: Work around untested code (+2 debt)
│
├─ Month 6: Can't refactor due to uncertainty (+5 debt)
│
├─ Year 1: Rewrite required (+20 debt)
```

<!-- Speaker notes: Debt compounds over time. What starts as a small shortcut can lead to massive costs later. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(74, 222, 128, 0.05), rgba(30, 41, 59, 0.2))" -->

## Shortcuts That Age Well

<div class="icon-grid">
  <div class="icon-card">🔍 <span class="highlight">Simplified first version (YAGNI)</span></div>
  <div class="icon-card">🎯 <span class="highlight">Targeted test coverage</span></div>
  <div class="icon-card">📝 <span class="highlight">Manual processes first</span></div>
  <div class="icon-card">📊 <span class="highlight">Basic monitoring</span></div>
</div>

<!-- Speaker notes: These shortcuts are reversible and have manageable long-term consequences. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(244, 63, 94, 0.05), rgba(30, 41, 59, 0.2))" -->

## Shortcuts That Blow Up Later

```javascript
// Shortcut: Hard-coded configuration
const API_KEY = "abc123"; // We'll make this configurable later

// Shortcut: Magic numbers
if (users.length > 1000) { // Why 1000?
  enablePagination();
}

// Shortcut: Inconsistent error handling
try {
  // Critical operation
} catch (e) {
  console.log("Error occurred"); // No details, no reporting
}
```

<!-- Speaker notes: These patterns create invisible constraints that limit future changes and create unexpected failures. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(244, 63, 94, 0.05), rgba(30, 41, 59, 0.2))" -->

## Case Study: The Database Migration

<div class="case-study">
  <h3>Scenario: MongoDB → PostgreSQL</h3>
  
  <p><strong>Shortcuts taken:</strong></p>
  <ul>
    <li>No comprehensive test suite</li>
    <li>Limited observability</li>
    <li>No rollback plan</li>
    <li>Single big-bang migration</li>
  </ul>
  
  <p><strong>Result:</strong> <span class="danger">36-hour outage, data inconsistencies, lost revenue</span></p>
</div>

<!-- Speaker notes: Share the specific details of a real migration gone wrong. Emphasize how proper safety nets would have prevented or minimized the impact. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(74, 222, 128, 0.05), rgba(30, 41, 59, 0.2))" -->

## Case Study: Feature Flags Done Right

<div class="case-study">
  <h3>Scenario: Payment System Rewrite</h3>
  
  <p><strong>Safety nets implemented:</strong></p>
  <ul>
    <li>Feature flag with 1% initial traffic</li>
    <li>Comprehensive monitoring</li>
    <li>Side-by-side validation with old system</li>
    <li>Automated rollback triggers</li>
  </ul>
  
  <p><strong>Result:</strong> <span class="success">8 bugs caught before full rollout, zero customer impact</span></p>
</div>

<!-- Speaker notes: Contrast with a success story where proper safety nets were implemented, even though the timeline was aggressive. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## How to Think About Risk

<div class="icon-grid">
  <div class="icon-card">💥 <span class="highlight">Blast Radius</span><br>How many users affected?</div>
  <div class="icon-card">🔍 <span class="highlight">Detectability</span><br>How quickly will we know?</div>
  <div class="icon-card">⏪ <span class="highlight">Recoverability</span><br>How fast can we fix it?</div>
  <div class="icon-card">💰 <span class="highlight">Business Impact</span><br>What's the cost of failure?</div>
</div>

<!-- Speaker notes: This framework helps teams make conscious decisions about risk, rather than accidental ones. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Principles for Pragmatic Engineering

* <span class="highlight">Start small</span>: Minimal but effective safety nets
* <span class="highlight">Focus on critical paths</span>: Not all code needs the same protection
* <span class="highlight">Automate guardrails</span>: Make safety the easy choice
* <span class="highlight">Measure debt</span>: Track the cost of shortcuts
* <span class="highlight">Incremental improvement</span>: Better safety nets over time

<!-- Speaker notes: These principles help balance speed and safety without slowing teams down unnecessarily. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Risk Assessment Checklist

```javascript
// Before deploying, ask:
const safetyChecklist = {
  testing: "Do we have tests for critical paths?",
  monitoring: "Will we know if this breaks?",
  rollback: "Can we undo this change quickly?",
  blast_radius: "How many users could be affected?",
  detection: "How will we know if something goes wrong?",
  recovery: "What's our plan if this fails?"
};
```

<!-- Speaker notes: A simple checklist helps teams make conscious risk decisions rather than accidental ones. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Tools That Help

<div>
  <img class="tech-logo" alt="Jest" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/jest/jest-plain.svg">
  <img class="tech-logo" alt="Cypress" src="https://raw.githubusercontent.com/cypress-io/cypress-icons/master/src/logo/cypress-io-logo-round.svg">
  <img class="tech-logo" alt="Prometheus" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/prometheus/prometheus-original.svg">
  <img class="tech-logo" alt="Grafana" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/grafana/grafana-original.svg">
  <img class="tech-logo" alt="Datadog" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/datadog/datadog-original.svg">
</div>

<div class="info-box">
  <span class="highlight">Testing</span>: Jest, Cypress, Playwright<br>
  <span class="highlight">Observability</span>: Datadog, New Relic, OpenTelemetry<br>
  <span class="highlight">Resilience</span>: Polly, Hystrix, custom middleware<br>
  <span class="highlight">Deployment</span>: Feature flags, canary releases, GitOps
</div>

<!-- Speaker notes: These tools make implementing safety nets easier and more effective. The right tool can drastically reduce the cost of safety. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Key Takeaways

1. Safety nets provide <span class="highlight">confidence</span>, not bureaucracy
2. Context determines necessary safety level
3. Some shortcuts are strategic, others are reckless
4. Technical debt compounds over time
5. Invest in safety proportional to risk

<!-- Speaker notes: Reiterate the main points and emphasize that this is about pragmatic, context-aware decisions. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Conclusion: Finding The Balance

<div class="info-box">
  <span class="highlight">There's no single right approach – context matters</span>
</div>

* Make **intentional** decisions about safety nets
* Focus on **critical paths** that impact users and revenue
* Build a **culture** where safety and speed coexist
* Start with **minimal** but effective guardrails
* **Improve** incrementally over time

<div class="case-study">
<h3>Remember</h3>
<p>The goal isn't perfection – it's delivering value <span class="highlight">sustainably</span></p>
</div>

---

<!-- _class: lead -->
<!-- _backgroundImage: "radial-gradient(circle at 80% 80%, rgba(56, 189, 248, 0.15), transparent)" -->

## Q&A

Thanks—let's talk.  
Connect: @farisaziz12 • faris@smallpdf.com

![width:150px](https://cdn.worldvectorlogo.com/logos/smallpdf-1.svg)

<!-- Speaker notes: Be prepared for questions about specific technologies, team dynamics, and how to implement these practices incrementally. -->
