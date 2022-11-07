<template>
   <div class="hello">
     <h2>Please make your choice!</h2>
     <h3>{{ question }}</h3>
     <div>
       <input
         type="radio"
         v-model="choice"
         v-bind:value="answer1"
         v-on:change="choiceMade"
       />
       <label>{{ answer1 }}</label>
     </div>
     <div>
       <input
         type="radio"
         v-model="choice"
         v-bind:value="answer2"
         v-on:change="choiceMade"
       />
       <label>{{ answer2 }}</label>
     </div>
   </div>
 </template>
 <script>
 export default {
   name: 'WouldYouRather',
   // these are the properties that can be passed to the child component
   props: {
     question: String,
     answer1: String,
     answer2: String,
     id: Number,
   },
   data() {
     return {
       choice: ''
     }
   },
   methods: {
     choiceMade() {
       this.$emit('answer-changed', this.choice, this.id) // pass choice & id for tracking over to app.vue
     }
   }
 }
 </script>
 <style scoped>
 h3 {
   margin: 40px 0 0;
 }
 ul {
   list-style-type: none;
   padding: 0;
 }
 li {
   display: inline-block;
   margin: 0 10px;
 }
 a {
   color: #42b983;
 }
 </style>
 