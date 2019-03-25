<template>
  <div id="app">
    <Header/>
    <Todos v-bind:todos="todos" v-on:del-todo="handleTodoDel"/>
    <AddTodo v-on:add-todo="handleAddTodo" v-on:clear-all="clearAll"/>
    <TotalTasks/>
  </div>
</template>



<script>
import Todos from "./components/Todos";
import Header from "./components/layout/Header";
import AddTodo from "./components/AddTodo";
import TotalTasks from "./components/TotalTasks";

export default {
  name: "app",
  components: {
    Todos,
    Header,
    AddTodo,
    TotalTasks
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Shower",
          completed: false
        },
        {
          id: 2,
          title: "Study",
          completed: false
        },
        {
          id: 3,
          title: "Work",
          completed: false
        }
      ]
    };
  },
  methods: {
    handleTodoDel(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    handleAddTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
    clearAll() {
      this.todos = [];
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
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
