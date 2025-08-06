<script setup>
import DefaultTheme from "vitepress/theme";

const { Layout } = DefaultTheme;
</script>

<template>
  <Layout>
    <template #home-hero-image>
      <div class="custom-hero-content">
        <h3>Custom Hero Content</h3>
        <p>This replaces the hero image</p>
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
  height: 100%;
  background: rgba(34, 197, 94, 0.1);
  border-radius: 12px;
  padding: 2rem;
  text-align: center;
}

.custom-hero-content h3 {
  color: var(--vp-c-text-1);
  margin-bottom: 1rem;
}

.custom-hero-content p {
  color: var(--vp-c-text-2);
}
</style>
