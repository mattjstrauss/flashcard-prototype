<template>

  <div>
    
    <quiz v-if="viewState === 'quizzes'" v-for="quiz in quizzes" :key="quiz.id" v-bind:quiz="quiz" v-on:view-quiz="viewQuiz"></quiz>
  
    <div class="ui cards" v-if="viewState === 'cards'">
      
      <flash-card v-for="card in this.selectedQuiz.cards" :key="card.id" v-bind:card="card"></flash-card>

    </div>

  </div>

</template>

<script>

import Quiz from './Quiz';
import FlashCard from './FlashCard';

export default {
  props:['quizzes'],
  components: {
    Quiz,
    FlashCard,
  },
  data() {
    return {
      selectedQuiz: {card:[]},
      viewState: "quizzes",
    }
  },
  methods: {
    viewQuiz(quiz) {
      this.selectedQuiz = quiz;
      this.viewState = "cards";
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
