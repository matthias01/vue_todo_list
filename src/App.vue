<template>
  <div id="app">
   <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
   
  </div>
</template>

<script>
import Todos from './components/Todos.vue';
export default {
  name: 'app',
  components: {
    Todos,
  },
  data(){
    return{
      todos: [
        {
          id: 1,
          title: 'Todo 1',
          completed: false
        },
         {
          id: 2,
          title: 'Todo 2',
          completed: true
        },
         {
          id: 3,
          title: 'Todo 3',
          completed: false
        }
      ]
    }
  },
  methods:{
    deleteTodo(id){
     // console.log(id)
     //filter through and hide the todo with the id
    }
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
</style>
