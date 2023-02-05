<script setup>
import { ref, onMounted } from "vue";

const containerRefs = ref(null);
const cellRefs = ref([]);

onMounted(() => {
  const containerRect = containerRefs.value.getBoundingClientRect();
  const moveBallIndex = [0, 2, 6, 8];

  moveBallIndex.forEach((idx) => {
    const targetCell = cellRefs.value[idx];
    const cellRect = targetCell.getBoundingClientRect();
    const offsetX = containerRect.right - cellRect.right;
    const offsetY = containerRect.bottom - cellRect.bottom;
    targetCell.style.cssText = `--top: ${offsetY}px; --left: ${offsetX}px`;
  });
});
</script>

<template>
  <h3>綠球向右下移動</h3>
  <section ref="containerRefs" class="container container-move-right-corner">
    <div
      v-for="cell in 9"
      :key="cell"
      :class="['cell', { 'cell-flash': [3, 5, 9].includes(cell) }]"
      ref="cellRefs"
    />
  </section>
</template>

<style scoped>
.cell-flash {
  background: transparent;
  background: radial-gradient(
    circle,
    rgba(113, 81, 95, 0.6) 81%,
    rgba(0, 0, 0, 1) 100%
  );
}

.cell-flash:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: radial-gradient(
    circle,
    rgba(113, 81, 95, 1) 81%,
    rgba(0, 0, 0, 1) 100%
  );
  animation: flash 1s ease-in-out infinite;
}

.cell:nth-child(1):after,
.cell:nth-child(3):after,
.cell:nth-child(7):after,
.cell:nth-child(9):after {
  animation: moveToRightCorner 1.5s ease-in-out infinite;
}

@keyframes flash {
  0% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes moveToRightCorner {
  0% {
    top: 50%;
    left: 50%;
  }
  100% {
    top: calc(100% + var(--top, 0px));
    left: calc(100% + var(--left, 0px));
  }
}
</style>
