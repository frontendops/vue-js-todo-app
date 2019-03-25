<template>
  <div>
    <form @submit="addTodo" class="todo-form">
      <input type="text" v-model="title" placeholder="Add Todo">
      <input type="submit" value="submit" class="submit-btn">
    </form>

    <button class="clear-btn" @click="$emit('clear-all')">Clear All</button>
  </div>
</template>

<script>
import uuid from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: this.title,
      id: uuid.v4()
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      };

      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
  max-width: 600px;
  margin: 0 auto;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}

.submit-btn {
  background-color: #343f6d;
  color: white;
  font-size: 14px;
  text-decoration: none;
}

.clear-btn {
  margin-top: 40px;
  background-color: #687eda; /* Green */
  border: none;
  border-radius: 15px;
  color: white;
  padding: 8px 16px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.todo-form {
  margin-top: 35px;
}
</style>
