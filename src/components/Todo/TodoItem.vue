<template>
  <div class="todo-item" v-bind:class="{ 'is-complete': todo.completed }">
    <input type="checkbox" v-on:change="markComplete" />
    <span>{{ todo.title }}</span>
    <button v-on:click="$emit('del-todo', todo.id)" class="del">x</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete: function () {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo-item {
  display: flex;
  flex-direction: row;
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px dotted #ccc;
}

.is-complete {
  text-decoration: line-through;
}
.del {
  background-color: lightsalmon;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>