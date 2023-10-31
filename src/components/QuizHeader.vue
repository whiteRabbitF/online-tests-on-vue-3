<script setup>

const { questionStatus, barPercentage } = defineProps([
  "questionStatus",
  "barPercentage",
]);
</script>

<template>
  <header>
    <h3>Вопрос {{ questionStatus }}</h3>
    <div class="bar">
      <div class="completion" :style="{ width: barPercentage }"></div>
    </div>
  </header>
</template>


