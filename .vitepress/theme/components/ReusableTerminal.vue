<template>
  <div class="terminal">
    <div class="terminal-header">
      <span class="dot red"></span>
      <span class="dot yellow"></span>
      <span class="dot green"></span>
    </div>
    <div class="terminal-body">
      <div class="output">
        <span :id="outputId"></span
        ><span v-if="showCursor" class="cursor"></span>
      </div>
      <div class="press-enter-overlay" :id="overlayId">
        <div class="press-enter" :id="buttonId">[ Press Enter ]</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";

const props = defineProps({
  commandText: {
    type: String,
    required: true,
  },
  content: {
    type: Array,
    required: true,
  },
  mode: {
    type: String,
    default: "logs", // 'logs' or 'code'
  },
  terminalId: {
    type: String,
    required: true,
  },
});

const showCursor = ref(true);
const outputId = `typedText-${props.terminalId}`;
const overlayId = `pressEnterOverlay-${props.terminalId}`;
const buttonId = `pressEnter-${props.terminalId}`;

onMounted(() => {
  const typedTextEl = document.getElementById(outputId);
  const pressEnterEl = document.getElementById(buttonId);
  const pressEnterOverlayEl = document.getElementById(overlayId);
  const outputEl = document.querySelector(`#${outputId}`).parentElement;

  let cmdIndex = 0;

  function typeCommand() {
    if (cmdIndex < props.commandText.length) {
      typedTextEl.textContent += props.commandText[cmdIndex];
      cmdIndex++;
      setTimeout(typeCommand, 60);
    } else {
      setTimeout(() => {
        pressEnterOverlayEl.style.display = "flex";
      }, 300);
    }
  }

  function showContent() {
    pressEnterOverlayEl.style.display = "none";
    showCursor.value = false;
    const cursor = document.querySelector(".cursor");
    if (cursor) cursor.remove();

    if (props.mode === "code") {
      // Show code content
      const pre = document.createElement("pre");
      pre.style.cssText = `
        background: #0d1117;
        color: #e6edf3;
        padding: 20px;
        border-radius: 8px;
        margin-top: 10px;
        overflow-x: auto;
        white-space: pre;
        font-family: 'SF Mono', Monaco, 'Inconsolata', 'Roboto Mono', Consolas, 'Courier New', monospace;
        font-size: 14px;
        line-height: 1.5;
        max-height: 400px;
        overflow-y: auto;
      `;

      const code = document.createElement("code");
      code.innerHTML = props.content.join("\n");
      pre.appendChild(code);
      outputEl.appendChild(document.createElement("br"));
      outputEl.appendChild(pre);
    } else {
      // Show logs content
      let i = 0;
      function nextLine() {
        if (i < props.content.length) {
          if (
            i === props.content.length - 1 &&
            props.content[i].includes("%c")
          ) {
            const span = document.createElement("span");
            span.innerHTML =
              props.content[i].replace("%c", '<span class="highlight">') +
              "</span>";
            outputEl.appendChild(document.createElement("br"));
            outputEl.appendChild(span);
          } else {
            outputEl.appendChild(document.createElement("br"));
            outputEl.appendChild(document.createTextNode(props.content[i]));
          }
          i++;
          setTimeout(nextLine, 20);
        }
      }
      setTimeout(nextLine, 150);
    }
  }

  // Start typing on load
  typeCommand();

  // Handle click
  pressEnterEl.addEventListener("click", showContent);

  // Handle Enter key only when this terminal's overlay is visible
  const handleKeyDown = (e) => {
    if (e.key === "Enter" && pressEnterOverlayEl.style.display === "flex") {
      showContent();
    }
  };

  document.addEventListener("keydown", handleKeyDown);
});
</script>

<style scoped>
.terminal {
  background: #161b22;
  color: #d1d5db;
  border-radius: 8px;
  width: 100%;
  height: 100%;
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

/* Syntax highlighting for code */
:deep(pre code) {
  color: #e6edf3;
}

:deep(.keyword) {
  color: #ff7b72;
}

:deep(.string) {
  color: #a5d6ff;
}

:deep(.comment) {
  color: #8b949e;
  font-style: italic;
}

:deep(.function) {
  color: #d2a8ff;
}

:deep(.variable) {
  color: #ffa657;
}
</style>
