<template>
  <div class="wyr">

    <h2>Please make your choice!</h2>

    <!-- show the question -->
    <h3>{{ question }}</h3>

    <!-- create two radio buttons and v-model them to the choice string in Vue data -->
    <!-- bind one to each answer, and get the text via the answer1 and answer2 props from the parent -->
    <!-- when the user selects an option, call the choiceMade method -->
    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade">
    <label>{{ answer1 }}</label>
    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2 }}</label>

  </div>
</template>

<script>
export default {
  // set the name for the component
  name: 'WouldYouRather',
  // set the props, which are received from the parent
  props: {
    question: String,
    answer1: String,
    answer2: String,
  },
  // create the data object/function
  data() {
    return {
      // create a placeholder string for choice
      choice: ''
    }
  },
  methods: {
    // create the choiceMade method
    choiceMade() {
      // send 'answer-changed' to the parent, which contains the choice string
      this.$emit('answer-changed', this.choice)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.wyr {
  border: 2px black solid;
  background-color: darkseagreen;
}
</style>
