<template>
  <div >
    <AddTodo v-on:add-todo="addTodo"/>
   <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
   
  </div>
</template>

<script>
import Todos from '../components/Todos.vue';

import AddTodo from '../components/AddTodo';
import axios from 'axios';
import { constants } from 'crypto';

export default {
  name: 'Home',
  components: {
    Todos, AddTodo
  },
  data(){
    return{
      todos: []
    }
  },
  methods:{
    //emit del-todo passed from Todo component which was passed from todoitem component
    deleteTodo(id){
     // console.log(id)
     //filter through and hide the todo with the id
     //this.todos = this.todos.filter(todo => todo.id !== id);
     axios.delete('https://jsonplaceholder.typicode.com/todos/${id}')
     .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
     .catch(err => console.log(err));
    },
    addTodo(newTodo){
      //console.log(newTodo);
      const { title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));
      // this.todos = [...this.todos, newTodo]; // ... is a spread operator to copy all todos to todo while adding the new todo
    }
    
    },
    created(){
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
          .then(res => this.todos = res.data)
          .catch((err) => console.log(err));
    }
}
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn{
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px, 20px;
  cursor: pointer;
}

.btn:hover{
  background: #999;
}
</style>
