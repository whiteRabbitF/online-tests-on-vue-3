<script setup>

const { question } = defineProps(["question"]);
const emit = defineEmits(["selectOption"]);

const emitSelectedOption = (isCorrect) => {
  emit("selectOption", isCorrect);
};
</script>

<template>
  <div class="question-container">
    <h1 class="question">
      {{ question.text }}
    </h1>
  </div>

  <div class="options-container">
    <div
      v-for="option in question.options"
      :key="option.id"
      @click="emitSelectedOption(option.isCorrect)"
      class="option"
    >
      <p class="option-label">{{ option.label }}</p>
      <div class="option-value">
        <p class="variants">{{ option.text }}</p>
      </div>
    </div>
  </div>
</template>

