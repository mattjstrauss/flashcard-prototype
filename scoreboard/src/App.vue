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
      const maxId = Math.max.apply(Math, this.quizzes.map(function(q) {return q.id}));
      const nextId = maxId + 1;
      this.quizzes.push({
        id: nextId,
        title: newQuiz.title,
        description: newQuiz.description,
        cards: []
      });
    }
  },
  data () {
    return {
      quizzes: [{
        id: 1,
        title: 'Chapter 1',
        description: 'This is a sample description.',
        cards: [
          {
            id: 1,
            term: "Some Word",
            definition: 'Some definition',
          },
          {
            id: 2,
            term: "Another Word",
            definition: 'Some other definition'
          }
        ]
      },
      {
        id: 2,
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
