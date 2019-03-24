<template>
  <div class="container">
    <div v-bind:class="{'is-complete':todo.completed}" class="item">
      <div class="item-left">
        <input type="checkbox" v-on:change="markComplete">
      </div>
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.del {
  border-radius: 100px;
  background-color: red;
  color: white;
}

.item {
  background-color: #707898;
  color: white;
  display: flex;
  padding: 10px;
  border-radius: 15px;
  max-width: 400px;
  margin: 0 auto;
  margin-top: 15px;
  justify-content: space-between;
}

.item.is-complete {
  text-decoration: line-through;
  background-color: #987078;
}

.item-left {
  display: inline;
}
</style>
