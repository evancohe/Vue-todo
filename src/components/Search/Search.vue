<template>
  <div class="todo">
    <h1>TODO</h1>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <form>
      <input
        class="search-input"
        type="text"
        placeholder="Search todos"
        required
      /><br />
      <input type="checkbox" /><span>Show completed todos</span>
    </form>
  </div>
</template>

<script>
export default { name: "Search" };
</script>

<style scoped>
.todo {
  background-color: lightgray;
}
</style>