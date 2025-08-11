---
layout: home
hero:
  name: "Cronflow"
  text: "The Fastest Code-First Workflow Automation Engine"
  tagline: Built with Rust + Bun for unparalleled performance. Replace limited visual tools with flexible, fast code-first workflows.
  image:
    src: /code.png
    alt: Cronflow Code
  actions:
    - theme: brand
      text: Get Started
      link: /guide/
    - theme: alt
      text: View on GitHub
      link: https://github.com/dali-benothmen/cronflow
    - theme: alt
      text: API Reference
      link: /api/

features:
  - icon: 🚀
    title: Lightning Fast
    details: 90x faster than traditional tools. Process 10,000+ records in 2ms with true concurrency.
  - icon: 💾
    title: Memory Efficient
    details: Only 0.49MB memory per step vs 500MB+ in traditional tools. 10x less memory consumption.
  - icon: 💰
    title: Zero Cost
    details: Replace $50/month n8n servers with a single npm package. Zero infrastructure costs.
  - icon: 🔧
    title: Code-First
    details: Version control your workflows with Git. Express complex logic with TypeScript and Rust.
  - icon: ⚡
    title: Production Ready
    details: Built with Rust for reliability and Bun for speed. Ready for production in 30 seconds.
  - icon: 🎯
    title: Developer Friendly
    details: Full TypeScript support, comprehensive API, and extensive examples.
---

<div class="developer-experience-section">
  <div class="dx-content">
    <div class="dx-text">
      <h2>Developer Experience That Actually Works</h2>
      <p>
        Stop fighting with limited visual interfaces. With Cronflow, you write real code that does exactly what you need. 
        No more "integration doesn't support this endpoint" or "this transformation isn't available" frustrations.
      </p>
    </div>
    <div class="dx-features-container">
      <div class="dx-features">
        <div class="dx-feature">
          <div class="dx-feature-icon icon" data-v-e8895942="">🔧</div>
          <div class="dx-feature-content">
            <h4>Zero Integration Limits</h4>
            <p>Build any integration yourself. Connect to any API, database, or service without waiting for platform updates.</p>
          </div>
        </div>
        <div class="dx-feature">
          <div class="dx-feature-icon icon" data-v-e8895942="">⚡</div>
          <div class="dx-feature-content">
            <h4>True Flexibility</h4>
            <p>Implement complex business logic, custom transformations, and advanced error handling that visual tools can't handle.</p>
          </div>
        </div>
        <div class="dx-feature">
          <div class="dx-feature-icon icon" data-v-e8895942="">🚀</div>
          <div class="dx-feature-content">
            <h4>Production Ready</h4>
            <p>Full TypeScript support, proper testing, version control, and deployment pipelines. Built for real development teams.</p>
          </div>
        </div>
      </div>
    </div>
    <div class="dx-terminal">
      <div class="terminal" id="dx-terminal">
        <div class="terminal-header">
          <span class="dot red"></span>
          <span class="dot yellow"></span>
          <span class="dot green"></span>
        </div>
        <div class="terminal-body">
          <div class="output">
            <span id="dx-typedText"></span><span class="cursor" id="dx-cursor"></span>
          </div>
          <div class="press-enter-overlay" id="dx-pressEnterOverlay">
            <div class="press-enter" id="dx-pressEnter">[ Press Enter ]</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<style>
/* Override VitePress default colors with green theme */
:root {
  --vp-c-brand: #22c55e;
  --vp-c-brand-light: #4ade80;
  --vp-c-brand-lighter: #86efac;
  --vp-c-brand-dark: #16a34a;
  --vp-c-brand-darker: #15803d;
  --vp-c-brand-highlight: #22c55e;
  --vp-c-brand-hover: #4ade80;
  --vp-c-brand-active: #16a34a;
  
  /* Override indigo colors with green variations */
  --vp-c-indigo-1: #86efac;
  --vp-c-indigo-2: #4ade80;
  --vp-c-indigo-3: #22c55e;
  
  /* Override purple colors with green variations */
  --vp-c-purple-1: #bbf7d0;
  --vp-c-purple-2: #86efac;
  --vp-c-purple-3: #4ade80;
}

/* Override button colors specifically */
.VPButton.brand {
  background-color: #22c55e !important;
  border-color: #22c55e !important;
}

.VPButton.brand:hover {
  background-color: #4ade80 !important;
  border-color: #4ade80 !important;
}

.VPButton.alt {
  border-color: #22c55e !important;
  color: #22c55e !important;
}

.VPButton.alt:hover {
  background-color: #22c55e !important;
  color: white !important;
}

/* Override any remaining blue colors */
.VPHomeHero .actions .VPButton.brand {
  background-color: #22c55e !important;
  border-color: #22c55e !important;
}

.VPHomeHero .actions .VPButton.brand:hover {
  background-color: #4ade80 !important;
  border-color: #4ade80 !important;
}

/* Hero background effects */
:root {
  --vp-home-hero-image-background-image: linear-gradient(
    -45deg,
    rgba(34, 197, 94, 0.1) 0%,
    rgba(34, 197, 94, 0.05) 25%,
    rgba(34, 197, 94, 0.1) 50%,
    rgba(34, 197, 94, 0.05) 75%,
    rgba(34, 197, 94, 0.1) 100%
  );
  --vp-home-hero-image-filter: blur(120px);
}

.VPHomeHero .image {
  position: relative;
}

.VPHomeHero .image::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(
    circle at center,
    rgba(34, 197, 94, 0.15) 0%,
    rgba(34, 197, 94, 0.1) 30%,
    rgba(34, 197, 94, 0.05) 60%,
    transparent 100%
  );
  border-radius: 50%;
  filter: blur(80px);
  z-index: -1;
}

.VPHomeHero .image::after {
  content: '';
  position: absolute;
  top: 20%;
  right: -30%;
  width: 60%;
  height: 60%;
  background: linear-gradient(
    45deg,
    rgba(34, 197, 94, 0.1) 0%,
    rgba(34, 197, 94, 0.05) 50%,
    transparent 100%
  );
  border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
  filter: blur(60px);
  z-index: -1;
}

/* Enhanced white box container for the image */
.VPHomeHero .image img {
  z-index: 1;
  background: white;
  border-radius: 20px;
  transform: rotate(5deg);
  top: 15%;
  left: 45%;
  box-shadow: 
    0 20px 60px rgba(0, 0, 0, 0.15),
    0 8px 32px rgba(0, 0, 0, 0.1),
    0 0 40px rgba(34, 197, 94, 0.3),
    0 0 80px rgba(34, 197, 94, 0.2);
  padding: 20px;
  border: 3px solid #22c55e;
}

/* Performance Benchmark Styles - Static Only (No Animations) */
.performance-benchmark {
  margin: 2rem auto;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 
      0 20px 60px rgba(0, 0, 0, 0.1),
      0 8px 32px rgba(0, 0, 0, 0.05),
      0 0 40px rgba(34, 197, 94, 0.2);
  border: 2px solid rgba(34, 197, 94, 0.3);
  backdrop-filter: blur(10px);
}

.benchmark-title {
  text-align: center;
  margin-top: 0 !important;
  margin-bottom: 4rem;
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--vp-c-text-1);
  position: relative;
}

.benchmark-title::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 3px;
  background: linear-gradient(90deg, #22c55e, #4ade80);
  border-radius: 2px;
}

.bench {
  margin: 0;
  padding: 0;
}

.bench a {
  color: var(--vp-c-text-1);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.bench a:hover {
  color: #22c55e;
  text-decoration: underline;
}

/* Static progress bars */
.cronflow-bar {
  width: 0.4%;
}

.make-bar {
  width: 67%;
}

.n8n-bar {
  width: 50%;
}

.zapier-bar {
  width: 100%;
}

.benchmark-details {
  margin-top: 2rem;
  padding: 1rem;
  background: var(--vp-c-bg-soft);
  border-radius: 12px;
  border: 1px solid var(--vp-c-divider);
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

.detail-item {
  margin-bottom: 0.25rem;
  font-size: 0.8rem;
  color: var(--vp-c-text-2);
  line-height: 1.3;
}

.detail-item:last-child {
  margin-bottom: 0;
}

.detail-item strong {
  color: var(--vp-c-text-1);
}

/* Developer Experience Section */
.developer-experience-section {
  margin: 2rem auto 4rem auto;
  padding: 3rem 2rem 4rem 2rem;
  max-width: 1200px;
}

.dx-content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.dx-text {
  text-align: center;
  max-width: 900px;
  margin: 0 auto;
}

.dx-features-container {
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
}

.dx-text h2 {
  font-size: 2.2rem;
  font-weight: 700;
  color: var(--vp-c-text-1);
  margin-bottom: 1.5rem;
  line-height: 1.2;
  background: linear-gradient(135deg, var(--vp-c-text-1) 0%, rgba(34, 197, 94, 0.8) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.dx-text > p {
  font-size: 1.1rem;
  color: var(--vp-c-text-2);
  line-height: 1.6;
  margin-bottom: 0;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

.dx-features {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  margin-top: 0;
}

.dx-feature {
  background: var(--vp-c-bg-soft);
  border: 1px solid var(--vp-c-divider);
  border-radius: 12px;
  padding: 1.5rem;
  text-align: left;
  transition: all 0.25s;
}

.dx-feature:hover {
  border-color: var(--vp-c-brand);
}

.dx-feature-icon {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
  border-radius: 6px;
  background-color: var(--vp-c-default-soft);
  width: 48px;
  height: 48px;
  font-size: 24px;
  transition: background-color 0.25s;
}

.dx-feature-content h4 {
  font-size: 1rem;
  font-weight: 600;
  color: var(--vp-c-text-1);
  margin: 0 0 0.5rem 0;
  line-height: 1.4;
}

.dx-feature-content p {
  font-size: 0.875rem;
  color: var(--vp-c-text-2);
  line-height: 1.6;
  margin: 0;
}

.dx-terminal {
  position: relative;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Terminal styles for DX section */
.dx-terminal .terminal {
  background: #161b22;
  color: #d1d5db;
  border-radius: 8px;
  width: 100%;
  min-height: 500px;
  box-shadow: 0 0 30px rgba(0, 0, 0, 0.6);
  overflow: hidden;
  margin: 0 auto;
}

.dx-terminal .terminal-header {
  background: #1f2937;
  padding: 8px 12px;
  display: flex;
  align-items: center;
  gap: 6px;
}

.dx-terminal .dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  display: inline-block;
}

.dx-terminal .dot.red {
  background: #ff5f56;
}

.dx-terminal .dot.yellow {
  background: #ffbd2e;
}

.dx-terminal .dot.green {
  background: #27c93f;
}

.dx-terminal .terminal-body {
  padding: 20px;
  min-height: 280px;
  position: relative;
  text-align: left;
}

.dx-terminal .output {
  white-space: pre-wrap;
  line-height: 1.4em;
}

.dx-terminal .press-enter-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: none;
  justify-content: center;
  align-items: center;
  z-index: 10;
}

.dx-terminal .press-enter {
  padding: 8px 16px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 4px;
  color: #9ca3af;
  cursor: pointer;
  animation: dx-blink 1.2s infinite;
  font-size: 14px;
}

@keyframes dx-blink {
  0%, 50%, 100% {
    opacity: 1;
  }
  25%, 75% {
    opacity: 0.4;
  }
}

.dx-terminal .cursor {
  display: inline-block;
  width: 8px;
  background: #d1d5db;
  animation: dx-cursorBlink 1s infinite;
  margin-left: 2px;
}

@keyframes dx-cursorBlink {
  0%, 50% {
    opacity: 1;
  }
  51%, 100% {
    opacity: 0;
  }
}

.dx-terminal .highlight {
  color: #10b981;
  font-weight: bold;
}

/* Code syntax highlighting */
.dx-terminal .keyword {
  color: #ff7b72;
}

.dx-terminal .string {
  color: #a5d6ff;
}

.dx-terminal .comment {
  color: #8b949e;
  font-style: italic;
}

.dx-terminal .function {
  color: #d2a8ff;
}

.dx-terminal .variable {
  color: #ffa657;
}

.dx-terminal pre {
  background: transparent;
  color: #e6edf3;
  padding: 0;
  border-radius: 0;
  margin: 10px 0 0 0;
  overflow-x: auto;
  white-space: pre;
  font-family: 'SF Mono', Monaco, 'Inconsolata', 'Roboto Mono', Consolas, 'Courier New', monospace;
  font-size: 14px;
  line-height: 1.5;
  max-height: 350px;
  overflow-y: auto;
}

/* Responsive design */
@media (max-width: 768px) {
  .performance-benchmark {
      margin: 1rem;
      padding: 1.5rem;
  }
  
  .bench {
      font-size: 11px;
      line-height: 16px;
  }
  
  .bench > div > div {
      left: 100px !important;
  }
  
  .bench > div > div[style*="right: 100%"] {
      width: 100px !important;
  }
  
  .developer-experience-section {
    margin: 1rem 1rem 2rem 1rem;
    padding: 2rem 1rem 3rem 1rem;
  }
  
  .dx-content {
    gap: 2.5rem;
  }
  
  .dx-text h2 {
    font-size: 1.8rem;
  }
  
  .dx-text > p {
    font-size: 1rem;
  }
  
  .dx-features {
    grid-template-columns: 1fr;
    gap: 1rem;
  }
  
  .dx-feature {
    padding: 1.25rem;
  }
  
  .dx-terminal .terminal {
    min-height: 400px;
  }
}
</style>

<script>
// Ensure this only runs on the client side
if (typeof window !== 'undefined') {
  let dxTerminalInitialized = false;
  let dxTerminalObserver = null;

  function initDXTerminal() {
    if (dxTerminalInitialized) return;
    
    const commandText = "$ nano workflow.js";
    const typedTextEl = document.getElementById("dx-typedText");
    const pressEnterEl = document.getElementById("dx-pressEnter");
    const pressEnterOverlayEl = document.getElementById("dx-pressEnterOverlay");
    const terminalEl = document.getElementById("dx-terminal");
    
    console.log('Trying to init DX terminal...', { typedTextEl, pressEnterEl, pressEnterOverlayEl });
    
    if (!typedTextEl || !pressEnterEl || !pressEnterOverlayEl || !terminalEl) {
      // Elements not ready yet, try again in 100ms
      setTimeout(initDXTerminal, 100);
      return;
    }
    
    dxTerminalInitialized = true;
    console.log('DX Terminal initializing...');
    
    const outputEl = typedTextEl.parentElement;

    const workflowCode = `<span class="keyword">import</span> { <span class="variable">cronflow</span> } <span class="keyword">from</span> <span class="string">'cronflow'</span>;
<span class="keyword">import</span> { <span class="variable">z</span> } <span class="keyword">from</span> <span class="string">'zod'</span>;

<span class="comment">// Define AI customer service workflow</span>
<span class="keyword">const</span> <span class="variable">customerServiceAI</span> = <span class="variable">cronflow</span>.<span class="function">define</span>({
  <span class="variable">id</span>: <span class="string">'ai-customer-service'</span>,
  <span class="variable">name</span>: <span class="string">'AI Customer Service Automation'</span>
});

<span class="comment">// Webhook trigger for incoming support tickets</span>
<span class="variable">customerServiceAI</span>
  .<span class="function">onWebhook</span>(<span class="string">'/support/ticket'</span>, {
    <span class="variable">schema</span>: <span class="variable">z</span>.<span class="function">object</span>({
      <span class="variable">ticketId</span>: <span class="variable">z</span>.<span class="function">string</span>(),
      <span class="variable">customerEmail</span>: <span class="variable">z</span>.<span class="function">email</span>(),
      <span class="variable">message</span>: <span class="variable">z</span>.<span class="function">string</span>(),
      <span class="variable">priority</span>: <span class="variable">z</span>.<span class="function">enum</span>([<span class="string">'low'</span>, <span class="string">'medium'</span>, <span class="string">'high'</span>])
    })
  })
  .<span class="function">step</span>(<span class="string">'analyze-sentiment'</span>, <span class="keyword">async</span> (<span class="variable">ctx</span>) => {
    <span class="keyword">const</span> <span class="variable">sentiment</span> = <span class="keyword">await</span> <span class="variable">openai</span>.<span class="function">analyzeSentiment</span>(<span class="variable">ctx</span>.<span class="variable">payload</span>.<span class="variable">message</span>);
    <span class="keyword">return</span> { <span class="variable">sentiment</span>, <span class="variable">confidence</span>: <span class="variable">sentiment</span>.<span class="variable">confidence</span> };
  })
  .<span class="function">step</span>(<span class="string">'generate-response'</span>, <span class="keyword">async</span> (<span class="variable">ctx</span>) => {
    <span class="keyword">const</span> <span class="variable">response</span> = <span class="keyword">await</span> <span class="variable">openai</span>.<span class="function">generateResponse</span>({
      <span class="variable">message</span>: <span class="variable">ctx</span>.<span class="variable">payload</span>.<span class="variable">message</span>,
      <span class="variable">sentiment</span>: <span class="variable">ctx</span>.<span class="variable">last</span>.<span class="variable">sentiment</span>,
      <span class="variable">customerData</span>: <span class="keyword">await</span> <span class="function">getCustomerHistory</span>(<span class="variable">ctx</span>.<span class="variable">payload</span>.<span class="variable">customerEmail</span>)
    });
    <span class="keyword">return</span> <span class="variable">response</span>;
  })
  .<span class="function">if</span>(<span class="string">'needs-human-review'</span>, (<span class="variable">ctx</span>) => <span class="variable">ctx</span>.<span class="variable">last</span>.<span class="variable">confidence</span> < <span class="variable">0.8</span>)
  .<span class="function">humanInTheLoop</span>({
    <span class="variable">timeout</span>: <span class="string">'2h'</span>,
    <span class="variable">description</span>: <span class="string">'Customer service review required'</span>,
    <span class="variable">onPause</span>: <span class="keyword">async</span> (<span class="variable">ctx</span>, <span class="variable">token</span>) => {
      <span class="keyword">await</span> <span class="function">notifyAgent</span>(<span class="variable">ctx</span>.<span class="variable">payload</span>.<span class="variable">ticketId</span>, <span class="variable">token</span>);
    }
  })
  .<span class="function">else</span>()
  .<span class="function">step</span>(<span class="string">'auto-approve'</span>, (<span class="variable">ctx</span>) => ({ <span class="variable">approved</span>: <span class="keyword">true</span> }))
  .<span class="function">endIf</span>()
  .<span class="function">step</span>(<span class="string">'send-response'</span>, <span class="keyword">async</span> (<span class="variable">ctx</span>) => {
    <span class="keyword">await</span> <span class="function">sendEmail</span>({
      <span class="variable">to</span>: <span class="variable">ctx</span>.<span class="variable">payload</span>.<span class="variable">customerEmail</span>,
      <span class="variable">subject</span>: <span class="string">'Re: Support Ticket #'</span> + <span class="variable">ctx</span>.<span class="variable">payload</span>.<span class="variable">ticketId</span>,
      <span class="variable">body</span>: <span class="variable">ctx</span>.<span class="variable">steps</span>[<span class="string">'generate-response'</span>].<span class="variable">output</span>.<span class="variable">message</span>
    });
    <span class="keyword">return</span> { <span class="variable">sent</span>: <span class="keyword">true</span>, <span class="variable">timestamp</span>: <span class="keyword">new</span> <span class="function">Date</span>() };
  })
  .<span class="function">action</span>(<span class="string">'update-crm'</span>, <span class="keyword">async</span> (<span class="variable">ctx</span>) => {
    <span class="keyword">await</span> <span class="variable">crm</span>.<span class="function">updateTicket</span>(<span class="variable">ctx</span>.<span class="variable">payload</span>.<span class="variable">ticketId</span>, {
      <span class="variable">status</span>: <span class="string">'resolved'</span>,
      <span class="variable">aiHandled</span>: <span class="keyword">true</span>,
      <span class="variable">sentiment</span>: <span class="variable">ctx</span>.<span class="variable">steps</span>[<span class="string">'analyze-sentiment'</span>].<span class="variable">output</span>.<span class="variable">sentiment</span>
    });
  });`;

    let cmdIndex = 0;

    function typeCommand() {
      console.log('Typing character:', cmdIndex, commandText[cmdIndex]);
      if (cmdIndex < commandText.length) {
        typedTextEl.textContent += commandText[cmdIndex];
        cmdIndex++;
        setTimeout(typeCommand, 60);
      } else {
        console.log('Typing complete, showing press enter button');
        setTimeout(() => {
          pressEnterOverlayEl.style.display = "flex";
        }, 300);
      }
    }

    function showCode() {
      pressEnterOverlayEl.style.display = "none";
      const cursor = document.getElementById("dx-cursor");
      if (cursor) cursor.remove();

      // Hide the typed command text
      typedTextEl.style.display = "none";

      const pre = document.createElement("pre");
      const code = document.createElement("code");
      code.innerHTML = workflowCode;
      pre.appendChild(code);
      outputEl.appendChild(pre);
    }

    // Start typing on load
    setTimeout(typeCommand, 1000);

    // Handle click and Enter key
    pressEnterEl.addEventListener("click", showCode);
    document.addEventListener("keydown", (e) => {
      if (e.key === "Enter" && pressEnterOverlayEl.style.display === "flex") {
        showCode();
      }
    });
  }

  // Setup intersection observer for lazy loading
  function setupDXTerminalObserver() {
    const terminalSection = document.querySelector('.developer-experience-section');
    
    if (!terminalSection) {
      // Try again later if section not ready
      setTimeout(setupDXTerminalObserver, 100);
      return;
    }
    
    const observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting && !dxTerminalInitialized) {
            console.log('DX Terminal section is visible, initializing...');
            initDXTerminal();
            observer.unobserve(entry.target);
          }
        });
      },
      {
        threshold: 0.1, // Trigger when 10% of the section is visible
        rootMargin: '50px' // Start loading 50px before it comes into view
      }
    );
    
    observer.observe(terminalSection);
    dxTerminalObserver = observer;
  }

  // Initialize when DOM is ready
  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', setupDXTerminalObserver);
  } else {
    // DOM is already loaded
    setTimeout(setupDXTerminalObserver, 100);
  }

  // Also try when the page is fully loaded
  window.addEventListener('load', function() {
    setTimeout(setupDXTerminalObserver, 500);
  });
}
</script>
