<template>
  <div class="terminal">
    <div class="terminal-header">
      <span class="dot red"></span>
      <span class="dot yellow"></span>
      <span class="dot green"></span>
    </div>
    <div class="terminal-body">
      <div class="output">
        <span id="typedText"></span><span class="cursor"></span>
      </div>
      <div class="press-enter-overlay" id="pressEnterOverlay">
        <div class="press-enter" id="pressEnter">[ Press Enter ]</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from "vue";

onMounted(() => {
  const commandText = "$ node workflow.js";
  const typedTextEl = document.getElementById("typedText");
  const pressEnterEl = document.getElementById("pressEnter");
  const pressEnterOverlayEl = document.getElementById("pressEnterOverlay");
  const outputEl = document.querySelector(".output");

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

  let cmdIndex = 0;

  function typeCommand() {
    if (cmdIndex < commandText.length) {
      typedTextEl.textContent += commandText[cmdIndex];
      cmdIndex++;
      setTimeout(typeCommand, 60);
    } else {
      setTimeout(() => {
        pressEnterOverlayEl.style.display = "flex";
      }, 300);
    }
  }

  function printLogs() {
    pressEnterOverlayEl.style.display = "none";
    const cursor = document.querySelector(".cursor");
    if (cursor) cursor.remove();

    let i = 0;
    function nextLine() {
      if (i < logLines.length) {
        if (i === logLines.length - 1) {
          const span = document.createElement("span");
          span.innerHTML =
            logLines[i].replace("%c", '<span class="highlight">') + "</span>";
          outputEl.appendChild(document.createElement("br"));
          outputEl.appendChild(span);
        } else {
          outputEl.appendChild(document.createElement("br"));
          outputEl.appendChild(document.createTextNode(logLines[i]));
        }
        i++;
        setTimeout(nextLine, 20);
      }
    }
    setTimeout(nextLine, 150);
  }

  // Start typing on load
  typeCommand();

  // Handle click and Enter key
  pressEnterEl.addEventListener("click", printLogs);
  document.addEventListener("keydown", (e) => {
    if (e.key === "Enter") printLogs();
  });
});
</script>

<style scoped>
.terminal {
  background: #161b22;
  color: #d1d5db;
  border-radius: 8px;
  width: 100%;
  height: 90%;
  max-width: 650px;
  box-shadow: 0 0 30px rgba(0, 0, 0, 0.6);
  overflow: hidden;
  margin: 0 auto;
}

.terminal-header {
  background: #1f2937;
  padding: 8px 12px;
  display: flex;
  align-items: center;
  gap: 6px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  display: inline-block;
}

.dot.red {
  background: #ff5f56;
}

.dot.yellow {
  background: #ffbd2e;
}

.dot.green {
  background: #27c93f;
}

.terminal-body {
  padding: 20px;
  min-height: 280px;
  position: relative;
  text-align: left;
}

.output {
  white-space: pre-wrap;
  line-height: 1.4em;
}

.press-enter-overlay {
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

.press-enter {
  padding: 8px 16px;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 4px;
  color: #9ca3af;
  cursor: pointer;
  animation: blink 1.2s infinite;
  font-size: 14px;
}

@keyframes blink {
  0%,
  50%,
  100% {
    opacity: 1;
  }
  25%,
  75% {
    opacity: 0.4;
  }
}

.cursor {
  display: inline-block;
  width: 8px;
  background: #d1d5db;
  animation: cursorBlink 1s infinite;
  margin-left: 2px;
}

@keyframes cursorBlink {
  0%,
  50% {
    opacity: 1;
  }
  51%,
  100% {
    opacity: 0;
  }
}

:deep(.highlight) {
  color: #10b981;
  font-weight: bold;
}
</style>
