<template>
  <div class="question-box-container">
    <div class="question-box">
    <h1 class="question" v-html="currentQuestion.question"></h1>
    <hr class="break">
    <div class="answer-container">
      <p v-for='(answer,index) in shuffledAnswers' 
      :key='index' 
      v-html="answer"
      @click="!answered ? selectAnswer(index) : ''"
      class="answer"
      :class="[answerClass(index)]">
      </p>
    </div>
    <button class="btn blue"
    @click="submitAnswer"
    :disabled="selectedIndex===null || answered===true"
    >
      Submit
    </button>
    <button class="btn green"
    @click='newQuestion'
    >Next</button>
    </div>
  </div>
</template>
<script>
export default{
  props:{
    currentQuestion:Object,
    newQuestion:Function,
    increment:Function
  },
  data(){
    return {
      selectedIndex:null,
      shuffledAnswers:[],
      correctIndex:null,
      answered:false
    }
  }, 
  methods:{
    selectAnswer(index){
      this.selectedIndex=index;
    },
    submitAnswer(){
      let isCorrect =false;
      if (this.selectedIndex===this.correctIndex){
        isCorrect=true;
      }
      this.increment(isCorrect);
      this.answered=true;
    },
    shuffleAnswers(){
      let answers=[...this.currentQuestion.incorrect_answers,this.currentQuestion.correct_answer]
      let numOfAnswers= answers.length;
      let newShuffledAnswers=[];
      for(let count=0; count<numOfAnswers;count++){
        let randomNum=Math.floor(Math.random() * answers.length);
        newShuffledAnswers.push(answers[randomNum]);
        answers.splice(randomNum,1);
      }
      this.shuffledAnswers=newShuffledAnswers
      this.correctIndex=this.shuffledAnswers.indexOf(this.currentQuestion.correct_answer)
    },
    answerClass(index){
      let answerClass=''
      if (this.answered){
        if(this.correctIndex===index){
          answerClass='correct'
        }else if(this.selectedIndex===index){
          answerClass='incorrect'
        }
      }else{
        if(this.selectedIndex===index){
          answerClass='selected'
        }
      }
      return answerClass
    }
  },
  computed:{
    answers(){
      let answers= [...this.currentQuestion.incorrect_answers]
      answers.push(this.currentQuestion.correct_answer)
      return answers
    }
  },
  watch:{
    currentQuestion:{
      immediate:true,
      handler(){
        this.selectedIndex=null;
        this.shuffleAnswers();
        this.answered=false;
      }
    }
  }
}
</script>
<style scoped>
.question-box-container{
  background-color: #EEEEEE;
}

.question-box{
  margin:20px 10vw 10px 10vw;
  background-color:#EFB7B7;
  border-radius: 3px;
  padding: 10px;
}
.question{
  font-size:2em;
  margin-bottom: 0;
}
.break{
  border: 5px dashed #000000;
  border-left: none;
  border-right: none;
  border-bottom: none;
  height:0;
  margin-bottom: 25px;
  margin-top:25px;
}

.answer-container{
  margin-bottom:25px;
}

.answer{
  background-color: #BD4B4B;
  padding: 10px;
  margin-left:auto;
  margin-right:auto;
  max-width:400px;
  margin-top:10px;
  margin-bottom:10px;
  transition: background-color 0.3s;
}

.answer:hover{
  background-color: #EEEEEE;
  cursor: pointer;
}

.answer:first-child{
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}
.answer:last-child{
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
}

.answer.selected{
  background-color: #008CBA;
}

.answer.correct{
  background-color: #4CAF50;
}

.answer.incorrect{
  background-color: #DC3546;
}

.btn{
  padding: 8px;
  margin:5px;
  font-size:1em;
  border:none;
  border-radius:3px;
  transition: background-color 0.1s;
  cursor:pointer;
}

.btn.blue{
  background-color: #008CBA;
}
.btn.blue:hover{
  background-color: #007094;
}
.btn.blue:active{
  background-color: #008CBA;
}

.btn.green{
  background-color: #4CAF50;
}
.btn.green:hover{
  background-color: #3c8c40;
}
.btn.green:active{
  background-color: #4CAF50;
}
</style>