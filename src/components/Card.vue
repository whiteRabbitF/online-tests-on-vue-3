<script setup>

import { useRouter } from "vue-router";

const router = useRouter();
const { quiz } = defineProps(["quiz"]);

const navigateToQuiz = () => {
  router.push(`/quiz/${quiz.id}`);
};

</script>

<template>
  <div class="quiz-cards">
  <div @click="navigateToQuiz" class="card">
    <img :src="quiz.img" alt=""/>
    <div class="card-text">
      <h2>{{ quiz.name }}</h2>
      <p class="num-of-questions">{{ quiz.questions.length }} вопросов</p>
    </div>
  </div>
</div>
</template>
