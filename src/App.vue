<template>
  <img alt="Vue logo" src="./assets/logo.png">
  
  <div class="container">
    <input class="input-bar" type="text" v-model="inputTodo" v-on:keyup.enter="onEnter" placeholder="What do u need to do...">
    <!-- component -->
    <Todo :todosProps="this.todos" @deleteTodo="deleteInTodo($event)" @doneCheck="doneCheck($event)"/>
  </div>

</template>

<script>
// import SearchBar from './components/Search.vue';
import Todo from './components/Todo.vue';

export default {
  name: 'App',
  components: {
    Todo
  },
  data(){
    return{
      inputTodo:'',
      todos:[
      {
        id:1,
        name:'Cong viec 1',
        done:false,
      },
      {
        id:2,
        name:'Cong viec 2',
        done:false,
      },
      {
        id:3,
        name:'Cong viec 3',
        done:false,
      },
      {
        id:4,
        name:'Cong viec 4',
        done:false,
      }
    ],
    }
  },
  methods:{
    onEnter(){ 
      this.todos.push({ id:Math.floor(Math.random()*100),
          name:this.inputTodo,
          done:false
        });
      this.inputTodo='';

    },
    deleteInTodo(event){
      const index = this.todos.findIndex(x => x.id ===event);
      this.todos.splice(index, 1); 
    }, 
    doneCheck(event){
      const index = this.todos.findIndex(x => x.id ===event);
      this.todos[index].done=!this.todos[index].done;
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container{
  margin:auto;
  width: 50%;
  padding:12px;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  border-radius:4px;
}

.input-bar{
  padding:8px;
  width:70%;
  font-size: 20px;
}

</style>
