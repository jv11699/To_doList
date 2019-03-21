<template>
  <div id="app">
    <Header />
     <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos = "sort()" v-on:del-todo="deleteTodoItem"/>
  </div>
</template>

<script>
import Todos from './components/Todos';
import Header from './components/layout/Header';
import AddTodo from './components/AddTodo';
export default {
  name: 'app',
  components: {
     Header,
     Todos,
     AddTodo
  },
    data(){
      return {
          todos: [
              { //these are testing
                 id: 1,
                 title: "Todo One",
                 completed: false,
                 date:  3,
                 delete: false
              },
              {
                  id: 2,
                  title: "Todo Two",
                  completed: false,
                  date: 4,
                  delete: false
              },
              {
                  id: 3,
                  title: "todo three",
                  completed: true,
                  date: 1,
                  delete: false

              }
          ]
      }
    },
    methods:{
      deleteTodo(id){
          //filter a high order function

          this.todos = this.todos.filter(todo => todo.id !== id);

      },
      deleteTodoItem(id){
          setTimeout(this.deleteTodo.bind(null,id),700);
      },
      addTodo(newTodo){

          //it adds to a portion before the checked ones
          for(var i =0; i < this.todos.length; i++){
              if(this.todos[i].completed){
                  break;
              }
          }
          //inserts the new todo before a complete one
          newTodo.title != ''?this.todos.splice(i,0,newTodo): alert("You Must Type in Something");
      },
        sort(){
          /*   SORTS THE ITEMS ACCORDINGLY
             for(var i = 0; i < this.todos.length; i++){
                    if(this.todos[i].completed){
                        var temp = {id: this.todos[i].id,title: this.todos[i].title, completed:false}
                        //this.todos.splice(i,1);
                        this.todos.push(temp)
                    }
                }*/
                return this.todos;
            }
    }


}

</script>

<style>
  *{
    box-sizing: border-box;
    margin: 12px;
    padding: 0;
  }
  body{
    font-family: Arial, Melvetica, sans-serif;
    text-align: center;
    line-height: 1.4;
    overflow-x: hidden;
  }
  .btn{
      display: inline-block;
      border: none;
      background: #555;
      color: #fff;
      padding: 7px 20px;
      cursor: pointer;
  }
  .btn:hover{
      background: #666;
  }
</style>
