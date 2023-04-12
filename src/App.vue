<template>
  <div id="app">

    <h1>Would you rather...</h1>
    <would-you-rather v-bind:key="question.id"
    v-for="question in questions"
    v-bind:id="question.id"
    v-bind:question="question.wyrQuestion"
    v-bind:answer1="question.wyrAnswer1"
    v-bind:answer2="question.wyrAnswer2"
    v-on:answer-changed="answerChanged">
    </would-you-rather>

    <p v-for="message in userSelectionMessages" v-bind:key="message">
    {{  message }}</p>

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      // array of question objects, three or more questions
      questions: [
        {
          id: 0,
          wyrQuestion: 'Would you rather be a fast swimmer or a fast runner?',
          wyrAnswer1: 'Fast swimmer',
          wyrAnswer2: 'Fast runner',
          userSelectionMessage: ''
        },
        {
          id: 1,
          wyrQuestion: 'Would you rather have a cat or a dog?',
          wyrAnswer1: 'Dog',
          wyrAnswer2: 'Cat',
        },
        {
          id: 2,
          wyrQuestion: 'Would you rather work remote or in the office?',
          wyrAnswer1: 'Remote',
          wyrAnswer2: 'In the office',
        },
      ],
      userSelectionMessages: []
    }
  },
  methods: {
    answerChanged(choice, wyrComponentId) {
      this.userSelectionMessages[wyrComponentId] = choice
    }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: rgb(146, 194, 233);
}

body {
  background: lightpink;
}
</style>
