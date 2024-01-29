<template>
    <div class="todo-list">
        <TodoItem v-for="(item, index) in list" 
        :key="index"
        :title="item.title"
        />
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
    name: 'TodoList',
    components: {
        TodoItem
    },
    props: {
        list: {
            type: Array,
            default: []
        }
    }
}
</script>

<style scoped>
.todo-list {
    color: white;
    background-color: black;
    border-radius: 6px;
    padding: 10px;
}
</style>