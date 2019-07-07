<template>
  <div>
    <input type="checkbox" @change="markComplete" v-bind:checked="todo.completed" />
    <span class="label">{{todo.title}}</span>
    <button class="delete" @click="$emit('deleteTodo',todo.id)">X</button>
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

<style>
</style>
