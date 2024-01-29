
<template>
  <div id="app" class="container">
    <header>
      <img alt="Vue logo" class="logo" src="./assets/logo.svg"/>
      <h1>Todo App</h1>
    </header>

    <main>
      <TodoList/>
    </main>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
    name: 'App',
    components: {
      TodoList,
    },
    
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}
.container {
  max-width: 600px;
  margin: 0 auto;;
}
#app {
  color: #2c3e50;
  margin-top: 60px;
  font-size: 24px;
}

.logo {
  display: block;
  margin: 20px auto;
  height: 75px;
}
header{
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}

</style>
