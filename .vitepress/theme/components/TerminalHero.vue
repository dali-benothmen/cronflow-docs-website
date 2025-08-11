<template>
  <ReusableTerminal
    :command-text="'$ node workflow.js'"
    :content="logLines"
    mode="logs"
    terminal-id="hero"
  />
</template>

<script setup>
import ReusableTerminal from "./ReusableTerminal.vue";

const logLines = [
  "Step 1: Fetching customer orders from API...",
  "Step 2: Validating payment status...",
  "Step 3: Checking inventory levels...",
  "Step 4: Processing order fulfillment...",
  "Step 5: Generating shipping labels...",
  "Step 6: Sending confirmation emails...",
  "Step 7: Updating analytics dashboard...",
  "Step 8: Triggering inventory restock alerts...",
  "✔ E-commerce automation completed successfully.",
  "%cExecuted in 118ms | Memory usage: 54MB 🚀",
];
</script>
