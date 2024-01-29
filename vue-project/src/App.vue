
<template>
  <div id="app">
    <header>
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
      <h1>Todo App</h1>
    </header>

    <main>
      <TodoList :list="tasks"/>
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
    data () {
      return {
        tasks: [
          {
            title: 'Task 1',
            status: 'pending'

          },
          {
            title: 'Task 2',
            status: 'completed'

          },
          {
            title: 'Task 3',
            status: 'pending'

          },
          {
            title: 'Task 4',
            status: 'pending'

          }
        ]
      }
    }
}
</script>

<style scoped>
header{
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 10px;
}

</style>
