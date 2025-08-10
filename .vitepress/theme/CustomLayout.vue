<script setup>
import DefaultTheme from "vitepress/theme";
import TerminalHero from "./components/TerminalHero.vue";

const { Layout } = DefaultTheme;
</script>

<template>
  <Layout>
    <template #home-hero-image>
      <div class="custom-hero-content">
        <TerminalHero />
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
