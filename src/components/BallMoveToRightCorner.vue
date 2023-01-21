<template>
  <h3>綠球向右下移動</h3>
  <section class="container container-move-right-corner">
    <div class="cell" style="--t: 200px; --l: 400px"></div>
    <div class="cell"></div>
    <div class="cell cell-flash" style="--t: 200px"></div>
    <div class="cell"></div>
    <div class="cell cell-flash"></div>
    <div class="cell"></div>
    <div class="cell" style="--l: 400px"></div>
    <div class="cell"></div>
    <div class="cell cell-flash"></div>
  </section>
</template>

<style scoped>
.cell:nth-child(1):after,
.cell:nth-child(3):after,
.cell:nth-child(7):after,
.cell:nth-child(9):after {
  animation: moveToRightCorner 1.5s ease-in-out infinite;
}

@keyframes moveToRightCorner {
  0% {
    top: 50%;
    left: 50%;
  }
  100% {
    top: calc(100% + var(--t, 0px));
    left: calc(100% + var(--l, 0px));
  }
}
</style>
