<template>
  <div class="wyr">

    <!-- show the question from the parent -->
    <p>Would you rather {{ question.question }}</p>

    <!-- create two radio buttons and v-model them to the choice string in Vue data -->
    <!-- bind one to each answer -->
    <!-- when the user selects an option, call the choiceMade method -->
    <input type="radio" v-model="choice" v-bind:value="question.answer1" v-on:change="choiceMade">
    <label class="answer">{{ question.answer1 }}</label>
    <input type="radio" v-model="choice" v-bind:value="question.answer2" v-on:change="choiceMade">
    <label class="answer">{{ question.answer2 }}</label>

  </div>
</template>

<script>

export default {
  // name the component
  name: "WouldYouRatherQuestion",
  props: {
    // define the question prop as an object
    question: Object,
  },
  data() {
    return {
      // placeholder for choice
      choice: '',
    }
  },
  methods: {
    choiceMade() {
      // send the choice and question ID back to the parent when a selection is made
      this.$emit('answer-changed', this.choice, this.question.id)
    }
  }
}
</script>

<style scoped>
.answer {
  font-family: Futura,serif;
}
</style>