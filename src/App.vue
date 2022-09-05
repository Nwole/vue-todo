<template>
  <div class="container">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Header from './components/Layout/Header.vue'
import AddTodo from './components/AddTodo.vue'
import Todos from './components/Todos.vue'
import axios from 'axios'
export default {
  name: 'App',
  data(){
    return{
      todos:[]
    }
  },

  methods:{
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => this.todos = this.todos.filter((todo) => todo.id !==id)
)
      .catch(error => console.log(error))
    },
    addTodo(newTodo){
      const{id, title, completed} = newTodo
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => {
        const data = {...res.data, id}
        // console.log(data)
        this.todos = [...this.todos, data]
        }
)
      .catch(error => console.log(error))
    }
  },

  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
   .then(res => this.todos = res.data)
   .catch(error => console.log(error))
  },
  components: {
    Todos,
    Header,
    AddTodo
}
}
</script>

<style scoped>
.container{
  width: 40%;
  margin: auto;
}
body{
font-family: Arial, Helvetica, sans-serif;
line-height: 1.4;
}

</style>
