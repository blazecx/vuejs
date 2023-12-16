<script>
export default{
  data(){
    return{
      // todo
      todo: "",
      todos: [],
      isDone: false,
      id: 0,

    }
  },

  methods:{
    // todo
    addTodo(){

      this.todos.push({id: this.id,
         text: this.todo,
         isComlpete: this.isDone
      });
      this.todo = "";

    },
    removeTodo(index){
      console.log(index);
      this.todos.splice(index, 1)
    },
  }
}
</script>

<template>

<h1 class="title">Todo app</h1>
  <div class="wrap">
    <p>{{ todo }}</p>
    <input type="text" v-model="todo" placeholder="text">
    <button @click="addTodo(id++)">add todo</button>
    <div v-for="(todo, index) in todos" :key="todo">
      <span class="todoId">{{ index }}. </span>
      <span class="todoText "  :class="{todoIsShow: todo.isComlpete}" @dblclick="removeTodo(index)"> {{ todo.text }}</span>
      <input type="checkbox" v-model="todo.isComlpete">
      <button @click="updateTodo(index, todo.text)"></button>
    </div>
  </div>
</template>

<style scoped>
.title{
  text-align: center;
}
.wrap{
  border: 1px solid black;
  height: 250px;
  width: 250px;
}

.todoId{
  color: red;
}

.todoText{
  margin-left: 5px;
  text-transform: capitalize;

}
  .todoIsShow{
    color: blue;
    text-decoration: line-through;
  }


</style>
