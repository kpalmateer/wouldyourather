<template>
  <div id="app">

    <h1>Would you rather...</h1>

    <!-- create a div and use v-for to loop it once for each question in the array -->
    <div v-for="question in questions" id="question">
      <!-- call answerChanged when WouldYouRatherQuestion emits a choice -->
      <!-- send the props to WouldYouRatherQuestion for the current question -->
      <would-you-rather-question
          v-on:answer-changed="answerChanged"
          :question="question"
      >
      </would-you-rather-question>
    </div>

  </div>
  <div>
    <h3>You chose:</h3>
    <!-- use v-for again to loop over the choices array and display each choice -->
    <ul>
      <li class="choice" v-for="choice in choices">{{ choice }}</li>
    </ul>
  </div>
</template>

<script>
// import the components
import WouldYouRatherQuestion from "@/components/WouldYouRatherQuestion.vue";

export default {
  // name the app
  name: 'App',
  // define the components
  components: {
    WouldYouRatherQuestion,
  },
  // create the data object/function
  data() {
    return {
      // create an array of questions
      questions: [
        {
          id: 0,
          question: 'be the author of a popular book or a musician in a band who released a popular album?',
          answer1: 'Author',
          answer2: 'Musician'
        },
        {
          id: 1,
          question: 'live on a sailboat or in a cabin deep in the woods?',
          answer1: 'Sailboat',
          answer2: 'Cabin'
        },
        {
          id: 2,
          question: 'be able to control water or fire?',
          answer1: 'Water',
          answer2: 'Fire'
        }
      ],
      // create a placeholder for the choices array
      choices: []
    }
  },
  methods: {
    // when the answer is changed, add the user's selection to the choices array
    answerChanged(choice, id) {
      // use the question ID to add the choice to the array
      // this will update the array if the answer changes, rather than just adding a new item
      this.choices[id] = choice
    }
  }
}
</script>

<style>
.choice {
  font-family: Futura,serif;
}

#question {
  background: lightcyan;
}

#app {
  font-family: Helvetica,serif;
}

body {
  background: lavenderblush;
}
</style>
