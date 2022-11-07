<template>
  <!-- template tag needs to have exactly one child element -->
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>Would you rather?</h1>
    <!-- you can use the uppercase style, but the dashes between is the convention for writing vue tagnames
         There is no valid HTML tag with dashes-->
    <!-- TODO v-for to loop over the list of questions & answers -->
    <would-you-rather
      v-for="(question) in questionsArray"
      :key="question.id"
      v-bind:question="question.wyrQuestion"
      v-bind:answer1="question.answer1"
      v-bind:answer2="question.answer2"
      v-bind:id="question.id"
      v-on:answer-changed="answerChanged"
    >
    </would-you-rather>
    <!-- 'app' is the main page, WouldYouRather is inside it,
         we need to specifiy that app should show this component-->
    <!-- create unordered list of selections -->
    <p id="ywr">You Would Rather...</p>
    <!-- loop over userSelectionsArray, put each response in an unordered list. -->
    <ul id="userSelectionsArray">
      <li v-for="(selection) in userSelectionsArray">
        {{ selection }}
      </li>
    </ul>
  </div>
</template>
<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  // Create a questions array to hold all the questions/possible answers
  data() {
    return {
      questionsArray: [
        {
          id: 0,
          question: 'Would you rather team up with Wonder Woman or Captain Marvel',
          answer1: 'Wonder Woman',
          answer2: 'Captain Marvel',
        },
        {
          id: 1,
          question:'Would you rather find true love today or win the lottery next year?',
          answer1: 'Find true love',
          answer2: 'Win the lottery',
        },
        {
          id: 2,
          question: 'Would you rather have another 10 years with your partner or a one-night stand with your celebrity crush?',
          answer1: '10 years with my partner',
          answer2: 'One night stand with my celeberity crush',
        }
      ],
      userSelectionsArray: [
      ],
    }
  },
  methods: {
    // use question IDs to update user choices-- insert them at correct index (which matches the id#)
    // replace the old response when a new choice is made for each question
      answerChanged(choice, id) {
        this.userSelectionsArray.splice(id, 1, choice)
      }

  }
}
</script>
<style>

body {
  background: thistle;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}

#ywr {
  background: mediumseagreen;
}
</style>
