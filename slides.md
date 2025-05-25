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

![width:150px](https://cdn.worldvectorlogo.com/logos/smallpdf-1.svg)

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(244, 63, 94, 0.1), rgba(30, 41, 59, 0.9))" -->

## The Real Cost of Safety Nets

<div class="info-box">
  <span class="highlight">Safety practices have measurable costs</span>
</div>

- Test creation adds **15-35%** to initial development time<sup>1</sup>
- CI/CD setup requires **40+ hours** of engineering investment<sup>2</sup>
- Comprehensive monitoring costs **$15-50** per host monthly<sup>3</sup>
- **68%** of teams report delaying tests due to delivery pressure<sup>4</sup>

<div class="case-study">
<h3>The Balancing Act</h3>
<p>How do we balance immediate delivery with long-term sustainability?</p>
</div>

<div class="footer">
<sup>1</sup> IBM Systems Sciences Institute  <sup>2</sup> GitLab DevSecOps Survey 2021  <sup>3</sup> Datadog & New Relic pricing models  <sup>4</sup> State of Testing Report 2022
</div>

<!-- Speaker notes: Present the real data around the costs of implementing safety practices. This frames the conversation in terms of trade-offs rather than right/wrong choices. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(244, 63, 94, 0.05), rgba(30, 41, 59, 0.7))" -->

## The "Fast Follow" Challenge

```typescript
// Industry research shows:
const actualCompletion = {
  plannedTestFollowUps: 100,
  completedWithin1Sprint: 38,
  completedWithin3Sprints: 57,
  neverCompleted: 24
};

// State of DevOps Report indicates:
// 72% of "fast follows" take 3+ sprints
// 24% never happen at all
```

<div class="info-box">
According to the State of DevOps Report 2022, teams that implement safety practices upfront are 2.4x more likely to meet their delivery targets long-term.<sup>5</sup>
</div>

<div class="footer">
<sup>5</sup> DORA State of DevOps Report 2022  <sup>6</sup> Agile Testing Survey by Ministry of Testing
</div>

<!-- Speaker notes: Use actual industry data to show the gap between intentions and execution while acknowledging the real challenges teams face with "fast follows." -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(74, 222, 128, 0.05), rgba(30, 41, 59, 0.7))" -->

## Business Realities & Practical Constraints

<div class="split-screen">
<div>

### Valid Business Reasons
- Startup survival: **82%** of failed startups cite "ran out of cash"<sup>7</sup>
- Market validation: **35%** of features are rarely/never used<sup>8</sup>
- Competitive pressure: **63%** of businesses prioritize speed<sup>9</sup>
- Resource constraints: Average team has **3.4 engineers**<sup>10</sup>

</div>
<div>

### Practical Solutions
- **Targeted** safety nets
- **Phased** implementation
- **Risk-based** prioritization
- **Measured** trade-offs

</div>
</div>

<div class="footer">
<sup>7</sup> CB Insights Startup Failure Report  <sup>8</sup> Pendo Feature Adoption Report  <sup>9</sup> McKinsey Digital Survey 2021  <sup>10</sup> Stack Overflow Developer Survey 2022
</div>

<!-- Speaker notes: Present balanced facts about business constraints while offering practical middle-ground approaches. This isn't about skipping safety but about being strategic about implementation. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

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

<div class="container">
<div>

### Professional
- 👨‍💻 Staff Software Engineer @ Smallpdf
- 🧾 Focus: Payments infrastructure & monetization
- 🎤 Conference speaker & workshop instructor

### Background
- 🌐 Connected TV, FinTech, Fitness Tech, Monetization/Growth
- 📚 Web performance & engineering leadership

### Community
- 💌 Contributor: Raycast extensions
- 🚀 Founder of ZurichJS

</div>
<div>

![bg right:25% width:180px height:180px](https://placekitten.com/400/400)

**Previous Companies:**
![width:60px](https://cdn.worldvectorlogo.com/logos/smallpdf-1.svg)
![width:60px](https://cdn.worldvectorlogo.com/logos/navro-1.svg)
![width:60px](https://cdn.worldvectorlogo.com/logos/eurosport-2021.svg)
![width:60px](https://cdn.worldvectorlogo.com/logos/discovery-channel-2019.svg)

**@farisaziz12**

</div>
</div>

<!-- Speaker notes: Brief intro - emphasize experience with both rapid shipping and stable systems -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## The Day Everything Went Wrong

```javascript
// A simple config change
setConfig({
  databaseConnection: process.env.NEW_DB_CONNECTION
});

// Deployed Friday at 4:30 PM
// No tests, no monitoring, no rollback plan
```

<div class="info-box">
  <span class="danger">⚠️ 18,000 users affected</span><br>
  <span class="warning">⏱️ 3 hours to detect</span><br>
  <span class="danger">🛑 8 hours to resolve</span>
</div>

<!-- Speaker notes: Tell the story about a real deployment that went sideways because we skipped safety checks. Focus on consequences and detection delay. -->

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## What Is a Safety Net?

<blockquote>
Anything that gives you <strong>confidence</strong> when shipping code
</blockquote>

* Not just tests
* Not just metrics
* Something that catches you when you fall

---

<!-- _backgroundImage: "linear-gradient(to bottom right, rgba(56, 189, 248, 0.05), rgba(30, 41, 59, 0.2))" -->

## Pillars of Confidence

<div class="icon-grid">
  <div class="icon-card">🧪 Testing</div>
  <div class="icon-card">📊 Observability</div>
  <div class="icon-card">🛡️ Resilience</div>
  <div class="icon-card">🔄 Feedback</div>
</div>

<!-- Speaker notes: These four pillars work together to create confidence. We'll explore each in more detail and discuss where they can be optional vs essential. -->

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

<!-- Speaker notes: Observability is about asking questions of your system after it's deployed. Without it, you're flying blind. -->

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
