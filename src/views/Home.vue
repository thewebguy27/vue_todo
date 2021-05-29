<template>
  <div id="app">
  
    <AddTodos v-on:add-todo="AddTodo"></AddTodos>
 <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>

import Todos from '../components/Todos';
import AddTodos from '../components/AddTodo';
import axios from 'axios';
export default{
  name:'Home',
  components:{
    // store here todos data
    Todos,
   
    AddTodos

  },
  data(){
    // is a function that returns object
    return{
      todos:[]
    }
  }
  ,
  methods:{
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then( this.todos = this.todos.filter(todo =>todo.id !== id))
      .catch(err=>console.log(err))
     
    },
    AddTodo(newTodo){
      const {title,complete}=newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos',{
        title,
        complete
      })
      .then(response=>this.todos=[...this.todos,response.data])
      .catch(err=>console.log(err))
      
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(response=>this.todos = response.data)
    .catch(err=>console.log(err))
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
}
 .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
</style>
