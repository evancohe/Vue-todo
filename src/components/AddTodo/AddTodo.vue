<template>
  <div>
    <form @submit.prevent="addTodo">
      <input
        class="todo-input"
        type="text"
        v-model="title"
        placeholder="What do you need to do"
        required
      /><br />

      <input class="add-btn" value="Submit" type="submit" />
    </form>
  </div>
</template>

<script>
// import { v4 as uuidv4 } from "uuid";

export default {
  name: "AddTodo",
  data() {
    return {
      title: "",
    };
  },
  props: ["todos"],
  methods: {
    addTodo: function () {
      const newTodo = {
        title: this.title,
        completed: false,
      };
      this.$emit("add-todo", newTodo);
      this.title = "";
    },
  },
};
</script>

<style>
</style>