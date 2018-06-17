<template>

  <div>

    <transition name="fade" mode="out-in">

      <div v-if="viewState === 'quizzes'" key="quizzes">
    
        <quiz v-bind:id="'quiz_' + quiz.id" v-for="quiz in quizzes" :key="quiz.id" v-bind:quiz="quiz" v-on:view-quiz="viewQuiz" v-on:delete-quiz="deleteQuiz"></quiz>

      </div>

      <div v-if="viewState === 'cards'" key="cards">

        <button class="ui labeled icon button back" v-on:click="viewQuizzes">
          
          <i class="arrow circle left icon"></i>
          
          Back

        </button>
  
        <div id="card-view" class="ui cards">
    
          <flash-card v-for="card in this.selectedQuiz.cards" :key="card.id" v-bind:card="card"></flash-card>

        </div>

      </div>

    </transition>

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
      selectedQuiz: {cards:[]},
      viewState: "quizzes",
    }
  },
  methods: {
    viewQuiz(quiz) {
      this.selectedQuiz = quiz;
      this.viewState = "cards";
      this.$emit('change-state', {
        viewState: "cards",
        activeQuiz: quiz.id
      });
    },
    viewQuizzes() {
      this.viewState = "quizzes",
      this.$emit('change-state', {
        viewState: "quizzes",
        activeQuiz: 0
      });
    },
    deleteQuiz(quiz) {
      const quizId = quiz.id;
      const parent = this;

      $('#quiz_' + quizId).fadeOut('slow', function() {
        const quizIndex = parent.quizzes.indexOf(quiz);
        parent.quizzes.splice(quizIndex, 1);
      });

    }
  }
}

</script>

<style>

.fade-enter-active,
.fade-leave-active {
  transition: .5s ease opacity;
}

.fade-enter,
.fade-leave-to {
 opacity: 0; 
}

#card-view {
  margin: 30px 0 0;
}
</style>
