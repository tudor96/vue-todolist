<template>
  <div
    class="todo-item"
    v-bind:class="{ 'is-complete': todo.completed }"
    v-on:click="markComplete"
  >
    <div>
      <div class="custom_check"></div>
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="del">Delete</button>
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
    },
  },
};
</script>

<style scoped>
.todo-item {
  background-color: white;
  font-weight: 500;
  padding: 10px;
  margin: 10px;
  color: #6a8bad;
  cursor: pointer;
}
.is-complete {
  text-decoration: line-through 2px #dee5f8;
}
.del {
  background-color: rgb(255, 105, 105);
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 75px;
  cursor: pointer;
  float: right;
}

.del:hover {
  box-shadow: 0 4px 8px rgba(255, 105, 105, 0.623);
}
.custom_check {
  height: 10px;
  width: 10px;
  border: 2px solid;
  padding: 4px;
  margin: auto;
  margin-right: 10px;
  border-radius: 50%;
  display: inline-block;
}
.is-complete .custom_check {
  background-color: #41b983;
}
</style>
