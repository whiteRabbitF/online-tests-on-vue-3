<script setup>
import q from "../data/data.json";
import { ref, watch } from "vue";
import Card from "../components/Card.vue";
import gsap from "gsap";


const quizzes = ref(q);
const search = ref("");

watch(search, () => {
  quizzes.value = q.filter((quiz) =>
    quiz.name.toLocaleLowerCase().includes(search.value.toLocaleLowerCase())
  );
});

const beforeEnter = (el) => {
  console.log("before enter");
  el.style.opacity = 0;
  el.style.transform = "translateY(-60px)";
};

const enter = (el) => {
  console.log("enter");
  gsap.to(el, {
    y: 0,
    opacity: 1,
    duration: 0.5,
    delay: el.dataset.index * 0.3
  })
}
</script>

<template>
  <div>
    <header>
      <h1>Пройдите тестирование по интересующему направлению и узнайте свой уровень знаний!</h1>
      <h2>онлайн-тесты на самые популярные языки программирования</h2>
      <input v-model.trim="search" id="search" type="text" placeholder="Поиск..." />
    </header>

    <div class="options-container">
      <TransitionGroup 
        appear
        @before-enter="beforeEnter"
        @enter="enter"
      >
        <Card 
          v-for="(quiz, index) in quizzes" 
          :key="quiz.id" 
          :quiz="quiz" 
          :data-index="index"
        />
      </TransitionGroup>
    </div>
  </div>
</template>

<style scoped>
header {
  margin-bottom: 10px;
  margin-top: 30px;
  align-items: center;
}

h1{
  display: block;
  width: 1400px;
  height: 140px;
  color: #fcfcfcb6;
  background-color: #23626613;
  border-radius: 25px;
  text-align: center;
  font-size: 42pt;
  margin-left: 320px;
  padding: 20px;
}

h2 {
  display: block;
  width: 1400px;
  height: 40px;
  color: #fcfcfcb6;
  background-color: #23626613;
  border-radius: 25px;
  text-align: center;
  font-size: 30pt;
  margin-left: 320px;
  padding: 20px;
}

input {
  border: none;
  background-color: rgba(70, 67, 67, 0);
  padding: 15px 80px;
  border-radius: 5px;
  font-size: 18pt;
  color: azure;
  margin-bottom: 50px;
  margin-left: 380px;
  padding: 20px 50px;
}



.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}
</style>
