<template>
  <div id="app">
    <Header/>
    <QuestionBox/>
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
