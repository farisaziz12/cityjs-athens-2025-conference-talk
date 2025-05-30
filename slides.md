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

## The Fast Follow Fallacy

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

<!-- Speaker notes: These four pillars work together to create confidence. Each pillar has different appropriate implementations depending on context, and they all complement each other. Fast feedback loops are critical - they include local dev environments, CI pipeline speed, feature flags, and canary deployments. For example, feature flags let you control rollout with code like:
```javascript
// Feature flag for controlled rollout
if (featureFlag.isEnabled('new-payment-flow', user.id)) {
  return renderNewPaymentUI();
} else {
  return renderExistingPaymentUI();
}
```
Fast feedback loops let you detect and fix issues quickly. They're the difference between a 5-minute fix and a 5-hour crisis. -->

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

## Let's Talk About DORA

<div style="display: flex; justify-content: center; align-items: center; height: 70%;">
  <img src="https://static.wixstatic.com/media/9110e9_4e00d633a1bb42b3b03817695c045a5b~mv2.jpg/v1/fill/w_568,h_318,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/9110e9_4e00d633a1bb42b3b03817695c045a5b~mv2.jpg" alt="Dora the Explorer" style="max-height: 400px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.3);">
</div>

<!-- Speaker notes: Start with this joke about Dora the Explorer before transitioning to the real DORA metrics. "Now let's talk about DORA... Oh wait, not that DORA!" This sets a lighter tone before diving into the technical metrics. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## DORA Metrics: Measuring Engineering Performance

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem;">
  <div>
    <h3 style="margin-top: 0; color: var(--primary);">Key Metrics</h3>
    <ul style="margin-top: 0.5rem;">
      <li><strong>Deployment Frequency</strong>: How often you deploy to production</li>
      <li><strong>Lead Time for Changes</strong>: Time from commit to production</li>
      <li><strong>Mean Time to Recovery</strong>: How long to restore service</li>
      <li><strong>Change Failure Rate</strong>: % of deployments causing failure</li>
    </ul>
  </div>
  <div>
    <h3 style="margin-top: 0; color: var(--primary);">Performance Levels</h3>
    <div style="font-size: 0.85em; width: 100%;">
      <table style="width: 100%; border-collapse: collapse; font-size: 0.9em;">
        <thead>
          <tr style="border-bottom: 1px solid rgba(255,255,255,0.1);">
            <th style="text-align: left; padding: 0.4rem;">Level</th>
            <th style="text-align: left; padding: 0.4rem;">Deployment Frequency</th>
            <th style="text-align: left; padding: 0.4rem;">Lead Time</th>
            <th style="text-align: left; padding: 0.4rem;">MTTR</th>
            <th style="text-align: left; padding: 0.4rem;">Change Failure Rate</th>
          </tr>
        </thead>
        <tbody>
          <tr style="border-bottom: 1px solid rgba(255,255,255,0.1);">
            <td style="padding: 0.4rem;"><strong>Elite</strong></td>
            <td style="padding: 0.4rem;">Multiple/day</td>
            <td style="padding: 0.4rem;">< 1 day</td>
            <td style="padding: 0.4rem;">< 1 hour</td>
            <td style="padding: 0.4rem;">0-15%</td>
          </tr>
          <tr style="border-bottom: 1px solid rgba(255,255,255,0.1);">
            <td style="padding: 0.4rem;"><strong>High</strong></td>
            <td style="padding: 0.4rem;">1/day-1/week</td>
            <td style="padding: 0.4rem;">1 day-1 week</td>
            <td style="padding: 0.4rem;">< 1 day</td>
            <td style="padding: 0.4rem;">16-30%</td>
          </tr>
          <tr style="border-bottom: 1px solid rgba(255,255,255,0.1);">
            <td style="padding: 0.4rem;"><strong>Medium</strong></td>
            <td style="padding: 0.4rem;">1/week-1/month</td>
            <td style="padding: 0.4rem;">1 week-1 month</td>
            <td style="padding: 0.4rem;">1 day-1 week</td>
            <td style="padding: 0.4rem;">31-45%</td>
          </tr>
          <tr>
            <td style="padding: 0.4rem;"><strong>Low</strong></td>
            <td style="padding: 0.4rem;">1/month-1/6 months</td>
            <td style="padding: 0.4rem;">1-6 months</td>
            <td style="padding: 0.4rem;">1 week+</td>
            <td style="padding: 0.4rem;">46-60%</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</div>

<!-- Speaker notes: DORA metrics provide objective ways to measure engineering performance. They're backed by research across thousands of organizations and show strong correlation with business outcomes. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(244, 63, 94, 0.05), rgba(30, 41, 59, 0.2))" -->

## The Cost of Flying Blind

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem;">
  <div>
    <h3 style="margin-top: 0; color: var(--danger);">Business Impact</h3>
    <div style="background: rgba(30, 41, 59, 0.5); padding: 1rem; border-radius: 8px; margin-top: 0.5rem;">
      <p style="margin: 0 0 0.5rem 0;"><strong>$10M ARR Business</strong></p>
      <ul style="margin: 0; padding-left: 1.2rem;">
        <li>$1,141 revenue per hour</li>
        <li>99.9% uptime = 8.76 hours downtime/year</li>
        <li><span class="danger">$10,000+ direct cost per year</span></li>
      </ul>
    </div>
    <div style="background: rgba(30, 41, 59, 0.5); padding: 1rem; border-radius: 8px; margin-top: 0.75rem;">
      <p style="margin: 0 0 0.5rem 0;"><strong>Change Failure Impact</strong></p>
      <ul style="margin: 0; padding-left: 1.2rem;">
        <li>5% failure rate × 3.5 hour MTTR</li>
        <li>100 deploys/year = 17.5 hours downtime</li>
        <li><span class="danger">$20,000+ annual failure cost</span></li>
      </ul>
    </div>
  </div>
  <div>
    <h3 style="margin-top: 0; color: var(--danger);">Hidden Costs</h3>
    <ul style="margin-top: 0.5rem;">
      <li><strong>Customer Trust</strong>: ~30% will switch services after one bad experience</li>
      <li><strong>Engineering Time</strong>: Incident response diverts from new features</li>
      <li><strong>Team Morale</strong>: Firefighting increases burnout</li>
      <li><strong>Opportunity Cost</strong>: Slower development velocity</li>
    </ul>
  </div>
</div>

<!-- Speaker notes: These calculations show the real business impact of poor observability and high change failure rates. The hidden costs often far outweigh the direct revenue loss. For a $10M ARR business, poor safety nets can easily cost $100,000+ annually when all factors are considered. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## The Language of Confidence

<div class="info-box">
  <span class="highlight">Words reveal our confidence level in our systems</span>
</div>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem;">
  <div style="background: rgba(244, 63, 94, 0.1); padding: 1rem; border-radius: 8px; border-left: 4px solid var(--danger);">
    <h3 style="margin-top: 0; color: var(--danger);">Low Confidence</h3>
    <ul style="margin-top: 0.5rem;">
      <li>"It <em>should</em> work this way..."</li>
      <li>"I <em>think</em> this is what happens..."</li>
      <li>"I <em>have a feeling</em> this is the issue..."</li>
      <li>"Let's just try it and see what happens..."</li>
    </ul>
  </div>
  <div style="background: rgba(74, 222, 128, 0.1); padding: 1rem; border-radius: 8px; border-left: 4px solid var(--success);">
    <h3 style="margin-top: 0; color: var(--success);">High Confidence</h3>
    <ul style="margin-top: 0.5rem;">
      <li>"This is how it works..."</li>
      <li>"Our metrics show..."</li>
      <li>"The logs indicate..."</li>
      <li>"I can see from the traces that..."</li>
    </ul>
  </div>
</div>

<!-- Speaker notes: The language we use reflects our confidence in our systems. When we use tentative language, it signals a lack of visibility and understanding. The pillars of confidence give us the tools to speak with certainty about our systems. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## "We Don't Deploy on Friday..."

<div style="margin-bottom: 1rem;">
  <div class="info-box warning">
    <span class="highlight">When your team avoids deploying on "Thursday+1"...</span>
  </div>
</div>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem;">
  <div>
    <h3 style="margin-top: 0; color: var(--primary);">Code Freeze Symptoms</h3>
    <ul style="margin-top: 0.5rem;">
      <li>No deployments on Fridays</li>
      <li>Freeze periods before holidays</li>
      <li>Blackout windows for "critical times"</li>
      <li>Delayed releases due to fear</li>
    </ul>
  </div>
</div>

<!-- Speaker notes: Code freezes are a symptom, not a solution. When teams avoid deploying at certain times, it reveals cracks in their safety nets. The real solution is to fix the pillars that give you confidence, not to avoid deploying. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

# Where You Can Cut Corners (Safely)

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
  <ul style="margin: 0.5rem 0; padding-left: 1.5rem;">
    <li><span class="highlight">Payment processing</span></li>
    <li><span class="highlight">Authentication systems</span></li>
    <li><span class="highlight">Data migrations</span></li>
    <li><span class="highlight">Core business workflows</span></li>
    <li><span class="highlight">High-volume API endpoints</span></li>
  </ul>
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

## Deployment Strategies for Confidence

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem;">
  <div>
    <h3 style="margin-top: 0; color: var(--primary);">Trunk-Based Development</h3>
    <ul style="margin-top: 0.5rem;">
      <li>Short-lived branches (< 1 day)</li>
      <li>Frequent merges to main</li>
      <li>Feature flags for WIP code</li>
      <li>CI for every commit</li>
    </ul>
  </div>
  <div>
    <h3 style="margin-top: 0; color: var(--primary);">Atomic Deployments</h3>
    <ul style="margin-top: 0.5rem;">
      <li>Small, self-contained changes</li>
      <li>Lower cognitive load to review</li>
      <li>Easier to test thoroughly</li>
      <li>Simpler to rollback if needed</li>
    </ul>
  </div>
</div>

<div class="info-box success" style="margin-top: 1rem;">
  <span class="highlight">Small changes → Small blast radius → Higher confidence</span>
</div>

<!-- Speaker notes: These deployment patterns directly support your safety nets by making changes smaller, more predictable, and easier to verify. The smaller the change, the smaller the potential blast radius of any issue. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Feature Flags: Getting Them Right Makes All The Difference

<div class="split-screen">
<div>

### Key Principles
- Flag OFF = 100% original code path
- Flag ON = new implementation
- Duplicate code is your friend
- Never modify existing code paths
- Gradual rollout with percentage controls

</div>
<div>

```javascript
function processCheckout(order) {
  // Feature flag pattern that preserves the original code
  if (featureFlags.isEnabled('new-checkout-flow', { 
    userId: order.userId,
    percentage: 5 // Start with just 5% of traffic
  })) {
    return newCheckoutImplementation(order);
  } else {
    // Original code completely untouched
    return originalCheckoutImplementation(order);
  }
}
```

</div>
</div>

<div class="info-box success" style="margin-top: 0.5rem;">
  <span class="highlight">Properly implemented feature flags = instant rollback capability</span>
</div>

<!-- Speaker notes: Feature flags are powerful because they allow you to ship code to production without activating it. The key is that the OFF state must leave the original code completely untouched - don't be afraid of some code duplication here as it's temporary and ensures safety. Start with a small percentage rollout and monitor carefully before increasing. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Conclusion: Finding The Balance

<div class="info-box" style="text-align: center; padding: 1.5rem; max-width: 80%; margin: 0 auto 2rem auto;">
  <span class="highlight" style="font-size: 1.4em;">There's no single right approach – context matters</span>
</div>

<div style="display: flex; justify-content: center;">
  <ul style="list-style-type: none; padding: 0; max-width: 80%;">
    <li style="margin-bottom: 1rem; font-size: 1.2em;">
      <span class="highlight">🎯 Targeted safety</span>: Invest where it matters most
    </li>
    <li style="margin-bottom: 1rem; font-size: 1.2em;">
      <span class="highlight">📈 Strategic shortcuts</span>: Know when to take them
    </li>
    <li style="margin-bottom: 1rem; font-size: 1.2em;">
      <span class="highlight">🔄 Incremental improvement</span>: Build better over time
    </li>
    <li style="margin-bottom: 1rem; font-size: 1.2em;">
      <span class="highlight">🗣️ Clear communication</span>: Language reflects confidence
    </li>
  </ul>
</div>

<div style="text-align: center; margin-top: 1.5rem; font-style: italic; color: var(--primary); font-size: 1.3em;">
  "The goal isn't perfection – it's delivering value sustainably"
</div>

---

<!-- _class: lead -->
<!-- _backgroundImage: "radial-gradient(circle at 80% 80%, rgba(56, 189, 248, 0.15), transparent)" -->

## Thank you!

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; margin-top: 2rem;">
  <div style="display: flex; flex-direction: column; align-items: center; text-align: center;">
    <div style="width: 200px; height: 200px; display: flex; justify-content: center; align-items: center;">
      <img src="https://i.postimg.cc/2yGKxQLQ/frame-12.png" alt="Connect QR Code" style="max-width: 100%; max-height: 100%; border-radius: 8px;">
    </div>
    <p style="margin: 0;">Connect with me<br><span style="color: var(--primary); font-weight: bold;">@farisaziz12</span></p>
  </div>
  <div style="display: flex; flex-direction: column; align-items: center; text-align: center;">
    <div style="width: 200px; height: 200px; display: flex; justify-content: center; align-items: center;">
      <img src="https://i.postimg.cc/NF7Jb1Ss/frame-13.png" alt="Feedback QR Code" style="max-width: 100%; max-height: 100%; border-radius: 8px;">
    </div>
    <p style="margin: 0;">Session Feedback<br><span style="color: var(--secondary); font-weight: bold;">Let me know your thoughts!</span></p>
  </div>
</div>

<!-- Speaker notes: Thank the audience and encourage them to connect with you on social media or provide feedback through the QR codes. Be ready for questions on specific technologies, team dynamics, and how to implement these practices incrementally. -->
