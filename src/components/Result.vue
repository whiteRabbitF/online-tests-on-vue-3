<script setup>
import { RouterLink } from "vue-router";


const { numberOfCorrectAnswers, quizQuestionLength } = defineProps([
  "quizQuestionLength",
  "numberOfCorrectAnswers"
]);
</script>

<template>
  <div class="results">
    <p>Ваш результат...</p>

    <h1>{{ numberOfCorrectAnswers }} / {{ quizQuestionLength }}</h1>

    <RouterLink to="/">ВЕРНУТЬСЯ НА ГЛАВНУЮ</RouterLink>

  </div>
</template>

