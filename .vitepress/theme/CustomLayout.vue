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
            <span class="platform-name">Make.com</span>
            <div class="slider-container">
              <div class="slider-placeholder"></div>
              <div class="slider-progress make-progress"></div>
            </div>
            <span class="time-label">3.5s</span>
          </div>

          <div class="benchmark-item">
            <span class="platform-name">n8n</span>
            <div class="slider-container">
              <div class="slider-placeholder"></div>
              <div class="slider-progress n8n-progress"></div>
            </div>
            <span class="time-label">4s</span>
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
              Cronflow runs on a free Oracle VPS (1vCPU, 1GB RAM) at $0/month,
              while Make.com ($16/month Pro), n8n ($50/month Pro), and Zapier
              ($19.99/month Pro) run on cloud platforms.
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
  animation-duration: 1s;
}

.make-progress {
  animation-duration: 4s;
}

.n8n-progress {
  animation-duration: 5s;
}

.zapier-progress {
  animation-duration: 8s;
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

.make-progress {
  --target-width: 25%;
}

.n8n-progress {
  --target-width: 30%;
}

.zapier-progress {
  --target-width: 100%;
}
</style>
