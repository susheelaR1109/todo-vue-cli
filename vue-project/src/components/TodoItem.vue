<template>
    <div class="list-item">
        <div class="todo-item-left">
            <input type="checkbox" v-model="todo.status">
            <div v-if="!todo.editing" @dblclick="editTodo(todo)" 
                class="todo-item-label" :class="{ completed : todo.status }">
                {{ todo.title }}</div>
            <input v-else type="text" class="todo-item-edit" 
                v-model="todo.title" v-focus 
                @blur="doneEdit(todo)"  
                @keyup.enter="doneEdit(todo)"
                @keyup.esc="cancelEdit(todo)">
        </div>
        
        <div class="remove-item"
        @click="removeTodo(index)">
            &times;</div>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: {
        todo: Object,
        // status: String,
        // editing: String,
        index: Number,
        todos: {
            type: Array,
            default: []
        }
    },
    data () {
        return {
            beforeEditCache:''
        }
    },
    methods: {
        removeTodo(index) {
            this.todos.splice(index,1)
        },
        editTodo(todo){
            todo.editing = true;
            this.beforeEditCache = todo.title;
        },
        doneEdit(todo) {
            if(todo.title.trim() == ''){
                todo.title = this.beforeEditCache
            }
            todo.editing = false;
        },
        cancelEdit(todo){
            todo.title = this.beforeEditCache;
            todo.editing = false;
        }
    },
    directives: {
        focus: {
            inserted: function(el) {
                el.focus()
            }
        }
    }
}
</script>

<style lang="scss">
.list-item {
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.remove-item {
    cursor: pointer;
    margin-left: 14px;
    &:hover {
        color: black
    }
}
.todo-item-left {
    display: flex;
    align-items: center;
}
.todo-item-label {
    padding: 10px;
    border: 1px solid white;
    margin-left: 12px;
}
.todo-item-edit {
    font-size: 24px;
    color: #2c3e50;
    margin-left: 12px;
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    font-family: 'Avenir', Arial, Helvetica, sans-serif;
    &:focus {
        outline: none;
    }
}
.completed { 
    text-decoration: line-through;
    color: gray;
}
</style >