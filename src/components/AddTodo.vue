<template>
  <div>
    <form @submit="addTodo">
        <input v-model="title" name="title" placeholder="AddTodo..."/>
        <input type="submit" value="submit" class="btn"/>
    </form>
  </div>
</template>

<script>
import {v4 as uuid} from 'uuid'
export default {
name: 'AddTodo',
data(){
    return{
        title: ''
    }
},
methods:{
    addTodo(e){
        e.preventDefault()
        // console.log("I was called")
    const newTodo ={
        id: uuid(),
        title: this.title,
        completed: false
    }
    if(this.title.trim() !== '')
    this.$emit('add-todo', newTodo)
    this.title = ''

    }
}
}
</script>

<style scoped>
form{
    display: flex;
}
input[type="text"]{
    flex: 1;
    padding: 5px;
}
input[type="submit"]{
    flex: 10;
}
.btn{
  display: flex;
  align-items: center;
  border: none;
  background-color: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover{
  background-color: #666;
}
</style>