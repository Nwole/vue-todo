<template>
  <div class="todo-item" >
    <p class="para1" v-bind:class="{'is-completed': todo.completed}">
        <input type="checkbox" v-on:change="markComplete"/>
        {{todo.title}}
    </p>
    <button class="del" @click="$emit('del-todo', todo.id)">X</button>
  </div>
</template>

<script>
export default {
    name: 'TodoItems',
    props: ['todo'],
    methods:{
        markComplete(){
            this.todo.completed = !this.todo.completed
        }
    }

}
</script>

<style scoped>
.todo-item{
    background-color: '#f4f4f4';
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    display: flex;
 
}
.is-completed{
    text-decoration: line-through;
}
.del{
    background-color: #df3434;
    color: #fff;
    border: none;
    text-align: center;
    padding: 5px 9px;
    border-radius: 50px;
    cursor: pointer;
    margin-left: auto;
    width: 40px;
    height: 40px;
    border-radius: 30px; 
}

</style>