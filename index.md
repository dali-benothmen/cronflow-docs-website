---
layout: home
hero:
  name: "Cronflow"
  text: "The Fastest Code-First Workflow Automation Engine"
  tagline: Built with Rust + Bun for unparalleled performance. Replace complex workflow infrastructure with a single package.
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

<div class="performance-benchmark">
  <h3 class="benchmark-title">Performance Benchmark</h3>
  <figure class="bench" style="position: relative; max-width: 670px; height: 140px; font-size: 13px; line-height: 20px; margin: 0 auto; margin-top: 50px;">
    <div>
      <!-- Grid lines -->
      <div style="position: absolute; left: 0%; top: 0; width: 1px; bottom: 0; background: rgba(127, 127, 127, 0.25);"></div>
      <div style="position: absolute; left: 16.67%; top: 0; width: 1px; bottom: 0; background: rgba(127, 127, 127, 0.25);"></div>
      <div style="position: absolute; left: 33.33%; top: 0; width: 1px; bottom: 0; background: rgba(127, 127, 127, 0.25);"></div>
      <div style="position: absolute; left: 66.67%; top: 0; width: 1px; bottom: 0; background: rgba(127, 127, 127, 0.25);"></div>
      <div style="position: absolute; left: 100%; top: 0; width: 1px; bottom: 0; background: rgba(127, 127, 127, 0.25);"></div>
      <!-- Cronflow Bar -->
      <div style="position: absolute; left: 0; top: 3px; width: 0.4%; height: 14px; background: rgba(191, 191, 191, 0.2);"></div>
      <div style="position: absolute; left: 0; top: 3px; height: 14px; background: #22c55e;" class="bench-bar cronflow-bar"></div>
      <div style="position: absolute; right: 100%; top: 0px; width: 120px; height: 20px; text-align: right; white-space: nowrap; margin-right: 8px; font-weight: bold;">
          <a href="/guide/">Cronflow</a>
      </div>
      <div style="position: absolute; left: 0.4%; top: 0px; height: 20px; margin-left: 8px; font-weight: bold;" class="cronflow-time time-label">
          118ms
      </div>
      <!-- n8n Bar -->
      <div style="position: absolute; left: 0; top: 23px; width: 50%; height: 14px; background: rgba(191, 191, 191, 0.2);"></div>
      <div style="position: absolute; left: 0; top: 23px; height: 14px; background: #22c55e;" class="bench-bar n8n-bar"></div>
      <div style="position: absolute; right: 100%; top: 20px; width: 120px; height: 20px; text-align: right; white-space: nowrap; margin-right: 8px;">
          <a href="https://n8n.io/">n8n</a>
      </div>
      <div style="position: absolute; left: 50%; top: 20px; height: 20px; margin-left: 8px;" class="n8n-time time-label">
          15s
      </div>
      <!-- Make.com Bar -->
      <div style="position: absolute; left: 0; top: 43px; width: 67%; height: 14px; background: rgba(191, 191, 191, 0.2);"></div>
      <div style="position: absolute; left: 0; top: 43px; height: 14px; background: #22c55e;" class="bench-bar make-bar"></div>
      <div style="position: absolute; right: 100%; top: 40px; width: 120px; height: 20px; text-align: right; white-space: nowrap; margin-right: 8px;">
          <a href="https://make.com/">Make.com</a>
      </div>
      <div style="position: absolute; left: 67%; top: 40px; height: 20px; margin-left: 8px;" class="make-time time-label">
          20s
      </div>
      <!-- Zapier Bar -->
      <div style="position: absolute; left: 0; top: 63px; width: 100%; height: 14px; background: rgba(191, 191, 191, 0.2);"></div>
      <div style="position: absolute; left: 0; top: 63px; height: 14px; background: #22c55e;" class="bench-bar zapier-bar"></div>
      <div style="position: absolute; right: 100%; top: 60px; width: 120px; height: 20px; text-align: right; white-space: nowrap; margin-right: 8px;">
        <a href="https://zapier.com/">Zapier</a>
      </div>
      <div style="position: absolute; left: 100%; top: 60px; height: 20px; margin-left: 8px;" class="zapier-time time-label">
        1min
      </div>
      <!-- Time scale -->
      <div style="position: absolute; left: 0%; top: 84px; width: 50px; margin-left: -25px; text-align: center;">0s</div>
      <div style="position: absolute; left: 16.67%; top: 84px; width: 50px; margin-left: -25px; text-align: center;">5s</div>
      <div style="position: absolute; left: 33.33%; top: 84px; width: 50px; margin-left: -25px; text-align: center;">10s</div>
      <div style="position: absolute; left: 66.67%; top: 84px; width: 50px; margin-left: -25px; text-align: center;">20s</div>
      <div style="position: absolute; left: 100%; top: 84px; width: 50px; margin-left: -25px; text-align: center;">30s</div>
    </div>
  </figure>
  <div class="benchmark-details">
      <div class="detail-item">
          <strong>Cronflow:</strong> Free Oracle VPS (1vCPU, 1GB RAM) • $0/month
      </div>
      <div class="detail-item">
          <strong>n8n:</strong> Cloud Platform • $20/month Starter
      </div>
      <div class="detail-item">
          <strong>Make.com:</strong> Cloud Platform • $16/month Pro
      </div>
      <div class="detail-item">
          <strong>Zapier:</strong> Cloud Platform • $19.99/month Pro
      </div>
      <div class="detail-item" style="margin-top: 0.5rem; padding-top: 0.5rem; border-top: 1px solid var(--vp-c-divider);">
          <em>We ran a 12-step computational heavy workflow (No API calls).</em>
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
}
</style>
