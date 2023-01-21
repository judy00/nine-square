<template>
  <h3>綠球向右移動</h3>
  <section class="container">
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell cell-flash"></div>
    <div class="cell"></div>
    <div class="cell cell-flash"></div>
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell"></div>
    <div class="cell cell-flash"></div>
  </section>
</template>

<style scoped>
.cell:nth-child(1):after,
.cell:nth-child(3):after,
.cell:nth-child(7):after,
.cell:nth-child(9):after {
  animation: moveToRight 3s ease-in-out infinite;
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
