<template>
  <h3>綠球向右移動、不被遮蓋</h3>
  <section class="container">
    <div
      v-for="cell in 9"
      :key="cell"
      :class="['cell', { 'cell-flash': [3, 5, 9].includes(cell) }]"
    />
  </section>
</template>

<style scoped>
/* 閃爍格子 */
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
  animation: moveToRight 3s ease-in-out infinite;
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

@keyframes moveToRight {
  0% {
    left: 50%;
  }
  100% {
    left: calc(50% + 500px);
  }
}
</style>
