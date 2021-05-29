<template>

    <div>
        <h1>Todos</h1>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"></TodoItem>
        </div>
        </div>    
</template>
<script>
import TodoItem from './TodoItem.vue';
export default {
    name:'todos',
    // props
    props:["todos"],
    components:{
        TodoItem
    }
}
</script>
<style scoped>

</style>