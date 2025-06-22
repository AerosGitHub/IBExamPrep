<script setup lang="ts">
import terms from '../assets/jsonFiles/terms.json';
import questions from '../assets/jsonFiles/questions.json';
import { ref } from 'vue';

const questions_type_chooser = ref(true);
const displaying = ref({
  question: '',
  answer: '',
})

function termsChoose() {
  questions_type_chooser.value = false;
  const randInt = Math.floor(Math.random() * Object.keys(terms).length)
  displaying.value = {
    question: Object.keys(terms)[randInt]!,
    answer: Object.values(terms)[randInt]!,
  }
}

function questionsChoose() {
  questions_type_chooser.value = false;
  const randInt = Math.floor(Math.random() * Object.keys(questions).length)
  displaying.value = {
    question: Object.keys(questions)[randInt]!,
    answer: Object.values(questions)[randInt]!,
  }
}
</script>

<template>
  <div style="width: 100%; height: 100vh">
    <div
      v-if="questions_type_chooser"
      class="chooseType"
      :style="{
        display: 'flex',
        justifyContent: 'center',
        alignItems: 'center',
        width: '100%',
        height: '100%',
      }"
    >
      <div class="button big-button" @click="termsChoose">Термины</div>
      <div class="button big-button" @click="questionsChoose">Определения</div>
    </div>
    <div
    v-if="!questions_type_chooser"
    >
      <div></div>
      <div class="display-question">
        {{displaying.question}}
      </div>
      <div class="display-answer">
        {{displaying.answer}}
      </div>
    </div>
  </div>
</template>

<style scoped>
.button {
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 20px;
  box-shadow: rgba(156, 156, 156, 0.66) 2px 2px 10px;
  margin: 20px;
  font-size: 40px;
  transition: all 0.3s ease;
  background-color: white;
  color: black;
}

.button:hover {
  background-color: #569565;
  color: white;
}

.big-button {
  width: 400px;
  height: 100px;
}
</style>
