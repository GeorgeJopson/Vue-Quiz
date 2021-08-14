<template>
  <div class="question-box-container">
    <div class="question-box">
    <h1 class="question">Question</h1>
    <hr class="break">
    <p>
      List of Answers
    </p>
    <button class="btn blue">Submit</button>
    <button class="btn green">Next</button>
    </div>
  </div>
</template>
<style scoped>
.question-box-container{
  background-color: #EEEEEE;
}
.question-box{
  margin:10px;
  background-color:#EFB7B7;
  border-radius: 3px;
  padding: 10px;
}
.question{
  font-size:2em;
}
.break{
  border: 5px dashed #000000;
  border-left: none;
  border-right: none;
  border-bottom: none;
  height:0;
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