<template>
  <div id="app">
    <div class="container">
      <div class="card">
        <Header />
        <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
        <AddTodo v-on:add-todo="addNewTodo" />
      </div>
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import Header from "./components/layout/Header";
import axios from "axios";

export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete("https://jsonplaceholder.typicode.com/todos/${id}")
        .then(() => (this.todos = this.todos.filter((todo) => id !== todo.id)))
        .catch((err) => {
          console.log(err);
        });
    },
    addNewTodo({ title, completed }) {
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((err) => {
          console.log(err);
        });
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=20")
      .then((res) => {
        this.todos = res.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@200;400;500;700&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  line-height: 1.4;
  font-family: "Poppins", sans-serif;
  background-color: #e4f5ef;
}

.container {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vw;
}
.card {
  width: 40%;
  background-color: white;
  border-radius: 6px;
  box-shadow: 0 4px 15px rgb(0 0 0 / 5%);
  padding: 10px;
}
</style>
