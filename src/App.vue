<!--Main Vue app which refers TodoList.vue file from components folder -->

<template>
  <div id="app">
    <!-- image for the webpage-->
    <img src="./assets/logo.png" class="logo">

    <!-- Calling TodoList.vue from components folder 
         Instead of <TodoList/> we can also cll the file 
         using <todo-list> </todo-list> --> 
    <TodoList/>
  </div>
</template>

<!-- Declaration of all the components and their locations -->
<script>
  import TodoList from './components/TodoList'
  export default {
    name: 'App',
    components: {
      TodoList
    }
  }
</script>

<!-- Default Styling of App.vue boilerplate -->
<style>
  * {
    box-sizing: border-box;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    font-size: 150%;
    color: #2c3e50;
    margin-top: 60px;
  }

  .logo {
    display: block;
    margin: 0px auto;
    height: 80px;
  }
</style>
