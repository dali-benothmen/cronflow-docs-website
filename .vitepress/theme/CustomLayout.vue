<script setup>
import DefaultTheme from "vitepress/theme";

const { Layout } = DefaultTheme;
</script>

<template>
  <Layout>
    <template #home-hero-image>
      <div class="custom-hero-content">
        <div class="benchmark-container">
          <div class="benchmark-item">
            <span class="platform-name">Cronflow</span>
            <div class="slider-container">
              <div class="slider-placeholder"></div>
              <div class="slider-progress cronflow-progress"></div>
            </div>
            <span class="time-label">118ms</span>
          </div>

          <div class="benchmark-item">
            <span class="platform-name">n8n</span>
            <div class="slider-container">
              <div class="slider-placeholder"></div>
              <div class="slider-progress n8n-progress"></div>
            </div>
            <span class="time-label">15s</span>
          </div>

          <div class="benchmark-item">
            <span class="platform-name">Make.com</span>
            <div class="slider-container">
              <div class="slider-placeholder"></div>
              <div class="slider-progress make-progress"></div>
            </div>
            <span class="time-label">20s</span>
          </div>

          <div class="benchmark-item">
            <span class="platform-name">Zapier</span>
            <div class="slider-container">
              <div class="slider-placeholder"></div>
              <div class="slider-progress zapier-progress"></div>
            </div>
            <span class="time-label">1min</span>
          </div>

          <div class="benchmark-description">
            <p>
              We ran a 12-step computational heavy workflow (No API calls).
              <br />
              Cronflow runs on a free Oracle VPS (1vCPU, 1GB RAM) at $0/month,
              while Make.com ($16/month Pro), n8n ($20/month Starter), and
              Zapier ($19.99/month Pro) run on cloud platforms.
            </p>
          </div>
        </div>
      </div>
    </template>
  </Layout>
</template>

<style>
.custom-hero-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 95%;
  background: transparent;
  border-radius: 50px;
  text-align: center;

  border: 1px solid rgba(34, 197, 94, 0.2);
  backdrop-filter: blur(10px);
}

.benchmark-container {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  max-width: 425px;
}

.benchmark-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  width: 100%;
}

.platform-name {
  color: var(--vp-c-text-1);
  font-weight: 500;
  min-width: 70px;
  text-align: left;
  font-size: 0.9rem;
}

.slider-container {
  flex: 1;
  position: relative;
  height: 8px;
  background: transparent;
}

.slider-placeholder {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(127, 127, 127, 0.2);
  border-radius: 4px;
}

.slider-progress {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  background: #22c55e;
  border-radius: 4px;
  width: 0;
  animation: fillProgress 8s ease-out forwards;
}

.cronflow-progress {
  animation-duration: 0.1s;
}

.n8n-progress {
  animation-duration: 10s;
}

.make-progress {
  animation-duration: 15s;
}

.zapier-progress {
  animation-duration: 20s;
}

.time-label {
  color: var(--vp-c-text-2);
  font-size: 0.8rem;
  font-weight: 500;
  min-width: 50px;
  text-align: right;
}

.benchmark-description {
  margin-top: 1rem;
  padding-top: 1rem;
  border-top: 1px solid var(--vp-c-divider);
}

.benchmark-description p {
  color: var(--vp-c-text-2);
  font-size: 0.75rem;
  line-height: 1.4;
  margin: 0;
  text-align: left;
}

.benchmark-description a {
  color: #22c55e;
  text-decoration: none;
  font-weight: 500;
}

.benchmark-description a:hover {
  text-decoration: underline;
}

@keyframes fillProgress {
  from {
    width: 0;
  }
  to {
    width: var(--target-width);
  }
}

.cronflow-progress {
  --target-width: 4%;
}

.n8n-progress {
  --target-width: 50%;
}

.make-progress {
  --target-width: 67%;
}

.zapier-progress {
  --target-width: 100%;
}

/* Fix image container positioning */
.image-container[data-v-89d2fc22] {
  transform: none !important;
}

/* More specific selectors for build mode */
.VPHomeHero .image-container {
  transform: none !important;
}

.VPHomeHero .image-container[data-v-89d2fc22] {
  transform: none !important;
}

/* Target any image container in the hero */
.VPHomeHero .image .image-container {
  transform: none !important;
}

/* Override any transform on image containers */
div[class*="image-container"] {
  transform: none !important;
}

/* Ensure logo stays in proper position */
.VPNav .logo {
  position: relative !important;
  top: auto !important;
  bottom: auto !important;
  left: auto !important;
  right: auto !important;
  transform: none !important;
}

/* Additional build-mode specific overrides */
.VPHomeHero .image img {
  z-index: 1;
  background: white;
  border-radius: 20px;
  transform: rotate(5deg) !important;
  top: 15%;
  left: 45%;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.15), 0 8px 32px rgba(0, 0, 0, 0.1),
    0 0 40px rgba(34, 197, 94, 0.3), 0 0 80px rgba(34, 197, 94, 0.2);
  padding: 20px;
  border: 3px solid #22c55e;
}

/* Force override any VitePress default transforms */
.VPHomeHero .image-container,
.VPHomeHero .image-container *,
.VPHomeHero .image > div {
  transform: none !important;
}
</style>
