<template>
  <div id="app">
    <Header
    :numCorrect='numCorrect'
    :numTotal='numTotal'
    />
    <QuestionBox
    v-if='questions.length'
    :currentQuestion='questions[index]'
    :newQuestion='newQuestion'
    :increment='increment'
    />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import QuestionBox from './components/QuestionBox.vue'
export default {
  name: 'App',
  components: {
    Header,
    QuestionBox
  },
  data(){
    return{
      questions: [],
      index:0,
      numCorrect:0,
      numTotal:0,
      questionCount:0
    }
  },
  methods: {
    increment(isCorrect){
      if(isCorrect){
        this.numCorrect++;
      }
      this.numTotal++;
    },
    newQuestion(){
      this.index++;
      this.questionCount++;
      if(this.questionCount%10==0){
        this.moreQuestions();
      }
    },
    moreQuestions(){
      fetch('https://opentdb.com/api.php?amount=10&category=18&type=multiple',{
        method:'get'
      }).then((response) =>{
        return response.json()
      }).then((jsonData)=>{
        this.questions= jsonData.results
      });
      this.index=0;
    }
  },
  mounted: function(){
    this.moreQuestions();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  margin-top: 0;
  background-color: #EEEEEE;
  height:100%;
}
</style>
