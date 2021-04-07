<template>
  <div id="app">
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <AddTodo v-on:add-todo="addTodo" />
  </div>
</template>

<script>
import Todos from "../components/Todo/Todos";
import AddTodo from "../components/AddTodo/AddTodo";
import axios from "axios";
export default {
  name: "Home",
  components: { Todos, AddTodo },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo: function (id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(
          (res) =>
            (this.todos = this.todos.filter((todo) => todo.id !== id, res.data))
        )
        .catch((err) => console.log(err));
    },
    addTodo: function (newTodo) {
      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((err) => console.log(err));
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px auto;
  width: 70%;
}
</style>
