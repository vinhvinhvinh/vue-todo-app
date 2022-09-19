<template>
    
    <ul  class="ul-container">
      <li class="todo-item" v-for='todo in todos' :key='todo.id'>
        <div class="flex-item">
          <span><input type="checkbox" @click="doneCheck(todo.id)"></span>
          <span :class="{ 'done': todo.done  }">{{todo.name}}</span>
          <div class="todo-del" @click="deleteTodo(todo.id)">🗑</div>
        </div>
      </li>
    </ul>
  
</template>

<script>

export default {
// eslint-disable-next-line vue/multi-word-component-names
name: 'Todo',
props:{
  todosProps:{
    type:Array,
    default(){
      return [];
    },
  },
  delete(id){
    return this.todos.filter(todo=>todo.id!==id);
  },
},
data(){
  return {
    todos:this.todosProps,
  }
},
methods:{
  deleteTodo(id){
    this.$emit('deleteTodo', id);
  },
  doneCheck(id){
    this.$emit('doneCheck', id);
  }
}
}


</script>

<style>
li{
list-style:none;
}

.ul-container{
margin:auto;
width:70%;
padding:24px;
}

.todo-item{
width:100%;
border:1px solid rgb(143, 143, 143);
padding:4px;
margin-bottom: 4px;
border-radius:4px;
background:rgb(238, 238, 238);
}

.flex-item{
display: flex;
justify-content: space-between;
}

.todo-del{
cursor:pointer;
}

.done{
text-decoration: line-through;
color: #aeaeae;;
}

</style>
