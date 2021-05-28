<template>
  <div class="todo_container">
    <div v-bind:key="todo.id" v-for="todo in todos">
      <TodoItem
        v-bind:todo="todo"
        v-on:del-todo="$emit('del-todo', todo.id)"
      ></TodoItem>
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "Todos",
  props: ["todos"],
  components: {
    TodoItem,
  },
  setup() {},
};
</script>

<style scoped>
.todo_container {
  overflow-x: auto;
  max-height: 60vh;
}
</style>
