<template>
  <div id="app">
    
    <quiz-list v-bind:quizzes="quizzes"></quiz-list>
    <create-quiz v-on:create-quiz="createQuiz"></create-quiz>

  </div>
</template>

<script>

import QuizList from './components/QuizList';
import CreateQuiz from './components/CreateQuiz';

export default {
  name: 'App',
  components: {
    QuizList,
    CreateQuiz
  },
  methods: {
    createQuiz(newQuiz) {
      this.quizzes.push({
        title: newQuiz.title,
        description: newQuiz.description,
        cards: []
      });
    }
  },
  data () {
    return {
      quizzes: [{
        title: 'Chapter 1',
        description: 'This is a sample description.',
        cards: [
          {
            term: "Some Word",
            definition: 'Some definition'
          }
        ]
      },
      {
        title: 'Chapter 2',
        description: 'This is a another sample description.',
        cards: [
         
        ]
      }]
    }
  }
}
</script>

<style>
#app {
  margin-top: 60px;
}
</style>
