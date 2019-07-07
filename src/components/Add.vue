<template>
  <div>
    <input type="text" v-model="title" placeholder="Add todo...." />
    <button @click="addTodo">Add</button>
  </div>
</template>

<script>
export default {
  name: "Add",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        id: Math.floor(Math.random() * 999),
        title: this.title,
        completed: false
      };
      this.$emit("addTodoEvent", newTodo);
      this.title = "";
    }
  }
};
</script>

<style>
</style>
