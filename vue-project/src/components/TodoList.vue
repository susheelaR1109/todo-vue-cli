<template>
    <div>
        <input type=" text" class="todo-input" 
        placeholder="What needs to be done" 
        v-model="newTodo" @keyup.enter="addTodo">
        <div class="todo-item">
            <TodoItem v-for="(todo, index) in todos" 
            :key="todo.id"
            :todo="todo"
            :index="index"
            :todos="todos"
            />
        </div>
    </div>
    
</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
    name: 'TodoList',
    data () {
        return {
            newTodo: '',
            idForTodo:3,
            todos: [
            {
                'id':1,
                'title': 'Task 1',
                'status': false,
                'editing': false,
            },
            {
                'id':2,
                'title': 'Task 2',
                'status': false,
                'editing': false,
            },
            ]
        }
    },
    methods: {
        addTodo() {
            if(this.newTodo.trim().length == 0){
                return
            }
            this.todos.push({
                id: this.idForTodo,
                title: this.newTodo,
                completed: false,
            })
            this.newTodo=''
            this.idForTodo++
        },
        // removeTodo(index) {
        //     this.todos.splice(index,1)
        // }
    },
    components: {
        TodoItem
    },
    props: {
        // list: {
        //     type: Array,
        //     default: []
        // }
    }
}
</script>

<style lang="scss">
.todo-input {
    width: 100%;
    padding: 10px 18px;
    font-size: 18px;
    margin-bottom: 16px;

    &:focus {
        outline: 0;
    }
}
.todo-list {
    color: white;
    background-color: black;
    border-radius: 6px;
    padding: 10px;
}

</style>