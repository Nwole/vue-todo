<template>
  <div >
    <div v-for="todo in todos" :key="todo.id">
        <TodoItems v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItems.vue'
import TodoItems from './TodoItems.vue';
export default {
name: 'Todos',
components: {
    TodoItem,
    TodoItems
},
props: ['todos']
}
</script>

<style scoped>

</style>