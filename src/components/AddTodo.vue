<template>
  <form @submit="addTodo" class="container_buttons">
    <input type="text" v-model="title" name="title" class="input" />
    <input type="submit" value="+ New Todo" class="button" />
  </form>
</template>

<script>
// import { uuid } from "vue-uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        // id: uuid.v1(),
        title: this.title,
        completed: false,
      };
      this.$emit("add-todo", newTodo);
      this.title = "";
    },
  },
};
</script>

<style scoped>
.container_buttons {
  padding-top: 20px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: -25px;
}
.button {
  color: white;
  background-color: #42b983;
  border: 0;
  border-radius: 75px;
  padding: 10px 20px;
  box-shadow: 0 4px 15px #41b983c7;
  font-size: 16px;
  height: 40px;
}
.input {
  color: #42b983;
  border: 2px solid #42b983;
  background-color: white;
  border-radius: 75px;
  padding: 10px 20px;
  margin-right: 10px;
  flex: 1;
  box-shadow: 0 4px 15px rgb(0 0 0 / 5%);
  max-height: 40px;
  font-size: 16px;
}
</style>
