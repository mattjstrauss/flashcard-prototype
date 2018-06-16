<template>
  <div>
    <div v-for="quiz in quizzes" class="ui centered card">
      <div class="content">
        <div class="header">{{quiz.title}}</div>
        <div class="meta">{{quiz.description}}</div>
      </div>
      <div class="extra content">
        <span class="left floated">
          <i class="sticky note icon"></i>
          {{quiz.cards.length}}
        </span>
      </div>
    </div>
  </div>

</template>

<script>

export default {
  props:['quizzes']
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
