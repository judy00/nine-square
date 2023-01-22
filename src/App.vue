<script setup>
import BallMoveToRight from "./components/BallMoveToRight.vue";
import BallMoveToRightOnTop from "./components/BallMoveToRightOnTop.vue";
import BallMoveToRightCorner from "./components/BallMoveToRightCorner.vue";
</script>

<template>
  <div class="container">
    <BallMoveToRight />
    <BallMoveToRightOnTop />
    <BallMoveToRightCorner />
  </div>
</template>

<style scoped>
.container {
  margin: auto;
  padding-top: 40px;
  padding-bottom: 40px;
}
</style>
