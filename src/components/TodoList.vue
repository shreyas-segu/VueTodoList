<template>
  <div>
    <TodoItem
      v-bind:key="todo.id"
      v-for="todo in todos"
      v-bind:todo="todo"
      @deleteTodo="$emit('deleteTodo',todo.id)"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  components: {
    TodoItem
  },
  props: ["todos"]
};
</script>

<style>
</style>
