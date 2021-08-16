<template>
  <div class="question-box-container">
    <div class="question-box">
    <h1 class="question" v-html="currentQuestion.question"></h1>
    <hr class="break">
    <div class="answer-container">
      <p v-for='(answer,index) in answers' :key='index' class="answer" v-html="answer">
      </p>
    </div>
    <button class="btn blue">Submit</button>
    <button class="btn green" @click='next'>Next</button>
    </div>
  </div>
</template>
<script>
export default{
  props:{
    currentQuestion:Object,
    next:Function
  },
  computed:{
    answers(){
      let answers= [...this.currentQuestion.incorrect_answers]
      answers.push(this.currentQuestion.correct_answer)
      return answers
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
}

.answer:first-child{
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}
.answer:last-child{
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
}

.btn{
  padding: 8px;
  margin:5px;
  font-size:1em;
  border:none;
  border-radius:3px;
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