<template>
  <div class="header">
    <h1 class="title">My Quiz</h1>
    <h3 class="counter">Counter: {{numCorrect}}/{{numTotal}}</h3>
  </div>
</template>
<script>
export default{
  props:{
    numCorrect:Number,
    numTotal:Number
  }
}
</script>
<style scoped>
.header{
  background-color: #BD4B4B;
  padding: 10px;
  display: block;
  margin:0;
  text-align: left;
}
.title{
  display:inline-block;
  margin: 5px 20px 5px 0px;
  font-size:2em;
}
.counter{
  display: inline-block;
  font-size:1.5rem;
}
</style>