<template>
    <div class="list-item">
            <div class="task-title">{{ title }}</div>
            <button>Add</button>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: {
        title: String,
        status: String
    }
}
</script>

<style scoped>

</style >